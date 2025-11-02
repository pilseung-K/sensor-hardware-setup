Vimba SDK Camera Setup Guide (Allied Vision GT/U-Series)<br>
Allied Vision사의 **GigE Vision (GT 시리즈)** 및 **USB3 Vision (U 시리즈)** 카메라의 하드웨어 설정, 드라이버 설치 및 초기 코드를 다룹니다.

**하드웨어 세팅**<br>
Prosilica GT 1290 (GT Series)

![Prosilica GT 1290 카메라 외형](../images/Prosilica_GT_1290.png)
| 용도/설명 | 규격 |
| :--- | :--- |
| **데이터 전송 표준** | **GigE Vision** |
| **전력 공급 방식** | **PoE (Power over Ethernet)** |
| **전원 공급 장치** | **PoE 스위치 (또는 인젝터)** |
| **전송 케이블** | **CAT 5e 이상의 이더넷 케이블** |

Alvium 1800 U-319 (USB Series)

![Alvium 1800 U 319 카메라 외형](../images/Alvium_1800_U-319.png)
| 용도/설명 | 규격 |
| :--- | :--- |
| **인터페이스** | **USB3 Vision** |
| **데이터 및 전원 공급** | **USB 3.0 케이블** |
| **권장 케이블** | **USB Standard-A to Micro-B (잠금 나사 타입 권장)** |



**소프트웨어 세팅**<br>
* **Vimba X SDK 다운로드:** [Allied Vision 공식 다운로드 페이지로 이동](https://www.alliedvision.com/en/products/software/vimba-x-sdk/)

```bash
# 1. 다운로드 폴더로 이동 (다운로드 파일이 여기 있다고 가정)
cd Download

# 2. SDK 파일을 /opt 디렉토리에 관리자 권한으로 압축 해제
sudo tar -xzf VimbaX_Setup-2025-2-Linux64.tar.gz -C /opt

# 3. CTI 폴더로 이동하여 GenTL 환경 설정 스크립트 실행
cd /opt/VimbaX_2025-2/cti
sudo bash ./Install_GenTL_Path.sh

# 4. 시스템 재부팅 (환경 변수 완전 적용)
sudo reboot

# 5. GenTL 환경 변수가 올바르게 설정되었는지 확인 (선택 사항)
echo "$GENICAM_GENTL64_PATH"

# 6. Vimba X Viewer 실행하여 카메라 연결 및 이미지 확인
/opt/VimbaX_2025-2/bin/VimbaXViewer
```
**Vimba X ROS2 driver**<br>
#### 3.1 ROS 2 Humble 설치 가이드

* **운영체제:** Ubuntu 22.04 LTS (Jammy Jellyfish)
* **공식 설치 문서:** [ROS 2 Humble 공식 설치 페이지로 이동](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debs.html)

#### 3.2 Vimba ROS 2 드라이버 설치 가이드

이 저장소는 Allied Vision에서 공식 제공하는 ROS 2 드라이버를 사용합니다.

* **Vimba ROS 2 드라이버 Git 저장소:** [VimbaX ROS 2 Driver Git 저장소로 이동](https://github.com/alliedvision/vimbax_ros2_driver)
* **릴리스 (Release) 설치 파일:** [Vimba X ROS 2 Driver v1.0.0 릴리스 페이지](https://github.com/alliedvision/vimbax_ros2_driver/releases/tag/v1.0.0)

**2.4 Python 환경 설정 및 라이브러리 설치**<br>
Vimba 카메라를 Python에서 제어하기 위해서는 Vimba Python 라이브러리가 필요합니다.

```bash
# 1. Python 가상 환경 (Virtual Environment) 생성 및 활성화 (선택 사항)
# python3 -m venv vmbpy_env
# source vmbpy_env/bin/activate

# 2. Vimba Python 라이브러리 설치
pip install vmbpy

# 3. 설치 확인 및 테스트 (Python 인터프리터)
# python3
# >>> import vmbpy
# >>> print(vmbpy.__version__)
```
