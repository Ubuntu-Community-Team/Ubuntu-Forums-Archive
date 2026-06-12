---
title: "Ready to dump Winows and reclaim the disk space. How?"
date: 2007-05-10
forum: General Help
---

### Post by trmiv on 2007-05-10
I have Feisty installed on my laptop dual-booting with XP.  Since it's a laptop, space is at a premium and now that I'm comfortable with Ubuntu I really want to dump XP and go straight linux on this machine (and run XP in vmware).  Windows was on here first with two partitions.  One 10gb C, and a 70gb D.  I used gparted to resize the D and free space for Ubuntu which I installed into an 8gb /, 1gb swap and the rest to /home.   So now I want to get rid of windows and reclaim the lost space to Ubuntu.  

Now obviously the best way to do this would be to just back my files up, wipe the disk clean and reinstall Feisty.  But I've spent so much time tweaking my desktop, getting my fonts right, loading programs, getting my mx510 mouse working, etc, etc, etc that I REALLY don't want to have to do that stuff over.  Is there a way I can get rid of windows and reclaim the lost space and add it to the storage I have in my home partition?  Here is my partition table:

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1021     8195008+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4631        9729    40957717+   7  HPFS/NTFS
/dev/sda3            1022        2005     7903980   83  Linux
/dev/sda4            2006        4630    21085312+   5  Extended
/dev/sda5            2006        2129      995998+  82  Linux swap / Solaris
/dev/sda6            2130        4630    20089251   83  Linux

```

---

### Post by Stephen Howard on 2007-05-10
I'd probably save key files to a cd then reinstall ubuntu.  Once the reinstall is finished you can copy across the saved files.

The ones I'd save are:

[INDENT]your entire /home directory.
/etc/hosts
/etc/host.conf
/etc/resolv.conf
/etc/modules
/etc/X11/xorg.conf 
/etc/network/interfaces 
/etc/apt/sources.list[/INDENT]

The above might vary depending on the extent of your existing customisations, but the key ones are **xorg.conf** and the **/home directory.**

Also give some thought to the partition structure you want - a separate /home partition is very valuable because that allows you to nuke your linux installation but retain your personal settings in the /home partition.

Use this command to copy directories with all their attibutes (but keep in mind that upon reinstallation your user ID number might change - though probably not assuming your laptop only has a single user account):

```
cd /path/to/src/dir
find . | cpio -pdumv /path/to/dest/dir
```

---

### Post by firebadger on 2007-05-10
Yes, but it's slightly risky.  I would back everything up so that you could recover if need be and then use GParted to delete and resize your partitions as required.  The [GParted]("http://gparted.sourceforge.net/") Live CD is really useful for this sort of thing.

---

### Post by trmiv on 2007-05-10
So backup the stuff Stephen Howard told me to, backup all my windows stuff and then try to delete the NTFS partitions and resize the linux partitions into it.  Is there anything I need to keep in mind when I resize the C windows partition?

---

### Post by firebadger on 2007-05-10
Just make sure you have everything you need backed up from the whole physical drive.  Partitioning is risky.

Also, I don't quite understand your final sentence.  I thought you were deleting all the Windows partitions?

---

### Post by trmiv on 2007-05-10
I just mean when I delete what is the C partition and resize it.  It's the first partition on the disk, is it going to cause any issues when I resize it into my Linux partition?  I'd like to make it part of /.  Also, what about grub?  Since windows won't be there anymore is there something I need to do?

---

### Post by Stephen Howard on 2007-05-10
Hi trmiv,
[I]
It's the first partition on the disk, is it going to cause any issues when I resize it into my Linux partition? [/I]

You will probably need to mark it as the boot sector so that the master boot record is properly inserted - gparted likely has an appropriate menu option to do that.  I think the ubuntu installation will handle grub automagically and it will simply live in a /boot directory under /.

PS:  When restoring the backed up system configuration files (ie the ones that live in /etc), don't just blindly copy them back.  First do a 'diff' comparing the new ones with the backed up version to see what differences there are and consciously decide whether you need to do anything (ie, if video/mouse/kbd is working fine, then you probably don't want to copy over xorg.conf).

---

