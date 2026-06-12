---
title: "[SOLVED] My SD is now read-only?!"
date: 2008-05-15
forum: General Help
---

### Post by YAOMTC on 2008-05-15
EDIT: Uh... if you're ever unable to write to SD, *make sure that it's not locked.* It's such a little switch, easy to forget about if you don't take the SD out of the reader.

---

### Post by YAOMTC on 2008-05-17
.

---

### Post by storm99999 on 2008-05-17
Hmm, you can force the file system to recognize you as the owner by using the command "sudo chown -R <your username> <the location of your sd card>", which will recursively change the owner of the files to you.  After that, you can just right click the directory and go to properties, permissions, and set the owner's (which should be you now) permissions to read and write.

Best of luck there.

---

### Post by sdennie on 2008-05-17
How have you formatted the disk?  If it's formatted as ext3 or something that properly follows unix permissions, it's possible that, upon fresh install of Hardy, your user id is no longer the same and so you know longer own the files.

---

### Post by jongkind on 2008-05-17
Maybe it is something very trivial: there is a little switch on the SD card, make sure that it is set so that it allows writing.

---

### Post by chrisccoulson on 2008-05-17
Is it formatted with FAT32? If so, chown and chmod will not work as the filesystem has no concept of Unix file permissions. The access permissions are determined solely by mount options. Besides, if you're getting an error saying the volume is read-only, chown and chmod won't work on *any* filesystem. The file-system has to be mounted read-write first.

There are a few reasons why it is mounting read-only: There could be a write protect switch set in the wrong position, the 'ro' was specified as a mount option or the filesystem has errors

My guess is that it is the latter.

I'm going to assume that your SD card has a FAT32 filesystem on it, and you are auto-mounting it. With this assumption, do the following:
[LIST=1]
[*]Open a terminal and run:
```
tail -f /var/log/syslog
```
[*]Connect your SD card whilst monitoring the output in the terminal you've just opened
[/LIST]
If you see anything that references 'Filesystem panic' or any errors, then your filesystem has errors and will need fixing (this will be why it is read only). If you're unsure, post the output here.

If your SD card has errors, you need to run fsck. Working on the assumption that this is a FAT32 filesystem again:
```
sudo dosfsck -a -v /dev/sdxx
```
...where /dev/sdxx is the device node for your SD card

---

### Post by philgenius on 2008-08-27
```
Aug 27 17:47:25 1951-44U kernel: [25480.647108] sd 9:0:0:0: [sdc] Attached SCSI removable disk
Aug 27 17:47:25 1951-44U kernel: [25480.647182] sd 9:0:0:0: Attached scsi generic sg3 type 0
Aug 27 17:47:25 1951-44U NetworkManager: <debug> [1219873645.357834] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_58f_6335_058F011111B1_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 27 17:47:25 1951-44U NetworkManager: <debug> [1219873645.537337] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_SD_MMC_Card_Reader_058F011111B1_0_0'). 
Aug 27 17:47:25 1951-44U NetworkManager: <debug> [1219873645.665495] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3030_3961'). 

```

That's the output. Any ideas? Is it the fact that I have Hardy?

---

