---
title: "Boot goes to grub rescue mode (error: unknown filesystem)"
date: 2015-01-15
forum: General Help
---

### Post by oygle on 2015-01-15
I have a laptop with win 8.1 on it. Then I installed Kubuntu 14.04 alongside it. I could not boot into win 8.1, so I ran "boot repair" and then I was able to boot to win 8.1 or Kubuntu. Time went on and for various reasons, I decided to wipe the win 8.1 , and only have Kubuntu 14.04 on he laptop. Less problems that way.

So I booted the Kubuntu iso and installed Kubuntu. When it came to the disk section, I deleted all partitions, then set up EXT4 partitions, one to boot from, one as swap and the other as the main data partition. The install went fine, all updates applied.

I then rebooted and got ..

> error: unknown filesystem.
Entering rescue mode...
**grub rescue>**

I have read a few posts about similar problems ..

> **grub rescue > ls**
 (hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos1)
**ls hd0**
error: unknown filesystem.

I don't know how it thinks it is MSDOS partitions when I specified EXT4 ? If I specify the next one it says EXT2 ..

> **grub rescue > ls (hd0,msdos6)**
(hd0,msdos6): Filesystem is ext2.

---

### Post by sudodus on 2015-01-15
MSDOS means that it is a MSDOS partition table (which is the old kind of partition table, default in gparted, as opposed of GUID partition table alias GPT). It is not a problem, you are still having ext4 file systems.

There is some other problem. Did you also change the UEFI/BIOS setting from UEFI to CSM or BIOS or whatever it is called in the UEFI/BIOS menu system? Was the installation of Kubuntu good?

If you run in UEFI mode you need a GUID partition table. If you run in 'CSM or BIOS or whatever it is called' mode, you can have both kinds of partition tables.

See also these links

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by oygle on 2015-01-15
> **sudodus said:**
> Did you also change the UEFI/BIOS setting from UEFI to CSM or BIOS or whatever it is called in the UEFI/BIOS menu system? Was the installation of Kubuntu good?

If you run in UEFI mode you need a GUID partition table. If you run in 'CSM or BIOS or whatever it is called' mode, you can have both kinds of partition tables.


Yes I did. I had such a problem with UEFI so that I could not boot from CD/DVD in UEFI mode at all. No matter what I tried changing in the 'BIOS' settings or the boot options. So, all I could do was to install win 8.1 in 'legacy' mode and install Kubuntu 14.04 in legacy mode. Simply becasue the Dell BIOS settings wouldn't let me use UEFI and boot from another device. The options to boot to another device would disappear when I changed to UEFI/secure mode.

So, I decided I didn't need win 8.1 at all, and to just install Kubuntu 14.04 . The install went well, but I think because I used 'Boot-repair' before the install, that I may have messed something up. I would prefer a GPT partition table. Maybe I should also see if there are any BIOS updates. Oops, can't update the BIOS from Kubuntu.

> **sudodus said:**
> See also these links[https: up on those links; thanks for your help.//help.ubuntu.com/community/InstallingANewHardDrive](https: up on those links; thanks for your help.//help.ubuntu.com/community/InstallingANewHardDrive)

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

I will read up on those links; thanks for your help.

---

### Post by oygle on 2015-01-15
Because the only method to try and fix this is to "Try Kubuntu", I have used the "Startup Disk Creator" and now have Kubuntu 14.04 on a bootale USB. It will save time I hope.

Have read quite a number of other posts now, and don't seem to be getting anywhere. Here is some output about the HDD ..

> kubuntu@kubuntu:~$ **sudo lshw -C disk**
  *-disk                  
       description: ATA Disk
       product: ST1000LM024 HN-M
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 2BA3
       serial: S314J90F448953
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=d5925537
  *-cdrom
       description: DVD-RAM writer
       product: DVD+-RW GU90N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       logical name: /cdrom
       version: A100
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /cdrom
          capabilities: partitioned partitioned:dos
          configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=145a0686 state=mounted
  *-disk
       description: SCSI Disk
       product: xD/SD/M.S.
       vendor: Generic-
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 1.00
       serial: 3
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk
       description: SCSI Disk
       product: SanDisk Ultra
       vendor: SanDisk
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdc
       version: PMAP
       serial: A92504044070
       size: 58GiB (63GB)
       capabilities: removable
       configuration: ansiversion=6 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdc
          size: 58GiB (63GB)
          capabilities: partitioned partitioned:dos
          configuration: signature=9973d54b
kubuntu@kubuntu:~$ 


Is it possible to completely "start again" by erasing the current boot area,etc ? I'm certain that a simple reinstall is not the answer, as the MBR (or whatever it is called these days) has faults.

---

### Post by oygle on 2015-01-15
Ran the [Boot-Reapir]("https://help.ubuntu.com/community/Boot-Repair") utilty, selected "advanced options". Then I tried to wipe everything with DBAN, but it failed to do a "quick" erase. Then ran the Kubuntu install again, this time manually setting the partitions and forcing a format on 2 partitions. The install went fine, no problems. Have rebooted since, and no grub error messages, etc.

All seems okay.  :)

I must say the help/support on these forums is excellent.

Whilst I was in the process of using win 8.1, I was reminded by all the complexities of using M$ products and all that go with them. Give me *nix flavour any day. Fortunately it became such a "time waste" and spinning wheels with windooze that I ruled out the need to run [SPLINK software]("http://www.selectronic.com.au/sppro/splink.htm"). I can live without it, and an alternative [MATE3]("http://www.outbackpower.com/outback-products/communications/item/mate3") runs on Linux, Mac and Windows.

---

### Post by sudodus on 2015-01-16
Congratulations and welcome as an advanced user :KS

---

