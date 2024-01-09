[![HitCount](https://hits.dwyl.com/snt-arg/s_graphs_docker.svg?style=flat-square&show=unique)](http://hits.dwyl.com/snt-arg/s_graphs_docker)
<p align="center">
  <h1 align="center">Multi S-Graphs: an Efficient Real-time Distributed Semantic-Relational Collaborative SLAM</h1>
    <p align="center">
    <a href="https://scholar.google.com/citations?user=zKbiZzwAAAAJ&hl=es&oi=sra"><light>Miguel Fernandez Cortizas</light></a>
    ·
    <a href="http://hriday.bavle.com/"><light>Hriday Bavle</light></a>
    ·
    <a href="https://scholar.google.com/citations?user=Afdcjx4AAAAJ&hl=es&oi=ao"><light>David Perez-Saura</light></a>
    <br>
    <a href="https://wwwen.uni.lu/snt/people/jose_luis_sanchez_lopez"><light>Jose Luis Sanchez-Lopez</light></a>
    ·
    <a href="https://scholar.google.com/citations?user=apPMLQ4AAAAJ&hl=es&oi=ao"><light>Pascual Campoy</light></a>
    ·
    <a href="https://wwwen.uni.lu/studies/fstm/interdisciplinary_space_master/holger_voos"><light>Holger Voos</light></a>
  </p>

  <h3 align="center"><a href="https://arxiv.org/pdf/2305.03441.pdf">Paper</a> | <a href="https://vimeo.com/cvarupm/multi-s-graphs?share=copy">Video</a></h3>
  
</p>

<br>

<p align="center">
  <a href="">
    <img src="./assets/img/banner.png" alt="Logo" width="60%" style="background-color:white;">
  </a>
</p>

## [TABLE OF CONTENTS](#table-of-contents)
- [Published Papers](#published-papers)
- [Getting started](#getting-started)
- [About Multi S-Graphs](#about-multi-s-graphs)
  - [Architecture](#architecture)
- [Example on Datasets](#example-on-datasets)
  - [Download Datasets](#download-datasets)
  - [Real Dataset](#real-dataset)
  - [Virtual Dataset](#virtual-dataset)
- [ROS Related](#ros-related)
  - [Nodelets](#nodelets)
  - [Services](#services)
  - [Parameters](#parameters)
  - [Published TFs](#published-tfs)
- [Instructions To Use Multi S-Graphs](#instructions-to-use-multi-s-graphs)
- [License](#license)
- [Maintainers](#maintainers)


## Published Papers

1. [Multi S-graphs: A Collaborative Semantic SLAM architecture
   ](https://arxiv.org/abs/2305.03441)
   - **Citation**
     ```latex
      @misc{fern2023multi,
        title={Multi S-graphs: A Collaborative Semantic SLAM architecture},
        author={Miguel Fernandez-Cortizas and Hriday Bavle and Jose Luis Sanchez-Lopez and Pascual Campoy and Holger Voos},
        year={2023},
        eprint={2305.03441},
        archivePrefix={arXiv},
        primaryClass={cs.RO}
      }
     ``` 

2. [S-Graphs+: Real-time Localization and Mapping leveraging
Hierarchical Representations
   ](https://arxiv.org/abs/2212.11770)
   - **Citation**
     ```latex
      @misc{bavle2022sgraphs+,
        title = {S-Graphs+: Real-time Localization and Mapping leveraging Hierarchical Representations},
        author={Hriday Bavle and Jose Luis Sanchez-Lopez and Muhammad Shaheer and Javier Civera and Holger Voos},
        year={2022},
        publisher = {arXiv},
        year = {2022},
        primaryClass={cs.RO}
     }
     ``` 

2. [Situational Graphs for Robot Navigation in Structured Indoor Environments
   ](https://arxiv.org/abs/2202.12197)
   - **Citation**
     ```latex
      @ARTICLE{9826367,
        author={Bavle, Hriday and Sanchez-Lopez, Jose Luis and Shaheer, Muhammad and Civera, Javier and Voos, Holger},
        journal={IEEE Robotics and Automation Letters}, 
        title={Situational Graphs for Robot Navigation in Structured Indoor Environments}, 
        year={2022},
        volume={7},
        number={4},
        pages={9107-9114},
        doi={10.1109/LRA.2022.3189785}}
     ```

## Getting started

1. Clone this repository

2. Pull the docker image from DockerHub

```sh
docker pull sntarg/multi_s_graphs:latest
```
<!-- 3. Build the image??
```sh
cd [/path/to/repository/folder]
docker build . -t multi_s_graphs_container
``` -->
3. Allow multicast for Zenoh and display access for visualization
```sh
sudo ifconfig lo multicast
xhost +
```
4. Compose a container from image using docker_compose.yml configuration.
```sh
cd [/path/to/repository/folder]
docker compose up -d
```
This command also incorporates the flags `d`, which makes the container run in the detached mode

5. Open a terminal inside the container
```sh
docker exec -ti multi_s_graphs_container bash
```
6. Execute an instance of Multi S-Graphs
```sh
./tmux_launch.bash [robot_namespace] [path/to/robot/rosbag]
```

## About Multi S-Graphs

### Architecture

<p align="center">
<a href="">
<img src="./assets/img/architecture.png" alt="Tf tree" width="80%" style="background-color:white;">
</a>
</p>

## Example on Datasets

**Note:** For each command below, please execute them in separate terminal windows!

### Download Datasets

[Real Dataset](https://uniluxembourg-my.sharepoint.com/:u:/g/personal/hriday_bavle_uni_lu/EQN2qUn1P1dKuzcZqan8o3UBrBMa8b5Pcspupm_CBFHTgA?e=JxYnAJ)

[Virtual Dataset](https://uniluxembourg-my.sharepoint.com/:u:/g/personal/hriday_bavle_uni_lu/EWy7dyDnGzFLh3LMR0VXYQABne9B_NZ0YCM-o_PF8PPY5g?e=xoThE1)

### Real Dataset
1. Open a terminal inside the container
```sh
docker exec -ti multi_s_graphs_container bash
```
2. In this terminal inside the container, execute an instance of Multi S-Graphs for Robot1
```sh
./tmux_launch.bash robot1 rosbags/?_split_robot1.bag
```
3. In a different window, open another terminal inside the container
```sh
docker exec -ti multi_s_graphs_container bash
```
4. In this terminal inside the container, execute an instance of Multi S-Graphs for Robot2
```sh
./tmux_launch.bash robot1 rosbags/?_split_robot2.bag
```

### Virtual Dataset
1. Open a terminal inside the container
```sh
docker exec -ti multi_s_graphs_container bash
```
2. In this terminal inside the container, execute an instance of Multi S-Graphs for Robot1
```sh
./tmux_launch.bash robot1 rosbags/?_split_robot1.bag
```
3. In a different window, open another terminal inside the container
```sh
docker exec -ti multi_s_graphs_container bash
```
4. In this terminal inside the container, execute an instance of Multi S-Graphs for Robot2
```sh
./tmux_launch.bash robot1 rosbags/?_split_robot2.bag
```

## ROS Related

### Nodelets

> s_graphs is composed of **3** main nodelets.

- **s_graphs_nodelet**

  - Subscribed Topics

    - `/odom` ([nav_msgs/Odometry](http://docs.ros.org/en/noetic/api/nav_msgs/html/msg/Odometry.html))
      - The odometry from the robot.
    - `/filtered_points` ([sensor_msgs/PointCloud2](http://docs.ros.org/en/melodic/api/sensor_msgs/html/msg/PointCloud2.html))
      - The data from the Lidar sensor.

  - Published Topics

    - `/s_graphs/markers` ([visualization_msgs/MarkerArray](http://docs.ros.org/en/noetic/api/visualization_msgs/html/msg/MarkerArray.html))
      - The markers represents the different s_graphs layers.
    - `/s_graphs/odom2map` ([geometry_msgs/TransformStamped](http://docs.ros.org/en/api/geometry_msgs/html/msg/TransformStamped.html))
      - Sets where the robot pose is within the map (world).
    - `/s_graphs/odom_pose_corrected` ([geometry_msgs/PoseStamped](http://docs.ros.org/en/noetic/api/geometry_msgs/html/msg/PoseStamped.html))
      - The pose of the robot once odom2map is applied.
    - `/s_graphs/odom_path_corrected` ([nav_msgs/Path](http://docs.ros.org/en/noetic/api/nav_msgs/html/msg/Path.html))

      - The path of the robot once the odom2map is applied.

    - `/s_graphs/map_points` ([sensor_msgs/PointCloud2](http://docs.ros.org/en/melodic/api/sensor_msgs/html/msg/PointCloud2.html))
      - The points that represent the first layer of S-Graphs.
    - `/s_graphs/map_planes` (s_graphs/PlanesData)
      - Current planes seen by the robot.
    - `/s_graphs/all_map_planes` (s_graphs/PlanesData)
      - All the planes that were seen by the robot.

- **room_segmentation_nodelet**

  - Subscribed Topics

    - `/voxblox_skeletonizer/sparse_graph` ([visualization_msgs/MarkerArray](http://docs.ros.org/en/noetic/api/visualization_msgs/html/msg/MarkerArray.html))
      - Represents the free space where the robot can go to. This is also knonw as free-space clusters.
    - `/s_graphs/map_planes` (s_graphs/PlanesData)
      - Current planes seen by the robot.

  - Published Topics

    - `/room_segmentation/room_data` (s_graphs/RoomsData)
      - Contains all the necessary information about the rooms in a floor.

- **floor_plane_nodelet**

  - Subscribed Topics

    - `/s_graphs/all_map_planes` (s_graphs/PlanesData)
      - All the planes that were seen by the robot.

  - Published Topics

    - `/floor_plan/floor_data` (s_graphs/RoomData):
      - Constains all the necessary information about each floor.

### Services

- `/s_graphs/dump` (s_graphs/DumpGraph)

  - save all the internal data (point clouds, floor coeffs, odoms, and pose graph) to a directory.

- `/s_graphs/save_map` (s_graphs/SaveMap)
  - save the generated map as a PCD file.

### Parameters

All the configurable parameters are listed in _launch/s_graphs.launch_ as ros params.

### Published TFs

- `map2odom`: The transform published between the map frame and the odom frame after the corrections have been applied.

<p align="center">
<a href="">
<img src="./assets/img/Tf-tree.png" alt="Tf tree" width="80%">
</a>
</p>

## Instructions To Use Multi S-Graphs

1. Define the transformation between your sensors (LIDAR, IMU, GPS) and base_link of your system using static_transform_publisher (see line #94, s_graphs.launch). All the sensor data will be transformed into the common `base_link` frame, and then fed to the SLAM algorithm. Note: `base_link` frame in virtual dataset is set to `base_footprint` and in real dataset is set to `body` 

2. Remap the point cloud topic of **_PrefilteringNodelet_**. Like:

```xml
  <node pkg="nodelet" type="nodelet" name="hdl_prefilter" args="load s_graphs/PrefilteringNodelet hdl_prefilter_nodelet_manager">
    <remap from="/velodyne_points" to="/rslidar_points"/>
  ...
```

3. If you have an odometry source convert it to base ENU frame, then remove the **_ScanMatchingNodelet_** from line #37 to #50 in `s_graphs.launch` and then remap odom topic in **_SGraphsNodelet_** like 

```xml
  <node pkg="nodelet" type="nodelet" name="s_graphs" args="load s_graphs/SGraphsNodelet s_graphs_nodelet_manager" output="screen"> 
    <remap if="$(eval arg('env') == 'real')" from="/odom" to="/platform/odometry" />
  ...
```
Note: If you want to visualize the tfs correctly then your odom source must provide a tf from the `odom` to `base_link` frame.  

## License

This package is released under the **BSD-2-Clause** License.

Note that the cholmod solver in g2o is licensed under GPL. You may need to build g2o without cholmod dependency to avoid the GPL.

## Maintainers

- <ins>**Hriday Bavle**</ins>
  - **Email:** hriday.bavle@uni.lu
  - **Website:** https://www.hriday.bavle.com/
- <ins>**Miguel Fernandez-Cortizas**</ins>
  - **Email:** miguel.fernandez.cortizas@upm.es
- <ins>**David Perez-Saura**</ins>
  - **Email:** david.perez.saura@upm.es