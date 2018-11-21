# ROS_MoveIt

샘플링 타임(dt) 바꾸기

우선, industrial_core 패키지를 빌드해야함!!!!!! (이 패키지 없으면 적용이 안 됨)

그리고 , test_ws/src/final_config/launch/ompl_planning_pipeline.xml

이 파일에서 sample time duration 값 원하는 대로 변경해주면 됨



Catkin Build 코드

cd ~/test_ws/src

rosdep install -y --from-paths . --ignore-src --rosdistro kinetic

cd ..

catkin build

source ~/ws_moveit/devel/setup.bash

(source ~/.bashrc 이 코드로도 가능함. 왜냐믄  echo 'source ~/test_ws/devel/setup.bash' >> ~/.bashrc 코드를 이전에 적용시켜놔서)




작동 순서.
1. 가제보 실행
roslaunch final_gazebo robotic_arm_bringup_gazebo.launch

2.MoveIt RVIZ 실행
roslaunch final_gazebo robotic_arm_bringup_rviz.launch

3. RVIZ 화면 내에서 Fixed Frame -> dummy_link 로 설정

3-1. Add 버튼 누르고, Motion Planning 추가

3-2. Motion Planning 더블 클릭해서 아래 항목들 열리면, Planning Scene Topic : /planning_scene 으로 변경

3-3. 마우스 커서 맨 윗 쪽 검정부분으로 가져가면   File, Panels, Help 뜨는데 Panels 클릭. -> Add new panel 클릭 -> 
   맨 밑에 RvizVisualTooslGui 선택
   
4. Repeatability Test할 코드 실행 
roslaunch moveit_tutorials move_group_interface_tutorial.launch

4-1. MoveIt 화면 왼쪽 하단에 RvizVisualToolsGui 에 NEXT버튼 누를 때마다 다음 명령 실행
     Continue 버튼 누르면 한번에 쭉 진행.
