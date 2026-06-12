---
title: "HOWTO: Burn DVD"
date: 2005-07-11
forum: General Help
---

### Post by kelvinq on 2005-07-11
I scoured the web for easy to follow instructions for burning my SuSE Linux 9.3 using (Ubuntu) Linux but I couldn’t find detailed ones. Most of them just referred me to use k3b, which I didn’t want to.

So here’s an (hopefully) easy to follow instructions for burning DVDs in Linux using [cdrecord-ProDVD](ftp://ftp.berlios.de/pub/cdrecord/ProDVD/) .

Frist of all, cdrecord-ProDVD seems to be a project of cdrecord. Correct me if I’m wrong.

1) Download cdrecord-ProDVD latest binary and license key (cdrecord-wrapper.sh free for non-commercial use).

2) Place them both in your /usr/bin directory. Chmod them if you need to (sudo chmod +x filename). You might also have to rename the binary to cdrecord-ProDVD so that the wrapper can find it.

3) You’ll need to issue a command along this line:
sudo cdrecord-wrapper.sh dev=(device name) path-to-iso

As you might already have realised, you’ll be accessing the binary via the wrapper.

To find out the device name to your dvd burner, use mount.

kelvinq@ubuntu:~/Desktop/downloads$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hda5 on /home type ext3 (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdb on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=kelvinq)

Your device name is then /dev/hdb. You can of course symlink it if you want to, but I don’t find a need.

4) Once you issue that command, cdrecord-ProDVD assumes that you are writing in tao mode. If your drive, like mine, doesn’t support it, you’ll get an error. To find out what mode your drive supports, issue cdrecord-wrapper.sh dev=/dev/hdb -checkdrive

kelvinq@ubuntu:~/Desktop/downloads$ cdrecord-ProDVD dev=/dev/hdb -checkdrive
Cdrecord-ProDVD-Clone 2.01b31 (i686-pc-linux-gnu) Copyright (C) 1995-2004 J\uffffrg Schilling
Unlocked features:
Limited features:
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.8'.
Device type : Removable CD-ROM
Version : 0
Response Format: 2
Capabilities :
Vendor_info : 'BENQ '
Identifikation : 'DVD DD DW1620 '
Revision : 'B7T9'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
cdrecord-ProDVD: This version of cdrecord limits DVD-R/DVD-RW support to -dummy or 1 GB real.
cdrecord-ProDVD: If you need full DVD-R/DVD-RW support, ask the Author for cdrecord-ProDVD.
cdrecord-ProDVD: Free test versions and free keys for personal use are at [ftp://ftp.berlios.de/pub/cdrecord/ProDVD/](ftp://ftp.berlios.de/pub/cdrecord/ProDVD/)
Using generic SCSI-3/mmc-2 DVD-R/DVD-RW driver (mmc_dvd).
Driver flags : DVD MMC-3 SWABAUDIO BURNFREE
**Supported modes: PACKET SAO**

In bold, my drive supports sao. So my final command is:
sudo cdrecord-wrapper.sh -sao dev=/dev/hdb ./SUSE-9.3-Eval-DVD.iso

cdrecord-ProDVD successfully detected my drive type, media speed (2x), type (DVD-RW) and burned the iso perfectly.

kelvinq@ubuntu:~/Desktop/downloads$ sudo cdrecord-wrapper.sh -sao dev=/dev/hdb ./SUSE-9.3-Eval-DVD.iso
Cdrecord-ProDVD-Clone 2.01b31 (i686-pc-linux-gnu) Copyright (C) 1995-2004 J\uffffrg Schilling
Unlocked features: ProDVD Clone
Limited features:
This copy of cdrecord is licensed for: private/research/educational_non-commercial_use
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.8'.
Device type : Removable CD-ROM
Version : 0
Response Format: 2
Capabilities :
Vendor_info : ‘BENQ ‘
Identifikation : ‘DVD DD DW1620 ‘
Revision : ‘B7T9&#8242;
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc-2 DVD-R/DVD-RW driver (mmc_dvd).
Driver flags : DVD MMC-3 SWABAUDIO BURNFREE
Supported modes: PACKET SAO
Starting to write CD/DVD at speed 2 in real SAO mode for single session.
Last chance to quit, starting real write 0 seconds. Operation starts.
Turning BURN-Free off
Track 01: Total bytes read/written: 4488353792/4488353792 (2191579 sectors).

5) As you can see from above, output was pretty bare during the burning process. You might want to tweak it to your needs with cdrecord-wrapper.sh -help to see the available options.

Hope that helps. 

This post is also available [here](http://www.kquee.com/blog/2005/07/11/burn-dvds-in-linux/) .

---

