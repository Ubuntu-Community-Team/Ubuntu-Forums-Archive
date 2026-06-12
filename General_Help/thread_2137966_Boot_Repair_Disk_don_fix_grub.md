---
title: "Boot Repair Disk don fix grub"
date: 2013-04-22
forum: General Help
---

### Post by Zackreffil on 2013-04-22
I recently I install windows 8 and in another partition i have Ubuntu 12.10, i use the boot repair disk one time before and the Grub menu was restored but this time that doesn't work, i see in the advanced options and the options "Grub" doesn't appear and the tabs was lock it.

Any suggestion to unlock that options?

Thanks for your time, i'm desperate
Please somebody help me

---

### Post by oldfred on 2013-04-22
Run the BootInfo report and post the link it gives to see details of your configuration.

---

### Post by Zackreffil on 2013-04-22
Well, here it is the link
[http://paste.ubuntu.com/5593959/](http://paste.ubuntu.com/5593959/)
I hope you can help me
the bigger partition is the one it contains Linux Ubuntu 12.10

Here is the picture of "Boot Repair" and doesn't appear Grub options

[IMG]https://fbcdn-sphotos-e-a.akamaihd.net/hphotos-ak-prn1/603876_648978451785909_148486740_n.jpg[/IMG]

---

### Post by oldfred on 2013-04-22
Partitioning is a bit unusual. But it looks like your extended partition has a lot of empty space between the start and swap. I suspect that was your Linux partition. 

I would try testdisk. You can run from liveCD/DVD/Flash installer. But have to install it from repository. It also is in many Linux repair liveCDs.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Zackreffil on 2013-04-22
Quick question, i use the testdisk in windows or in the livecd of Ubuntu?

---

### Post by oldfred on 2013-04-22
I gather there is a Windows version, but never have used it. I have used the Linux version for just a few things. Not sure if there are differences in how the Windows version really works or not.
But general principles are use Windows tools for Windows and Linux tools for Linux. 
Since it is a Linux partition, Windows may not ever see it.

---

### Post by Zackreffil on 2013-04-23
Finally, I can fix my problem with the testdisk, i write again the table of partitions and after that i use the Boot repair disk to reinstall the Grub menu.

My Problem was [COLOR=Navy] [/COLOR][COLOR=Navy][SOLVED][/COLOR]

---

### Post by oldfred on 2013-04-23
Glad that worked. :)

---

