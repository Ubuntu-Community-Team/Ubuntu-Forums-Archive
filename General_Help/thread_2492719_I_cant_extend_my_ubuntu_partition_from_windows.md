---
title: "I cant extend my ubuntu partition from windows"
date: 2023-11-21
forum: General Help
---

### Post by lakepenrose on 2023-11-21
I already have an unallocated partition but I cant move that and I can't access ubuntu because there isn't even enough space to log into ubuntu. everything is done from windows but I cannot resize/move the ubuntu partition, nor the unallocated partition.

Unallocated is next to the Ubuntu partition. (cannot use screenshots, don't know why)

|  WINDOWS  | UNALLOCATED  | UBUNTU  |  OTHER   |

Anyways, how would I get unallocated to be added to ubuntu without gparted on live usb but using windows disk management?

---

### Post by ajgreeny on 2023-11-21
I would not use Windows to repair or carry out such management of Linux partitions in case it causes problems.

I admit I don't have or use Windows any more and have not done so for 18 years, so it may be safe to do what you're asking about.
However, I think it is much safer to boot to your live Ubuntu system and do everything from that using gparted.

Once in gparted, and assuming the the space is really unallocated and not simply free space in another partition, you should be able to extend the Ubuntu partition into that unallocated space.

Be sure you back up all your personal files before doing anything like this as there is always a risk editing partitions that you could lose everything; it may be unlikely but such disasters can, and do, happen occasionally.

---

### Post by yancek on 2023-11-21
Avoid this problem in the future by regularly running the command:  df -h  from Ubuntu if you are putting a lot of new data or installing a lot of software.  Start with a reasonably large root filesystem partition (25-30GB).

You either have unallocated space or partition.  You can have free space within a partition but that is not the same as unallocated space which is outside any partition.  The information you posted seems to indicate that you have unallocated space between windows and Ubuntu.  If you want to move Ubuntu to the left, you will be moving the boot files and there is a fair possibility you will have problems booting after ward.  I would definitely not use windows Disk Management for this as a live Linux OS from a usb with gparted will work much better.  If you have a Linux OS a on a usb, post the output of the command:  sudo fdisk -l here as that will give more detailed information on the actual size/location of partitions and sectors.

---

### Post by lakepenrose on 2023-11-23
With the state Linux is in with free space. I have no access to Linux nor gparted, I installed Linux to C: alongside Windows. So I have no ability to use anything other than disk management that I know of.

---

### Post by Rubi1200 on 2023-11-23
You need to boot the computer using a liveUSB with any recent version of Ubuntu. Then choose to Try Ubuntu. Once at the desktop, open a terminal either from the menu or with Ctr+Alt+T and run these commands:

```
sudo fdisk -l
```

and

```
df -hT -x squashfs -x tmpfs -x devtmpfs
```

Copy the output from the terminal and reply here using Go Advanced >> paste the output >> highlight the pasted text and then click on the # icon to wrap the text with code tags.

Once we see the results it will be easier to advise you on the next steps.

---

### Post by yancek on 2023-11-23
You need to get more information as suggested in multiple posts, use a live usb of any Linux, preferably a recent Ubuntu and post the output requested above.  I've seen sites that indicate this is possible with 3rd party commercial software and some that indicate it may be possible with windows 10/11.  Better off going to a windows forum or the miscrosoft support site for that info.

---

