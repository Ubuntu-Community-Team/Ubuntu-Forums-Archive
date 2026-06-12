---
title: "Is possible use 2 mount point in same partition ?"
date: 2021-09-17
forum: General Help
---

### Post by aug7744 on 2021-09-17
When installing is possible select in each disk partition a OS mount point.

Is possible select one partition to be mount point for /OPT and /VAR at same time ?

Disk layout may be

sda1 8 MB bios-grub
sda2 500 MB ext4 /boot
sda3 12 GB BTRFS /
sda4 12 GB /OPT and /VAR

Thanks for your reply.

---

### Post by guiverc on 2021-09-17
I have a NFS share I mount to / ; however years ago when `chromium` switched to snap (*mid-2019 from memory*), it was outside of reach to snaps (`snap-connect` only allowed you to add /mnt/ or /media/) so rather than switch my NFS share to a new location; I mount it twice - once where I've always had it (so I don't need to re-learn), and a second (identical) mount in /mnt/ so `chromium` (browser in snap) can.

I have done this (*and partitions too*) **with installers**, but these days I'd forget about `/opt` at install time, and just add it post-install (via `/etc/fstab` or the *file-system table*), as various installers have their *quirks* and I tend to try and keep it simpler so the installer is less troublesome.

Ubuntu installers *currently* are 
- *debian installer (old & being replaced by subiquity*)
- ubiquity
- calamares (okay two *flavors* use this one, not main Ubuntu)
- subiquity
- *canary* (I forget it's real name; if it has one; will replace `ubiquity`)
but you didn't say which; thus I'd just install & make the changes post-install.

---

### Post by aug7744 on 2021-09-17
I use Lubuntu.
I want to avoid fragmentation in /var and also create a write cache buffer for both /opt and /var

---

### Post by HermanAB on 2021-09-17
"I want to avoid fragmentation in /var" - Fragmentation is not a problem with modern file systems.
"cache buffer" - The operating system already does that.

---

### Post by TheFu on 2021-09-17
I think we need to clarify that disks aren't mounted.  File systems are what we mount.  Just like an mp4 file is just a container for a few different video/audio types of data, file systems can be placed into different types of containers.  Usually a file system would go into a partition, but there are ways to have a single partition hold multiple file systems. Historically, that would be by using LVM.  The entire partition would be given to a PV (physical volume) and a VG (volume group) would contain 1 or more PVs.  Then as space is needed, an LV (logical volume) can be created and resized from the available storage in the VG.

In the world of mounts, LVs are where we'd lay down a file system and mount it where desired.  For example, here's an fstab that used LVM mounts:
```
UUID=E7E6-D023                            /boot/efi vfat umask=0077      0 1
UUID=d62de6a2-5b69-4d3a-8a31-91040d274d9e /boot     ext2 defaults,noatime 0 2 
/dev/vg00/root                            /         ext4 noatime,errors=remount-ro 0 1
/dev/vg00/home                            /home     ext4 errors=remount-ro,noatime 0 2
/dev/vg00/stuff                           /stuff    ext4 errors=remount-ro,noatime 0 2
/dev/vg00/swap_1                          none      swap sw              0 0
```
The first 2 lines are typical UUIDs and regular partitions.
The /dev/vg00/ lines each point at different logical volumes.  The VG is named, vg00.  

I'm fairly certain that btrfs has a similar capability, but I've never used btrfs. You should look up the way to create the similar idea to a logical volume under btrfs and use that.  For LVM, the real power comes by NOT allocating all the storage in the VG and only making LVs the size needed for the next 2-3 months.  Resizing an LV to be larger is 5 seconds and the file system can be mounted, active, used during this command.  Resizing smaller is a major hassle and often risks data loss, so start small and extend bigger only as needed and where needed.
Here's a simple diagram showing parts of an LVM setup with an encrypted container.  You can ignore the encrypt LUKS container. Just the partition holds the PV for a non-encrypted version.  The type of partition primary or logical from the partition table doesn't matter to LVM. It doesn't care.
[ATTACH=CONFIG]289177[/ATTACH]
Hope that helps.  Having extra storage available for snapshots and to extend existing LVs as needed in LVM is an important aspect to have the most flexible solution.

Again, I think you probably should use the btrfs solution to this instead.  In fact, I'd be a little surprised if a different partition was needed between the OS and /var and /opt locations under btrfs.  [https://fedoramagazine.org/choose-between-btrfs-and-lvm-ext4/](https://fedoramagazine.org/choose-between-btrfs-and-lvm-ext4/) talks about subvolumes in btrfs. I think that's what you want.  I googled and found this: [https://blog.programster.org/btrfs-cheatsheet](https://blog.programster.org/btrfs-cheatsheet). The subvolume section seems clear, but I've never used it, so I don't actually KNOW anything.

You have some choices. Each with pros and cons. If it were me and I was already using btrfs elsewhere, I'd use it for this too.

---

### Post by aug7744 on 2021-09-21
@HermanAB

" "cache buffer" - The operating system already does that. "
I want to use writeback cache , but look how if not is enabled in system and using BTRFS.


@TheFu
Using BTRFS and enabling commit=3600 not works.

Thanks very much all informations.
Have a nice day.

---

