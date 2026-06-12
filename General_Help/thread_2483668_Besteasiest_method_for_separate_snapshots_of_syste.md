---
title: "Best/easiest method for separate snapshots of system files and /Home files?"
date: 2023-02-06
forum: General Help
---

### Post by Advait on 2023-02-06
Newbie here. I'm using Ubuntu 22.04 on ext4.

My goal is to have robust and separate snapshots of my system files and my /Home files.

I'm looking at Ubuntu on btrfs with separate subvolumes for system files and /Home. 

I'm aware of NixOS, MicroOS, BlenderOS, VanillaOS, etc. But I know almost nothing about them except they're (I think) examples of immutable file systems. Is one of them a better way to reach my goal?

---

### Post by TheFu on 2023-02-06
You need a volume manager to support snapshots.  There are 3 commonly used on Linux systems, but not all Linux distros support all of them (for their internal reasons).  And not all installations support any.

The list is:
* btrfs
* zfs
* lvm2

BTRFS is probably find to use provided you don't extend volumes across more than 1 storage device or use virtual machines.

ZFS isn't well supported across Linux distros because of the ZFS license being an edge condition as far as Linus is concerned.  Distros, like Ubuntu, have tried to integrate ZFS into their releases a few times with different levels of success.

LVM2 has been used in enterprise Linux since the 1990s.  It is very much like Veritas Volume Manager, so for people already familiar with that tool (or the clones used by Solaris, HP-UX, AIX, Irix, and others), the learning curve is tiny.  I suspect that LVM2 is the most supported option. [https://linuxhandbook.com/lvm-guide/](https://linuxhandbook.com/lvm-guide/)  The requirement that /boot/ be separate when LVM is used ended in 20.04 and later Ubuntu releases.  

 LVM2 is the same across all Linuxen.  I suspect BTRFS and ZFS commands are all the same across all Linux systems too, if there is support.

These three volume managers all support the proper term "snapshots".  A snapshot (usually named) freezes blocks of storage from a point in time and any changes or new files get placed into an area that is outside the snapshot.  Over time, that secondary location can fill with changes, since all the blocks used for each snapshot are frozen.

[https://www.howtogeek.com/272220/how-to-install-and-use-zfs-on-ubuntu-and-why-youd-want-to/](https://www.howtogeek.com/272220/how-to-install-and-use-zfs-on-ubuntu-and-why-youd-want-to/)

There are trade-offs in using volume managers. They add compatibility, but they also add flexibility and capabilities.  The downside is that they have to be put on the storage BEFORE any data is.  The migration from ext4 to LVM+ext4 would be to backup all the files off to different storage, wipe the ext4, tell LVM to make a PV, then a VG for that partition, then start creating LVs of the sizes needed for the next few months, not the entire space.  Leaving at least 20% of the VG allocated is important, if you want to support short-term snapshots, say for backups.  

The two that are integrated with file systems, perhaps have cleaner interfaces. Those are BTRFS and ZFS.  ZFS originated on Solaris and on that platform has been enterprise ready for nearly 20 yrs now.  It has been some time since I touched ZFS and I've never used ZFS.  I've been using LVM for nearly a quarter century now.  At this point, I'd deploy new data storage onto ZFS, for the OS, I'd still use LVM+ext4. There are many reasons for this.  I would only use BTRFS on a laptop (single drive) and not a laptop where I might need to run virtual machines.

[https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/) Please read that article before choosing btrfs, so ensure all those issues have been rectified for the release you plan to use.

---

### Post by TheFu on 2023-02-06
BTW, there are parts of all Unix systems that cannot be immutable.  For those areas, we place them into tmpfs or a ramdisk.  This is common for specialized devices that use flash storage with low write count support, like the old SDHC cards had.

Be certain to read and follow the Linux File System Hierarchy Standards document, which spells out which parts can be read-only.  For example, /usr/ should be fine as read-only, provided you don't plan to attempt patching the system.  Just beware that it isn't as simple as I think you believe it is. There are lots of places for specific needs on all Unix systems. Go read that document - I think the current standards were last approved in 2015.  Also, be aware that Ubuntu violates some of those standards.

Some no-name SDHC storage devices sitll have very low write count engineering capabilities, but if you stick with quality flash storage, at least 5 yrs should be possible for almost any, but the most extreme, write counts.  I used a quality USB flash drive for about a year with daily, continuous writes from a security camera before it failed.  I replaced that flash-based device with a USB HDD that was externally powered and it has been working non-stop the last 3-5 yrs.

---

### Post by Advait on 2023-03-02
I hired a tech support person and he got Ubuntu installed in VBox with btrfs in the root and home directories. Also installed timeshift-autosnap-apt and grub-btrfs. Now I'm seeing snapshots in the grub menu. Nice! Now I can play around with snapshots before going live.

---

