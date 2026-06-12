---
title: "USB disk change to read only"
date: 2007-05-23
forum: General Help
---

### Post by Beefeater on 2007-05-23
Ok my usb disk mounts fine and everything works. I go and cook some dinner or whatever and when I come back to transfer some files I get

mv: cannot create regular file `/media/usbdisk/foo.foo': Read-only file system

Took a look in the syslog .. I'm not happy. What to do?

Tankful for any help I can get.

EDIT: I should say that I can unmount it and plug it in again and everything is alright.

May 23 18:15:09 southpark kernel: [17681643.056000] sd 10:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
May 23 18:15:09 southpark kernel: [17681643.056000]     Additional sense: Logical unit not ready, initializing cmd. required
May 23 18:15:09 southpark kernel: [17681643.056000] end_request: I/O error, dev sdb, sector 12479
May 23 18:15:09 southpark kernel: [17681643.060000] sd 10:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
May 23 18:15:09 southpark kernel: [17681643.060000]     Additional sense: Logical unit not ready, initializing cmd. required
May 23 18:15:09 southpark kernel: [17681643.060000] end_request: I/O error, dev sdb, sector 8383
May 23 18:15:09 southpark kernel: [17681643.060000] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=2, block=1040
May 23 18:15:09 southpark kernel: [17681643.060000] Aborting journal on device sdb1.
May 23 18:15:09 southpark kernel: [17681643.076000] sd 10:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
May 23 18:15:09 southpark kernel: [17681643.076000]     Additional sense: Logical unit not ready, initializing cmd. required
May 23 18:15:09 southpark kernel: [17681643.076000] end_request: I/O error, dev sdb, sector 12527
May 23 18:15:09 southpark kernel: [17681643.076000] Buffer I/O error on device sdb1, logical block 1558
May 23 18:15:09 southpark kernel: [17681643.076000] lost page write due to I/O error on sdb1 
May 23 18:15:11 southpark dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 23 18:15:15 southpark kernel: [17681649.248000] EXT3-fs error (device sdb1) in ext3_reserve_inode_write: IO failure
May 23 18:15:15 southpark kernel: [17681649.248000] EXT3-fs error (device sdb1) in ext3_dirty_inode: IO failure
May 23 18:15:15 southpark kernel: [17681649.284000] ext3_abort called.
May 23 18:15:15 southpark kernel: [17681649.284000] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal
May 23 18:15:15 southpark kernel: [17681649.284000] Remounting filesystem read-only

---

### Post by booljayj on 2007-05-26
I'm no expert, but reading through those logs it seems as though it's trying to use an ext3 file system on your drive. Maybe changing that to fat or something else would help. Look around in these forums on how to edit fstab, that might get you started

---

### Post by Beefeater on 2007-05-26
> **booljayj said:**
> I'm no expert, but reading through those logs it seems as though it's trying to use an ext3 file system on your drive. Maybe changing that to fat or something else would help. Look around in these forums on how to edit fstab, that might get you started

Thanks for your reply.
Fat32 would have been an option if I didn't work with files > 4GB.
I'm not an expert when it comes to file systems. Is there something else that I could try?

But I don't think if it would help with another file system anyway, feels like it's a problem with the USB Controller itself.
It's just so bloody irritating, will not go with a DELL laptop ever again (had other issues in the past with this one)

Please, someone, help me out here.

---

### Post by robertzwo on 2008-02-13
I got the same problem with feisty and Knoppix 5.1 + Knoppix 5.2 on an dell inspiron 6400 N with 3.5'' 500 Gig Seagate ATA-IDE attached with external USB-Connector.
This switching to read-only-mode in ext3 seems to be some kind of  emergency action caused by an inconsistent ext3 file system. It happened always after the first try to change data.

fsck does not help. Each time I startet it, fsck found something to correct. Creating new errors instead of repairing the file system is dangerous, so my advise is  "Don't use fsck (in this situation)". Maybe I have destroyed some data, maybe even this read-only mode doesn't works correct - I don't know.

I "solved" the error by deactivating the "boot from USB" option in the system BIOS. (Yes, it is the fact of being enabled in the bios - it's not the question from where the computer just booted). It looks as if the BIOS provides some different kind of USB if USB-booting is enabled.

---

### Post by Beefeater on 2008-02-13
Hi,

I solved this 7-8 months ago and haven't had any problems since.

Create a executable file for example /usb/bin/usbhdfix and place the following in it.

```
#!/bin/bash
echo 1024 > /sys/block/$1/device/max_sectors
echo 1 > /sys/block/$1/device/scsi_disk:*/allow_restart
```

1024 works for me but I've also heard about people going lower than default with good results.
I have a Seagate FreeAgent which also have the problem with restarting after spinning down so solution for that is added as well.

Then create a udev-rule.

```
# /etc/udev/rules.d/50-fix_usb_hd.rules
SUBSYSTEMS=="scsi", ATTRS{vendor}=="Seagate", ATTRS{model}=="FreeAgentDesktop", RUN+="/usr/bin/usbhdfix %k"
```

Happy hunting :-)

---

