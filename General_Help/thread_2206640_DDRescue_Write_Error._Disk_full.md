---
title: "DDRescue Write Error. Disk full ?"
date: 2014-02-20
forum: General Help
---

### Post by Bala_Sakthivel on 2014-02-20
Hey Guys, I need some help here.. i am using DDRescue to retrive an image from my dieing 2 TB and the new disk is also 2 TB disk. when it is almost 99% done which was running for past 4 days now I receive this error "ddrescue: write error: Input/output error". Pasted the complete log below. I guess this is because the new disk running out of space ? System monitor shows i have only 4.1 kb space left

Any suggestion what to do next ? 
Just don't want to waste the 5 days effort my computer has put to get the image. 
what options i have? Can go ahead and create a remining image on another disk ?
Or Can just go ahead and extract the data from this image with out worring the remaining few data that has to be rescued ?
Or i need to start over again :( if yes then how to mitigate this problem

I ran lshw command to find out the disk details and both has exact disk spaces.

Thanks for the help.

[TABLE="width: 500"]
[TR]
[TD]ubuntu@ubuntu:/media/storage$ sudo ddrescue /dev/sdc hdimagenew.img resucenew.log


GNU ddrescue 1.16
Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:     2000 GB,  errsize:   2273 kB,  errors:      31
Current status
rescued:     2000 GB,  errsize:   2273 kB,  current rate:        0 B/s
   ipos:     2000 GB,   errors:      31,    average rate:        0 B/s
   opos:     2000 GB,     time since last successful read:       1 s
Copying non-tried blocks...
**ddrescue: write error: Input/output error**
ubuntu@ubuntu:/media/storage$ 

[/TD]
[/TR]
[/TABLE]


[TABLE="width: 500"]
[TR]
[TD]ubuntu@ubuntu:~$ sudo lshw -short | grep "sd[ac]"
/0/1/0.0.0     /dev/sda   disk        2TB ST2000DM001-1CH1
/0/1/0.0.0/1   /dev/sda1  volume      1863GiB Windows NTFS volume
/0/3/0.0.0     /dev/sdc   disk        2TB Ext HDD 1021
/0/3/0.0.0/1   /dev/sdc1  volume      1863GiB Windows NTFS volume
ubuntu@ubuntu:~$ 

[/TD]
[/TR]
[/TABLE]

---

