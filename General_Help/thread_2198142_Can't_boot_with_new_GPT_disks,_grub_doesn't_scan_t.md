---
title: "Can't boot with new GPT disks, grub doesn't scan them properly"
date: 2014-01-07
forum: General Help
---

### Post by ptomblin on 2014-01-07
I have a system with two pairs of disks in raid-1s, with lvm running on top of them. In the past, I've upgraded a pair at a time, using lvm to move from the old pair to the new pair and doing a grub-install on the new ones. This time the new pair were 3Tb, so I had to switch to using gpt for the first time. I believe I got everything set up on the pair correctly with parted:

```
ptomblin@allhats2:~$ sudo parted /dev/sda print
Model: ATA WDC WD30EFRX-68E (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049MB  2097MB  1049MB               1        bios_grub
 2      2097MB  3001GB  2998GB               primary  raid

ptomblin@allhats2:~$ sudo parted /dev/sdc print
Model: ATA WDC WD30EFRX-68E (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049MB  2097MB  1049MB               boot     bios_grub
 2      2097MB  3001GB  2998GB               primary  raid
```

And the raid is correctly set up, and lvm happily migrated everything over to the new pv.
grub-install didn't complain about anything, but when it boots it tells me it can't find lvm/lvm2-boot. So I had a look at the output from grub-install --debug, and it appears that it isn't scanning the GPT disks the way it scans the older disks. Because of that, it doesn't seem to know about the raid on the gpt disks. Here is the result of looking in the debug output for mentions of the disks or the raids:

```
egrep '(sd[a-f]|md/12)' /tmp/bar
+ /usr/sbin/grub-bios-setup --verbose --directory=/boot/grub/i386-pc --device-map= /dev/sda
/usr/sbin/grub-bios-setup: info: Looking for /dev/sda.
/usr/sbin/grub-bios-setup: info: /dev/sda is a parent of /dev/sda.
/usr/sbin/grub-bios-setup: info: Looking for /dev/sda.
/usr/sbin/grub-bios-setup: info: /dev/sda is a parent of /dev/sda.
/usr/sbin/grub-bios-setup: info: transformed OS device `/dev/sda' into GRUB device `hostdisk//dev/sda'.
/usr/sbin/grub-bios-setup: info: root is `(null)', dest is `hostdisk//dev/sda'.
/usr/sbin/grub-bios-setup: info: the size of hostdisk//dev/sda is 5860533168.
/usr/sbin/grub-bios-setup: info: Looking for /dev/sdb1.
/usr/sbin/grub-bios-setup: info: /dev/sdb is a parent of /dev/sdb1.
/usr/sbin/grub-bios-setup: info: /dev/sdb1 starts from 2048.
/usr/sbin/grub-bios-setup: info: opening the device hostdisk//dev/sdb.
/usr/sbin/grub-bios-setup: info: the size of hostdisk//dev/sdb is 3907029168.
/usr/sbin/grub-bios-setup: info: the size of hostdisk//dev/sdb is 3907029168.
/usr/sbin/grub-bios-setup: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sdb.
/usr/sbin/grub-bios-setup: info: Scanning for mdraid1x devices on disk hostdisk//dev/sdb.
/usr/sbin/grub-bios-setup: info: Scanning for mdraid09 devices on disk hostdisk//dev/sdb.
/usr/sbin/grub-bios-setup: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sdb.
/usr/sbin/grub-bios-setup: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sdb.
/usr/sbin/grub-bios-setup: info: Scanning for ldm devices on disk hostdisk//devsdb.
/usr/sbin/grub-bios-setup: info: scanning hostdisk//dev/sdb for LDM.
/usr/sbin/grub-bios-setup: info: Scanning for lvm devices on disk hostdisk//devsdb.
/usr/sbin/grub-bios-setup: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sdb.
/usr/sbin/grub-bios-setup: info: Scanning for mdraid1x devices on disk hostdisk//dev/sdb.
/usr/sbin/grub-bios-setup: info: Found array md/128.
/usr/sbin/grub-bios-setup: info: Inserting hostdisk//dev/sdb into md/128 (mdraid1x)
/usr/sbin/grub-bios-setup: info: the size of hostdisk//dev/sdb is 3907029168.
/usr/sbin/grub-bios-setup: info: Scanning for DISKFILTER devices on disk md/128.
/usr/sbin/grub-bios-setup: info: Scanning for mdraid1x devices on disk md/128.
/usr/sbin/grub-bios-setup: info: Scanning for mdraid09 devices on disk md/128.
/usr/sbin/grub-bios-setup: info: Scanning for mdraid09_be devices on disk md/128.
/usr/sbin/grub-bios-setup: info: Scanning for dmraid_nv devices on disk md/128.
/usr/sbin/grub-bios-setup: info: Scanning for ldm devices on disk md/128.
/usr/sbin/grub-bios-setup: info: scanning md/128 for LDM.
/usr/sbin/grub-bios-setup: info: Scanning for lvm devices on disk md/128.
/usr/sbin/grub-bios-setup: info: Inserting md/128 into lvm2 (lvm)
/usr/sbin/grub-bios-setup: info: Looking for /dev/sdd1.
/usr/sbin/grub-bios-setup: info: /dev/sdd is a parent of /dev/sdd1.
/usr/sbin/grub-bios-setup: info: /dev/sdd1 starts from 2048.
/usr/sbin/grub-bios-setup: info: opening the device hostdisk//dev/sdd.
/usr/sbin/grub-bios-setup: info: the size of hostdisk//dev/sdd is 3907029168.
/usr/sbin/grub-bios-setup: info: the size of hostdisk//dev/sdd is 3907029168.
/usr/sbin/grub-bios-setup: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sdd.
/usr/sbin/grub-bios-setup: info: Scanning for mdraid1x devices on disk hostdisk//dev/sdd.
/usr/sbin/grub-bios-setup: info: Scanning for mdraid09 devices on disk hostdisk//dev/sdd.
/usr/sbin/grub-bios-setup: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sdd.
/usr/sbin/grub-bios-setup: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sdd.
/usr/sbin/grub-bios-setup: info: Scanning for ldm devices on disk hostdisk//devsdd.
/usr/sbin/grub-bios-setup: info: scanning hostdisk//dev/sdd for LDM.
/usr/sbin/grub-bios-setup: info: Scanning for lvm devices on disk hostdisk//devsdd.
/usr/sbin/grub-bios-setup: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sdd.
/usr/sbin/grub-bios-setup: info: Scanning for mdraid1x devices on disk hostdisk//dev/sdd.
/usr/sbin/grub-bios-setup: info: Inserting hostdisk//dev/sdd into md/128 (mdraid1x)
/usr/sbin/grub-bios-setup: info: the size of hostdisk//dev/sdd is 3907029168.
```

Note that it doesn't see /dev/sda2, it doesn't scan /dev/sda for mdraid1x the way it scans the two older disks (sdb and sdd), it doesn't scan /dev/sdc all, and because it doesn't scan sda or sdc for mdraid1x, it doesn't know about md/127, which is the raid that sits on them.

Currently I can boot the system by using the old drives, but I want to get this working so I can migrate the old pair to 3Tb as well.

---

### Post by oldfred on 2014-01-07
I do not know RAID nor LVM.

But with RAID you boot from the root of the RAID, so should the bios_grub be inside the RAID?
My normal installs with grub in a MBR need the bios_grub in the drive I boot from.

Boot-Repair knows RAID better than I do, but it does not auto create bios_grub partitions, so if needed inside the RAID it may not work.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by ptomblin on 2014-01-07
> **oldfred said:**
> 
       Post the link to the Create BootInfo report. Is part of Boot-Repair:



This is what boot-repair from the command line gives me:
```
/usr/share/boot-sav/gui-g2slaunch.sh: line 29: 17855 Segmentation fault      (core dumped) $G2S $1 -g ./$PACK_NAME.glade -s ./$APPNAME.sh --combobox="@@_combobox_format_partition@@col" --combobox="@@_combobox_bootflag@@col" --combobox="@@_combobox_ostoboot_bydefault@@col" --combobox="@@_combobox_purge_grub@@col" --combobox="@@_combobox_separateboot@@col" --combobox="@@_combobox_efi@@col" --combobox="@@_combobox_sepusr@@col" --combobox="@@_combobox_place_grub@@col" --combobox="@@_combobox_add_kernel_option@@col" --combobox="@@_combobox_restore_mbrof@@col" --combobox="@@_combobox_partition_booted_bymbr@@col"

