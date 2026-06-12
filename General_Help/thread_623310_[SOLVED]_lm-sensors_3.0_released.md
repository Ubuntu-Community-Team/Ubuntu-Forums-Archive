---
title: "[SOLVED] lm-sensors 3.0 released"
date: 2007-11-25
forum: General Help
---

### Post by drs305 on 2007-11-25
lm-sensors 3.0 was released yesterday. How do I install it?  I used lm_sensors 2 but installed it via synaptic.

The install instructions simply say "make all"  and "make install" . After extracting the folder, changing into to that directory, and running those two commands, there is obviously more to it (or more commands). (I'm referring to the initial installation, not running sensors-detect afterward). I have the dependencies listed in the INSTALL file on my machine and I saw the notes about disregarding some errors during instalation due to specific hardware not on my computer.

Thanks for your inputs. 

Here is the link to lm_sensors 3.0 for those that don't want to wait until it's in the repositories:
[http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)

---

### Post by drs305 on 2007-11-25
I eventually found some old notes from my previous installation of lm-sensors and they worked for version 3.0 as well. I must have found this advice on the net somewhere as I could not have come up with this by myself and it is not mentioned anywhere in the INSTALL file.

I ran the following commands from within the unzipped lm 3.0 directory:
(edited)  See post #4 if you get error messages about creating directories.
```

make clean
make user
make user_install

```

Once I ran these commands and followed the notes generated during the installation (including deleting some old files and adding some lines to an etc/rc* file) I got the program up and running.

---

### Post by rbmorse on 2007-11-25
Is sudo required if you are running make user and make user_install?

---

### Post by drs305 on 2007-11-25
Thanks for that observation! My answer is ... I'm not sure.

It was the only way I got it to work initially. When I ran it without sudo, I got several warnings that permission wasn't available to make several usr/local directories. I ran it with sudo and it worked. I've since run the installation as a normal user and it appears to have worked that way also but that may be because the directories had already been created when I ran it earlier with sudo. I also had to use sudo to follow some of the instructions generated during the install (e.g. running '/sbin/ldconfig' to update libraries).

 I'll remove the sudo from the post but leave it here for posterity should a normal user install not work for others.

I've also spent some time on the lm-sensors site and found those instructions buried in a section on manual installations. That may be where I got the commands in the first place. Seems like they should be placed in the INSTALL file to me. Us noobs are easily confused....

---

### Post by drs305 on 2007-11-26
Since others may find this thread during a search and wish to install lm-sensors 3.0 before it reaches the official repositories, here is some other information to help with the installation.

The dependencies noted by INSTALL and as listed in synaptic are:  make, gcc, bison, flex, sysfsutils, rdd, perl
```
sudo aptitude install make gcc bison flex sysfsutils rdd perl
```
If you get a warning about " No rule to make target `sysfs/libsysfs.h' " add libsysfs-devel with synaptic.

Download the archive from the link earlier or below and extract the folder.
Change to the directory of the new folder and run the 3 commands from the first post. As noted in the install file, you may get some error messages relating to what the app finds on your system. The INSTALL file provides some details.
Important: Several instructions are generated in the terminal output while the installation is in progress. Once the install is complete, scroll through the output and make sure you follow any instructions generated. You must follow the instructions. The installation is not completely automated.

Once installed, run:
```
sudo sensors-detect
```
Read the notes as this runs. At then end, it will tell you copy several lines into a file in one of the /etc/rc*.d folders so the modprobe lines are read during startup. The asterisk is replaced by a number. Check your /etc folder to see which folders are available. I named my new file S70-sensors and put it in /etc/rc2.d  It seems to work there. I know enough to know the different folders have something to do with when they are loaded. You can do a search to learn more about that. I believe the S is necessary, the name can be anything. You will have to use administrative powers (sudo) since the file goes in the /etc directory.

The configuration information for lm-sensors 3 is actually located in /etc/sensors3.conf . I did not have an /etc/sensors.conf file after installation. This is the file where you can make changes to the output. After making any changes to this file, you must run the following command before the changes will take effect:
```
sudo sensors -s
```

The lm-sensors site says version 3 works differently than previous versions. There are already patches for some of the common apps used with the program, such as  xsensors, gkrellm, and sensors-applet. These are found on the download page at [http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)
Note: I looked at the patches. They are code. If someone would like to explain to a noob how you would apply the patches that would be great.

To run the program as is, run:
```
sensors
```

If the output doesn't look correct or you want to know more about the setting up the configuration files, I found these two pages helpful:
[http://www.lm-sensors.org/wiki/iwizard/1](http://www.lm-sensors.org/wiki/iwizard/1)  wizards
[http://www.lm-sensors.org/wiki/Configurations](http://www.lm-sensors.org/wiki/Configurations)  known motherboard configurations

---

