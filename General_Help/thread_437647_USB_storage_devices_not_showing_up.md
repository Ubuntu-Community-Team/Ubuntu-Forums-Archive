---
title: "USB storage devices not showing up"
date: 2007-05-09
forum: General Help
---

### Post by Arthur D on 2007-05-09
I'm running xubuntu with fiesty and the only usb devices that work for me are the mouse and keyboard, the storage devices like my camera dvd player and mp3 player don't show up at all. They have before and sometimes it will work but most of the time it doesn't.

---

### Post by gradedcheese on 2007-05-09
Use dmesg to see what's going on.  First, clear its output: "sudo dmesg -c" and then insert the device.  Wait a few seconds and run "dmesg" to see the messages, post them here.   Or post the result of:

```

dmesg | tail

```

after plugging the device in a waiting for a few seconds.

---

### Post by Arthur D on 2007-05-09
This is what I got.

[PHP][34592.624000] usb 3-3: new high speed USB device using ehci_hcd and address 50
[34592.884000] usb 3-3: configuration #1 chosen from 1 choice
[34592.884000] scsi10 : SCSI emulation for USB Mass Storage devices
[34592.884000] usb-storage: device found at 50
[34592.884000] usb-storage: waiting for device to settle before scanning
[34597.884000] usb-storage: device scan complete
[34598.032000] scsi 10:0:0:0: CD-ROM            Memorex  DVD16+/-DL4RWlD2 JWS5 PQ: 0 ANSI: 0
[34603.628000] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[34603.628000] sr 10:0:0:0: Attached scsi CD-ROM sr0
[34603.628000] sr 10:0:0:0: Attached scsi generic sg0 type 5
[/PHP]

---

### Post by gradedcheese on 2007-05-09
ok, so it looks like it found a USB CD-ROM drive, is that what you plugged in?

---

### Post by Arthur D on 2007-05-09
Yeah but it doesn't show up in my file system or as an icon on the desktop. I have tried different discs but that makes no difference.

---

### Post by gradedcheese on 2007-05-09
hmm, try putting a disk in a mounting it manually.  First check what the device name is, usually for a SCSI CD-ROM (which is what this one appears as) it's /dev/scd0, for the first one, and so on.

```

sudo mount -t iso9660 /dev/cdrom /mnt

```

(replace /dev/cdrom with the right device)

---

### Post by Arthur D on 2007-05-09
[PHP]arthur@arthur-laptop:~$ ls -l /dev/disk/by-id
total 0
lrwxrwxrwx 1 root root  9 2007-05-08 13:40 ata-FUJITSU_MHT2080AT_PL_NN4FT4B1695F -> ../../hda
lrwxrwxrwx 1 root root 10 2007-05-08 13:40 ata-FUJITSU_MHT2080AT_PL_NN4FT4B1695F-part1 -> ../../hda1
lrwxrwxrwx 1 root root 10 2007-05-08 13:40 ata-FUJITSU_MHT2080AT_PL_NN4FT4B1695F-part2 -> ../../hda2
lrwxrwxrwx 1 root root 10 2007-05-08 23:41 usb-Memorex_DVD16+.-DL4RWlD2_9900000000001A9C-0:0 -> ../../scd0
arthur@arthur-laptop:~$ sudo mount -t iso9660 usb-Memorex_DVD16+.-DL4RWlD2_9900000000001A9C-0:0 /mnt
mount: special device usb-Memorex_DVD16+.-DL4RWlD2_9900000000001A9C-0:0 does not exist
[/PHP]

---

### Post by gradedcheese on 2007-05-09
It's scd0, so:

```

sudo mount -t iso9660 /dev/scd0 /mnt
ls /mnt

```

---

### Post by Arthur D on 2007-05-09
[PHP]arthur@arthur-laptop:~$ sudo mount -t iso9660 /dev/scd0 /mnt
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

arthur@arthur-laptop:~$ dmesg | tail
[36083.784000] sr 15:0:0:0: Attached scsi generic sg0 type 5
[36407.244000] attempt to access beyond end of device
[36407.244000] sr0: rw=0, want=68, limit=4
[36407.244000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[38084.656000] attempt to access beyond end of device
[38084.656000] sr0: rw=0, want=68, limit=4
[38084.656000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[38118.960000] attempt to access beyond end of device
[38118.960000] sr0: rw=0, want=68, limit=4
[38118.960000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
arthur@arthur-laptop:~$ 
[/PHP]

---

### Post by gradedcheese on 2007-05-09
ouch :(  I don't have anything more off the top of my head, perhaps it's time for you to file a bug over at launchpad, including the output from your last post and a description of the device in question.   Or perhaps someone else has some good ideas?

---

### Post by Arthur D on 2007-05-09
Thanks for the help I will see if anyone else has an idea before I report a bug.

---

### Post by antiigrav on 2007-10-09
This problem started for me with the last ubuntu automatic software update.

Before this all usb storage devices would auto-mount.

Now only very very occasionally will they - no pattern is obvious.

When they dont (most of the time) they dont even show up under places -> computer.

Please post back to this thread if you get anywhere with the bug report.

Thanks.

---

### Post by antiigrav on 2007-10-10
I think i figured out the cause of my problem:

(Coincidence with the ubuntu update which is prob not the cause:)

[B]I (after shutdown) unplugged a ntfs sata drive from my system.

When ubuntu restarted, the ntfs driver (config tool) probably failes (silently) when it doesn't find the drive again and takes whatever does usb-device-detection down with it.[/B]

I havnt resolved the problem yet: I just plugged the sata drive back in!

So i will have to look into removeing the drive from a config file somewhere... any ideas plz anyone?

---

