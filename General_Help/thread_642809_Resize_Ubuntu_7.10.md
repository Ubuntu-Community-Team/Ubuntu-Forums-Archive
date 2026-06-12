---
title: "Resize Ubuntu 7.10"
date: 2007-12-17
forum: General Help
---

### Post by kingkilr on 2007-12-17
I just installed Ubuntu 7.10 with Wubi(went great)!  Homever I just read the tutorial on how to install World of Warcraft with Wine(this was originally supposed to be only for my coding:lolflag: ) and now I think I'm up to the task.  However, I didn't allot nearly enough space for Ubuntu, there is plenty of space on the windows partition that ubuntu is installed on, but I can't find any instructions on how to resize Ubuntu.

Any help would be appreciated! Thanks

---

### Post by chewearn on 2007-12-17
To resize ubuntu partition:

1. Boot from LiveCD (the partition must be unmounted for you to be able to resize it).  You can use your Ubuntu liveCD, [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/"), or other partition tool.

2. If you use Ubuntu LiveCD, go to: top panel > System > Administration > Partition Editor.  If you use GParted LiveCD, it will boot to the working GParted application.

The rest should be self-explanatory, since GParted application is GUI.

---

### Post by daspooky on 2007-12-17
> **AstalaVista said:**
> To resize ubuntu partition:

1. Boot from LiveCD (the partition must be unmounted for you to be able to resize it).  You can use your Ubuntu liveCD, [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/"), or other partition tool.

2. If you use Ubuntu LiveCD, go to: top panel > System > Administration > Partition Editor.  If you use GParted LiveCD, it will boot to the working GParted application.

The rest should be self-explanatory, since GParted application is GUI.

Does that procedure work for wubi?

---

### Post by chewearn on 2007-12-17
Opps, sorry about that, missed the word "Wubi".
No, I don't think the procedure will work with Wubi.

Here is [WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by ago on 2007-12-17
Do that,

1) create a large contiguous empty file in windows
2) in linux format the file as ext3 (mkfs.ext3 /host/path/to/file)
3) mount it 
4) cp -a /usr/* /path/to/mountpoint
5) add a line to /etc/fstab to mount /usr to your new mount point
6) reboot, you can now delete the files previously in root.disk/usr

similar procedure for /home, if you look into this forum there are more detailed guides. You can also use LVPM for that.

---

### Post by kingkilr on 2007-12-17
I ended up just reinstalling Wubi, because I'm so scared of breaking things.  It's up and running now, but I have a few graphics problems, to some other section of the forums I go!

---

