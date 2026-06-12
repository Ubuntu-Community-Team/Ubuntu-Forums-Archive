---
title: "HELP!!! disk read error occurred"
date: 2007-12-10
forum: General Help
---

### Post by kishorebudha on 2007-12-10
Hi. I did a reinstall of Ubuntu on a machine which already had XP. So the machine became a dual boot. I logged in to ubuntu first and then to XP. After I logged back to Ubuntu I was unable to access the NTFS partition. When I logged in a second time, the partition is gone -- though it is listed  in the /media folder

When I tried to mount it I got the following message:

$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

Now I am unable to log into XP. I get disk read error occurred. How do I get my XP partition back please?

---

