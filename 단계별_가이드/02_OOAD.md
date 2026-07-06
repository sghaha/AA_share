# Phase 2. OOAD 실습 (원본 4.2) — 누가 무엇을 하는가

> [← Phase 1 요구공학](01_요구공학.md) · [인덱스](README.md) · [다음: Phase 3 아키텍처 설계 →](03_아키텍처설계.md)

## 🧭 이 단계가 의미하는 것
시스템을 **"누가(Actor) 무엇을(Use Case) 한다"** 로 구조화하는 단계입니다. 기능 요구사항을 그림 한 장(Use Case Diagram)으로 정리해 **시스템의 경계와 범위를 확정**합니다.

의미상 이건 "기능 요구사항의 시각화"입니다. Phase 1이 문장·시나리오였다면, Phase 2는 **행위자 관점의 지도**를 그려서 이해관계자와 팀이 "이 시스템이 무엇을 하는 물건인지" 한눈에 합의하게 만듭니다. 이 UC들이 뒤에서 설계 대상의 단위가 됩니다.

## 🎯 목표(Output)
- Actor 목록 + 각 Actor Description
- Use Case Diagram
- Use Case 목록
- UC 명세서 2~3개 (Basic Flow 중심) / (optional) Sequence Diagram

## 📐 인증과제 설계서 어디에 들어가나
> 설계서 **3장 Architectural Driver → 3.1 Use Case Model** (3.1.1 Diagram, 3.1.2 Actor List, 3.1.3 Use Case List, 3.1.4~ UC 명세서).

## 👥 담당(3인)
- **팀원 B (리드)**: Actor·Use Case Diagram 총괄 + 제조/알림 UC
- **팀원 A**: 주문/결제 UC 상세
- **팀원 C**: 보안/권한(RBAC) UC
> UC별 병렬 작성 → B가 다이어그램으로 통합.

## ✅ 세부 진행 아이템

### [EX-1] Actor 도출
1. **Actor 식별** — 시스템과 직접 상호작용하는 대상. Phase 0의 System Context Diagram 외부 엔티티와 **일치시킨다**(설계서 점검기준). 예: 고객, 매장 직원, 매장 관리자, 시스템 관리자, 외부 결제 시스템, 외부 알림 시스템, AI 추론 엔진.
2. **Actor Description** — 각 Actor의 역할을 *구체적 행위* 로 기술. "고객: 매장 검색·주문 생성·결제·픽업 알림 수신…"
3. (선택) **Actor 일반화** — 공통 역할이 있으면 상위 Actor로 묶는다.

### [EX-2] Use Case Model
4. **Use Case 식별** — 각 Actor가 시스템에서 얻는 결과 단위로. 예: 매장 검색, 주문 생성, 결제 처리, 주문 접수, 제조 상태 변경, 픽업 알림 발송, 메뉴 관리, AI 예측 조회.
5. **Use Case Diagram 작성** — Actor–UC 연관선 연결.
6. **관계 평가** — `<<include>>`(필수 공통 기능, 예: "주문 생성" ⊃ "재고 검증"), `<<extend>>`(선택 확장, 예: "결제" ⟵ "쿠폰 적용")를 타당한 곳에만.

### [EX-3] UC 명세서
7. **UC 2~3개 선택** — 아키텍처적으로 중요한 핵심 흐름을 고른다. **추천: "주문 생성→결제→접수→제조완료→픽업 알림"** (Graceful Degradation·데이터 일관성·알림 연동이 다 걸림).
8. **명세 작성** — 각 UC에 대해:
   - Scenario List: 기본 흐름 / 선택 흐름 / 예외 흐름
   - 사전조건(Pre) · 사후조건(Post)
   - Step(단계별 흐름) — Basic Flow 중심 상세
9. (optional) **Sequence Diagram** — Actor·시스템·외부(결제/알림/AI) 간 상호작용을 시간순으로.

## 📎 참고자료
- [설계서 양식](../../../certification/SW아키텍처인증과제_설계서양식_작성가이드_20260625_convert.md) — 3.1 전체(다이어그램 작성법, `<<include>>`/`<<extend>>` 비교표, Actor/UC List·명세서 표 형식·작성사례). **이 단계는 양식의 예시가 특히 풍부하니 반드시 참고.**
- [요구사항 원문](<../AI기반 카페 모바일 오더 및 픽업 알림 시스템 구축_20260705_revised_convert.md>) — 2.2 주문 상태 8종, 2.3 주문 처리 흐름 7단계(= UC 시나리오의 뼈대)
- Phase 0의 System Context Diagram (Actor 일치 확인용)

## 💡 작성 팁 · 자주 하는 실수
- **UC 이름은 "동사+목적어" 결과 중심.** "주문 관리"(모호) → "주문 생성", "제조 완료 처리"(명확).
- `<<include>>`와 `<<extend>>` 남용 금지 — 진짜 필수 공통/선택 확장에만. 설계서 Table 8(비교표)로 판단.
- UC를 너무 잘게 쪼개지 말 것. **Actor가 원하는 결과 한 덩어리**가 UC 하나.
- 선택한 2~3개 UC는 Phase 3 설계·Phase 4 패턴의 실습 대상과 연결되게 고른다(예: 결제 UC → Phase 4 "결제수단 확장" 패턴).

## ☑️ 완료 체크리스트
- [ ] Actor 목록 + Description (Context Diagram과 일치)
- [ ] Use Case Diagram (`<<include>>`/`<<extend>>` 포함)
- [ ] Use Case 목록 (관련 System Feature ID 연결)
- [ ] UC 명세서 2~3개 (기본/선택/예외 흐름, Pre/Post)
- [ ] (optional) Sequence Diagram

---
> [← Phase 1 요구공학](01_요구공학.md) · [인덱스](README.md) · [다음: Phase 3 아키텍처 설계 →](03_아키텍처설계.md)
