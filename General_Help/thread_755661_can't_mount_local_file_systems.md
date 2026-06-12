---
title: "can't mount local file systems"
date: 2008-04-15
forum: General Help
---

### Post by rickycodie on 2008-04-15
so i don't know what happened, i installed xserver-xgl and then it freezes on me, so i restart in recovery mode and i get this error,

* mounting local filesystems . . . 
Failed to access ' /dev/disk/by-uuid/26CCE5FFCCE5C95F ' no such file or directory

and then i started x as root and ran gparted....it showed my disk as totally blank.... not even my windows partition showed up.

what is going on?

---

### Post by hal736 on 2008-04-15
First, don't panic.
Obviously, your Ubuntu is there, or you wouldn't be able to boot.  Running in single user mode(recovery mode) mounts root as read only, and doesn't mount all of the partitions.   Instead of running gparted in X, run fdisk at the command line.  This will give you the partitions of your hard drive.  On my T61p the following will work: fdisk /dev/sda 
You should then get something like this:

Command (m for help): 

type "p" (without the quotes) and it will print your partitions.

Here is what mine looks like:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         861     6914048   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         861        9551    69797888    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            9551       12161    20970241+   5  Extended
/dev/sda5            9551        9613      503431   82  Linux swap / Solaris
/dev/sda6            9614       10859    10008463+  83  Linux
/dev/sda7           10860       12161    10458283+  83  Linux

As for your issue with the xserver-xgl, I am not sure what the issue is, but if it doesn't freeze the whole system, and you can CTRL-ALT F2 (Hold CTRL-ALT then Hit F2) it will  put you at a login prompt,and  you should be able to start diagnosing the problem.  (also works with F1-F6).  To get back to the X window, Use the same procedure but with F7.  
 Hope this helps.

---

