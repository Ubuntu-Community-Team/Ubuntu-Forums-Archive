---
title: "Change user privileges from root for Sun VirtualBox"
date: 2008-05-07
forum: General Help
---

### Post by kazoo boy on 2008-05-07
Hi, I'm kind of a Linux newbie, but I'm hoping this will be pretty basic.

I've downloaded Sun xVM VirtualBox to do some virtualization with other distros. Anyway, when I attempt to run it, it says

> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}



So basically, I know where to go to change the permissions, but since there is no root user, I'm guessing that I'll have to change it from the command line using sudo. Unfortunately, I'm not well versed in the command line, so I'm not sure how to change the permissions for the file. 

I don't know if this is important or not, but I'm running Ubuntu 7.10 Gutsy Gibbon 64 bit on a Dell Dimension E521.

---

### Post by overdrank on 2008-05-07
> **kazoo boy said:**
> Hi, I'm kind of a Linux newbie, but I'm hoping this will be pretty basic.

I've downloaded Sun xVM VirtualBox to do some virtualization with other distros. Anyway, when I attempt to run it, it says



So basically, I know where to go to change the permissions, but since there is no root user, I'm guessing that I'll have to change it from the command line using sudo. Unfortunately, I'm not well versed in the command line, so I'm not sure how to change the permissions for the file. 

I don't know if this is important or not, but I'm running Ubuntu 7.10 Gutsy Gibbon 64 bit on a Dell Dimension E521.

HI and welcome, If you add user to the groups you will not need root for VB. System, administration, User groups.

---

### Post by kazoo boy on 2008-05-08
Ok, thanks. I actually went and found how to change the permissions, but I got rwx for EVERYBODY, I'm just hoping that for an application it won't be a big deal, but maybe that's a bad idea. Any thoughts?

P.S. I went ahead and added them to the groups, so if I need to change back the permissions, it shouldn't be a problem.

---

