---
title: "cdrom mount fail"
date: 2008-07-03
forum: General Help
---

### Post by jambroo on 2008-07-03
Hello people,

This cdrw used to work up until a while ago - but now when i try to mount it I get the following error:
> mount: block device /dev/hda is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I check dmesg I get this:
> [86996.031538] attempt to access beyond end of device
[86996.031548] hda: rw=0, want=68, limit=4
[86996.556379] attempt to access beyond end of device
[86996.556390] hda: rw=0, want=1252, limit=4
[86996.556399] attempt to access beyond end of device
[86996.556402] hda: rw=0, want=1028, limit=4
[86996.556406] UDF-fs: No partition found (1)
[86996.598145] attempt to access beyond end of device
[86996.598153] hda: rw=0, want=68, limit=4
[86996.598158] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16

The cdrom is being mounted like it always was in fstab:
> /dev/hda  /media/cdrom0  udf,iso9660  user,noauto  0  0

ls -l /dev/hda gives this:
> brw-rw-rw- 1 root cdrom 3, 0 2008-07-03 12:57 /dev/hda

I can't think of anything that ive done to affect the cdrw working.

-Jamie

---

### Post by VMC on 2008-07-04
Have you tried inserting a disk into your cdrom drive?

Here's my fstab line:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Yours shows /dev/hdx. That doesn't look right. Checking back, someone with almost the exact same issue had there's setup the same as yours.

---

### Post by tipiglen on 2008-07-04
try running this command and see what shows up.
```


sudo lshw -C disk

```
You should get a listing, containing something like this:
     ```

  *-cdrom
       description: DVD reader
       product: CDRW/DVD SM-308B
       vendor: SAMSUNG
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: T101
       serial: [SAMSUNG CDRW/DVD SM-308BT101C
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready

```
Then check your fstab file (/etc/fstab) and look for the line referring to your cdrom (it will probably contain a reference to udf and/or 9660 )

I solved the same problem by changing the entry in my /etc/fstab to identify the cdrom by the FIRST logical name listed. (mine showed scd0 (third), and I changed it to cdrom1)

It seemed worth trying, and it worked for me.

Hope it works for you

Salaam/Shalom/Shanthi/Dorood/Peace
Namaste -ed

---

### Post by DeathOnJuice on 2008-07-04
My cdrom used to be hda, so that might not be the problem. Hardy changed it to scd0, though.

What OS did you burn this disc in? I had a similar error when Vista, in Microsoft's ever-friendly-way, burned a disc in the Live File System (LFS), readable only by XP and Vista. Ubuntu thought it was corrupted UDF.

How did I solve it? I didn't actually fix the CD; if needed, try your CD on another computer, and copy the files to a flash drive. This may fix the problem even if it isn't related to LFS.

---

### Post by jambroo on 2008-07-06
Thanks for the replies people - sorry for the delay..

VDM - I have no /dev/scd* - and it comes up when i run "sudo lshw -C disk" with the logical name /dev/hda. Your fstab line had exec,utf8 extra in options - but that didn't seem to change anything.

tipiglen - I ran lshw and got the following. Unlike yours it only showed up with one logical name - but when I had a look in /dev/ there was a few that reference /dev/hda. They were: cdrom, cdrw, dvd and dvdrw.

>   *-cdrom
       description: DVD writer
       product: PIONEER DVD-RW DVR-111D
       vendor: Pioneer
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 1.23
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma4 status=ready
     *-medium
          physical id: 0
          logical name: /dev/hda


DeathOnJuice - I don't think it is a disc issue - ive tried blank CD-Rs and CDs burnt in Windows XP as well as Ubuntu.

---

