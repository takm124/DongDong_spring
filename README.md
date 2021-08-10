# DongDong

같은 동네에서 거래가능한 중고거래 웹사이트를 제작했습니다.

현존하는 중고거래 사이트들의 기본적인 기능에 좀 더 판매자 친화적인 기능을 더하여 구현했습니다.

판매자가 구매의사가 없는 사람과의 대화를 하지 않아도 되도록 "주문서"개념을 추가했습니다. 구매 의사가 있는 구매자가 주문서를 작성해 판매자에게 보내면, 판매자는 주문서를 보고 팔고싶은 사람을 선택해 1:1대화를 시작할 수 있습니다.



## 기술스택

- FrontEnd : JSP, css, javascript, bootstrap, ajax
- BackEnd : Java(8), Spring, MyBatis, Oracle, Maven
- Server : Tomcat



## 역할분배

- SeongHo Shin : PM, 1:1채팅, 소셜로그인, 웹 훅
- SangBeen Lee : 회원정보(마이페이지), 소셜로그인, 페이지보안(SSL)
- JaeHee Ahn : 게시글 CRUD, 멀티파일 업로드, 카테고리/키워드 검색, 끌올기능, 실시간 알림
- GiDong Du : 게시글 CRUD, 댓글기능, 관리자페이지, 데이터 통계작업
- MinSeok Jang : 메인페이지(페이징, 관심목록 위젯)
- SungSu Park : 회원가입 

## 실행방법

## SSL 적용방법
## 개발 테스트용으로 공인인증기관이 아닌 내가 인증기관 인거처럼 작업
   인증기관용 개인키 를 만들고, 웹브라우저에 설치될 루트 인증서도 만들어 사용
  
  필요한 파일은 cert 폴더에 압축하여 업로드.(keystore, .crt ...)
  keypass 는 "dongdong" 로 동일하게 적용.
  
  1. Tomcat 설정
    - server.xml 에 <Connector connectionTimeout="20000" port="8079" protocol="HTTP/1.1" redirectPort="8443"/> 바로 아래에
  <Connector SSLEnabled="true" clientAuth="false" keystoreFile="keystore 파일위치" keystorePass="dongdong" maxThreads="150" port="8443" protocol="org.apache.coyote.http11.Http11Protocol" scheme="https" secure="true" sslProtocol="TLS"/> 추가.
  
  2. 사설 root 인증서 설치 
    IE 웹브라우저
      1. IE 웹 브라우저에서 도구 ⇒ 인터넷 옵션 ⇒ 내용 ⇒ 인증서를 클릭.
      2. 신뢰할 수 있는 루트 인증기관 탭에서 "가져오기" 를 실행하여 앞에서 만든 rootca.crt 를 가져오기.
    크롬 브라우져 
      1. 설정 ⇒ 개인정보 및 보안 ⇒ 인증서 관리 에서 추가가능 


## 기능설명

### 비회원

- 게시글 열람 가능
- 카테고리, 키워드 검색 시 최근 글부터 확인 가능(별도의 필터링 없음)



### 회원

- 소셜 로그인
  - 카카오, 구글, 네이버
- 게시글 CRUD
  - 최대 5장의 사진까지 업로드 가능
- 마이페이지
  - 우리동네 인증(Kakao Map API 사용)
  - 회원 정보 수정
  - 거래내역
  - 작성글 보기
  - 주문요청함, 알림함
- 찜하기
- 댓글, 대댓글 작성
- 주문서 보내기(구매자)
  - 가격, 거래장소, 전달내용 작성해서 판매자에게 전송
- 신고하기
  - 부적절한 게시글, 댓글 신고 시 관리자페이지에서 확인하여 처리가능
- 실시간 알림
  - 댓글, 대댓글, 주문서도착 시 toast창으로 실시간 알림 확인
- 채팅
  - 판매자가 주문서를 보고 거래하고 싶을 때 채팅버튼을 클릭해 1:1대화를 시작할 수 있음
- 끌올(판매자)
  - 3일 간격 총 3번 게시글 끌어올리기 가능



### 관리자

- 통계 정보 확인
  - 글 등록 건수, 거래완료 건수, 회원가입 건수, 신고 건수별 통계 그래프로 확인 가능
  - 통계 기간으로 조회가능
  - 실시간 트랜잭션 비율 조회가능
- 신고 관리 및 계정 정지
  - 신고 내역 확인 후 계정정지 및 게시글,댓글 삭제
  - 회원의 제재 정보 조회 가능

