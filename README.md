# 🎇FINAL PROJECT - 🎇

### 00. 프로젝트 개요

> 한 학기 동안 배운 모든 내용을 종합한 영화 커뮤니티 사이트 개발



- #### 목표

  - 영화 정보 기반 추천 서비스 
  - 커뮤니티 서비스

  

- #### 팀원 정보 & 역할

| 이름   | 직위 | 역할     |
| ------ | ---- | -------- |
| 임지성 | 팀장 | Backend  |
| 이승아 | 팀원 | Frontend |



- #### 개발 환경

  - 언어
    - Python 3.7.7
    - Django 
    - Node 14.15.0
    - Vue.js 2.6+
  - 도구
    - vsCode
    - Chrome Browser
  - 아키텍처
    - Django REST API 서버 & Vue.js



---

### 01. UI 설계

> 카카오 Oven을 이용하여 웹페이지 레이아웃을 설계했다. 
>
> 목업을 팀원과 공유하여, 백엔드 담당 팀원 입장에서 보다 수월하게 데이터 구성을 할 수 있도록했다. 

![image-20201119200445724](README.assets/image-20201119200445724.png)

---

### 02. 컴포넌트 구조 설계

> 웹페이지 레이아웃에 따라 기능별 컴포넌트를 구분하고, 각 기능마다 컴포넌트의 구조를 설계했다.

![image-20201126145954973](README.assets/image-20201126145954973.png)

- Accounts : 회원가입, 로그인
- SideNavbar : 각 기능들로 이동할 수 있는 navbar
  - Home : 영화 검색, 영화 정보, 리뷰 확인, 추천 점수
  - Mypage : 다른 유저 검색, 개인 프로필, 작성한 리뷰, 팔로우
  - Community : 영화 필터링, 리뷰 작성, 확인, 수정, 삭제, 댓글 작성, 삭제, 좋아요
  - Analytics : 작성한 리뷰 기반 평가성향, 선호하는 장르, 팔로우한 유저 기반 영화 추천

---

### 03. 기능 구현

#### 1) `Accounts` : Signup / Login

> User 인증 서비스를 구현했다. 
>
> 회원가입과 로그인을 통해 인증해야 각 페이지에 접근할 권한을 가지게 된다. (Home 제외) 
>
> 

![image-20201126151533298](README.assets/image-20201126151533298.png)

```vue
<script>
// 생략
export default {
  // 생략
  data: function () {
    return {
      credentials: {
        username: "",
        password: "",
        passwordConfirmation: "",
      },
    };
  },
  methods: {
    signup: function () {
      axios
        .post(`${SERVER_URL}/accounts/signup/`, this.credentials)
        .then(() => {
          this.$router.push({ name: "Login" });
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>
```



- auto indent (진짜..최고의 기능)

`Shift` + `Alt` + `F`

----

### 04. 기타 추가 기능

#### 1) Scroll Top 버튼

> 웹페이지 기능상 세로로 길게 출력되는 경우가 많았다.
>
> 사용자의 편의를 위해 화면의 최상단으로 보내주는 버튼을 만들었다.  
>
> 응용하면 컴포넌트가 생성됐을 때, 화면 가장 위로 보내주는 기능도 만들 수 있다. 



```vue
<script>
created: function () {
  window.scrollTo(0, 0);
},
</script>
```





#### 