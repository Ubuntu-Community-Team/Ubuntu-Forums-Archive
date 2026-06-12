---
title: "Partitions not showing on 'Files' and launcher, only the entire disk."
date: 2017-04-14
forum: General Help
---

### Post by kayaksan on 2017-04-14
[IMG]https://i.redd.it/5w0cixgupkry.png[/IMG]

The disk (428GB) is partitioned to use dual boot (Windows 10/Ubuntu  16.04 LTS). However, the partitions aren't showed, only the total disk. I  can see them all through gparted and fdisk -l. Interestingly enough, when I live boot  and just try Ubuntu, all partitions appear.

in*

---

### Post by oldfred on 2017-04-14
Have you left Windows fast start up on?
The Linux NTFS driver only mounts working NTFS partitions. Or they cannot be hibernated nor need chkdsk.
You also then cannot boot Windows from grub if hibernation is on. And Windows on updates will probably turn it back on. So have Windows repair disk handy and Ubuntu live installer handy.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)
[http://mjg59.dreamwidth.org/24869.html](http://mjg59.dreamwidth.org/24869.html)

---

### Post by Keith_Helms on 2017-04-14
I don't think you're going to see a volume entry for those partitions that are mounted at boot time as part of your file system.

---

### Post by kayaksan on 2017-04-14
Thank you for the links. Yes, I made sure to disable fast startup. When it was enabled I couldn't even boot Ubuntu.


>  			 				[INDENT] 					I don't think you're going to see a volume entry for those  partitions that are mounted at boot time as part of your file system. 				
[/INDENT] 			
  			   		


Is there an application that makes it possible? Like, if I were to switch files, could I do that through the partitions?

---

### Post by efflandt on 2017-04-14
In "Files" app (nautilus), "+ Other Locations" should show your Linux partition(s) and other partitions that Linux can access. Other partitions that are not mounted can be mounted by clicking on them and if they have an eject button can be unmounted (umount) by clicking on that button.

---

### Post by kayaksan on 2017-04-15
>  			 				[INDENT] 					In "Files" app (nautilus), "+ Other Locations" should show your  Linux partition(s) and other partitions that Linux can access. Other  partitions that are not mounted can be mounted by clicking on them and  if they have an eject button can be unmounted (umount) by clicking on  that button. 				[/INDENT] 			
  			   		


I can't find '+ Other Locations', although I know they should appear.

---

