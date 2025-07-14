# 🤖 ROS 2 Gazebo 2-Wheel Robot Simulation

This project features a custom-built 2-wheeled differential-drive robot designed in **Fusion 360**, converted to URDF/Xacro, and simulated using **Gazebo Classic** with **ROS 2 Humble**. It includes a working differential-drive plugin setup and visual validation in RViz2.

---

## 🛠 Project Summary

- **CAD to Simulation**: Fusion 360 → Mesh (.stl) → URDF (.xacro)
- **Simulation Platform**: Gazebo Classic (with ROS 2 integration)
- **ROS Distro**: ROS 2 Humble
- **Package**: `ros2_bot_description`

---

## 📁 Folder Structure

```text
ros2_bot_description/
├── CMakeLists.txt
├── package.xml
├── launch/
│   ├── gazebo.launch.py               # Launches Gazebo + robot + plugins
│   └── state_publisher.launch.py      # Launches robot_state_publisher + RViz2
models/
├── meshes/
│   ├── base_link.stl
│   ├── left_wheel_1.stl
│   ├── right_wheel_1.stl
│   ├── lidar.stl
│   └── castor.stl
└── urdf/
    ├── materials.xacro
    ├── rmp_ros2.xacro
    └── rmp_ros2.gazebo

│   └── urdf/
│       ├── materials.xacro
│       ├── rmp_ros2.xacro
│       └── rmp_ros2.gazebo
└── README.md
----

🚀 Running the Simulation
1. Clone and Build
mkdir -p ~/ros2_ws
cd ~/ros2_ws
git clone https://github.com/parveezsyed28/ros2_bot_description.git
cd ..
colcon build --symlink-install
source install/setup.bash

2. Launch Gazebo
ros2 launch ros2_bot_description gazebo.launch.py

3. Launch State Publisher
ros2 launch ros2_bot_description state_publisher.launch.py

4. Control the Robot
ros2 run teleop_twist_keyboard teleop_twist_keyboard
----

🧠 Challenges Solved
🛠 Invisible robot in Gazebo: Fixed broken mesh file paths in Xacro.

⚙️ State publisher not launching: Adjusted state_publisher.launch.py to use proper ROS 2 syntax and arguments.

🔗 URDF loading issue: Resolved path errors by using FindPackageShare in gazebo.launch.py.
