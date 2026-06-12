---
title: "Share Evolution mail between Windows and Ubuntu"
date: 2006-10-10
forum: General Help
---

### Post by sawjew on 2006-10-10
Does anyone out there know of a way to share evolution folders between windows xp and Ubuntu.  Unfortunately I have to use XP occasionally and I would like to check my email while I am there.  I use Evolution exclusively because it provides all my calendar, tasks and contacts all together which Thunderbird doesn't.

I have a shared thunderbird folder on my laptop and I would like to accomplish the same with Evolution on my desktop.  A symlink would seem to be the easiest way but windows doesn't do symlinks and I can't store on my windows partition because it is ntfs and Ubuntu can't write to it.

Does anyone have any ideas?

---

### Post by Jongi on 2006-10-10
It's for reasons like these that I always create a small FAT32 partition. In that way programs common to Linux and XP can have a space to share data.

If your Ubuntu is on an ext2/3 partition, I seem to remember way back when I used to install on ext3 there was a driver for XP available to view ext2/3 partitions. I don't know how that has progressed in terms of being able to write to an ext3 partition as well.

If you are feeling brave, there is a program called ntfs-3g which allows linux to write to a ntfs partition. This is a risky path to take especially on a partition where losing information would be critical.

---

### Post by sawjew on 2006-10-10
I have windows on an ntfs partition, ubuntu on a reiserfs partition and a larger ext3 partition which is shared between the two systems.  The ext3 partition is my home partition for ubuntu and the documents directory is set as My Documents for Windows so all my documents are shared between the two systems.  I use the ext2ifs driver and windows reads/writes flawlessly to the ext3 partition.

I have my firefox directory shared using the ubuntu firefox directory as the common directory.  I have exactly the same setup on my laptop and I have firefox and thunderbird sharing between windows and linux (Xubuntu).

I am just in the process of trying the ntfs-3g drivers and I have read/write access to my ntfs partition.  Unfortunately I seem to have lost my desktop icon and Computer drive icon, but I can sort that out somehow.  I might try symlinking evolution now and see how it goes, all my critical files are on the ext3 partition.

---

### Post by Jongi on 2006-10-10
Is it then not possible to point the profiles for Evolution to the same place on the ext3 drive?

---

### Post by huygens on 2006-10-10
I am really curious, how do you tell Evolution where its profile is?

---

### Post by sawjew on 2006-10-10
> I am really curious, how do you tell Evolution where its profile is?

This is exactly what I am trying to find out.  I have spent hours searching and I have not found out the answer.  I am about to try symlinking the two profiles and see if that works.

---

### Post by castawaybcn on 2007-09-10
I know this is a rather old post, but I'm curious to know if you found a way out since I'm trying the same thing myself. And for a start I can't even copy some of the files onto a FAT32 partition :(
Should you have time please take a look at my post asking for some help
[http://ubuntuforums.org/showthread.php?p=3341572#post3341572](http://ubuntuforums.org/showthread.php?p=3341572#post3341572)
thanks a lot

---

