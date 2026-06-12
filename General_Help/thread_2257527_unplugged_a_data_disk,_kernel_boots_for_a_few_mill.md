---
title: "unplugged a data disk, kernel boots for a few milliseconds, then powers off PC"
date: 2014-12-20
forum: General Help
---

### Post by fface on 2014-12-20
Hi guys - I am running 14.04 LTS and I have ubuntu installed on a 512 GB SSD.   I also have a spinning disk, formerly used as a data disk, that i want to unplug as I have moved the data to the SSD (power rates in New England suck, so going all SSD).

When I unplug the disk (whilst the PC is powered off), power the PC back on, it goes through BIOS, boots the kernel for about a few milliseconds, then the PC is shutoff.   3-4 seconds later, PC is powered back on, and the cycle repeats.

Right  now, I have the spinning HDD plugged in, to allow the system to boot.

what do I need to do to remove this disk? 
what logs do y'all need?

thanks!

---

### Post by Bashing-om on 2014-12-20
fface; Hi !

There be that process.
OK, 
a) What is set in bios - as the boot priority to boot up ?
```

sudo fdisk -lu

```
so you get an idea of what hard dive is what.

b) where is grub installed to ? ( GRand Uninified Bootloader )
```

sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
sudo blkid
sudo grub-probe -t fs_uuid /boot/grub

```
Do the UUIDs agree and is the boot code installed where you think it is for the boot priority you have set in bios ?

Depending on what is, is what we do. Make it do what you want it to do.

[INDENT][INDENT]it IS all in the process
[/INDENT][/INDENT]

---

### Post by fface on 2014-12-20
>>a) What is set in bios - as the boot priority to boot up ?
validated it to be USB, DVD, HDD.  For HDD, it specifies the 512gb SSD

```

sudo fdisk -lu

```

Here it is.  /dev/sda is the SSD, /dev/sdb is the spinning I want to unplug:

root@leu:/var/log# fdisk -lu

Disk /dev/sda: 512.1 GB, 512110190592 bytes
255 heads, 63 sectors/track, 62260 cylinders, total 1000215216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000e34c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   992018431   496008192   83  Linux
/dev/sda2       992020478  1000214527     4097025    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       992020480  1000214527     4097024   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x735e6ffb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1      1465111935  2930272064   732580065   83  Linux
/dev/sdb2              63  1465111934   732555936   83  Linux


b) where is grub installed to ? ( GRand Uninified Bootloader )
```

sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
sudo blkid
sudo grub-probe -t fs_uuid /boot/grub

```

>>Do the UUIDs agree and is the boot code installed where you think it is for the boot priority you have set in bios ?

Everything looks good to me in terms of pointing to the right thing.
Here is the odd thing.  I get the grub menu with boot choices.  I pick one, I see just few lines of the kernel booting, then BAM!! the power goes off on the PC.  

root@leu:/var/log# debconf-show grub-pc
  grub-pc/install_devices_empty: false
  grub-pc/postrm_purge_boot_grub: false
* grub-pc/install_devices: /dev/disk/by-id/ata-Crucial_CT512MX100SSD1_14330CFC9234
  grub-pc/disk_description:
  grub-pc/timeout: 10
  grub-pc/chainload_from_menu.lst: true
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/hidden_timeout: true
  grub2/kfreebsd_cmdline:
  grub-pc/partition_description:
  grub-pc/install_devices_failed_upgrade: true
  grub2/device_map_regenerated:
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/install_devices_disks_changed:
  grub-pc/install_devices_failed: false
  grub2/linux_cmdline:
  grub-pc/kopt_extracted: false
  grub2/linux_cmdline_default: quiet splash

root@leu:/var/log# grub-probe -t device /boot/grub
/dev/sda1

fface>> this is right

root@leu:/var/log# blkid
/dev/sda1: UUID="f74048b8-1488-4069-a063-dc88a039e16b" TYPE="ext4" 
/dev/sda5: UUID="a9cae07c-5380-466d-9765-8ada934d6e98" TYPE="swap" 
/dev/sdb1: UUID="8e5137a5-8f19-4ac6-ab96-a7eb6f723c22" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="9066b230-d748-49e0-87ed-14fff84635bf" SEC_TYPE="ext2" TYPE="ext3" 

root@leu:/var/log# grub-probe -t fs_uuid /boot/grub
f74048b8-1488-4069-a063-dc88a039e16b

fface>> matches boot partition UUID

---

### Post by fface on 2014-12-20
here is another odd observation.  I set acpi=off in /etc/default/grub, reconfigured grub, then shutdown the PC.  Unplugged the spinninng HDD, then restarted the PC.  Linux boots, I can log in, i can get to tail -f /var/log/kern.log and/or do a few dmesg and then, BAM! lights out, PC turns off, waits about 4 seconds, turns back on, and starts the process over again.

