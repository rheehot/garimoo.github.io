﻿---
layout: post
title: "Performance Testing Guidance for Web Applications Chapter 2"
---
<br/>

이 글은 Microsoft의 Performance Testing Guidance for Web Applications 에 대한 글로, **직역과 오역이 다분히 많고, 저의 개인적인 생각을 추가하여 정리한 글** 임을 서두에 밝힙니다.

## Part 2 - Exemplar Performance Testing Approaches

### Chapter 4 - Web Application Performance Testing Core Activities
![Image](./assets/chap4.PNG)
 - 성능 테스트는 **일률적으로** 또는 **가장 적합한 방식으로** 적용할 수 없는 복잡한 활동이다. 서비스 별로 공통적으로 수행할 수 있는 작업이 거의 없다.

#### 7가지의 가장 중요한 테스팅 활동

##### __Activity 1. Identify the Test Environment__

- 먼저 테스트를 수행하는 환경과 성능 테스트를 실행하는 데에 필요한 도구 및 관련 하드웨어로 **테스트 환경을 구성** 한다.
- 환경 구성이 테스트의 결과에 영향을 끼치는 것은 당연할 뿐더러, 그 환경 자체가 테스트의 목적이 되기도 한다.
 - 새 하드웨어를 적용하는 것이 성능에 얼마나 영향을 끼치는 지를 알아보기 위해 테스트를 진행하기도 한다.
- 테스트 환경 구성의 가장 중요한 것은 **테스트 환경과 실제 환경의 유사점과 차이점에 대한 완벽한 이해** 이다.

###### 고려해야 할 점

- 일반적인 환경과 비슷하게 방화벽, DNS, 라우팅 등이 생성된 로드를 처리하는지 확인해야 한다.
- 로드 밸런서의 구성을 확인해야 한다.
- 테스트를 할 수 있는 통합 지점이 있는지 확인해야 한다.

##### __Activity 2. Identify Performance Acceptance Criteria__

- 테스팅 결과(퍼포먼스)에 대한 수용 기준을 파악해야 한다.
- 수용 기준의 값들로는 응답 시간, 처리량, 자원 활용량 등이 있다.

###### 고려해야 할 점

- 비즈니스적으로 생각해야 한다. 요구사항, 사용자의 기대치, 계약상 의무 등을 파악해야 한다.
- 스트레스 조건, 성과 지표, 최적화 목표 등을 생각해야 한다.

##### __Activity 3. Plan and Design Tests__

- 성능 테스트의 계획과 설계시에는
 - 중요하게 사용될 시나리오를 판별하고
 - 사용자 간의 적절한 변수를 설정하고
 - 테스트 데이터를 식별, 생성하고
 - 수집 할 메트릭을 지정해야 한다.

- 시나리오를 판별 할 때에는
 - 일반적인 시나리오
 - 업무적으로 중요한 시나리오
 - 성능이 집약되어 보여질 수 있는 시나리오
 - 기술 관련된 시나리오
 - 계약한 사람이 제일 관심 있어하는 시나리오
 - 가시성 높은 시나리오를 생각해야 한다.

###### 고려해야 할 점

- 테스트 설계시 이론이나 예측이 아닌 실제 사용에서 기대하는 것을 기반으로 만들어야 한다.
- 현실적인 테스트를 디자인하려면 사람, 네트워크 등 다른 상호 작용 시스템에 민감하게 만들어야 한다.
- 도구가 테스트의 설계에 영향을 미치도록 디자인해야 한다.

##### __Activity 4. Configure the Test Environment__

- 테스트 전 테스트를 위한 도구 및 리소스를 준비하면 수행할 수 있는 테스트의 양이 크게 늘어날 수 있다.
- 항상 발생하는 문제들(IP 스푸핑, 하드웨어 조달, 서버 운영 체제 호환성 문제) 등이 해결되었는지 확인해야 한다.
- 그리고 프로젝트 전체에서 로드 생성 환경 및 도구를 계속해서 업데이트할 계획을 세워야 한다.

###### 고려해야 할 점

