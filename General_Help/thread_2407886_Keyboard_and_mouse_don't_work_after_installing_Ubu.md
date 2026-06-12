---
title: "Keyboard and mouse don't work after installing Ubuntu"
date: 2018-12-10
forum: General Help
---

### Post by thecatalyst on 2018-12-10
Hi, 


I just flashed Ubuntu on my Intel Aero. Everything is working alright, I have Ubuntu startup screen, but my keyboard and mouse don't work. They work at the beginning, I can enter BIOS. But as soon as I enter Ubuntu it stops working. I'm using self-powered USB Hub. Tried to connect the keyboard directly. Still doesn't work. Tried to re-flash Ubuntu. Still the same problem. Please help :(


Best Regards 
Jamshid

---

### Post by rohankurane on 2018-12-26
Hi Jamshid, 
Were you able to resolve this problem ? 
I am facing the same issue - 

I first upgraded Yochto to the latest kernel using the iso file on intel website. Then flahsed the BIOS, FPGA and FC.

Then I installed Ubuntu 16.04.3 LTS which went fine. 

After completing the installation, I was asked to restart to complete the installation.

Upon restart the keyboard and mouse connected to the OTG cable are not  detected anymore so there is no way for me to interact with the RTF  drone.

 
Thanks
Rohan

---

### Post by thecatalyst on 2018-12-27
Hi Rohan,

the problem was solved. I installed Ubuntu without Internet and that solved my problem. I hope it will help you too

Best Regards 
Jamshid

---

### Post by rohankurane on 2018-12-28
Thanks Jamshid. Yes it did. 

I do have one more question for you -  

Once Ubuntu is installed, I do


[LIST]
[*]Add the Intel Aero Repository
[*]QGC configuration
[*]Configure the RealSense R200 camera
[/LIST]
         For that,  It asks me to do 

cd

sudo apt-get -y install git libusb-1.0-0-dev pkg-config libgtk-3-dev libglfw3-dev cmake

git clone [https://github.com/IntelRealSense/librealsense.git](https://github.com/IntelRealSense/librealsense.git)

cd librealsense
mkdir build && cd build
cmake ../ -DBUILD_EXAMPLES=true -DBUILD_GRAPHICAL_EXAMPLES=true
make

sudo make install

 

The  apt-get and git clone commands require  internet. How do I do them when  I am connected to the AERO-xxxx hotspot on the intel-aero ?

---

