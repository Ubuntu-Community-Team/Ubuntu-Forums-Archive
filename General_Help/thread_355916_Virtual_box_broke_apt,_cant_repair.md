---
title: "Virtual box broke apt, cant repair"
date: 2007-02-07
forum: General Help
---

### Post by maddog39 on 2007-02-07
Hello all,

Well I tried installing VMWare and of course that had to fail on the installation and when I tried to re-run the installer it gave me a bunch of BS about it being already installed... well anyway, becoming extremely frustrated, I decide toget VirtualBox instead. But that also fails during installation, and I was using the official Edgy deb package to install. But now apt got screwed really bad and nothing will load nor install and the update fails aswell and apt keeps telling me that the package 'virtualbox' needs to be reinstalled but that wont work either... Now what do I do? Ive been using ubuntu for almost 2 years and never had this problem.

Please help.
-maddog39

---

### Post by llamakc on 2007-02-07
You post the output from the error or a screenshot if you're using Synaptic. Then we can suggest what tools/commands to get beyond the problem.

---

### Post by chavo on 2007-02-07
I had trouble with virtual box too. Nothing i did on the command line would fix it. So I fired up synaptic and was able to uninstall it from there. Not sure why it worked, but it did.

---

### Post by maddog39 on 2007-02-07
I tried synaptic but synaptic wont list any packages, it rendered itself useless. Well here is my comand line output from apt-get:
```

maddog39@maddog39-desktop:~$ sudo apt-get remove virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

```
And trying to reinstall the package. All it needs to make successful install is have the kernel header files, problem is I need apt to install them..
```

maddog39@maddog39-desktop:~$ sudo dpkg -i '/home/maddog39/Desktop/VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb' 
Selecting previously deselected package virtualbox.
(Reading database ... 118243 files and directories currently installed.)
Preparing to replace virtualbox 1.3.2-20070114_Ubuntu_edgy (using .../VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb) ...
(Kernel module not found)...fail!
invoke-rc.d: initscript virtualbox, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
(Kernel module not found)...fail!
invoke-rc.d: initscript virtualbox, action "stop" failed.
dpkg: error processing /home/maddog39/Desktop/VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb (--install):
 subprocess new pre-removal script returned error exit status 1
-e 
Creating group 'vboxusers'. VM users must be member of that group!

No precompiled module for this kernel found -- trying to build one
Messages displayed during module compilation will be logged to /var/log/vbox-install.log
Compilation of kernel module failed, aborting installation
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /home/maddog39/Desktop/VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb
maddog39@maddog39-desktop:~$ 

```
Also when i try to reinstall the deb, I get an error saying its corrupted. I even redownloaded the deb from the VirtualBox website and that didnt make any difference. I have also tried aptitude but same error.

---

### Post by maddog39 on 2007-02-07
Okay I fixed the problem. But it wasnt as easy as I thought. Okay, well apparently this is a common problem, its in the VirtualBox FAQ..

[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)


Quite lengthy too for a software bug that disabled more than half my system, because in the process it managed corrupt my system password and I had to go into recovery mode and reset it. Then after I finished that FAQ apt-get wouldn't remove so I tried aptitude and this command works to uninstall it:
```

sudo aptitude purge virtualbox

```
and that removes it. But seriously, they need to work out there installer scripts, I thought I lost my whole system for a bit.

---

