---
title: "Safely uninstalling Ubuntu 12.04.1 LTS from Dual-booted Windows 7 PC?"
date: 2012-11-03
forum: General Help
---

### Post by Eirreann on 2012-11-03
I got myself a pretty nice laptop recently, and so I'm moving Ubuntu from my gaming desktop to there, so I can keep work and play separate, haha!  Anyway, I tried to search Google for ways to uninstall Ubuntu from a dual-booted PC safely, and found a lot of different methods of doing so.  Could anyone recommend to me the best one?  Preferably one that does not require me to reinstall Windows or wipe my hard drive?

P.S.  I don't know if this makes a difference, but when I installed Ubuntu I used the partitioning tools to make the Ubuntu partitions, rather than using the software on the disk to automatically install it alongside Windows.  When I did it that way, I noticed that the GRUB2 loader did not replace the usual Windows 7 boot loader... I actually had to use some 3rd party software to set it up so that my computer recognised that Ubuntu was installed and adjusted the Windows 7 boot loader to enable me to choose between Windows 7 and Ubuntu on start up, and only after I selected Ubuntu would it go to the GRUB2 loader, if that makes any sense.

---

### Post by 2F4U on 2012-11-04
There is a tool available to do this:

[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)

I guess the safest way would be to boot from a Ubuntu liveCD, install the application in the live session and remove Ubuntu from there.

Since you are using some third-party tool to manage the boot process you have to take care of this yourself.

---

### Post by black veils on 2012-11-04
best to give us info of your partition layout:

open the Terminal, copy-paste the following into it```
sudo fdisk -l
```that last character is a lower case L

press Enter

copy-paste the results to your post.

---

