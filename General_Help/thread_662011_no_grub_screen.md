---
title: "no grub screen"
date: 2008-01-08
forum: General Help
---

### Post by sabatier on 2008-01-08
Hi, I'd be grateful if someone could help me. I reinstalled windows - deleted the partition and created a new one of the exact same size, making sure not to interfere with any of my Ubuntu partitions. T

The problem is that when I turn on the PC, it boots straight into windows without giving the option to select either Ubuntu or Windows. I'm missing this:
 [IMG]http://screencasts.ubuntu.com/videos/20061204_installing_dual_boot.jpeg[/IMG]

Can anyone tell me how I can get it back? By the way, I'm able to access the home and root partitions by means of the ext2 ifs utility for windows.

Best regards,

sabatier

---

### Post by mikewhatever on 2008-01-08
Reinstalling Windows overwrites GRUB in the MBR. See the link --> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29)

---

### Post by LaRoza on 2008-01-08
You need to reinstall grub, this issue comes up almost everyday....

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

