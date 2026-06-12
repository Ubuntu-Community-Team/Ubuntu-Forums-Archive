---
title: "Need some advice - intel graphics driver ( 855GM )"
date: 2012-12-04
forum: General Help
---

### Post by bluelight0 on 2012-12-04
First of all thanks for taking the time to read this.

I have a pretty old laptop with some alright specs.

Advent 7072
Intel Pentium M Processor 1.6GHz
1GB Ram
Intel 855 GM Graphics

I have run[ this test ]("https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements")

```
/usr/lib/nux/unity_support_test -p
```and received

```

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM x86/MMX/SSE2
OpenGL version string:  1.3 Mesa 8.0.4

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
**GL fragment program:      no**
GL vertex buffer object:  yes
GL framebuffer object:    yes
**GL version is 1.4+:       no**

**Unity 3D supported:       no**

```the thing I want to find out is will[ this page ]("http://askubuntu.com/questions/4658/how-to-install-intel-82852-855gm-driver")improve on what I have now and may possibly be able to run unity, if not then possibly run simple 3D games (many crash).

I have minecraft installed, which is meant to use opengl 2.0+ but according to the test I have something under 1.4.

If I run the test may it damage my system, and is it easily reversible?

Thankyou.

---

### Post by Isamu715 on 2012-12-04
What version of Ubuntu are you using?
> the thing I want to find out is will[ this page ]("http://askubuntu.com/questions/4658/how-to-install-intel-82852-855gm-driver")improve on what I have now and may possibly be able to run unity, if not then possibly run simple 3D games (many crash).This PPA provides an updated version of the Intel graphics driver. It may increase your GPU performance. Depending on how old your current driver is the performance increase may vary. It's completely reversible and rather safe.

---

### Post by NikTh on 2012-12-04
[B]If you use the Ubuntu 12.10  then the PPA not needed as Ubuntu  12.10 has the 2.20 intel driver by default. You can follow only the  steps for the SNA AccelMethod. 
[/B]

The PPA will upgrade you card driver to the latest. Also you have another option if you upgrade the driver. 
You have the option to test the SNA acceleration. The new driver Intel 2.20 supports SNA acceleration. 
So , first upgrade your Intel driver with these commands 
```
sudo add-apt-repository ppa:glasen/intel-driver
sudo apt-get update ; sudo apt-get dist-upgrade
```Then add SNA acceleration with the two commands below 

Create the folder
```
sudo mkdir /etc/X11/xorg.conf.d/
```Create the file 20-intel.conf and add the appropriate lines.
```
echo -e 'Section "Device"\n Identifier "Card0"\n Driver "Intel"\n Option "AccelMethod" "sna"\nEndSection' | sudo tee /etc/X11/xorg.conf.d/20-intel.conf
```Now , hit CTRL+ALT+F2 and login with username & password and execute the commands below
```
sudo service lightdm stop
sudo service lightdm start
```Above commands will stop and start the X-sever , and you will see the changes. 
You can test if SNA acceleration is enabled with the command 
```
cat /var/log/Xorg.0.log | grep -i sna
```the results should be something like below
```
(**) intel(0): Option "AccelMethod" "sna"
(II) intel(0): SNA initialized with Ironlake backend
```_**In case of a problem**_

Now , if you have any problem with the graphics - or and acceleration method. 

Remove the file 20-intel.conf to revert back to the UXA acceleration method
```
sudo rm /etc/X11/xorg.conf.d/20-intel.conf
```Restart X (commands are above) or reboot.

If you have a problem with the new driver , remove the PPA properly with below commands
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:glasen/intel-driver
sudo apt-get update
```Reboot for changes to take effect. 


Thanks

---

### Post by bluelight0 on 2012-12-04
I am on ubuntu 12.04

thank you very much

---

### Post by bluelight0 on 2012-12-04
Ok I got the message to appear, but unity just continually crashes and shows the prompt for error report.

I will look at ccsm because I may have changed some settings without relizing the difference between unity/unity 2d back then

thankyou for your help. if i cannot progress i will mark as solved because the drivers were installed.

---

