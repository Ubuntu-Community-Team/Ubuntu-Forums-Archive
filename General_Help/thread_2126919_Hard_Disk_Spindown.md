---
title: "Hard Disk Spindown"
date: 2013-03-18
forum: General Help
---

### Post by streat on 2013-03-18
I am new to the forum so I apologize if this is not the proper section. I am hoping to see if anyone has any solutions, I am currently running a samba media server with the greyhole utility through ubuntu desktop 12.04 64bit and I would like to spindown the drives that are not currently in being accessed. Does anyone have any suggestions for doing this? I dont mind waiting the 5-10 seconds necessary to spin up te drives when they are accessed through the network. Thank you in advance!!

---

### Post by tgalati4 on 2013-03-18
You can use *hdparm* with switches to set the spin-down time.  If the drive is being used for the OS, then the drive will keep spinning because of the log files and system use, so don't expect the OS drive to go to sleep.  

[http://askubuntu.com/questions/137577/put-hdds-in-standby-after-x-minutes-using-hdparm-doesnt-work](http://askubuntu.com/questions/137577/put-hdds-in-standby-after-x-minutes-using-hdparm-doesnt-work)

Green drives go to sleep automatically, so check if your drives are "Green".  Don't forget to install *smartmontools* to monitor the health of the drives.

---

### Post by streat on 2013-03-18
Thank you for the speedy response! I originally had the drives in a raid configuration so the greedy automatic spin down has been disabled and I have a mixture of green and non green drives. Just for clarification, hdparm sounds like it will do exactly what I'm looking for will mounted drives in use through samba be considered "OS drives"? Currently my OS is a solid state separate from all files. Thank you!

---

### Post by zero2xiii on 2013-03-18
Hay,

What *tgalati4* is refering to as "the drives used for the OS" are all the drives mounted for, under and inside folders such as:
/
/tmp
etc.

EDIT: All drives containing SWAP partitions as well. Unless 'swap-off' is activated.

Drives mounted under for example:
/media/some_drive/

Is not generalized as "operating system drives" as these has nothing to do with the functionality of the OS.

You stated (OP) that "Currently my OS is a solid state separate from all files." so all drives EXCEPT this drive (mounted as root) should be able to spin down.

Cheers

---

### Post by ceesbakker on 2013-09-07
Maybe this is a good tread to start? My server has 4 drives where the system drive is a SSD. There are three Harddisks that are used for storage. Normally these drives are sleeping and therefore the server uses just 27 watts on power consumption.

Early September I updated my system after more than three months where I had not looked at my server. Everything works fine after updating VirtualBox as well. There is a new kernel!


Well the next morning I notice the hard disks rotate all three. I notice that the power which has risen to 37 watts. After checking the configuration I find nothing I can change is different from before. With "find / media/d1 / amine -40" I searched for the files used by the entire system last half hour. With "sudo hdparm-C / dev / sdb" I check whether the drive is active.


It is now September 7th and today I noticed that an update was ready for VirtualBox. Version 4.2.18. All updated again. It has not helped.

Someone with the same issue?

---

### Post by tgalati4 on 2013-09-07
After updating, there are several indexes that probably need to be rebuilt:  slocate, any file index trackers, etc.  So I would expect some activity for a few hours after an update.  After several days, though, the disks should spin down.  Perhaps there are other machines that are using the disks--live mounts, that prevent them from spinning down?

What operating system are you running?  How does virtualbox fit in?  How is your system configured?

---

