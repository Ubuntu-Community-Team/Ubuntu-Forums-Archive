---
title: "Expand partition without losing configuration?"
date: 2014-06-02
forum: General Help
---

### Post by gabe7 on 2014-06-02
Hi all,

This is my first time posting, so I apologize if I provide irrelevant/omit relevent information. I started using ubuntu last year, and I'm loving it. Since then, I have been dual-booting ubuntu 13.04 and windows 7 on my Asus U47-A laptop. I just installed virtualbox, and have created a windows 7 VM which I think is sufficient for my windows-related use. Now, I would like to reallocate the disc space I have set aside for Windows to my Ubuntu partition, without losing my current configuration in Ubuntu-- i.e. I would like to retain not only my files, but also programs I have installed, etc. Does anyone who has done this have advice on the best/fastest/safest way to proceed? Thanks in advance,

-Gabe

P.S. The title of this post should be "Expand Partition *without* losing configuration." Obsiously, I would *not* like to lose my current configuration.

---

### Post by Bucky Ball on 2014-06-02
Welcome. Firstly, and slightly off-topic, 13.04 is no longer supported. I suggest you upgrade to 14.04 LTS.

Okay, now you are saying you want to get rid of Windows completely and use the space for Ubuntu's / partition? Then follow this:

Boot from a LiveCD or USB, 'Try Ubuntu', get to a desktop and open Gparted. In there you will see the Windows NTFS partition (and possibly other Win related NTFS partitions). Right click the NTFS partition and delete the Win partition then right click on Ubuntu's / partition and 'Resize'. Move the slider to use the free space you've left by deleting Win. Click apply and you're done! It may take awhile to resize but your Ubuntu files/folders/config will not (should not) be altered in any way.

Reboot and you should boot to the grub list or straight into Ubuntu. If not, follow one of the methods here to run Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Hope that helps and good luck.

---

### Post by oldfred on 2014-06-03
Edited title for you.

Another alternative, not that others are wrong, just what you may want to do.

I tend to prefer smaller system partitions and either data partition(s) which I use myself or a separate /home, so you separate system from data. This works for me, but I mount same data partitions in multiple installs. If you have one install the extra effort may not be worth while to set it up. But separate /home is still an alternative.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

    
       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Of course the only way to be sure with major changes is good backups.

---

