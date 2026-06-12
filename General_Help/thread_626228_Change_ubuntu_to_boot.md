---
title: "Change ubuntu to boot"
date: 2007-11-28
forum: General Help
---

### Post by Arminius_ on 2007-11-28
I recently tried to install XP after Ubuntu. When it installed, it stated that it was deactivating the other partition (ubuntu). How can I get Ubuntu to load?

---

### Post by meierfra on 2007-11-28
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Arminius_ on 2007-11-29
Thanks for the link. I tried unsuccessfully to find a one about my problem last night while running on a live cd. I'm going to give it a try when I get home tonight.

---

### Post by Arminius_ on 2007-11-29
I ran through the guide, and restarted. The problem is, I'm getting an "error 17: partition isn't mounted" or something like that. I remember that when I installed XP it unmounted my Unbuntu root partition. What can I use to mount root? I found this code on the link provided. It doesn't mention that as a use but it looks like a possibility.

> mkdir /mnt/root
mount /dev/xxx? /mnt/root
chroot /mnt/root /bin/bash
grub-install /dev/xxx

Any ideas or input from personal experience?:confused:

---

### Post by meierfra on 2007-11-29
Open a terminal, type
```
sudo fdisk -l
```
("l" is a lowercase L)

and post the output.

---

### Post by Arminius_ on 2007-11-29
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3e3d3e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6526    52420063+  83  Linux
/dev/sda3           19082       19457     3020220    5  Extended
/dev/sda5           19270       19457     1510110   82  Linux swap / Solaris

---

### Post by meierfra on 2007-11-29
It is /dev/sda1.  

But you really should not have to mount /dev/sda to install grub. Try this

```
sudo grub
```
and at the grub prompt:

```

root (hd0,0)
setup (hd0)
quit

```

If that didn't work, go ahead and try the chroot method:

```
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda1 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash

```
 
and then the same commands as  above:


```

sudo grub
root (hd0,0)
setup (hd0)
quit

```

and/or
```

sudo grub-install sda

```


But there is a chance that none of it works. You fdisk output looks a little bit suspicious. /dev/sda3 really should be /dev/sda2.   You might have to use testdisk ([Hermanzone on testdisk]("http://www.users.bigpond.net.au/hermanzone/p21.html"))   to fix your partition table.

---

### Post by Arminius_ on 2007-11-30
I only had time last night to try half the possibilities from your suggested code. I deleted the XP partition. I'm just going to install windows on an emulator. The only reason I want windows on my computer is so that I can actually use my Lexmark all-in-one.I will try the rest tonight or tomorrow. If that doesn't fix the problem, I'll give TestDisk a try. Thanks for all the help so far. This has actually been a great learning experience, though aggravating at times.

---

### Post by Arminius_ on 2007-11-30
Yeah, it looks like I'm gonna have to give Testdisk a try. If it doesn't work, I'm just gonna start over. I just recently installed it so there isn't anything critical that I couldn't live without. I really do appreciate all the help.:)

---