- 아무리 상식적으로 보일지라도 데이터가 수집되는 모든 시스템에서 클럭이 동기화되는지 확인해야 한다.
- 병목현상이 일어나기 전까지 생성할 수 있는 로드의 양을 결정해야 한다.
- 서버의 리소스 사용률을 모니터링하여, 로드가 분산되어있는지 확인해야 한다.

##### __Activity 5. Implement the Test Design__

- 사용중인 도구에 관계없이, 성능 테스트를 만드는 것은 일반적으로 단일 시나리오를 스크립팅 한 다음 이를 향상시키는 방향으로 진행되어야 한다.
- 가장 중요한 것은 테스트중인 어플리케이션이 실제 사용자와 시뮬레이션 된 사용자의 차이를 알 수 없도록 실제적인 테스트를 구현하는 것이다.

###### 고려해야 할 점

- 숨겨진 필드 또는 특수 데이터가 올바르게 처리되는지 확인해야 한다. (세션 ID 등)
- 트랜잭션의 유효성 검증이 올바르게 되었는지 확인해야 한다.
- 요청의 응답 시간을 측정하기 위해 테스트 스크립트의 요청 주위에 래퍼를 추가할 수도 있다.
- 테스트의 데이터와 기대치를 비교하여 상당한 가치를 얻을 수 있다.

##### __Activity 6. Execute the Tests__

- 테스트 실행은 다음 작업으로 이루어진다.
  1. 팀에서의 테스트 실행, 모니터링
  2. 테스트, 환경, 데이터의 상태 검증
  3. 테스트의 실행
  4. 테스트가 실행되는 동안 스크립트, 시스템, 데이터를 모니터링, 유효성 검사
  5. 테스트가 완료되면 결함이 있는지 검토
  6. 나중에 테스트를 반복하는 데에 필요한 테스트, 데이터 등의 보관
  7. 시작과 종료 시간, 데이터의 이름 등을 기록하여, 순차적으로 확인할 수 있게 함

- 테스트 실행 준비를 할 때에는 다음과 같은 것을 확인해야 한다.
 - 테스트 환경이 테스트의 설계 환경과 일치하는지 확인
 - 테스트를 실행하기 위해 스모크 테스트를 실행하여 성능 테스트를 실행할 준비가 되어있는지 확인
 - 현재의 주요 성능을 수집하도록 테스트가 구성되었는지 확인

###### 고려해야 할 점

- 데이터 업데이트에 대한 테스트 실행을 검증해야 한다.
- 모든 테스트를 세번씩 실행하자. 반복의 결과가 다르다면 어떤 요인때문인지 확인해야 한다.
- 상승 및 하강 기간을 적절하게 시뮬레이션 해야 한다.
- 문제를 이해하는 데에 진전이 없다고 생각된다면 하나 이상의 변수를 삭제한 다음 다시 테스트를 실행해야 한다.

##### __Activity 7. Analyze Results, Report, Retest__

- 단순히 테스트의 결과뿐만이 아닌, 테스트의 결론을 뒷받침하는 데이터가 필요하다.
- 결과를 얻은 방법에 대한 분석, 비교 및 세부 정보가 필요하다.
- 데이터를 분석할 때에는 다음과 같은 사항을 고려해야 한다.
 - 이터를 개별적으로, 그리고 팀에서 분석해라.
 - 병목현상을 수정하면 테스트를 반복하여 수정 사항의 유효성을 검증해야 한다.
 - 테스트를 마친다면 즉시 결과를 공유하고, 팀 전체에서 데이터를 사용할 수 있게 해야한다.
 - 현재 결과를 사용하여 다음 테스트의 우선 순위를 결정해야 한다.

- 대부분의 보고서는 _기술 보고서_ 혹은 _이해 관계자 보고서_ 중 하나에 속한다.

<br/>
### Chapter 5 - Coordinating Performance Testing with an Iteration-Based Process
![Image](./assets/chap5.PNG)
- 이번 장에서는 반복적인 프로세스 내에서 성능 테스트를 수행하는 데에 필요한 활동의 기본 개념과, 프로젝트에 즉시 적용할 수 있는 구체화 가능한 항목에 대해서 설명한다.

