# LIVELY

통장잔고2조의 LIVELY

함께 살아가는 생동감있는 지역 커뮤니티입니다. <br>
메인페이지에 실시간 위치기반의 교통량이 표시된 지도 api를 가져왔습니다.

▫ 제가 담당한 파트(회원관련 페이지 ,질문 게시판 )의 구현코드입니다.

- 회원 controller
  https://github.com/sopiabung/LIVELY/blob/main/FinalProjectLively/src/main/java/com/lively/member/controller/MemberController.java
- 회원 service 
  https://github.com/sopiabung/LIVELY/blob/main/FinalProjectLively/src/main/java/com/lively/member/service/MemberService.java
- 회원 mapper (쿼리문) <br> 
  https://github.com/sopiabung/LIVELY/blob/main/FinalProjectLively/src/main/resources/mybatis/mapper/member-mapper.xml  
- 질문 게시판 controller 
  https://github.com/sopiabung/LIVELY/blob/main/FinalProjectLively/src/main/java/com/lively/query/controller/QueryController.java
- 질문게시판 service 
  https://github.com/sopiabung/LIVELY/blob/main/FinalProjectLively/src/main/java/com/lively/query/service/QueryService.java
- 질문게시판 mapper (쿼리문) 
  https://github.com/sopiabung/LIVELY/blob/main/FinalProjectLively/src/main/resources/mybatis/mapper/query-mapper.xml

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
<details>
<summary>회원가입</summary>
<div markdown="1">

```java
	// 회원가입 화면
	@GetMapping("join")
	public String join(LocationVo locationVo, Model model) {
//		회원가입 화면에 지역데이터 넣을때 파라미터로 "LocationVo locationVo" 넣기
      List<LocationVo> locationList = ms.getLocationList(locationVo);
      
      model.addAttribute("locationList" , locationList);

		return "member/join";
		}

	// 회원가입 처리
	@PostMapping("join")
	public String join(MemberVo vo,Model model, HttpSession session, LocationVo locationVo) throws Exception {
		
		List<LocationVo> locationList = ms.getLocationList(locationVo);
		model.addAttribute("locationList", locationList);
		
		// 서비스
		int result = ms.join(vo);

		
		if (result != 1) {
			// 에러메세지 담아서 forwording 하기
			session.setAttribute("alertMsg", "회원가입 실패");
			return "member/join";
		}
		session.setAttribute("alertMsg", "회원가입완료! 로그인 해주세요 :)");
		return "redirect:/member/login";

	}// join

	// 아이디 중복확인
	@PostMapping("id-check") // url은 케밥케이스로
	@ResponseBody // 문자 그대로 반환되도록
	public String idCheck(String id) {

		int result = ms.checkId(id);

		if (result > 0) {
			return "isDup";
		} else {
			return "notDup";
		}
	}// idCheck
```
</div>
</details>

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

# 정연우
🙌🏼 현재의 자리에 안주하기보다는 성장을 고집합니다. 긍정에너지로 꿋꿋이 나아가겠습니다.
<br>
- 포트폴리오 : https://happynoo.notion.site/94e651c43c624e31a5098f0c35594143?pvs=4
- 공부기록 : [https://happynoo.notion.site/Programing-933f4fd792754e82b6b70404aac521b3?pvs=4](https://www.notion.so/Programing-933f4fd792754e82b6b70404aac521b3?pvs=21)
- KH정보교육원 개발자 양성과정 직업훈련 수료 (2022.11 ~2023.6)
- 숭실대학교 실용음악학과 4년제 학사 졸업 (2014.03 ~ 2018.02) 
- 컴퓨터 활용능력 2급 취득 
 
## Skill

> JAVA
Spring framework / Servlet / Mybatis
JDBC / Oracle sql developer
JSTL / EL
Ajax
> 

> JavaScript HTML CSS
jQuery
JSP

읽어주셔서 감사합니다!
좋은하루 되세요 😊
