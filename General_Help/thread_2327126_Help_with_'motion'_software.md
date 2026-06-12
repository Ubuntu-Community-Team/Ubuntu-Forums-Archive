---
title: "Help with 'motion' software"
date: 2016-06-07
forum: General Help
---

### Post by chris331 on 2016-06-07
Hello, please correct me/merge this thread, if need be.  I couldn't find the answer to my question, both here on the forums and on the net generally.
I am having problems with running the motion software. 
I have Ubuntu 16.04.
(From my terminal)

```

aandk@aandk-Aspire-V3-731:~$ lsb_release -a


No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial



```

Here is what I've done:

```

aandk@aandk-Aspire-V3-731:~$ sudo apt-get install motion
[sudo] password for aandk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mysql-client postgresql-client
The following NEW packages will be installed:
  motion
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/238 kB of archives.
After this operation, 834 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package motion.
(Reading database ... 409368 files and directories currently installed.)
Preparing to unpack .../motion_3.2.12+git20140228-8build1_amd64.deb ...
Unpacking motion (3.2.12+git20140228-8build1) ...
Processing triggers for systemd (229-4ubuntu6) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for doc-base (0.10.7) ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Setting up motion (3.2.12+git20140228-8build1) ...
aandk@aandk-Aspire-V3-731:~$ sudo motion
[13590912] [NTC] [ALL] conf_load: Processing thread 0 - config file /etc/motion/motion.conf
[13590912] [NTC] [ALL] motion_startup: Motion 3.2.12+git20140228 Started with SDL support
[13590912] [NTC] [ALL] motion_startup: Logging to file (/var/log/motion/motion.log)



```

The log file is quite large, so if you guys know where to look in the file, and just want me to paste the pertinent info, I will.. otherwise 
I will paste the contents of the whole log.

---

### Post by coldraven on 2016-06-08
From motion documentation
> [SIZE=3]**Installation on Ubuntu**[/SIZE] 
 Motion is part of the Ubuntu repository. You can click either click [here]("apt:motion") to install it via the Ubuntu Software-Center.  Or open up a terminal window and type:  **sudo apt-get install motion**  

Before we start configuring Motion, we need to copy the config file to  our Home folder so that the master copy won’t be affected. 
Open a  terminal and copy the configuration file to your Home folder with  following commands:  **mkdir .motion**  (Note: This will create a hidden folder “*.motion*” in your Home directory.)  [B]
sudo cp /etc/motion/motion.conf ~/.motion/motion.conf[/B]  (Note: This command will copy the original motion configuration file to its location.)  
Now can open the configuration file for editing:  **sudo nano ~/.motion/motion.conf**  
After you you have done so, start motion in the terminal simply by typing:  **sudo motion**

Did you create and edit a config file? When you have done that read this:
[http://lavrsen.dk/foswiki/bin/view/Motion/MotionGuideGettingItRunning](http://lavrsen.dk/foswiki/bin/view/Motion/MotionGuideGettingItRunning)

---

