---
title: "[SOLVED] Can't write to extra ext3 partition in GUI"
date: 2008-06-02
forum: General Help
---

### Post by johnnyhop on 2008-06-02
I've 4 partitions on my hard drive.  Sda4 is home sda1 is /, sda3 is swap and sda2 is a larger empty partition formatted as ext3.  Click and drag is good from sda2 to home but not home to sda2, must sudo from terminal to copy to sda2.  I've experimented with fstab and now wrote the same options as home, previously wrote all default options and changed "nouser" to "user" but permission denied when writing within KDE-Dolphin.

---

### Post by plucky on 2008-06-03
> Can't write to extra ext3 partition in GUI
I've 4 partitions on my hard drive. Sda4 is home sda1 is /, sda3 is swap and sda2 is a larger empty partition formatted as ext3. Click and drag is good from sda2 to home but not home to sda2, must sudo from terminal to copy to sda2. I've experimented with fstab and now wrote the same options as home, previously wrote all default options and changed "nouser" to "user" but permission denied when writing within KDE-Dolphin.



You probably need to change permissions for the partition for your user to write to the partition.

See the link on **Psychocats** website on [howto mount linux partitions](http://www.psychocats.net/ubuntu/mountlinux)


Good luck

---

