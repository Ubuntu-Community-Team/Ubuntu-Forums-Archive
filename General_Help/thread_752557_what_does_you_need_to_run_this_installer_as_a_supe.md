---
title: "what does you need to run this installer as a super user mean"
date: 2008-04-11
forum: General Help
---

### Post by valpobro on 2008-04-11
i am having the same problems as this guy
[http://ubuntuforums.org/showthread.php?t=740212](http://ubuntuforums.org/showthread.php?t=740212)

 the only thing is he got his to work and i can't. i know nothing about ubuntu and need step by step ways to do somthing.

some one please help me out

o and i have the same graphics card as him

---

### Post by 67GTA on 2008-04-11
You have to use ```
sudo
```, which gives you super user privileges like the administrator account in Windows. Open a terminal, type ```
sudo
```, and then just drag the installer to the terminal and select "paste". Make sure you leave a space between sudo and the installer. Hit enter, and it will ask you for your password. Type in your password and hit enter again, which should start the installer. You also need to check the properties of the installer script to make sure it is executable before you try to install. Right click on the script, select properties, and then the permissions tab. There will be a check box with "Is executable" next to it. Make sure it is checked.

---

### Post by Tyke91 on 2008-04-11
actually, sudo will give you the privileges of any user/group that you tell it to... but yeah, by default it is root. 

to find out more about why we need to have this important security feature, click below
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by valpobro on 2008-04-11
ok i got it to work but now that my drivers are installed when i go to the ati catalyst it just says there was a problem initializing catalyst control center linux edition. it could be caused by the following.
no ati graphics driver is installed or the ati driver is not functioning properly.
please install the ati driver  appropriate for your ati hardware, or configure using aticonfig

i'm going to try and install them again but while i do that if anyone knows what i should do that would help

---

### Post by 67GTA on 2008-04-11
Run ```
sudo aticonfig
``` in a terminal, and then reboot. It should be alright then.

---

