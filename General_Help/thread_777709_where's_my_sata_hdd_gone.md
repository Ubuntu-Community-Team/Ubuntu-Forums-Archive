---
title: "where's my sata hdd gone"
date: 2008-05-01
forum: General Help
---

### Post by pabc on 2008-05-01
I've been running HH since the release candidate via wubi and all has been fine except today I went to grab a file off my sata hdd and couldnt see the drive.

my 2 ide drives were present, XP and Backup but the Files disk is missing.

The strange thing is that the wubi instal is on that Files hhd.

I know it was there at some point so some upgrade has borked it.

Any ideas as to how I can trouble shoot this problem?

P

---

### Post by pabc on 2008-05-06
anyone? I was getting to the point of transfering the wubi install to a proper one having switched the 2 reamining apps I cant find linux replacements for onto my xp laptop but unless I can work out why I can no longer see the SATA HDD I'll be stuck on XP for a while yet.

I have read there is a known bug with some sata drives having to be swithed into a different mode via the bios but there is no option on my bios to change things.

Ideas - please?

---

### Post by pabc on 2008-05-10
OK, getting there slowly with all your help!

I've found the disk. it's at /dev/sda1

I've figured out how to mount it to /media/files

I'm sure I've can figure out how to get it mounted automatically via fstab.

But I cant see it in the places menu - any ideas?

Also, why arnt the 2 other ide hard disks mounted via fstab - where/how are they getting mounted automatically on login?

I'm trying to understand whats going on here with a lot of reading but some help would be nice - please?

---

### Post by Gina on 2008-05-10
Ah good - the telepathy is working :lolflag:

This is an area I want to sort out too (though I'm not using Wubi - all normal installs).  All drives used to be automatically installed - now they're not.  I think it's a matter of setting it up in fstab but it looks complicated.  

I've been using Ubuntu for just over a year now and learnt a lot but there is still a vast amount still to learn about Linux.

---

### Post by Xiong Chiamiov on 2008-05-10
You should be able to add a line something like this to your fstab:
```

/dev/sda1   /media/files   {filesystem}   defaults   0   1

```
with {filesystem} being instead ext3, fat, or whatever you're using.

---

### Post by pabc on 2008-05-10
well i've just plugged in an external HDD and it was instantlly mounted in /media and shows up in 'Places' so I'm guessing there is some automount daemon running which doesnt recognise my sata drive hence having to mount it via fstab.

---

### Post by AThomsen on 2008-05-10
My drives sometimes shows up in "Places->Removable media" menu and other times just in "Places". Did you check there?

---

### Post by pabc on 2008-05-10
yep - it's not there.

it looks like the automount daemon (autofs?) doesnt spot the sata disk like it does the ide ones/thumb drives/external hdds etc.

Bugger.

---

### Post by Gina on 2008-05-10
My SATA drive partitions appear in Places under Removable Media but aren't mounted.  When I run an application that uses a partition other than / or /home it can't find it until I open it with nautilus or mount it some other way.  This is something that has only occurred during the very last stages of Hardy development - everything was working fine earlier.

---

### Post by Gina on 2008-05-10
Set up my main data partition to mount in fstab.  Needed the directory for the mount point made though.

---

