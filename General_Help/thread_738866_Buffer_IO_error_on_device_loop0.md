---
title: "Buffer I/O error on device loop0"
date: 2008-03-29
forum: General Help
---

### Post by great_googley_moogley on 2008-03-29
I understand this bug has already been reported.  
[https://bugs.launchpad.net/wubi/+bug/204133]("https://bugs.launchpad.net/wubi/+bug/204133")

I've been having trouble with wubi 8.04. I've had this machine for about a month, and after trying the daily build from the minefield about once a week, and i keep getting this error.

xxxxx (read-only filesystem)
buffer I/O error on device loop0 logical block xxxx

at least that's as well as i can remember, not knowing any way to access a logfile.

it seems to install properly, reboots, and seems to be nearly finished loading when i get this error.

This is still present in Wubi 8.04 rev 459 using amd64 on real (cheap) hardware.

Additionally, while i doubt this is related, i've also been unable to install the Ubuntu 8.04 beta (x64) from the live cd to a real partition, as it hangs after the migration assistant.

---

### Post by ago on 2008-03-29
Can you try to run ntfs-3g.probe from a linux installation/livecd?

---

### Post by uppsju on 2008-04-30
Hi,

just installed the release version of Hardy Heron, 64-bit version.

I get the same error messages. That is, I am able to log in to Ubuntu, but if I then try to "sudo init 1" from a terminal, I get these messages.

I'm completely new to Linux, so could you explain to me or point me in the right direction how I run the ntfs-3g.probe?

To explain why I would want to go to the terminal server, it is to install the nvidia driver for the graphics card on my laptop. This is a bit of a dealbreaker for me, because otherwise I won't be able to do any work in resolutions higher than 800x600.

Thanks.

---

### Post by ago on 2008-04-30
You should boot from live CD and try to mount manually the windows partition then we can get the errors. 

Also try running chkdsk /r from windows on the drive where you have Ubuntu.

Basically your ntfs partition is mounted read-only and that usually happens when there is fs corruption or after an unclean shutdown.

---

### Post by uppsju on 2008-05-07
Hi,

I'm not sure why there would be problems with the NTFS partition, as while I'm working within Linux I'm not trying to access the NTFS partitions.

Anyway, I did do a chkdsk /r from windows, and found no errors on the ntfs partitions. I also did extensive sector checks which did not find any errors.

My thoughts would be there are either problems with the ext3 partition, or there is some other linux error.

How would I check this?

---

### Post by eddyeoq on 2009-10-30
I'm having the same problem. I installed ubuntu 9.04 on Wubi, then I upgraded to 9.10. I didn't have this problem in 9.04, I updated and now I cant shutdown properly.

---

### Post by reaganf2 on 2009-10-31
Same issue...
Installed 9.04 on WUBI...
Now after upgrading to 9.10, can't shut down properly and get the error message:
Buffer I/O error on device loop0 and the system just hangs...
Very disturbing...

---

### Post by murphdiggity on 2009-10-31
I am fairly new to the linux os but I have had 9.04 installed for about 2 months on my dualboot (XP) laptop. I upgraded to 9.10 last night and have the same issue, My pc does not want to shut down properly.

---

### Post by f00fyf00f3r on 2009-10-31
Hello, got this error while shutting down on my gfs acer aspire one 150/ZG5 running 9.10 wubi. Currently doing a chkdsk on the xp partition, after will do a fsck on her karmic and will update shortly

---

### Post by f00fyf00f3r on 2009-10-31
No dices, but this thread is hella old, you should start a new one

---

### Post by murphdiggity on 2009-10-31
well i just did a complete format of my hd and reinstalled the dual boot os's, works fine now

---

### Post by poo706 on 2009-11-01
This is getting talked about on all of these other threads:
[http://ubuntuforums.org/showthread.php?t=1306005](http://ubuntuforums.org/showthread.php?t=1306005)
[http://georgia.ubuntuforums.org/showthread.php?p=8216794](http://georgia.ubuntuforums.org/showthread.php?p=8216794)
[http://georgia.ubuntuforums.org/show....php?p=8206461](http://georgia.ubuntuforums.org/show....php?p=8206461)
[http://ubuntu-ky.ubuntuforums.org/sh....php?p=8212799](http://ubuntu-ky.ubuntuforums.org/sh....php?p=8212799)

The most promising thing I've seen is from the last one, and it's just a workaround at best. The advice from post #6 (from P4man) halfway worked for me. When I get the buffer errors, I can get it to shutdown without holding the power button, but I couldn't get it to reboot via that method. In doing searches for this nearly every day for the last few weeks, it looks like it's a problem that's hit Wubi before. And there's a lot of people talking about it, so I'm sure a fix will be released soon.

[poo]

---

### Post by john_3000 on 2009-11-05
Response #19 in this thread shows how to fix it


[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589)

---

### Post by gladiator70 on 2009-11-13
[https://bugs.launchpad.net/ubuntu/+s...it/+bug/468589]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589")
Response #19, yes it does work!!!!! Thank you so much. For those newbies like me, here is the fix step by step.
1) Run the following command:
gksudo gedit /etc/rc6.d/S40umountfs
2) Replace:[FONT=Verdana]
[/FONT]fstab-decode umount -f -r -d $WEAK_MTPTS[FONT=Verdana] 
[/FONT]with[FONT=Verdana]
[/FONT]fstab-decode umount -r -d $WEAK_MTPTS[FONT=Verdana]
[/FONT]and[FONT=Verdana]
[/FONT]fstab-decode umount -f -v -r -d $WEAK_MTPTS[FONT=Verdana]
[/FONT]with[FONT=Verdana]
[/FONT]fstab-decode umount -v -r -d $WEAK_MTPTS[FONT=Verdana]

[/FONT]3) Save the changes and then try to reboot.

This worked for me.

---

