---
title: "Upgrade to Ubuntu 16.04: no hard drive any more"
date: 2016-08-10
forum: General Help
---

### Post by scudsucker on 2016-08-10
Hi. I use Ubuntu on a daily basis at work; so I am less of a novice than many. However, my experience is only in hosting websites on Apache and Tomcat; so I am still very much a novice in other areas.

My home multimedia system is an old unbranded rescue from my office. I was running Ubuntu 14.x, (only Ubuntu, not dual OSs) and finally gave in to the upgrade to 16.04. After a reboot, my PC would not recognise the OS, and currently boots into GRUB rescue.  I managed to edit the Boot loader, so as to accept USB as first boot source. The PC is set in the Boot menu to use "mixed mode" - ie, both UEFI and whatever the other option is.... I've not been into the boot menu since, and am having trouble getting there again. 

I have no really valueable files on the system (I have backups) but would like to first attempt ot recover what is there; copying a couple of hundred GB over USB2 (my only option) is not going to be too much fun

I have created a bootable 16.04 USB, and I am typing from Firefox running in that on the PC right now.

What I have discovered is that the single 250GB hard-drive in the PC is apparently not mounted properly or the partition table is broken. It does actually mount- I can see files and folders - but it is apperaing as a removable drive (ie, has the "eject" icon next to it). /dev/sda1 is where the Ubuntu OS is installed, so it would be nice to get up recognised...

Screenshot from "Disks" showing /dev/sda1:

[https://s10.postimg.org/so45vylx5/dev_sda.png](https://s10.postimg.org/so45vylx5/dev_sda.png)



GParted says the drive is "unallocated" but (obviously) I do not want to reformat. This hints to me that the partition table may be broken, but I don't really know.

The output of **sudo fdisk -lu** (I posted the whole thing; the important info is at the bottom of the output)```

ubuntu@ubuntu:~$ sudo fdisk -lu
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1488424960 bytes, 2907080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000193f6

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 487368703 487366656 232.4G 83 Linux
/dev/sda2       487370750 488396799   1026050   501M  5 Extended
/dev/sda5       487370752 488396799   1026048   501M 82 Linux swap / Solaris


Disk /dev/sdb: 7.5 GiB, 8016363520 bytes, 15656960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x496eb40d

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *        2 15656959 15656958  7.5G  b W95 FAT32



```

The drive /dev/sdb1 is the thumb drive with the live installation of Ubuntu


The output of [B]sudo blkid
[/B]```

ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="bc5a46af-5a2a-4e3a-8ba0-3868f34a2eee" TYPE="ext4" PARTUUID="000193f6-01"
/dev/sdb1: LABEL="WININSTALL" UUID="4457-1A15" TYPE="vfat" PARTUUID="496eb40d-01"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="e06c642c-e3d9-4041-973f-f9a7deb50c2a" TYPE="swap" PARTUUID="000193f6-05"

```

Now. What can I do to get the /dev/sda1 drive booting up Ubuntu again?






As an aside, do not attempt to fix Ubuntu problems with a thumb drive on a USB2 port when you have a 1 year old daughter who knows about the power button... my under-powered machine takes over 15 minutes to boot up. Several times.

---

### Post by ajgreeny on 2016-08-10
Please do not use large images inline as you did.

I future please use URL or attach the image as a thumbnail by using the paperclip icon in the "Reply To Thread" toolbar.

---

### Post by oldfred on 2016-08-10
Have you tried fsck?
If an abnormal shutdown or power failure that is almost always required. But other events can need a fsck also.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

### Post by scudsucker on 2016-08-11
My apologies; I resized it to 800px wide (which has been an accepted standard max for many years) using an online image hosting service - using a live USB does not give me any image editors.

I will do as you suggest in future.

---

### Post by scudsucker on 2016-08-11
Thanks, oldfred - I have not.

I shall do so and report back.

Your suggestion that "abnormal shutdown or power failure" might have occurred is extremely likely (given my 1 year old's predeliction for the power button) and much more likely that the upgrade.

---

### Post by oldfred on 2016-08-11
Some major wrong if it takes 15 min to boot.
My laptop with 1.5GB of RAM and from 2006 takes about 40 sec. But not running Unity, using Ubuntu but fallback which is a lighter weight gui (like old style gnome2).
My new Raspberry Pi which really is Debian is about a minute or so.

What are specs & what version of Ubuntu?

---

### Post by scudsucker on 2016-08-19
Fsck basically informed me my hard drive is toast. I've added a second h/d on which I am in the process of installing 16.04 with a faint hope of recovery.

It still takes 15 to 20 minutes to boot off the USB. I suspect that the USB and the USB ports are USB1; but that is a little excessive.

When the machine was running it booted in +/- 30 seconds. I'm not terribly concerned about excessive boot time when booting off USB, that's something I do roughly once every five years.


I really appreciate your help, and suggestions.... sadly it looks like I wasted your time: the h/d is broken. But thank you for your help anyway.

---

