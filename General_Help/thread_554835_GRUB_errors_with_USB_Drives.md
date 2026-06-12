---
title: "GRUB errors with USB Drives"
date: 2007-09-19
forum: General Help
---

### Post by derekr44 on 2007-09-19
I've got two internal drives.

HDA1 - 200GB IDE with Windows XP (1st part XP, 2nd part XP recovery)
HDB1 - 160GB IDE with Ubuntu 7.04 (and all linux partitions)

I've noticed when I have my 80GB USB drive plugged in, I get a GRUB error.  When I unplug it and restart, it goes away.

I've also noticed that GRUB does not boot when my NAS device is connected on my LAN (very strange).  It simply sits there for a very long time, not booting to anything.

When running "sudo fdisk -l" in terminal, I have the following results:
> Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 572 24321 190771875 7 HPFS/NTFS
/dev/hda2 1 571 4586526 b W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 18700 150207718+ 83 Linux
/dev/hdb2 18701 19457 6080602+ 5 Extended
/dev/hdb5 18701 19457 6080571 82 Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 9728 78140128+ c W95 FAT32 (LBA)

When running "sudo mount" in terminal:
> proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/My Book type vfat (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umas k=077)

I did notice that I had two boot options set in fdisk for hda1 & hdb1 and fixed that.  But the booting with USB drives plugged in still persists.  Is this because of "/dev/sda1 1 9728 78140128+ c W95 FAT32 (LBA)"

---

### Post by derekr44 on 2007-09-19
Just checking in.  Anyone have any ideas?

---

### Post by dabl on 2007-09-19
Yes.

USB devices, including drives, are "dynamically" numbered, as they are plugged in to the USB bus. This is a cause of trouble in Linux, which is looking for a consistent ID number for a given device.  Here's more, and a method to deal with it:

[http://www.penguin.ch/dokuwiki/doku.php/debian:fstab?s=tacking](http://www.penguin.ch/dokuwiki/doku.php/debian:fstab?s=tacking)

:)

---

### Post by derekr44 on 2007-09-19
So very cool.  This explains a lot.

So I need to run:
> sudo ls -l

and modify fstab to include:
> /dev/disk/(results of ls -l go here for usb drive)   /media/backup   
    reiserfs   auto,users,rw,noatime,nodiratime   0 0

amirite?

---

### Post by wizkey on 2007-09-28
> **derekr44 said:**
> I've got two internal drives.

HDA1 - 200GB IDE with Windows XP (1st part XP, 2nd part XP recovery)
HDB1 - 160GB IDE with Ubuntu 7.04 (and all linux partitions)

I've noticed when I have my 80GB USB drive plugged in, I get a GRUB error.  When I unplug it and restart, it goes away.

I've also noticed that GRUB does not boot when my NAS device is connected on my LAN (very strange).  It simply sits there for a very long time, not booting to anything.


There are a number of reasons this can occur. Dabl already hit on it a bit earlier, but I'll elaborate.

When you plug in USB drives, this can change the drive order the BIOS reports. So if Grub was looking for root on (hd1,0), when the USB drive is plugged in root may actually be on (hd2,0) at runtime (i.e., at boot).

If you have a BIOS that allows you to specify drive order, place all your SCSI/ SATA/ PATA/ IDE drives at the top, and then your USB drives (if you see them) at the bottom.

What that does is prevent plugging in drives from affecting the drive order reported by the BIOS.

In addtion, some people have dual boot configurations and are using a FakeRaid / Softraid controller for Windows. Linux sees these drives as separate, but the BIOS will report only a single drive to Grub. The problem this causes is that if you run Grub from under Linux, the drive order will be different then what Grub sees at runtime (at boot).

The only way to get around that is get a Grub floppy or CD and boot to that. Super Grub Disk will do the job.

Once you get past all the upfront menu stuff, pick any option and then hit the c key. That will drop you down to a grub command line.

Once there, type:

find /boot/vmlinuz

It should come back with a number of hits. Make a note of the drive and partition. You should see something like (hd1,0). That's the *runtime* drive and partition Grub sees.

Once you know that runtime drive and partition info, you can type:

root (xx,x) <---- This should be the drive and partition information the find command gave you
setup (hd0) <--- That will write to the MBR the info about where your root is at
reboot <---------- Reboot command at Grub prompt

That's it. It took me a couple days to figure this out. It didn't help that I had both the MediaSentry softraid stuff and USB drives too, really took some time figure out that it was impossible to correct from under Linux, and has to be corrected at runtime. Hence the need for a Grub boot disk.

Hope it helps!

---

