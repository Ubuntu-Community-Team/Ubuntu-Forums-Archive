---
title: "Ubuntu 20 showing filesystem check hence taking too long to boot"
date: 2020-09-09
forum: General Help
---

### Post by ahti-sc on 2020-09-09
I installed Ubuntu 20 on a system with per-installed windows 10 Now every time I boot up to Ubuntu I get a filesystem checking message with a busy logo and takes long time to boot here is the log:

systemd-analyze:

```

Startup finished in 9.099s (firmware) + 12.480s (loader) + 3.629s (kernel) + 40.887s (userspace) = 1min 6.097s 
graphical.target reached after 40.795s in userspace


```

systemd-analyze blame | head :

```

20.845s plymouth-quit-wait.service                                                               
 9.345s snapd.service                                                                            
 8.393s NetworkManager-wait-online.service                                                       
 7.241s dev-sda5.device                                                                          
 7.056s networkd-dispatcher.service                                                              
 5.979s udisks2.service                                                                          
 4.590s accounts-daemon.service                                                                  
 3.837s NetworkManager.service                                                                   
 3.372s polkit.service                                                                           
 3.328s plymouth-read-write.service 


```

please help

---

### Post by Autodave on 2020-09-09
So, it boots in about 1 minute and 12 seconds?  That does not sound outrageous to me at all.  Please give us some specs on your equipment.

Don't forget that Win10 "seems" to boot instantly: that is because Win10 does not shut down: it merely hibernates.

---

### Post by ahti-sc on 2020-09-09
I had ubuntu 18.04 before and that was faster and didn't had to do that filesystem check every time I boot up. One of the reasons I moved to Ubuntu 20 was because of fast boot up but I don't seem to get it :(

core i5 6th gen
8gb ddr 4
1TB hdd

During installation I divided Ubuntu into just two partitions root and home.

---

### Post by sudodus on 2020-09-09
If there is a file system check at every boot of an installed system, something is wrong with the file system. Please fix it and check what might cause the damage.

It is different with a live or persistent live system. In such systems you should add the boot option [FONT=Courier New]**fsck.mode=skip**[/FONT] in order to get rid of the checking.

---

### Post by ajgreeny on 2020-09-09
Are you sure it is actually running a full filesystem check and not simply telling you the filesystem is clean which is what mine does.
A fast check happens at each boot but it is almost instantaneous so will not be causing your slow(?) boot; but like Autodave I do not think that your boot time is slow but it would help to see the output of commands ```
inxi -Fzx
sudo tune2fs -l /dev/sdx# | grep "Last checked:"
``` where sdx# is the root partition of your system.
The inxi command will show us your hardware and the tune2fs will show the last full filesystem check date.

---

### Post by ahti-sc on 2020-09-09
where to add fsck.mode=skip

---

### Post by ahti-sc on 2020-09-09
It shows the message without progress bar for 5-8 seconds. I don't see filesystem has been successfully completed or something like that it just boot up striaght. Will check the output of that command and give you reply with output.

---

### Post by sudodus on 2020-09-10
> **ahti-sc said:**
> where to add fsck.mode=skip

1. Please notice that this is relevant only for live and persistent live systems (not for installed systems).

2. You can add it temporarily by editing at the grub or syslinux boot menu, and you can add it by editing a configuration file (for grub: the file [FONT=Courier New]**grub.cfg**[/FONT]).

The following link can help you find how to add boot options, and [FONT=Courier New]**fsck.mode=skip**[/FONT] is a boot option,

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by maglin2 on 2020-09-10
[https://ubuntuforums.org/showthread.php?t=2449033](https://ubuntuforums.org/showthread.php?t=2449033)

---