##### __Activity 1. Understand the Project Vision and Context__

- 프로젝트의 비전과 상황 이해는 어떤 성능 테스트 활동이 필요하고 가치 있는지를 결정하기 위한 기초 작업이다.
- 반복 기반 프로세스로 작업하기 위해 중요한 부분은 정확한 질문을 하고, 각 단계와 관련된 올바른 작업을 수행하는 것이다.
- 상황에 따라 질문이 달라질 수 있지만, 밑의 샘플 질문들은 각 단계의 시작에서 물어봐야 할 것들이다.

###### SAMPLE CHECKLIST
 - 프로젝트 비전의 성과는 무엇인가?
 - 어플리케이션이 서비스의 성능에 미치는 영향은 무엇인가?
 - 우리가 고객을 위해 해결하고자 하는 문제점은 무엇인가?
 - 팀은 프로젝트 일정 및 리소스와 관련해서 어떻게 일정을 계획하는가?

##### __Activity 2. Identify Reasons for Testing Performance__

 - 성능을 테스트하는 이유가 명확하게 파악되어야 한다.
 - 위험과 관심 분야를 명확하게 파악하는 것은 구체적인 성능 테스트 활동이 프로젝트에 큰 가치를 부여할 것으로 판단 될 때이다.

###### SAMPLE CHECKLIST
- 성능 테스트가 이 프로젝트에 대해 완화시킬 수 있는 위험은 무엇인가?
- 이 프로젝트와 관련해서 어떤 성능 문제가 이미 존재하는가?
- 특정 성능 예상치가 이미 요구되는 것으로 알려져 있는가?

##### __Activity 3. Identify the Value Performance Testing Adds to the Project__

- 프로젝트 및 비즈니스 수준 목표를 구체적이고 식별 가능한 성능 테스트 활동으로 변환하는 것이 중요하다.
- 성과 평가 활동이 가치를 더하거나 중요한 정보를 제공할 가능성이 있는지, 이러한 활동이 현 시점에서 계획할만한 가치가 있는지에 대한 합의가 포함된다.

###### SAMPLE CHECKLIST
- 어떤 성능 테스트 활동이 성능 테스트의 목적을 달성하는 데에 도움을 주는지?
- 현재 알려진 성능 문제를 해결하는 데 어떤 성능 테스트 활동이 도움이 될지?


##### __Activity 4. Configure the Test Environment__

- 테스트를 실행하기 위해 도구와 리소스를 준비해야 한다.
- 로드 생성 도구와 테스트 시스템을 설정하고, 이 환경이 테스트를 수행할 수 있는 요구를 충족시키는지 확인해야 한다.

###### SAMPLE CHECKLIST
- 테스트중인 어플리케이션의 성능 테스트 환경은 누가 관리하는지?
- 이 어플리케이션의 리소스 모니터를 누가 구성하고 운영하는지?
- 누가 테스트중인 응용 프로그램을 재설정할 수 있는지?
- 여러 사용자를 시뮬레이트 하기 위한 보안 또는 인증 사항이 있는지?

##### __Activity 5. Identify and Coordinate Tasks__

- 성능 테스트 작업은 혼자서 발생하지 않는다. 따라서 팀과 협력하여 자원 및 일정을 조정해야 한다.
- 반복 주기를 계획할 때 테스터는 주기에 대해 결정된 목표애 따라 결정된다.

###### SAMPLE CHECKLIST
- 이 사이클의 성과 목표는 무엇인지?
- 시스템이 모든 성능 목표를 달성했는지?
- 마지막 반복 이후 튜닝이 완료되었는지?
- 사용 가능한 시간은 얼마나 되는지?
- 각 작업에 소요되는 시간은 얼마나 되는지?
- 가장 중요한 활동은 무엇인지?

##### __Activity 6. Execute Task(s)__

- 1~2일 단위로 작업을 수행해야 한다.
- 지금까지 계획했던 반복 작업을 수행할 차례이다.

###### SAMPLE CHECKLIST

