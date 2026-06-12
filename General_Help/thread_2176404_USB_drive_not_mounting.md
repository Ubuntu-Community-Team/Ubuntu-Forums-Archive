---
title: "USB drive not mounting"
date: 2013-09-24
forum: General Help
---

### Post by daka on 2013-09-24
I installed ubuntu 12.04 on a new Lenovo Edge 72 yesterday.  Now my USB drive is not mounting and I don't know if it is a hardware fault or  Windows 7 related NTFS issue.  Here is the error message.

Any suggestions on how to mount and more importantly how to save all that critical information ?

Thanks

sean


Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup_warn: magic: 0x46464952  size: 1024   usa_ofs: 29056  usa_count: 1068: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x0004fffb  size: 1024   usa_ofs: 65534  usa_count: 65534: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x0001fffe  size: 1024   usa_ofs: 65535  usa_count: 0: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x00020001  size: 1024   usa_ofs: 65532  usa_count: 3: Invalid argument
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by whitesmith on 2013-09-24
> **daka said:**
> I installed ubuntu 12.04 on a new Lenovo Edge 72 yesterday.  Now my USB drive is not mounting and I don't know if it is a hardware fault or  Windows 7 related NTFS issue.Help me understand your issue. Your Windows C: drive is sda and you attempted to install Ubuntu on the USB drive, sdb. Is that right?

---

### Post by daka on 2013-09-24
> **whitesmith said:**
> Help me understand your issue. Your Windows C: drive is sda and you attempted to install Ubuntu on the USB drive, sdb. Is that right?

Thanks for your reply

I did not try to install to sdb, it seemed to install ok to sda...I actually installed two linux operating systems and they both seem to boot perfectly in Grub.  Also Windows boots perfectly.

I do remember however, in the past, being surprised that sdb was suggested by default as the place to install bootloader during the install, so your question has me wondering.  I assumed that it would install to sda (as it has for years) but maybe it installed to sdb.  Is that what you see from the screenshot?  If so is there any hope of recovering the data?

Sean

---

