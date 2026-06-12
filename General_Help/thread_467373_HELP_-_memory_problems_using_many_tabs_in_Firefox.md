---
title: "HELP - memory problems using many tabs in Firefox"
date: 2007-06-07
forum: General Help
---

### Post by agger on 2007-06-07
I think this problem is related to a memory leak in Firefox, but it also has to do with the fact that swap may be allocated wrongly/not at all on my installed system.

BACKGROUND: I'm running on an old machine, 450MhZ Pentium II with 256 megs of RAM. I'm running a Xubuntu 7.04 installation, upgraded twice, dapper->edgy and edgy->feisty. I'm normaly using Xfce or Fluxbox as window manager.

Sometimes, especially when using Firefox with many tabs, or when starting the GIMP while working in Firefox, or when entering a page with Flash animations, everything comes to a halt, and all I'm seeing is the rotating disk which means "busy". 

*Sometimes* I can exit using CTRL-ALT_BACKSPACE, sometimes I can't - and the only way to exit is by pulling the plug.

Here's my theory: Firefox is using too much memory and not releasing it, and a sudden increase - e.g., starting the Gimp - causes the system to run out of memory, and the system to come to a grind.

Is this normal for low-end systems - or is it because my swap space is wrongly configured?

If I run "top" in a terminal, I get this:

```

top - 23:16:58 up 34 min,  2 users,  load average: 0.60, 0.76, 0.69
Tasks:  80 total,   2 running,  77 sleeping,   0 stopped,   1 zombie
Cpu(s):  2.6%us,  0.7%sy,  0.0%ni, 96.0%id,  0.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    256136k total,   249524k used,     6612k free,     1564k buffers
Swap:        0k total,        0k used,        0k free,    74284k cached


```
and this begs the question: Why Ok swap space? I didn't do anything special during installation, but with 256 Megs of RAM, why don't I have something like 256 Megs of swap space too?

And what do I do to get it? Is this my problem here?

Any help would be greatly appreciated.

best regards,
Carsten

---

### Post by Ozeuss on 2007-06-07
that might be your problem. when i had my swap not loading at startup, it would halt the system really quick. I wonder what it means by the "cached" swap.
does the system monitor reconize it at all? do you have a swap partition? if not, you can create a swap partition or file. there are more detailed howto's, but basically:
 if you allocated a partition (for instance using gparted), you can run
```
mkswap /dev/sdX
```
where x is the partition number for swap (or hdX, depends on your ubuntu)
and then 
```
sudo swapon -a
```
you should also edit your fstab, so the system will know to load swap automatically.

---

### Post by Ozeuss on 2007-06-07
something just occured to me, while re-reading your post. when upgrading from dapper to edgy, the fstab file is changed to the UUID naming method instead of the old one. it might break your swap. so, if you do have a swap partition already (if it is not formatted correctly, correct it), i suggest you try and correct the fstab from the UUID naming to the regular one.

---

### Post by agger on 2007-06-07
> **Ozeuss said:**
> something just occured to me, while re-reading your post. when upgrading from dapper to edgy, the fstab file is changed to the UUID naming method instead of the old one. it might break your swap. so, if you do have a swap partition already (if it is not formatted correctly, correct it), i suggest you try and correct the fstab from the UUID naming to the regular one.

These are the contents of my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=af5d3ddf-1201-492f-ac77-b685f5696622 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=ac45ee3f-c321-44c6-9276-075c19045a45 none swap sw 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

So what should I change it to? As it is, the "swapon -a" command fails with the message:

swapon: cannot stat /dev/disk/by-uuid/ac45ee3f-c321-44c6-9276-075c19045a45: No such file or directory

---

### Post by CheeseQueen452 on 2007-06-07
My advice is to upgrade your hardware. I had a 1ghz processor with 512mb of RAM, & streaming videos were painful to watch! They were choppy & skipped like a record! Now I have a 2ghz processor & 1gb of RAM, & things are much better. Once you upgrade, you'll notice a BIG difference!

> **agger said:**
> I think this problem is related to a memory leak in Firefox, but it also has to do with the fact that swap may be allocated wrongly/not at all on my installed system.

BACKGROUND: I'm running on an old machine, 450MhZ Pentium II with 256 megs of RAM. I'm running a Xubuntu 7.04 installation, upgraded twice, dapper->edgy and edgy->feisty. I'm normaly using Xfce or Fluxbox as window manager.

Sometimes, especially when using Firefox with many tabs, or when starting the GIMP while working in Firefox, or when entering a page with Flash animations, everything comes to a halt, and all I'm seeing is the rotating disk which means "busy". 

*Sometimes* I can exit using CTRL-ALT_BACKSPACE, sometimes I can't - and the only way to exit is by pulling the plug.

Here's my theory: Firefox is using too much memory and not releasing it, and a sudden increase - e.g., starting the Gimp - causes the system to run out of memory, and the system to come to a grind.

Is this normal for low-end systems - or is it because my swap space is wrongly configured?

If I run "top" in a terminal, I get this:

```

top - 23:16:58 up 34 min,  2 users,  load average: 0.60, 0.76, 0.69
Tasks:  80 total,   2 running,  77 sleeping,   0 stopped,   1 zombie
Cpu(s):  2.6%us,  0.7%sy,  0.0%ni, 96.0%id,  0.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    256136k total,   249524k used,     6612k free,     1564k buffers
Swap:        0k total,        0k used,        0k free,    74284k cached


```
and this begs the question: Why Ok swap space? I didn't do anything special during installation, but with 256 Megs of RAM, why don't I have something like 256 Megs of swap space too?

And what do I do to get it? Is this my problem here?

Any help would be greatly appreciated.

best regards,
Carsten

---

### Post by Ozeuss on 2007-06-08
first make sure that the swap really exists with
```
sudo fdisk -l
```
that will output your partition table, /dev/hda5 should read "82 Linux Swap/Solaris"

if that's ok, first copy your old fstab to have a backup, just in case.
```
cp /etc/fstab /home/$USER/fstab.backup
```
that will copy your fstab file to your home directory. you can put it anywhere you like.

then, your fstab should look like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=af5d3ddf-1201-492f-ac77-b685f5696622 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
# UUID=ac45ee3f-c321-44c6-9276-075c19045a45 none swap sw 0 0
/dev/hda5 none swap sw 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

as you can see, i commented out the swap UUID, and added a regular one.
now try 
```
sudo mount -a
``` which loads your partition tables from fstab or swapon -a, which load onl;y swap according to fstab.

---

### Post by agger on 2007-06-09
> **Ozeuss said:**
> 

as you can see, i commented out the swap UUID, and added a regular one.
now try 
```
sudo mount -a
``` which loads your partition tables from fstab or swapon -a, which load onl;y swap according to fstab.

Yay, it works! I now have 441748 K of swap. Thanks a lot, I expect to see a real improvement when running many tabs and other problems simultaneously now!

best regards,

Carsten

---

### Post by Ozeuss on 2007-06-09
great! glad it solved your problem.
BTW- i also suggest you 'tame' your firefox in about:config so it uses less memory. there are alot of guides out there.

---

### Post by Endolith on 2007-11-10
I had similar problems with the swap not being configured.  Now that I've got it configured, it still locks up sometimes, as I leave lots of things open in unfinished states.  Surely even the most careless user shouldn't be able to lock up the entire computer and make it unresponsive.  Is there a way to prevent this?  Why doesn't it start writing to any empty space it can find when the swap space runs out?

---