- 최근의 프로젝트 업데이트로 인해 현재 수행할 수 있는 프로젝트와 비교하여 작업을 어느 정도 가치 있게 만들었는지?
- 이 작업에 추가로 참여해야 할 팀원은 누구인지?
- 예비 결과가 의미가 있는지?
- 테스트가 우리가 예상한 데이터를 제공하는지?

##### __Activity 7. Analyze Results and Report__

- 반복적인 프로세스를 따라 가기 위해서는 결과를 신속하게 분석하고 공유해야 한다.

###### SAMPLE CHECKLIST

- 가치 있는 데이터인지?
- 데이터에서 의미를 도출하기 위해 더 많은 테스트가 필요한지?
- 튜닝이 필요한지? 튜닝할 부분을 알고 있는지?
- 성능 목표를 달성했는지?

##### __Activity 8. Revisit Activities 1-3 and Consider Performance Acceptance Criteria__

- 기본적인 정보가 변경되지 않았는지 확인해야 한다. (고객 정보 등의 새로운 정보를 통합하고 전략을 업데이트 해야한다)

###### SAMPLE CHECKLIST

- 서비스의 성능에 영향을 미치는 부분이 변경되었는지?
- 프로젝트 일정, 구조 또는 사용 가능한 자원이 변경되었는지?
- 성능 테스트 목표를 변경했는지?

##### __Activity 9. Reprioritize Tasks__

- 테스트 결과를 분석 후, 새로운 정보 및 기능 구성 요소의 가용성을 기반으로 지금까지의 전략에서 작업 우선 순위를 지정하고, 추가, 삭제한 뒤 Activity 5로 돌아가자.

### Chapter 6 - Managing an Agile Performance Test Cycle

- Activity 1. Understand Project Vision and Context
- Activity 2. Identify Reasons for Testing Performance
- Activity 3. Identify Value of Testing Performance
- Activity 4. Configure Test Environment
- Activity 5. Identify and Coordinate Tasks
- Activity 6. Execute Task(s)
- Activity 7. Analyze Results and Report
- Activity 8. Revisit Activities 1-3 and Consider Performance Acceptance Criteria
- Activity 9. Reprioritize Tasks

### Chapter 7 -  Managing the Performance Test Cycle in a Regulated (CMMI) Environment

- 오늘날의 소프트웨어 엔지니어링에서는 일부 시스템의 복잡성과 핵심 특성 때문에 규제가 필요하다. 시스템을 효과적이고 효율적으로 설계할 수 있을 정도로 유연하게 유지하는 것은 압력과 균형을 맞추기 항상 어렵다.
- CMMI(Capability Maturity Model Integration)은 일반적으로 유연한 것으로 간주되는 프로세스 패러다임의 예이다.
- 기존의 방식들과 비슷하지만 indentify와 analyze 방법에서 몇가지 추가적으로 해야 할 일이 있다.

##### __Activity 1. Understand the Process and Compliance Criteria__

- 이 단계는 성능 테스트와 관계가 없지만, 프로젝트 성공에 있어서 중요한 단계이다.
- 성능 테스트의 계획을 시작하기 전에 프로세스 및 준수 요구 사항을 완전하게 이해해야 한다.
- 이러한 규칙은 문서화되어있기 때문에 비교적 간단하게 처리가 가능하다.

##### __Activity 9. Report Results and Archive Data__

- 각 작업 항목이 끝나면 다음 성능 테스트를 실행하기 전에 결과를 통합하고 개발자, 설계자와 함께 공동 분석을 수행하는 것이 중요하다.
- 이런 분석 및 보고 기간은 휴식이 발생하는 기간이라고 생각하면 된다.
- 데이터에서 트랜드와 패턴을 찾아내는 데에 시간이 오래 거릴ㄹ 수 있다.

##### __Activity 10. Modify the Plan and Gain Approval for Modifications__

- 각 테스트 단계가 완료되면 성능 테스트 계획을 검토하는 것이 중요하다.
- 완료된 항목을 표시하고, 해당 항목을 평가해야 한다.
- 완료된 작업 항목이 다음 단계에 대한 대체 또는 예외 사례를 제거하는지, 혹은 다시 계획해야하는지를 고려해야 한다.