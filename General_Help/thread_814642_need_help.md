---
title: "need help"
date: 2008-05-31
forum: General Help
---

### Post by AznPat on 2008-05-31
i partition my hard drive wrong when i was installing my ubuntu now i cant see windows xp anywhere..i try to use the recovery disc for my laptop but grub just takes over,if any can help me or give an advice to get xp back i would appreciate it..i really need help..thank you

---

### Post by Lord Xeb on 2008-05-31
How did you install Ubuntu? Did you do all default?

---

### Post by AznPat on 2008-05-31
yeah i didnt really know what i was doing,i tried to do recovery cd but grub just comes up..can u help me out

---

### Post by Sef on 2008-05-31
Let's check out your partitions.

Applications > Accessories > Terminal

Then type or copy and paste in this code:  ```
sudo fdisk -l
``` Small L, then copy and paste the results in a new post.

---

### Post by buntunub on 2008-05-31
First, determine wether or not youve still got windows on your drive(s) -

```
$sudo fdisk -l
```

or 

```
$df -h
```

If its still there, and if it is, it should be on sda1, then all you have to do is fix your menu.lst to include the chainloader +1 on whatever setup your using (0,1) for example. Here is my /boot/grub/menu.lst as an example -

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by AznPat on 2008-05-31
> **Sef said:**
> Let's check out your partitions.

Applications > Accessories > Terminal

Then type or copy and paste in this code:  ```
sudo fdisk -l
``` Small L, then copy and paste the results in a new post.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef2aef2a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9566    76838863+  83  Linux
/dev/sda2            9567        9729     1309297+   5  Extended
/dev/sda5            9567        9729     1309266   82  Linux swap / Solaris

---

### Post by vvvladut on 2008-06-01
It's buh-bye XP then...

There are methods of trying to recover data, or partial data, from what used to be your XP partition. As a rule to start would be to stop using the partitions that overwrote the XP partition - and that pretty much means don't use this computer, in your case. 

You should wait for someone with a bit more Linux knowledge that could explain you how to try this, or search this forum, I've seen a few threads on the subject.

Next time you decide to install a new operating system, remember to backup, backup, backup your important data first. 

Sorry if I can't be of more help.

---

### Post by AznPat on 2008-06-01
i got a recovery cd but for some reason when i try to use it just goes straight to grub

---

### Post by Joeb454 on 2008-06-01
You're probably not booting from the CD then. You need to change your BIOS.

And is it a Full XP install disc? Or a recovery disc that requires the recovery partition that OEM's stick on PC's now?

---

