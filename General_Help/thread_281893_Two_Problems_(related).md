---
title: "Two Problems (related)"
date: 2006-10-21
forum: General Help
---

### Post by unquenchablefire on 2006-10-21
I have two problems that are most likely related. When i installed ubuntu, i did it on my second drive, and to make sure that nothing got messed up in the install, i disconnected my main drive before instalation. 

Now when i turn on my computer, if the main drive (the one with windows) is plugged in, i boot into windows. If its unplugged, it boots into Ubuntu. Naturally, this first drive is not seen in ubuntu. 

Is there a way to have this drive made visible in ubuntu and, and if it is, how would i get grub - which loads only when my first drive is unplugged - to offer windows xp as an option? 

Also, how do i view the files that were on my harddrive before i installed ubuntu? I did not format the drive, so they are still there, but it says that my volume cannot be mounted.

---

### Post by catlett on 2006-10-21
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902) This how to explains how to set up a dual boot the way ytou are doing. All you ned to do is follow the part about after the install. Basically you will make ubuntu the master drive and windows the slave drive and keep them both connected. Next you have to add an entry to the grub menu for windows.
You ned to mount the partition you want to view. Here is a hpw to about mounting a windows partition [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) This procedure will work even if the partition isn't your windows partition. This basically explains how to mount a partition that is formatted as fat32 or ntfs

---

### Post by DaveBorealis on 2006-10-21
> **unquenchablefire said:**
> 
Is there a way to have this drive made visible in ubuntu and, and if it is, how would i get grub - which loads only when my first drive is unplugged - to offer windows xp as an option? 


In addition to the other advice, you could also go into the BIOS and set the drive containing ubuntu as the default boot.  That way the MBR with GRUB gets launched with each boot, and then you can choose either OS via GRUB.

Best regards,
Dave

---

