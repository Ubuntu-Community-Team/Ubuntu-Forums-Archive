---
title: "Ubuntu 7.10: Cannot mount USB"
date: 2007-10-20
forum: General Help
---

### Post by backon18 on 2007-10-20
Just installed Ubuntu 7.10 on my X61. Everything seems to be working. Love the system. But one serious problem: I cannot mount usb! Help please!

After I plugged my usb memory key, the system tried to mount but failed. It said: Cannot mount volumn. invalid mount option when attemping to mount the volume 'TRAVELDRIVE'.

dmesg showed:
[ 386.388000] UDF-fs: No partition found (1)
[ 386.432000] Unable to identify CD-ROM format.
[ 465.116000] UDF-fs: No partition found (1)
[ 465.156000] Unable to identify CD-ROM format.
[ 492.632000] UDF-fs: No partition found (1)
[ 492.676000] Unable to identify CD-ROM format.
[ 533.748000] UDF-fs: No partition found (1)
[ 533.792000] Unable to identify CD-ROM format.
[ 592.784000] usb 6-2: USB disconnect, address 2
[ 598.296000] usb 6-2: new high speed USB device using ehci_hcd and address3
[ 598.432000] usb 6-2: configuration #1 chosen from 1 choice
[ 598.432000] scsi5 : SCSI emulation for USB Mass Storage devices
[ 598.432000] usb-storage: device found at 3
[ 598.432000] usb-storage: waiting for device to settle before scanning
[ 603.432000] usb-storage: device scan complete
[ 603.432000] scsi 5:0:0:0: Direct-Access Memorex TD Classic 003BPMAP PQ: 0 ANSI: 0 CCS
[ 603.660000] sd 5:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
[ 603.660000] sd 5:0:0:0: [sdb] Write Protect is off
[ 603.660000] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 603.660000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 603.664000] sd 5:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
[ 603.664000] sd 5:0:0:0: [sdb] Write Protect is off
[ 603.664000] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 603.664000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 603.664000] sdb: sdb1
[ 603.664000] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 603.664000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[ 604.240000] UDF-fs: No partition found (1)
[ 604.284000] Unable to identify CD-ROM format.

Then I tried manual mount&#65306;sudo mount -t vfat /dev/sdb /mnt/usb
But failed again:
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

---

### Post by DagMan on 2007-10-20
Was this a typo?
sudo mount -t vfat /dev/sdb /mnt/usb

if not then 
sudo mount -t vfat /dev/sdb1 /mnt/usb


also, is it a custom kernel or the stock one, and have you verified the stick is okay on another machine?

---

### Post by backon18 on 2007-10-20
Thanks a lot! I can manually mount it now. I still don't know why the automatic mount does not work.

---

### Post by mastercho on 2007-10-21
i have the same issue. probably should have removed the usb drive when upgrading. [http://picasaweb.google.com/nzwies/Random/photo#5123641637044768946](http://picasaweb.google.com/nzwies/Random/photo#5123641637044768946)

```

 dmesg | tail
[114396.899460] sdc: Mode Sense: 0b 00 00 08
[114396.899463] sdc: assuming drive cache: write through
[114396.902813] SCSI device sdc: 519872 512-byte hdwr sectors (266 MB)
[114396.903699] sdc: Write Protect is off
[114396.903705] sdc: Mode Sense: 0b 00 00 08
[114396.903707] sdc: assuming drive cache: write through
[114396.903713]  sdc: sdc1
[114396.915571] sd 4:0:0:0: Attached scsi removable disk sdc
[114396.915641] sd 4:0:0:0: Attached scsi generic sg3 type 0
[114398.550569] FAT: Unrecognized mount option "usefree" or missing value

```

is the dmesg | tail output. have a similar problem with my DVD drive not automounting anymore for some reason.

---

### Post by DagMan on 2007-10-21
The last post in this bug report might help though it's not the same exact issue.
[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)
> Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again. It works :-)

---

### Post by hfw on 2007-10-21
This is why I love the Ubuntu community!!

When something doesn't work, there is almost always somebody with the answer.  Removing the "usefree" option in gconf-editor fixed this problem for me.

My only question is why we have to do that.  This is something that worked by default in Feisty.

---

### Post by Twotoes on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/newreply.php?do=newreply&amp;noquote=1&amp;p=3585879](http://ubuntuforums.org/newreply.php?do=newreply&amp;noquote=1&amp;p=3585879) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am having a similar problem since I upgraded to Gutsy, my USB stick and camera both getting the same message, Cannot mount volume etc..  but the printer also USB connected is OK.
The USB stick and camera work on Kubuntu no problem.
 Using Dagnam's advice I entered 
