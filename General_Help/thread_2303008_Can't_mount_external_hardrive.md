---
title: "Can't mount external hardrive"
date: 2015-11-15
forum: General Help
---

### Post by Julian1968 on 2015-11-15
Hello

My external hardrive has been working fine for back ups but over the past few days I get the following message

Error mounting /dev/sdb1 at /media/julian/SAMSUNG: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/julian/SAMSUNG"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

I have no idea what to do with this can someone help me out please?

Thanks

---

### Post by yancek on 2015-11-15
It's a windows filesystem on the partition in question.  What happens when you follow the suggestion in the message to run chkdsk from windows?
Not mounting is a result in most cases of having the partition mounted in windows and not doing a full shutdown but just rebooting.  Windows 8 and newer hibernate by default.

---

### Post by Julian1968 on 2015-11-15
Thanks but Not sure why, I dont use windows at all. Its only ever been used on my Ubuntu 14 - I never just unplug the drive but exit properly

---

