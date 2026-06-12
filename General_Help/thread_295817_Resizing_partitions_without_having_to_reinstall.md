---
title: "Resizing partitions without having to reinstall?"
date: 2006-11-08
forum: General Help
---

### Post by jogebau on 2006-11-08
Hi,

This is what I want to do:

Ive got a laptop with 40 gigs of hd, two partitions one with ubuntu and one (the first one) XP. The XP partition is 30 Gigs, Ubuntu has 10. 

Now I want to flatten the XP partition, resize both to about 20 Gigs, and reinstall XP.

Is there any way of doing this without having to reinstall Ubuntu?

Im running edgy.

Thanks

---

### Post by taurus on 2006-11-08
I guess you can use gparted to resize your harddrive.

---

### Post by LenzM on 2006-11-08
> **jogebau said:**
> Hi,

This is what I want to do:

Ive got a laptop with 40 gigs of hd, two partitions one with ubuntu and one (the first one) XP. The XP partition is 30 Gigs, Ubuntu has 10. 

Now I want to flatten the XP partition, resize both to about 20 Gigs, and reinstall XP.

Is there any way of doing this without having to reinstall Ubuntu?

Im running edgy.

Thanks

If you're planning on wiping the XP drive it should be pretty easy.
Install 'gparted', it will appear as GNOME Partition Editor in System->Administration
Choose the windows partition and delete it, then choose the ubuntu partition and click on the resize button.
Then you can install windows in the unformatted space.
You're going to have to repair grub after you reinstall windows though.

---

### Post by aum11 on 2006-11-08
I use the gparted live distro and have found it excellent.  It will enable You to change your Linux root partition size.

With the xp partition, if you defrag it first so that all of the files are at the front of the partition, then You can then safely shrink it via gparted.  I mention this in case this will help avoid a reinstall of XP.

Naturally backup first if in any doubt.  This is dangerous territory.

---

### Post by jogebau on 2006-11-09
I just remebered that I might have another prob:

The Swap Partition might be between these two partitions, can I just move it, or will this cause problems?

CU

---

### Post by CatKiller on 2006-11-09
Since the first drive is for XP and is going to be made smaller, you're going to have to move the start of your (presumably) ext3 partition. You'll need to use the [GParted live cd]("http://gparted.sourceforge.net/livecd.php"), since the version included there has full move support. The version in the repositories is too old. The GParted cd does not mount swap partitions, so that should be OK too.

---

### Post by jogebau on 2006-11-09
yep all worked perfectly
thanks

---

