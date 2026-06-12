---
title: "Ubuntu(Xubuntu) will not boot after power failure"
date: 2019-03-29
forum: General Help
---

### Post by markjensen on 2019-03-29
I have Xubuntu installed with sda configured in LVM setup. Previously, I have used older, standard partitioning with a root, /boot, and swap all on separate sda1,2,3. I have always seemed to have problems with failing to boot after power loss, and I have learned to boot into a recovery mode and fsck, and this has fixed things reliably (side topic: Why in the hell isn't filesystem recovery more self-guided, perhaps prompted for when the system sees problems on boot?).

However, two days ago was my first power loss since switching to LVM (old drive was reporting imminent failure via SMART, so purchased a new HD).

If it tries a normal boot, the screen goes black, and it stays that way.

I boot into recovery, and can get to a Busybox/initramfs limited prompt. It reports "Waiting for root filesystem", then "Gave up waiting for root filesystem". It offers a few hints that boot arguments may be incorrect (these worked for many months on this install), but also states "ALERT! /dev/mapper/xubuntu--vg-root does not exist. Dropping to a shell!"

I have followed suggestions I have found elsewhere through google searches, including to ls dev at the initramfs shell, and if I don't see the filesystem to wait 10 seconds and try again. There were suggestions that RAID setup could be a problem, or setups installed dual-boot with wubi. None of these applied.

Booting off a LiveCD, I can mount and read the contents of my hard drive. I have read suggestions to use lvm tools to get information and will post the following. I suspect that I need to fix an error in the LVM-configured filesystems.```
ubuntu@ubuntu:~$ sudo lvm pvscan
  PV /dev/sda1   VG xubuntu-vg      lvm2 [<465.76 GiB / 4.00 MiB free]
  Total: 1 [<465.76 GiB] / in use: 1 [<465.76 GiB] / in no VG: 0 [0   ]

ubuntu@ubuntu:~$ sudo lvm vgscan
  Reading volume groups from cache.
  Found volume group "xubuntu-vg" using metadata type lvm2

ubuntu@ubuntu:~$ sudo lvm lvscan
  ACTIVE            '/dev/xubuntu-vg/root' [464.80 GiB] inherit
  ACTIVE            '/dev/xubuntu-vg/swap_1' [976.00 MiB] inherit

```
I'm not entirely sure what to do from here, so it seems reasonable to try to fsck the xubuntu-vg root.```
ubuntu@ubuntu:~$ sudo fsck /dev/xubuntu-vg/root
fsck from util-linux 2.32
e2fsck 1.44.4 (18-Aug-2018)
/dev/mapper/xubuntu--vg-root: clean, 538363/30466048 files, 48101510/121844736 blocks
```

it doesn't seem that either there is a problem there. Or that I am not doing things correctly.

After a few days out of town, and mentally rested, I spent some time digging back into this after my morning coffee.

I looked over the steps I took earlier, and see that when I did my fsck /dev/xubuntu-vg/root, I was looking at the live session's mount. NOT my hard drive. So that explains a lot. Figure I would spell out what I am doing here, should anyone else find this thread and it might be useful to them...

When I mount the hard drive (clicked on it in the GUI file browser), it appears when I do the mount command: ```
/dev/mapper/xubuntu--vg-root on /media/ubuntu/1d3ca2dc-c59a-4582-a538-8c529926b276 type ext4 (rw,nosuid,nodev,relatime,uhelper=udisks2)
``` So, when I try to fdisk that, I get:```
sudo fdisk /dev/mapper/xubuntu--vg-root
Welcome to fdisk (util-linux 2.32).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

The old ext4 signature will be removed by a write command.

Device does not contain a recognized partition table. Created a new DOS disklabel with disk identifier 0x5490643a.

Command (m for help):
```

I am VERY apprehensive about the warning that I will remove the old ext4 signature!

After a bit more consideration, I just jumped in.

Went ahead and did a```
sudo fsck -f /dev/mapper/xubuntu--vg-root 
fsck from util-linux 2.32
e2fsck 1.44.4 (18-Aug-2018)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/mapper/xubuntu--vg-root: 538364/30466048 files (0.3% non-contiguous), 48101511/121844736 blocks

```
It did not report any errors with this lvm filesystem. Yet, it still won't boot.

This has to be repairable, as I can read the hard drive filesystem when booting from my LiveCD. Have also tried a few lvm tools, sudo vgchange --ignorelockingfailure -ay, then sudo lvscan --ignorelockingfailure, then re-tried the sudo fsck -f /dev/mapper/xubuntu--vg-root that a webpage related to lvm recommended.

No success.  Any other ideas?

---

### Post by Rubi1200 on 2019-04-02
Just to give us a clearer picture of what your partitions look like please create a boot summary report and post it here:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thanks.

---

### Post by markjensen on 2019-04-02
[http://paste.ubuntu.com/p/VRyKWTqmyv/](http://paste.ubuntu.com/p/VRyKWTqmyv/)

I see this near the end:
```
Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *     2048 976771071 976769024 465.8G 8e Linux LVM

Disk /dev/mapper/xubuntu--vg-root: 464.8 GiB, 499076038656 bytes, 974757888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/mapper/xubuntu--vg-swap_1: 976 MiB, 1023410176 bytes, 1998848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to enable-raid) and reinstall the grub2 of mapper/xubuntu--vg-root into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s


```

The "boot-info" package would be nice to have on the Live/Install media, so it can be easily used in cases where the computer does not have an internet connection.

---

### Post by oldfred on 2019-04-03
I suggest running the re-install of grub from Boot-Repair.
I do not really know LVM, but those with LVM and encryption may not be mounted automatically in Boot-Repair, so just make sure your LVM volumes are mounted.

If you can boot to command line, it may be a video issue?
What video card/chip do you have?
What brand/model system?

Update:
This user solved same issue (not LVM) but had to chroot into system and rebuild initramfs.
I might then in Boot-Repair's Advanced options select the full reinstall of grub (not just to MBR) and add newest kernel. That will also refresh everything including initramfs.
[https://ubuntuforums.org/showthread.php?t=2245053](https://ubuntuforums.org/showthread.php?t=2245053)

---

### Post by markjensen on 2019-04-03
Yesterday, after running boot-info, I looked and ran boot-repair. I got to where to install the bootloader, and picked sda. This didn't work.

After seeing your post, I went back and did boot-repair again, but selected sda AND my LM volume.

This worked!  Thank you.

LVM seems more problematic if I'm going to lose the bootloader every power bump.

---

### Post by Rubi1200 on 2019-04-03
Glad to hear you sorted things out.

I have never used LVM but after reading your post I informed myself more.

The question is whether you really need it and what advantages it has for your particular setup.

In any event, we are glad this was resolved.

Good luck!

Edit: to help us solve similar issues in future would you be willing to post the boot info summary of the current setup so we can analyze for reference?

---

