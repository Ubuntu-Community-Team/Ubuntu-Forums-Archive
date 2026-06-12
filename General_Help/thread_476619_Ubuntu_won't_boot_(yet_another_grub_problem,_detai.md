---
title: "Ubuntu won't boot (yet another grub problem, details inside)"
date: 2007-06-17
forum: General Help
---

### Post by ticopelp on 2007-06-17
Somehow I managed to do it to myself yet again... I'm chalking this up as a learning process! 

I could use some help getting my Ubuntu install to boot again. Currently, it won't boot, or even give an error of any kind, it just goes to a blank screen when I start the machine. 

I tried reinstalling Grub... I couldn't get it to work. When I type

```
find /boot/grub/stage1
```

I get: 

> Error 15: File not found

Trying to setup grub manually resulted in 

> Error 17: Cannot mount selected partition

I even burned an ISO of Super Grub Disk and tried going that route, but it failed at everything I tried to do. 

I currently have only one HD on the machine. Here's the results of fdisk -l:

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
86 heads, 15 sectors/track, 242311 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1      208090   134217727+   4  FAT16 <32M

Disk /dev/hda1: 137.4 GB, 137438952960 bytes
86 heads, 15 sectors/track, 208089 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/hda1p1   *           1      208090   134217727+   4  FAT16 <32M
```

I suspect I may have screwed something up with my incompetence... if anyone has any ideas or help, I'd appreciate it a great deal. Thanks.

---

### Post by merlinus on 2007-06-17
Are you running from the ubuntu live cd?

If not, where did you enter 

```

sudo fdisk -l

```

because the results do not show any linux partitions.

-merlin

---

### Post by ticopelp on 2007-06-17
Yes, I'm running from the Live CD, that was from the terminal from the Live CD boot.

---

### Post by ticopelp on 2007-06-17
So, did I wipe my partition out when I tried to install grub manually?

---

### Post by merlinus on 2007-06-17
I am afraid that it sure looks that way....

fdisk is reporting two partitions, but they are exactly the same except for the name, and FAT16.

Hopefully you have backups of important data....

If not, you might try booting from a recovery cd, try to mount the partition, and see if the contents are visible.

Knoppix may also work -- [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

-merlin

---

### Post by louieb on 2007-06-17
You must be one those lets press this key and see what happens types. Weirdest fdisk -l listing I have ever seen. Don't have a clue I've never screwed one up so that it looks quite like that. Might try the System Rescue CD (Google it) it has a partition guessing program and a data recovery program on it.

---

### Post by ticopelp on 2007-06-17
Heh, yeah, I honestly don't know how I managed to screw it up so badly. It really wasn't my intent. 

I'm running Testdisk right now to try to retrieve my data and reinstall. The good news is, according to Testdisk, all the data appears to be there, I just have to recover it. But, I knew this was a possibility when I started, so it's not unexpected, and I know who to blame (me :))

Thanks for the help.

---

