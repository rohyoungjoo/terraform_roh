# 📌 Terraform 기반 Hybrid Cloud 인프라 구축 (2차 프로젝트)

## 📖 프로젝트 개요
본 프로젝트는 온프레미스 환경을 기반으로 AWS 클라우드를 DR(Disaster Recovery) 환경으로 확장한 Hybrid Cloud 아키텍처를 구축하는 것을 목표로 하였습니다.  

Terraform을 활용하여 AWS 인프라를 코드로 관리(IaC)하고,  
Site-to-Site VPN을 통해 온프레미스와 AWS를 연결하여 고가용성 및 장애 대응 구조를 설계하였습니다.

---

## 🎯 주요 목표
- 온프레미스 → AWS 확장을 통한 Hybrid Cloud 구성
- Site-to-Site VPN 기반 네트워크 연결
- AWS 인프라 Terraform 기반 자동화 (IaC)
- ALB + AWS WAF를 통한 클라우드 보안 계층 구성
- 장애 발생 시 Route53 기반 Failover 구조 설계

---

## 🏗️ 전체 아키텍처 (요약)
[ On-Premise (Primary) ]
↓
[ Site-to-Site VPN ]
↓
[ AWS (Secondary / DR) ]

AWS 구성:

VPC (Public / Private Subnet)
NAT Gateway
ALB (Application Load Balancer)
AWS WAF
ROSA (OpenShift Cluster)


---

## 📂 Terraform 구조

```
terraform_roh/
├── scripts/
├── stacks/
│   ├── 00-base-network/
│   ├── 10-net-sec/
│   └── 20-edge/
├── .gitignore
└── README.md
```

---

### 🔹 00-base-network
- VPC 생성
- Public / Private Subnet 구성
- Internet Gateway / NAT Gateway 설정
- Route Table 구성

### 🔹 10-net-sec
- Site-to-Site VPN 구성 (VGW 기반)
- Security Group 설정
- 네트워크 접근 제어 구성

### 🔹 20-edge
- ALB(Application Load Balancer) 구성
- AWS WAF(Web Application Firewall) 적용
- 외부 트래픽 진입 지점 (Edge Layer) 구성

---

## ⚙️ 사용 기술
- Terraform
- AWS
  - VPC
  - ALB
  - WAF
  - NAT Gateway
  - Site-to-Site VPN
- ROSA (Red Hat OpenShift on AWS)

---

## 🔐 보안 설계
- AWS WAF를 통한 L7 웹 공격 방어
- Security Group 기반 최소 권한 접근 제어
- Public / Private Subnet 분리를 통한 네트워크 격리
- 온프레미스 WAF + AWS WAF 이중 방어 구조

---

## 🌐 네트워크 설계
- Site-to-Site VPN으로 온프레미스 ↔ AWS 연결
- Private Subnet 기반 내부 리소스 보호
- NAT Gateway를 통한 Private Subnet 외부 통신 지원

---

## 🚀 주요 구현 내용 (내 역할)
- Terraform 기반 AWS 인프라 코드 작성 및 구조 설계
- VPC / Subnet / NAT Gateway 네트워크 구성
- Site-to-Site VPN 구성 및 연결 테스트
- ALB + AWS WAF 적용을 통한 보안 구조 설계
- Terraform 모듈 구조 설계 및 리팩토링

---

## 📈 기대 효과
- 인프라 자동화를 통한 운영 효율성 증가
- 장애 발생 시 빠른 복구 가능한 DR 환경 구축
- 확장 가능한 클라우드 기반 인프라 확보
- 보안 강화된 Hybrid Cloud 아키텍처 구현

---

## 📌 느낀 점
Terraform을 활용하여 인프라를 코드로 관리하면서  
수동 작업 대비 효율성과 일관성이 크게 향상되는 것을 경험하였습니다.  

특히 Hybrid Cloud 환경에서  
네트워크 연결(VPN), 보안(WAF), 트래픽 흐름을 직접 설계하며  
실무에 가까운 인프라 설계 경험을 쌓을 수 있었습니다.
