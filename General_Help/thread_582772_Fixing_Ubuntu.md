---
title: "Fixing Ubuntu"
date: 2007-10-20
forum: General Help
---

### Post by Sanctus Messor on 2007-10-20
So for those who helped last time, I just had to redo the entire thing. So its a completely fresh install and I'm not sure how to tell which sata port its on. So my rig is set up with one 500GB HDD for my Ubuntu and one 500GB HDD for my Windows (I play games  XD) I installed the Ubuntu and got everything up and running then install my windows and got everything up and running and then when I went back to boot the hard drive with Ubuntu on it GRUB Error 17'd me out... EVERY TIME... So how can this be remedied? I am afraid to reinstall Ubuntu fo fear that it my run over my Windows and I'll have to redo that. 

Here was one option, thoughts. Redo it all one last time, RAID0 the two HDD's and partition it out for Ubuntu and Windows. Also, I was advised to use reiserfs format for my Ubuntu, should I stick with ext3 or which would you recommend?

Thanks for the help everyone,
It is greatly appreciated.
Sanctus

---

### Post by Page on 2007-10-20
I wouldn't do a raid if you're just going to partition the whole thing again anyway. I would just allocate one of the drives to each OS.  Unless you are planning to reinstall windows again, I wouldn't mess with partitions, since it is easy to hose your system if you do something wrong. (e.g. resize NTFS partitions without having the packages necessary to do it safely)  I tell everyone who asks that the safest way to try out ubuntu is to find a spare hard drive someplace, install it, and put ubuntu on that. 

I haven't used ReiserFS, so I can't advise you on that. Ext3 has always served my needs rather well.

When setting up a dual boot, oyu have to install windows first, and then install ubuntu. (if you did it the other way, I'm surprised you still have grub installed, windows usually nukes any other bootloader during install)

Windows also seems to like being on the master drive, Ubuntu seems to do just fine on the slave.


Another reason is that your grub may be configured wrong. Post your grub's menu.lst file. (located in /boot/grub)

---

