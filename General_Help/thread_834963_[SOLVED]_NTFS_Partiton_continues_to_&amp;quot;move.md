---
title: "[SOLVED] NTFS Partiton continues to &amp;quot;move&amp;quot;"
date: 2008-06-20
forum: General Help
---

### Post by bmxmann on 2008-06-20
Hello,

I have been using Hardy for a little while now.  I started off as a Windows user, so I still have all the files that I care about on an NTFS partiton (though I no longer run Windows at all).

I have been using Amarok to play all of my music that I have stored on my NTFS partition.  I currently have 2 HD's installed, one SATA drive that has my NTFS partition, as well as my Swap and EXT3 partiton that Ubuntu is installed on.  The other drive is an IDE which I was using to test out OSx86.  

The biggest problem that I currently face is that I have gone and modified the fstab file, and added in   

/dev/sda3 /mnt/Content ntfs-3g defaults,locale=en_US.UTF-8 0 0 umask=0222 0 0

To mount my NTFS partiton automatically every time.  This works fine and dandy most of the time, but for some reason my NTFS partiton will change from /dev/sda3 to /dev/sdb3.  So when I log in, I have some folders on my desktop that are shortcuts to some of my folders on the NTFS partition, and they will display the broken link image.  I then go and open Places, select the name of my NTFS drive which mounts it to /media/.  I then go into a terminal and do a df -h, see what the partition is set for now /sda or /sdb, change the fstab file to reflect it, and then reboot the computer.

can I put a wild card in place of a or b?  is there some simple thing that I am missing?  i have not been able to find any reasoning to when it will change.  Did that make any sense?


another issue that I think will probably be an easy fix for you Linux gurus is that my boot loader is installed on the IDE drive that OSx is installed on, so it is no longer allowing me to boot to OSx, and when I take the IDE drive out, I can no longer boot into ubuntu.  I imagine that there is a command that will re-run the grub installer (or whatever boot loader they are using now), I just have no idea what that would be. Or could I add OSx to the grub menu?  not sure how I would do that though (did it once for Windows, but I cant even see the OSx partitions in linux).

any help would be appreciated, its not a huge deal for me as I know how to fix it, but the wife gets a bit cranky when she cant listen to her music! :guitar:

---

### Post by logos34 on 2008-06-20
> **bmxmann said:**
> is there some simple thing that I am missing? 

Use UUIDs.

**sudo blkid**

or

**ls -l /dev/disk/by-uuid**

substitute for '/dev/sda3' in fstab.  Also, you should be using uuid im /boot/grub/menu.lst also (i.e.
'kopt=root=' and 'kernel' lines with 'root=UUID=xxx-xxxx-xxx...')

> 
another issue that I think will probably be an easy fix for you Linux gurus is that my boot loader is installed on the IDE drive that OSx is installed on, so it is no longer allowing me to boot to OSx, and when I take the IDE drive out, I can no longer boot into ubuntu. 

[install grub to the MBR of the sata]("http://ubuntuforums.org/showthread.php?t=224351"), and change the 'root' lines in menu.lst to (hd**0**,?).  Put the sata first in the Bios hard disk boot order.

---

### Post by bmxmann on 2008-06-21
Just want to thank you!

Also, I did forget to change the menu.lst file before rebooting, I had to hit esc at the grub menu, press e for edit, and then change hd1,1 to hd0,1 then press b. I then changed the menu.lst for grub (sudo gedit /boot/grub/menu.lst) and change the location to hd0,1, as it had hd1,1.  In case anyone else runs into this issue (you know, inability to follow instructions).

Also using the UUID for the partition has been working perfect so far!  cant understand why it was changing..

---

### Post by logos34 on 2008-06-21
Glad to hear it's working now.  

Mark thread as 'Solved'.

Enjoy!

---