As soon as I plug in the spinning HDD, all is good... system stays up.

So, I think everything is in order wrt to booting, boot files, etc.

something is REALLY funny with the system causing a total power off...

---

### Post by fface on 2014-12-20
motherboard is an intel desk top DH67BL


# lspci

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

---

### Post by Bashing-om on 2014-12-20
fface; Humm ....

You have done the next thing ( re-configure grub ) that I can think of.

As grub appears to be all in order, all I can think of presently is "it specifies the 512gb SSD" <- make sure that the SSD is placed as the first boot priority in bios - rather than any other device. 
Might try and disable '30_os-prober' ( in: /etc/grub.d) in the SSD install , update grub once more and with the spinning hard dive grub out of the picture, see what results when re-booting.

Then again, nother thought, what is set up in the File System Table ? :
```

cat /etc/fstab

```
See that the spinning hard drive is not mounted .

On an outside chance, is there anything suspicious logged in '/var/log/dmesg' , /var/log/syslog , /var/log/kern.log ?

[INDENT][INDENT]make sure we are not lying to our system
 [/INDENT][/INDENT]

---

### Post by fface on 2014-12-21
>>As grub appears to be all in order, all I can think of presently is "it specifies the 512gb SSD" <- make sure that the SSD is placed as the first boot priority in bios - rather than any other device. 

Yes, I made sure this was the case.  I will double check it, however.

>>Might try and disable '30_os-prober' ( in: /etc/grub.d) in the SSD install , update grub once more and with the spinning hard dive grub out of the picture, see what results when re-booting.

I can try that

>>Then again, nother thought, what is set up in the File System Table ? :

I commented out all mount points to that disk, so it should not be trying to mount it.
Anyway, if the kernel powered down the system as a result of a mount point that couldn't be fulfilled, that would be Bad!

>>On an outside chance, is there anything suspicious logged in '/var/log/dmesg' , /var/log/syslog , /var/log/kern.log ?

I checked dmesg, kern.log - seeing nothing, will re-check.
I didn't check syslog.   I was "tail -f" on kern.log one time when it happened and nothing.... the lights just go out.

---

### Post by fface on 2014-12-21
OK - disabling os-prober (I set the variable to "true" in /etc/default/glub seems to have had no effect.

HOWEVER

I removed all SATA devices, including the SATA cables from the motherboard, and now it seems to be staying up.
This also includes removal of my DVD drive.    The ONLY SATA plugged in is the crucial 512GB SSD.
Going to try to plug in the DVD next.... standby...

---

### Post by fface on 2014-12-21
512 GB SATA disk plus DVD causes the issue to occur - system just powers off after about 90s of activity, even tho I am not accessing the DVD drive.  WEIRD.  

Note: I have now plugged in two SSDs - a 64gb and a 512gb - so far, system is staying up.
But, bummer I cannot get the DVD to work.

so, something is weird with that combination: DVD + SSD is causing some toxic mix.
has nothing to do with the spinning HDD near as I can tell.

---

### Post by fface on 2014-12-21
Well, I spoke too soon.  The two SSDs in there eventually caused the system to power down randomly, maybe 5 mins after boot.
I'm going to go back to a single SSD only and see if she stays up.

---

### Post by fface on 2014-12-21
A potential clue?

Dec 21 07:56:29 leu kernel: [    9.892794] hda-intel 0000:00:1b.0: Unstable LPIB (14108 >= 1764); disabling LPIB delay counting

Note: this occurred when I was accessing the *second* SSD - i was doing an fdisk followed by mkfs.ext4 on it.

---

### Post by fface on 2014-12-21
Did not stay up with single SSD.  I am beginning to suspect something weird with the SSD.  I will get Crucial's latest FW and update it.  Maybe something with that ?

---

### Post by fface on 2014-12-21
No FW update for the MX100 SSD I am using.  I'm puzzled.  Other suggestions? 
Pretty odd!!

---

### Post by Bashing-om on 2014-12-21
fface; Wow, Yes, something really weird !

What I would do - as you have done all else - is:
Power the system down, unplug the power cord form the power supply, hold the power button down for a few seconds to discharge the capacitors (CMOS). and also unplug the power leads to the mother board for a few seconds (reset the buss controller ).  Plug all back in and power back up and boot to the bios set up.
Make sure there that the defaults in-place are compatible with the USB hardware . - Plug and play is "enabled" as ubuntu is a fully modern system fully supporting this ability . Only plug back in the bare minimum hardware to boot the system and then; add one piece back into the system at a time and reboot , see what the effect is . - maybe keep in mind to spare off that DVD drive ?

[INDENT][INDENT]fault isolation
[INDENT][INDENT][INDENT]if it ain't software, must be firmware
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

