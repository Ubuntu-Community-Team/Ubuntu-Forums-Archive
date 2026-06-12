---
title: "system freezes and can't mount disks after changing connections"
date: 2020-03-15
forum: General Help
---

### Post by Thomas_Price on 2020-03-15
How does Ubuntu keep track of drives and figure out how to mount them?

Running 18.04.4 LTS and decided to clean out the case and switch out an old storage HDD with bad sectors (not the main OS drive) with a new SSD.  In doing this, I also switched the cables to different places on the motherboard. Ran into some issues with "Failed to start Load Kernel Modules", but fixed that by switching things around again, commenting out other drives from /etc/fstab and rebooting a bunch.

Now, my system is much slower, and basically freezes if I try to mount any other partitions or do any disk operations. I can't even open gparted.  It also seems like one of the drives is not seen by the whole system.  For instance /dev/sdb shows up when running the "Disks" program, but not when running fdisk:
```

[FONT=Arial]Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors[/FONT]
[FONT=Arial]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=Arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=Arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=Arial]Disklabel type: gpt[/FONT]
[FONT=Arial]Disk identifier: E545301A-18A1-4EE2-95CB-[/FONT][FONT=Arial]EF64CB5EA5C3[/FONT]

[FONT=Arial]Device         Start       End   Sectors  Size Type[/FONT]
[FONT=Arial]/dev/sda1       2048 126982143 126980096 60.6G Linux filesystem[/FONT]
[FONT=Arial]/dev/sda3  126982144 955369484 828387341  395G Linux filesystem[/FONT]




[FONT=Arial]Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors[/FONT]
[FONT=Arial]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=Arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=Arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]


[FONT=Arial]Disk /dev/sdd: 465.8 GiB, 500107862016 bytes, 976773168 sectors[/FONT]
[FONT=Arial]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=Arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=Arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=Arial]Disklabel type: dos[/FONT]
[FONT=Arial]Disk identifier: 0x00044173[/FONT]

[FONT=Arial]Device     Boot     Start       End   Sectors   Size Id Type[/FONT]
[FONT=Arial]/dev/sdd1              63 204796619 204796557  97.7G 83 Linux[/FONT]
[FONT=Arial]/dev/sdd2       204796620 409593239 204796620  97.7G 83 Linux[/FONT]
[FONT=Arial]/dev/sdd3       409593240 976768064 567174825 270.5G 83 Linux[/FONT]


[FONT=Arial]Disk /dev/sde: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors[/FONT]
[FONT=Arial]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=Arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=Arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=Arial]Disklabel type: dos[/FONT]
[FONT=Arial]Disk identifier: 0x000dbedd[/FONT]

[FONT=Arial]Device     Boot      Start        End    Sectors   Size Id Type[/FONT]
[FONT=Arial]/dev/sde1             2048 2539571199 2539569152   1.2T 83 Linux[/FONT]
[FONT=Arial]/dev/sde2       2539571200 3907028991 1367457792 652.1G 83 Linux[/FONT]

```

Looked at logs and didn't see much, but maybe this is a clue from syslog:
```

[FONT=Roboto][FONT=Arial]udisksd[965]: Error performing housekeeping for drive /org/freedesktop/UDisks2/drives/WDC_WD3200AAKX_001CA0_WD_WCAYUZ030525: Error updating SMART data: Error sending ATA command CHECK POWER MODE: Unexpected sense data returned:#0120000: 70 00 0b 00  00 00 00 0a  00 00 10 00  00 00 00 00    p...............#0120010: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00    ................#012 (g-io-error-quark, 0) [/FONT][/FONT]
```[FONT=Roboto][FONT=Arial]

Any help or troubleshooting greatly appreciated!!




[/FONT]



[/FONT]

---

### Post by TheFu on 2020-03-15
in the days before systemd, mounts were controlled by the fstab and perhaps autofs.

Then the systemd-team decided they wanted to "improve" things and sorta modified how the fstab works without screaming about the change to the world or having the fstab file even have a comment to explain the new methods.  For example, some fields in the fstab are ignored by the systemd-mount subsystem.

Any GUi tool being used to mount storage most likely isn't using what i call "real mounts."  Real mounts show up inside the /etc/mtab.  This information is shown when we type '**mount**' w/o any options.

if you want help with the fstab, then please post yours wrapped in 'code tags' here.  We also need the output from **blkid |egrep -v loop** and  **lsblk -e 7 -o name,size,type,fstype,mountpoint**

Please.  All wrapped in *code tags*.

I've never trusted the Disks program (real name  is gnome-disks), but gparted has not let me down for the specific things it does, assuming no HW faults.  gnome-disks seems to lie.

---

### Post by Thomas_Price on 2020-03-19
The next couple of times I booted into my system, I got stuck at the desktop load and couldn't even get to the terminal.  I could see that there was a whole lot of background cpu activity, but even waiting several hours never resolved the problem.

I ended up just copying off the couple of files that I didn't have backed up and reinstalling Ubuntu Mate 19.10.  Re-setting up another system is a pain, but was probably the easier option.

Thank you for attempting to help.  Much appreciated.

---