sudo mount -t vfat /dev/sdb1 /mnt/usb
and received
mount: mount point /mnt/usb does not exist
A  question asked by DagMan is it a  custom kernal or the stock one ? I don't know.
and his advice - Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options etc - 
I'd like to try but how do you get to the gconf-editor?

---

### Post by daafjay on 2007-10-22
To get to gconf-editor, click Applications>Accessories>Terminal.

In the terminal, enter <sudo gconf-editor> (without the brackets).

Navigate to Storage>default_options>vfat. Double click on <mount_options>, and the Edit Key will open. Click on <unfree> and then select Remove. Click <OK> and exit.

---

### Post by moonliter on 2007-10-22
> **daafjay said:**
> To get to gconf-editor, click Applications>Accessories>Terminal.

In the terminal, enter <sudo gconf-editor> (without the brackets).

Navigate to Storage>default_options>vfat. Double click on <mount_options>, and the Edit Key will open. Click on <unfree> and then select Remove. Click <OK> and exit.

It didn't work for my mp4 usb player and when I type lsusb on the terminal nothing happens

> moonliter@loki:~$ lsusb


---

### Post by mdl76 on 2008-02-15
so i guess this has not been fixed... my 7.10 will not mount ntfs volume.
no wonder people are still using windoz...

---

### Post by strabes on 2008-02-15
> **mdl76 said:**
> so i guess this has not been fixed... my 7.10 will not mount ntfs volume.
no wonder people are still using windoz...

[http://ubuntuforums.org/showthread.php?t=582045](http://ubuntuforums.org/showthread.php?t=582045)

Perhaps if you were not using a proprietary, closed-source, and inferior filesystem that had to be reverse engineered you would not run into so many problems. By the way, have you tried reading or writing to an ext3 filesystem in windows?

[Few updates are released](https://wiki.ubuntu.com/StableReleaseUpdates) after stable releases of ubuntu. If you want a completely stable system install debian etch and enable security updates.

---

### Post by rikonen on 2008-02-16
> **backon18 said:**
> Just installed Ubuntu 7.10 on my X61. Everything seems to be working. Love the system. But one serious problem: I cannot mount usb! Help please!

After I plugged my usb memory key, the system tried to mount but failed. It said: Cannot mount volumn. invalid mount option when attemping to mount the volume 'TRAVELDRIVE'.

dmesg showed:
[ 386.388000] UDF-fs: No partition found (1)
[ 386.432000] Unable to identify CD-ROM format.
[ 465.116000] UDF-fs: No partition found (1)
[ 465.156000] Unable to identify CD-ROM format.
[ 492.632000] UDF-fs: No partition found (1)
[ 492.676000] Unable to identify CD-ROM format.
[ 533.748000] UDF-fs: No partition found (1)
[ 533.792000] Unable to identify CD-ROM format.
[ 592.784000] usb 6-2: USB disconnect, address 2
[ 598.296000] usb 6-2: new high speed USB device using ehci_hcd and address3
[ 598.432000] usb 6-2: configuration #1 chosen from 1 choice
[ 598.432000] scsi5 : SCSI emulation for USB Mass Storage devices
[ 598.432000] usb-storage: device found at 3
[ 598.432000] usb-storage: waiting for device to settle before scanning
[ 603.432000] usb-storage: device scan complete
[ 603.432000] scsi 5:0:0:0: Direct-Access Memorex TD Classic 003BPMAP PQ: 0 ANSI: 0 CCS
[ 603.660000] sd 5:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
[ 603.660000] sd 5:0:0:0: [sdb] Write Protect is off
[ 603.660000] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 603.660000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 603.664000] sd 5:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
[ 603.664000] sd 5:0:0:0: [sdb] Write Protect is off
[ 603.664000] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 603.664000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 603.664000] sdb: sdb1
[ 603.664000] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 603.664000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[ 604.240000] UDF-fs: No partition found (1)
[ 604.284000] Unable to identify CD-ROM format.

Then I tried manual mount&#65306;sudo mount -t vfat /dev/sdb /mnt/usb
But failed again:
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

I had similar problem, the reason was that I made installation from USB key and installation program made a wrong expection that it's CDROM and included that in fstab. This PC do not have CDROM at all.

To solve the problem type:
sudo gedit /etc/fstab

and add # mark in beginning of line where cdrom is introduced, example:

before 
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

after
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

save the file, restart, and enjoy :guitar:

Regards,
Rami

---

### Post by Schnitty on 2008-04-29
Rami - that was the perfect solution!  i totally spaced that i had installed from a usb drive.  thanks for the help!

---

