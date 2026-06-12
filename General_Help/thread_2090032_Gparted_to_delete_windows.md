---
title: "Gparted to delete windows"
date: 2012-12-01
forum: General Help
---

### Post by Enigmapond on 2012-12-01
Can I simply re-format to ext4, the partition containing Windows with gparted to delete this horrible thing taking up space on my computer? Thanks in advance!

---

### Post by gnusci on 2012-12-01
Well, you can use GParted to modify you partitions, it is a great software, I use it every time, but Disk Utility is also great now.

---

### Post by gerowen on 2012-12-01
> **Enigmapond said:**
> Can I simply re-format to ext4, the partition containing Windows with gparted to delete this horrible thing taking up space on my computer? Thanks in advance!

GParted has a LiveCD version you can download to just delete the partition altogether, and then stretch your Ubuntu partition up to fill the rest of the space.  As always I would recommend backing up anything you like as a "just in case" measure.  The reason I mention the LiveCD version is because I don't believe you'd be able to resize your Ubuntu partition while it was mounted and in use, so you'd have to do it from a LiveCD.

---

### Post by ohnonot on 2012-12-01
i would say the answer is a simple yes.

but the other answers aren't wrong.

stretching an existing partition with ubuntu on it over your whole hard drive might be possible but definitely takes some time and potential risk.
but why not just use the extra partition as it is? it's fairly easy to add it to your fstab so it gets mounted automatically.

---

### Post by Enigmapond on 2012-12-01
Thank you all for your responses! I will try the live CD for gparted as that seems easiest.

> **ohnonot said:**
> i would say the answer is a simple yes.

but the other answers aren't wrong.

stretching an existing partition with ubuntu on it over your whole hard drive might be possible but definitely takes some time and potential risk.
but why not just use the extra partition as it is? it's fairly easy to add it to your fstab so it gets mounted automatically.

You mean keep it NTFS? for what purpose....or do you mean just have it as a separate partition formated ext4? Can you explain more what you mean and just how to add it to fstab? Thanx again!

---

### Post by ohnonot on 2012-12-02
> **Enigmapond said:**
> Thank you all for your responses! I will try the live CD for gparted as that seems easiest.
You mean keep it NTFS? for what purpose....or do you mean just have it as a separate partition formated ext4? Can you explain more what you mean and just how to add it to fstab? Thanx again!
erm, just let me get this clear:
you have a computer with both linux and windows on different partitions and now you want to get rid of the one containing windows?
in that case you don't need a livecd.
just fire up gparted, select your hard drive in question in the top right corner, identify the windows partition, highlight it and choose partition->delete.
apply changes.
then highlight the free space, choose partition->new and create ext4 partition or whatever you prefer. which you can then use for movies or pictures of dubitable nature or what. apply changes.

[edit: forgot the fstab thing. you can see the uuid from gparted and add it to fstab with a mount point of your choice and default settings]

you're done with windows now, congratulations!

---

### Post by Enigmapond on 2012-12-02
Right on all accounts and right on for the solution! I was just needing verification that's all I need do. Trashing that piece of bad code now. Thank you & Cheers!

---