```
So evidently the part of the linked page where they say you can run it from the command line was a lie. Not everybody logs into X as the only way to interact with their computers. I guess I'll have to get back to you when I have physical access to my computer again.

---

### Post by oldfred on 2014-01-07
I have a gui, but it just ran from terminal in my system. So it may need a gui?
Normally users run it from a liveCD or the Ubuntu liveDVD or flash drive which has a gui.

---

### Post by ptomblin on 2014-01-11
Well, now that I have access to the physical display, I was able to run boot-repair, and it said it repaired the boot, but the same thing happens as before - I get the grub boot screen, two errors about bad sectors on /dev/fd0, a message about being unable to read lvm/lvm2-boot, and then the grub-rescue prompt.

[http://paste.ubuntu.com/6733247/](http://paste.ubuntu.com/6733247/)

---

### Post by oldfred on 2014-01-11
I know the default installs of LVM use a /boot outside of the LVM. And installs of RAID install grub to the / (root) of the RAID not the MBR of a drive.
And a bios_grub is only 1 or 2MB unformatted. It is not a /boot partition, but just a place for core.img which with MBR is after the MBR in sectors 2 thru whatever space it needs but before first partition. With gpt that space does not exist so a bios_grub is needed.
With RAID then I do not know if you need bios_grub inside RAID, or since also LVM need /boot outside RAID & LVM?

Hopefully someone that knows RAID & LVM will post. 

I can move thread to server sub-forum as your configuration is server type and those that know servers may see your thread.

---

### Post by ptomblin on 2014-01-11
> I know the default installs of LVM use a /boot outside of the LVM. And installs of RAID install grub to the / (root) of the RAID not the MBR of a drive.

Neither of those things are true. I installed this system several years ago, and /boot has always been on /dev/lvm/boot, and grub was installed to the MBR. I've migrated this setup from a pair of 500Gb drives to a pair of 500Gb plus a pair of 1Tb drives to a pair of 1Tb drives plus a pair of 2Tb drives to two pairs of 2Tb drives, and never had any problems with any of those migrations. In every case, I updated grub to use the new pair of drives with the command "grub-install /dev/sda".

---

### Post by oldfred on 2014-01-11
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

           If you do need to replace a faulty drive, after the drive has been replaced and synced, grub will need to be            installed.  To install grub on the new drive, enter the following:           > 

 sudo grub-install /dev/md0

            Replace /dev/md0 with the appropriate array device name.

---

