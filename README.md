# **비재무데이터를 활용한 중소기업 휴폐업예측 모델 제안 및 결정요인 분석**
### **2023 통계데이터 활용대회 대상 수상**

- 구성 : 팀 프로젝트 (3인)
- 기간 : 2023.06. ~ 2023.07.
- 사용 분석 도구 : `Python`(`Jupyter Notebook`), `R`

- 실험 설계 및 검증
    - 설명변수 : 기업의 재무 및 비재무 데이터
        - 변수 선택 : 재무 데이터
            - t-검정을 통해 총 88개의 변수 중 통계적으로 유의한 47개의 변수를 분석에 사용.
        - 비재무 변수 수집
            - 웹크롤링을 통해 네이버 기사 데이터 및 연봉, 입·퇴사율 데이터 수집 및 반영.
        - 파생 변수 생성
            - 재무 데이터 : 기간 내(18~21년) 변화율
            - 뉴스 데이터
                - 금융 감성분석 진행
                    - 사전 학습된 KLUE/BERT-base 모델을 사용
                    - 각 기업 별 긍정, 부정, 중립 뉴스의 비율 변수 생성
                - 총 기사 수 파생 변수 생성
        - 결측치 대체
            - 입퇴사율 및 연봉 데이터의 결측치
            - MICE(`method = ‘rf’`)로 결측치 대체
    - 반응변수 : 기업의 휴폐업 여부 (이진변수)
- 모델 설계
    - 재무 데이터 단독 사용 : Logistic 회귀, SVM, Tree 기반 모형(Decision Tree, Random Forest, XGB, LGBM 등), 딥러닝 기반 모형(TabNet)
    - 비재무 데이터 추가 : Logistic 회귀, Random Forest, XGB, LGBM
    - 평가 지표 :  AUC, F1 score, KS 통계량
- 결과
    - 모델 성능 및 해석
        - 재무 모델과 비재무 모델 모두 Tree 기반 모델(XGB, LGBM)이 가장 우수한 성능
            - 재무 KS : 0.787, F1 : 0.852 (LGBM 기준 )
            - 비재무 KS : 0.826, F1 : 0.880 (LGBM 기준 )
            - 비재무 데이터 추가 활용 시 모델의 예측 성능 향상 → 휴폐업 예측에 있어 비재무 데이터의 유효성 확인.
        - 변수 중요도 확인(Feature Importance)
            - 총 직원 수 및 연봉, 퇴사율 등의 비재무 데이터의 중요성 확인 (기준 모델 : LGBM).
        - 변수 중요도 확인(SHAP)
            - 연봉 및 직원 수는 폐업 확률과 음의 관계를 가지며, 중립 뉴스 기사 비율과 퇴사율은 폐업 확률과 양의 관계를 갖는 것을 파악 (기준 모델 : LGBM).
- 의의 및 기대 효과
    - 모델의 성능 향상을 통해 중소기업의 생존에 대한 비재무 변수의 중요성 파악.
    - 재무 데이터가 충분하지 않은 신생 기업에 대한 평가 변수의 다양화.
    - 폐업 예상 판별 중소기업에 대한 변수(항목) 별 세분화된 컨설팅 가능.
    - 정확한 중소기업 휴폐업 예측을 통한 기업 경제 안정화 및 사회·경제적 효율성 증대.
    - 중소기업에 대한 긍정적 인식 함양 및 이에 따른 지원 & 투자 활성화.
