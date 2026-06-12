---
title: "Ubuntu and Windows 10"
date: 2018-06-02
forum: General Help
---

### Post by concerro on 2018-06-02
I used to have Windows 7 and Ubuntu a few years ago. I could access my Windows 7 files from Ubuntu, and even use the programs. I think WINE allowed me to do it. 

I'm thinking of going back to Unbuntu with my next laptop which will come with Windows 10.  If I have the latest version of Ubuntu on an external HD will I be able to access my Windows 10 programs, and files?

PS: I'm aware that WINE and PlayonLinux might not work with every program. I'm more concerned with being able to access files than use Windows programs. The programs are just a bonus if I can get them to run on Linus.

---

### Post by Autodave on 2018-06-02
You may be able to. But, you will have to disable *fast boot* in the BIOS.

---

### Post by oldfred on 2018-06-02
+1 on Autodave's suggestion.

The Windows fast start up is just hibernation. And it locks up all NTFS partitions, even those on external drives.
And Windows will turn fast start up back on with updates which may be in back ground. So if issues accessing NTFS, you need to first check if fast start up is back on. If not then NTFS may need chkdsk.

And grub will dual boot working Windows,or Windows that is not hibernated nor needs chkdsk. Best is UEFI install, as then you can still directly boot Windows from UEFI boot menu. And you may need your Windows repair flash drive. 

I normally suggest setting the Windows main partition ( the c: drive) as read only, and use a separate NTFS shared data partition for all data you may want in both systems. But fast boot still must be off to use any NTFS as read/write.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

