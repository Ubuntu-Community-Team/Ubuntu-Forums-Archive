---
title: "How do I make a partition that'll be read/writable and appear after a fresh install?"
date: 2008-02-07
forum: General Help
---

### Post by jorwex on 2008-02-07
Hey all,

So I would like to format some empty space at the end of my drive with an ext3 partition, and give it a volume name so that it'll appear on my desktop automatically after a fresh install of Ubuntu. I tried to do all of that last night, but I screwed some things up. The two NTFS partitions that I have left over from my switch from windows have always magically appeared on my desktop, but I tried to do what I asked above and couldn't get it to work. Also, when I previously tried to do all that, the labels for my 2 NTFS partitions displayed fine on my desktop, but not in Gparted in the Label column---BUT my freshly labelled ext3 partition did have a label in that column...is that an indication of something wrong?

[IMG]http://glue.umd.edu/~jwexler/gparted_screen.png[/IMG]

---

### Post by bodhi.zazen on 2008-02-07
#################
Mount
#################

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)
[indent]Vista: Install the fs-driver using the "Windows XP compatibility mode"[/indent]

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by jorwex on 2008-02-07
What about after I do a fresh install of Ubuntu? Will these settings stick?

---

### Post by bodhi.zazen on 2008-02-07
I am not exactly sure what you are asking.

When doing a fresh install on Ubuntu you are given the opportunity to set up your partitions as a part of the install.

After you have installed Ubuntu, if you want to change how your partitions are mounted (or permissions), at any time, you need to follow the directions I posted.

---

### Post by jorwex on 2008-02-07
When you install ubuntu you're given the option to format partitions and are given a choice as to which drive you install on. 

It doesn't ask you which disks you want auto-mounted...it just does it, and I don't know what determines that. 

thats what my question was. sorry if i came off like a douchebag. 

**how does ubuntu decide what it automatically mounts without any user input** (like my NTFS partitions)**?**

---

### Post by bodhi.zazen on 2008-02-07
I attached two screen shots ....

When you install, select manual partitioning (see "part1.png")

On the next screen you will see all your partitions. Select one for root ( / ), format that  ....
Select your others. If you do NOT want them to be auto mounted after the install, manually edit the mount point to nothing, blank. If you want automount, keep the default or change the mount point.

DO NOT FORMAT any partition with data you wish to keep.

The installer will then set up /etc/fstab for you. 

I do not have a lot of partitions on that screen shot, but I think you get the idea ... (see "part2.png")

===========

Post install, you will need to manually edit /etc/fstab. I gave you a link.

In the options column change "defaults" to noauto.

If you want to add a partition, add a line for it in /etc/fstab. There is no gui tool to do this for you.

```
sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab
```

---

