---
title: "Booting Ubuntu"
date: 2006-10-08
forum: General Help
---

### Post by Darrage on 2006-10-08
I've just installed a Windows partition on my Ubuntu machine, and now it's blocked out Linux. I still have a Linux partition, I just can't get in to it. I'm guessing I have to edit the boot.ini?

---

### Post by meng on 2006-10-08
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Darrage on 2006-10-08
> #

Select Manual Partition
#

Mount your appropriate linux partions:

    *

      /
    *

      /boot
    *

      swap
    *

      ...

#

DO NOT FORMAT THEM.
#

Finish the manual partitio

When I get to the part when I click manual partition, my hard drive is showing up as a single unallocated partition. :S

---

### Post by Darrage on 2006-10-08
Some screenshots if they'll help...

[GParted (and the partition editor in the install package) says I just have a blank harddrive.]("http://img242.imageshack.us/img242/6682/screenshotdg0.png")

But system->administration->disks shows that I have a Windows partition and a Linux one..

[http://img237.imageshack.us/img237/6709/screenshot1oa3.png](http://img237.imageshack.us/img237/6709/screenshot1oa3.png)

[http://img237.imageshack.us/img237/9758/screenshot2yo1.png](http://img237.imageshack.us/img237/9758/screenshot2yo1.png)

---

### Post by meng on 2006-10-08
It's a bit worrying that you can't examine free space on your Linux partition. I don't know exactly what it means though.

---

### Post by Darrage on 2006-10-08
Oh dear. Well, I got the idea that following this link might be a good idea:

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

So I did, but now when I restart, Grub shows 4(!) Linux partitions and no Windows ones. However, Grub encounters an error when it tries to open ANY of them, even the recovery ones.

How do I stop grub opening at the start now? I'm hoping then I'll at least be able to get into Windows.

---

