# LIDAR Robot Simulation Using Gazebo and ROS2

## Overview

This project implements a robot that uses LIDAR sensors for navigation and obstacle avoidance within the Gazebo simulation environment. The robot is controlled using ROS (Robot Operating System), and the system integrates an xbox controller which is used to control the movement of the robot.

The LIDAR sensor is the primary input device used to detect obstacles and map the environment. 

## Features

- LIDAR sensor for environment mapping and obstacle detection.
- ROS-based robot control and communication.
- Integration with Gazebo for realistic 3D simulation.

## Requirements

Before you begin, ensure you have the following software installed:

- [ROS](https://www.ros.org/) (ROS2 Jazzy)
- [Gazebo](http://gazebosim.org/) (The simulation environment)
- [rviz](http://wiki.ros.org/rviz) (For visualizing sensor data)

### Dependencies

To run the robot in the Gazebo simulation, you will need the following ROS packages:

- `ros-jazzy-joy-*`                 – Joystick related packages
- `ros-jazzy-ros-gz`                – Interface between Gazebo and ROS.
- `ros-jazzy-ros2-control`          – Packages of the ros2-control framework
- `ros-jazzy-gz-ros2-control`       – Integrates ros2-control framework with gazebo.
- `ros-jazzy-ros2-controllers`      – Contains Differential Drive Controller, Forward Command Controller, Joint Trajectory Controller
- `ros-jazzy-joint-state-publisher` - Publishes joint states of the robot to the ROS network.


Install them (if not already installed):

```bash
sudo apt install ros-jazzy-ros2-control ros-jazzy-ros2-controllers ros-jazzy-ros-gz ros-jazzy-gz-ros2-control ros-jazzy-joy-* ros-jazzy-joint-state-publisher
```


## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/nochilli/lidar-bot.git
   ```

2. Navigate to the project directory:

   ```bash
   cd lidar-controlled-robot
   ```

3. Build the workspace:

   ```bash
   colcon build
   ```
   
## Running the Simulation

### Launching the Gazebo Simulation

To launch the robot and Gazebo environment:

```bash
ros2 launch lidar-bot lidar-bot_spawn.launch.py
```

This will start Gazebo with the robot in the environment and initialize the LIDAR sensor.

### Visualizing in RViz

The launch file automatically opens RViz with predefined configurations to visualize the robot’s position, LIDAR scans, and more.

## Robot Control

The robot uses differential drive for movement control. The control node subscribes to the joystick input and drives the robot by publishing velocity commands to the `/cmd_vel` topic.

Basic control commands include:

- **Forward motion**: Moving the robot in a straight line.
- **Turn motion**: Turning the robot left or right.

## Troubleshooting

- **Gazebo crashes or freezes**: Ensure that Gazebo is properly configured and that your machine has enough resources to run the simulation.
- **No LIDAR data in RViz**: Make sure the LIDAR sensor is properly connected and publishing data to the correct topic (`/scan`).
- **Robot not moving**: Verify the control node is publishing velocity commands and that the robot's joints are properly configured.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- This project uses ROS and Gazebo, which are open-source platforms for robotics simulation.
- The LIDAR model used is based on real-world specifications and adapted for simulation purposes.

---
