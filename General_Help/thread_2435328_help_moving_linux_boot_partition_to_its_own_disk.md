---
title: "help moving linux boot partition to its own disk"
date: 2020-01-19
forum: General Help
---

### Post by phildo2 on 2020-01-19
I have a hard disk (let's call it "sda") which has multiple partitions allowing me to boot into windows 10 or ubuntu 18. This is a totally functional setup.

However, I have purchased a new hard disk ("sdb") and would like to move linux onto this, and then expand windows to the full first hard disk ("sda").

My current partitions (given from `lsblk`) are:

sda
- sda1 847M /boot/efi
- sda2 954M [SWAP]
- sda3 29.8G //<- this is my linux root filesystem
- sda4 16M  //<- I have no idea what this is
- sda5 347.6G //<- windows filesystem
- sda6 474M //<- I have no idea what this is

I've hooked up my second disk, and have created the following:

sdb
- sdb1 226.6G //<- hoping for this to be my new ubuntu file system
- sdb2 11.9G //<- hoping for this to be swap for the new filesystem

I've formatted sdb1 to ext4, mounted it, and copied the entirety of sda3 to (after mounting both from a live disk, I ran `cp -a /mnt/sda3/* /mnt/sdb1/`. cd'ing into the mounted sdb1 looks "correct" (ie, apparently identical to sda3). I've also formatted sdb2 as linux-swap.

When I initially set up sda years ago, I was flying by the seat of my pants and only "got it working" after multiple wipe/reinstalls. So it's safe to say I don't fully understand the bios->efi->grub->os pipeline, or where each part resides, etc...

Does anyone have ideas for next steps?

---

### Post by CatKiller on 2020-01-19
As a general rule, you don't need a swap partition. A swap file is fine.

The two places that you'll need to amend the UUIDs to reflect your new partitions are fstab and Grub. Grub can stay in the existing EFI partition, but it will need to point to your new / partition for the next stage of the boot process instead of the old one.

The first part is pretty easy. It's just a text file that you can access from a live USB. The second part I *think* you can do manually by editing your Grub config, chrooting, then running *update-grub*, but I think the Boot-Repair image is able to do that automatically if you prefer.

---

### Post by phildo2 on 2020-01-19
Ok, so I've deleted sdb2 and expanded sdb1 to take up the full hard drive (thanks for the tip!). I've gone into sdb1:/etc/fstab and changed the root mount point to the UUID of sdb1, deleted the entry for the swap partition, and left the entry for mounting /boot/efi the same (still pointing at the UUID of sda1).

And now I've gone into /etc/default/grub, and it doesn't look like there are any settings there worth changing? (Nothing mentions any given drive or partition...). I guess my next step is to chroot to sdb1 and run update-grub? I'll see what that does and report back...

In the mean time, I know this isn't a windows forum, but do you have any ideas how to expand the windows partition to the full disk? I assume there won't be an easy way to preserve the EFI partition as-is?

Edit: ok, I tried `sudo chroot /mnt/newroot`, but then attempting to run `update-grub` fails complaining that /dev isn't mounted?

---

### Post by yancek on 2020-01-19
You can use Disk Management in windows to expand the OS partition.  Don't do anything with the EFI partition.
So you need to mount the partition you want to access on the external drive from Ubuntu.  The link below provides details on the process.

[https://bartsimons.me/ubuntu-linux-chroot-guide/](https://bartsimons.me/ubuntu-linux-chroot-guide/)

---

### Post by oldfred on 2020-01-19
I prefer to have an ESP on every drive, even though Ubiquity will only install grub to the first drive seen, usually sda or first NVMe drive.

Your ESP controls which Ubuntu install it will boot. You cannot have duplicate UUID or you will have major issues. One time it may use one partition and next the other and get out of sync.

I prefer new clean install, so you get new UUID and reinstall of grub. Then you can copy /home to new partition or to your new install if not a separate partition. Separate partition for /home and/or your data is suggested, but not required.

While normally mounted with no permissions in fstab, your ESP has a 3 line grub.cfg that is a configfile to the full grub.cfg in your install.

Typical configfile in UEFI's ESP.

```
fred@fred-Z170N-focal:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid b913e1bc-6f08-4984-b653-9a604d95470a root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

---

### Post by Dennis N on 2020-01-20
> Ubiquity will only install grub to the first drive seen, usually sda or first NVMe drive

**@oldfred;**

Things have changed: With NVMe and SATA drives present, Ubiquity now accepts the choice for installing boot loader to the ESP on sda or the NVMe drive. On my initial NVMe installation, I selected sda for the boot loader location and Linux on the NVMe, and sda1 is where the boot loader installed (see below). For the second install, I chose the NVMe for the boot loader (Linux also on the NVMe), and on the NVMe is where it went.

```
Filesystem                        Size  Used Avail Use% Mounted on
udev                              5.8G     0  5.8G   0% /dev
tmpfs                             1.2G  2.0M  1.2G   1% /run
**/dev/mapper/sn500_vg-ubuntu_1804   16G   11G  4.3G  71% /**
tmpfs                             5.9G     0  5.9G   0% /dev/shm
tmpfs                             5.0M  4.0K  5.0M   1% /run/lock
tmpfs                             5.9G     0  5.9G   0% /sys/fs/cgroup
/dev/mapper/os_vg2-Common          85G   47G   34G  58% /mnt/Common-Files
**/dev/sda1                          79M   25M   55M  31% /boot/efi**
tmpfs                             1.2G   16K  1.2G   1% /run/user/121
tmpfs                             1.2G   32K  1.2G   1% /run/user/1000

```
The 2nd install - bootloader installed on NVMe:

```
Filesystem                       Size  Used Avail Use% Mounted on
udev                             7.8G     0  7.8G   0% /dev
tmpfs                            1.6G  1.9M  1.6G   1% /run
**/dev/mapper/wdsn500-ubuntu_1904   31G   14G   16G  47% /**
tmpfs                            7.8G     0  7.8G   0% /dev/shm
tmpfs                            5.0M  4.0K  5.0M   1% /run/lock
tmpfs                            7.8G     0  7.8G   0% /sys/fs/cgroup
**/dev/nvme0n1p1                    99M  7.7M   91M   8% /boot/efi**
/dev/mapper/os_vg-Common         214G  171G   34G  84% /mnt/Common-Files
tmpfs                            1.6G  8.0K  1.6G   1% /run/user/123
tmpfs                            1.6G   24K  1.6G   1% /run/user/1000

```

---

