---
title: "Failed to connect to lvmetad"
date: 2018-07-14
forum: General Help
---

### Post by dan452 on 2018-07-14
Hello everyone,


I hope you are well and that time will allow you to help me with the following error in ubuntu:


I'm struggling for a few days to find a solution to my problem on a ubuntu 18.04
I have tried all the suggestions on many forums, but unfortunately I have not found a simple solution to solve this problem.


I have recently upgraded Ubuntu 16.04 to Ubuntu 18.04  with enabling full disk encryption and with LVM. After this upgrade, every time I'm starting the machine, I see some messages appearing on the boot screen. 


(for more details, please see the attached photo)


I need yours precious help, I hope someone help me with a simple solution!


Please let me know,
Dan.

---

### Post by Dennis N on 2018-07-14
Only informative. I frequently see the same. lvmetad caches information about logical volumes on your system for the benefit of lvm commands. A command would otherwise have to scan your system every time you run an lvm command. 

It probably hasn't started yet, and a backup process of scanning for lvm devices is used instead until it does.

After you log in, you can check if its running using htop and filter (F4) for 'lvm'. I see **/sbin/lvmetad -f** in Ubuntu 18.04.

[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/logical_volume_manager_administration/metadatadaemon](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/logical_volume_manager_administration/metadatadaemon)

---

### Post by dan452 on 2018-07-14
Thanks for your suggestion.


I specify that this error prevents me from getting the graphical interface...
I can not acces ubuntu only with Ctrl + Alt * F1.

---

### Post by Dennis N on 2018-07-14
There is no error indicated in your image - it's just a warning. As it says, device scanning is being used instead. The device scan succeeded because it informs you that Ubuntu found your volume group, and that two logical volumes are now activated (and accessible). I get these identical lines and the computer always has continued to login screen and desktop. So I suspect your failure to reach the graphical login screen  and desktop has another cause - not the lvmetad. Look for other reasons for not loading the login GUI.

---

