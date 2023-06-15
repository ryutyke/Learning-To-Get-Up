# Learning-To-Get-Up

설명 영상 : https://youtu.be/sk4Bt2QC1OI

UE 5.1 Project file download
https://drive.google.com/file/d/1y1xESAXIlklTxi6SKGNC1uiMccggZest/view?usp=sharing

주제 : SAC 강화학습 알고리즘, Strong to Weak 방법으로 기립 애니메이션 생성

참고한 논문 :
Tao, T., Wilson, M., Gou, R., & van de Panne, M. (2022, August 7). Learning to Get Up. Special Interest Group on Computer Graphics and Interactive Techniques Conference Proceedings. ACM. https://doi.org/10.1145/3528233.3530697

동기 : 게임 속 캐릭터의 기립 모션이 부자연스러웠다. 누워있는 모습의 형태는 다양하지만, 모든 초기 상태에 대해서 애니메이션을 제작할 수 없기 때문이다.
강화학습으로 어떤 초기 상태에서라도 일어날 수 있는 액터를 학습할 수 있다면 다양한 초기 상태에 대해서 아주 쉽게 애니메이션을 제작할 수 있을 것이다.

결과 :
어떻게 누워있든지 상관없이 일어날 수 있는 결과물이 나왔다.
결과물이 후처리가 필요한 퀄리티이긴 하지만, 더 긴 시간 학습시키거나 더 적절한 파라미터 값과 리워드를 사용한다면 더 좋은 결과물이 나올 것이다.
또한 참고한 논문에서 소개한 slow까지 적용한다면 자연스러운 모션이 나올 것이다.

해당 기술의 장점으로는
1. 학습 훈련 데이터 (기존 애니메이션, 영상)이 필요 없다.
2. 모션 캡쳐로는 쉽지 않은 다리 여러 개, 팔 여러 개, 긴 팔 등 인간이 아닌 비현실 개체에 대해서도 애니메이션 생성이 가능하다.

기립 애니메이션 외에도 Reward 값의 변경만으로 다양한 동작을 학습시킬 수 있었다. 
SAC와 Strong to Weak를 사용하여 학습 데이터 없이 빠르게 학습시킬 수 있었다.

============================================================================================

파이썬 코드를 실행한 후, 언리얼을 플레이하면 학습된 데이터를 볼 수 있습니다.
현재 코드는 제가 학습시킨 모델을 load해서 이어서 학습시키는 것이고,

처음부터 학습시키고자 하면 122번줄을 
self.add_argument("--load_dir", default=None, type=str)
으로 바꾸면 됩니다.
