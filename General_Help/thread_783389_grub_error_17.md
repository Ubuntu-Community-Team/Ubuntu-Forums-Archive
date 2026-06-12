---
title: "grub error 17"
date: 2008-05-05
forum: General Help
---

### Post by paul101 on 2008-05-05
hi,


when i started up my pc this morning i get

> GRUB Loading stage 1.5.

GRUB loading, please wait...
Error 17



it just hangs there :(


i'm using the xubuntu live cd to post this :lolflag: (its a quad boot... xp, vista ubuntu and xubuntu)

---

### Post by lesergi on 2008-05-05
I think this helps you:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by paul101 on 2008-05-05
a big thank you for that... i can access xp and vista but...


when i go onto ubuntu, i get

> failed to mount drive

error 17


and xubuntu simply fails to exist!!

---

### Post by paul101 on 2008-05-05
sorry about the rather impatient bump (i'm going to bed in an hour)

---

### Post by lesergi on 2008-05-06
Mmmm... Did you use any partition program like Partition Magic in Windows??

I think your partitions numbers changed...

When you was in LiveCD, paste the content of /etc/fstab:

```
cat /etc/fstab
```

---

### Post by paul101 on 2008-05-06
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda11 swap swap defaults 0 0
/dev/sda13 swap swap defaults 0 0
/dev/sda5 swap swap defaults 0 0
/dev/sda7 swap swap defaults 0 0
/dev/sda8 swap swap defaults 0 0
/dev/sda9 swap swap defaults 0 0


i had partition magik installed before, and used it for my windows partitions (about 2 weeks ago)

---

### Post by lesergi on 2008-05-06
Do you know which partition is the linux root?

---

### Post by paul101 on 2008-05-06
no, i dont know...

i'm concidering formatting the whole hard drive and just installing xubuntu, then dual boot Vista and ubuntu when i get my hands on a vista disk


edit: i havent really got much on my pc :lolflag:

---

### Post by didac on 2008-05-06
After booting with the live-CD do in a terminal

```
sudo fdisk -l
```

and post it here

---

### Post by paul101 on 2008-05-06
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55aac49c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3583    28780416    7  HPFS/NTFS
/dev/sda2            3584        5789    17719598+   7  HPFS/NTFS
/dev/sda3            5790       36483   246549555    f  W95 Ext'd (LBA)
/dev/sda5           35374       35751     3036222   82  Linux swap / Solaris
/dev/sda6            5790        9798    32202229+  83  Linux
/dev/sda7           27969       28346     3036253+  82  Linux swap / Solaris
/dev/sda8           28347       34717    51175026   83  Linux
/dev/sda9           34718       34995     2233003+  82  Linux swap / Solaris
/dev/sda10          34996       35373     3036253+  82  Linux swap / Solaris
/dev/sda11          35752       36117     2939832   82  Linux swap / Solaris
/dev/sda12          36118       36483     2939863+  82  Linux swap / Solaris

Partition table entries are not in disk order



now, i just want to format the whole thing and install xubuntu on it

---

### Post by didac on 2008-05-06
OK, if you like strong solutions . . .

Maybe you could try one more time. Error 17 is caused by a shifting of partitions numbers. Boot again, press any key to prevent grub from booting the default and drop to a command line. There type:

```
root (hd0,4)
```

which could be your root partition. Grub will tell you. If not, try 

```
root (hd0,6)
```

Alternate from 0,3 to 0,7 until it recognizes it as an ext3 partition.

Once you get it, type:

```
kernel /boot/vmli
```

and press TAB to autocomplete the line. Add to that line 

```
root=/dev/sda6 ro
```

sda6 if root is (hd0,4). sda8 if root is (hd0,6)

Enter the full line, and type:

```
initrd		/boot/initrd.im
```

and press tab again to autocomplete. Then press enter.

Now type 

```
boot
```

and grub should start booting.

You'll have to reflect the new root in your /boot/grub/menu.lst

---

### Post by paul101 on 2008-05-06
i much prefer the machene-gun-method of re-formatting my hard drive lol as

windows xp is running out of space
windows vista is running out of space

my partitions look more like a train wreck :lolflag:


edit: i never use winduhs anyway

---

