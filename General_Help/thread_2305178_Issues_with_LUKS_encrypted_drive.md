---
title: "Issues with LUKS encrypted drive"
date: 2015-12-03
forum: General Help
---

### Post by Konrad_Stoudenmire on 2015-12-03
My laptop has two physical drives.  A SSD drive which has several logical volumes for the OS.  It's encrypted via LUKS and works fine.  The issue I'm having is with the second hard drive.  It's a 1TB drive that I encrypted with LUKS.  First issue is that I can't get it to unlock on boot.  I have the "Unlock at startup" option checked.  Second issue is that once I manually unlock it, I can't manually lock it.  I get an error window that starts with "Error locking /dev/dm-8 (/dev/sda1): Command-line 'cryptsetup luksClose "luks-148253c8-c044-4324-bbbb-a78c0fc63f12" exited with non-zero exit status 5: device-mapper: remove ioctl on luks-148253c8-c044-4324-bbbb-a78c0fc63f12 failed: Device or resource busy"  The later part of that error repeats about 20 times with the last line stating the drive is still in use.  There is nothing running that is utilizing that drive as far as I know.  There are a few logical volumes that I have created on that drive that also fail to mount during boot.  I have to skip mounting those to boot up.  Once booted, I can unlock the 1TB drive fine and the volumes mount with no problem.

The volumes that I have created on the 1TB drive work fine.  Well almost.  I tried to create a folder to use as share for a virtual machine, but my virtual machine fails to start when I use a folder on a volume created on the 1TB drive.  The share works fine if the folder is on a volume on the SSD drive.  Pretty sure I've hosed something up in regards to the 1TB drive.

Please help me troubleshoot this issue!  This is driving me crazy and I'm not very familiar with Linux.

---

