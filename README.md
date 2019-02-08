# Change
Modify the commit `88f08f0` from the original driver to force `timestamp_mode` to `ptp4l`. Adopted from `ethz/ouster_example` fork since they probably don't update their driver.
It is assumed that your computer supports hardware timestamp, `ptp4l` is installed and correctly configured and the service starts on boot.
If NOT, do these steps first (copy from `ethz/ouster_example)` fork for ease of access):
+ Install ptp : `sudo apt install linuxptp` 
+ Edit the config file `systemctl edit --full ptp4l` with content: `ExecStart=/usr/sbin/ptp4l -i <your ethernet interface>`
+ Make it run on boot: `sudo systemctl enable ptp4l` 
+ Reboot or `systemctl daemon-reload`
+ Run the ros node and check if received messages have timestamps from your computer clock
  

# OS-1 Example Code
Sample code for connecting to and configuring the OS-1, reading and visualizing
data, and interfacing with ROS.

See the `README.md` in each subdirectory for details.

## Contents
* [ouster_client/](ouster_client/README.md) contains an example C++ client for the OS-1 sensor
* [ouster_viz/](ouster_viz/README.md) contains a visualizer for the OS-1 sensor
* [ouster_ros/](ouster_ros/README.md) contains example ROS nodes for publishing point cloud messages

## Sample Data
* Sample sensor output usable with the provided ROS code is available
  [here](https://data.ouster.io/sample-data-2018-08-29)
