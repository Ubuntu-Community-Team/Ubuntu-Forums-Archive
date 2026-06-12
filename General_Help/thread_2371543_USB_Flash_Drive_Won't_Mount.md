---
title: "USB Flash Drive Won't Mount"
date: 2017-09-15
forum: General Help
---

### Post by skanger on 2017-09-15
A 128GB PNY USB flash drive I use mostly to store photos. The drive had 36GB free and I was copying 30GB off of a 32GB card when it halted about halfway through the copy. The drive did get warm to the touch.

Here's the error message:


Error mounting /dev/sda1 at /media/me/PROGRAMS: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sda1" "/media/me/PROGRAMS"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


I'm not using software RAID. I have had some problems with this and another of the same drive when copying files. I use them on several Ubuntu 16.04 laptops and desktops. Originally I was using them with a Windows 10 tablet which is probably why this one was formatted NTFS.

Any help or suggestions are greatly appreciated.

---

### Post by oldfred on 2017-09-15
If Windows NTFS, then you need to run chkdsk first. That cannot be done from Linux.

Also Windows 10 likes to leave partitions mounted as part of its fast start up.
Best to make sure correctly unmounted/removed if used with Windows.

[https://technet.microsoft.com/en-us/library/cc730714.aspx](https://technet.microsoft.com/en-us/library/cc730714.aspx)

---

### Post by skanger on 2017-09-15
Thanks.
I knew I made a mistake not reformatting that drive to FAT. 

Can I do the mount/unmount eject in Windows 7? That's all I have available at the moment.

---

### Post by oldfred on 2017-09-15
It is too late for an unmount, I believe. That is only when you unplug it.

But the chkdsk if important.
Probably best to use newest Windows, but my only experience was running chkdsk with XP, then with Windows 7 and 7 fixed some things that XP did not.

Best to also run chkdsk multiple times as it does not fix all errors on one pass.
And /b parameter is better (see info on link above) if newer Windows not sure if available in Windows 7.

---

