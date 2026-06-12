---
title: "Recovery..."
date: 2014-07-09
forum: General Help
---

### Post by sc.ciprian on 2014-07-09
Hello everyone,


My windows got corrupted for some reason and I need to do a backup of some files I had on the Windows partition. I decided to use the Ubuntu LiveCD and managed to get access to all the partitions, except the Windows partition! Every time I try to open the Windows partition I get a message box that says: "Unable to access 113GB volume drive" and in the box there is this:

> 
Error mounting /dev/sda2 at /media/ubuntu/9AF20287F20267B9: Command-line `mount -t "ntfs" -o"uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda2" "/media/ubuntu/9AF20287F20267B9"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).Failed to mount '/dev/sda1': Input/output errorNTFS is either inconsistent, or there is a hardware fault, or it's aSoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windowsthen reboot into Windows twice. The usage of the /f parameter is veryimportant! If the device is a SoftRAID/FakeRAID then first activateit and mount a different device under the /dev/mapper/ directory, (e.g./dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentationfor more details.

Well...The thing is I have never used Ubuntu before and I really have no idea what does it mean, except trying to do an chkdsk in Windows, but which I cannot boot up...I only need to backup those files.

Any help or advice, please? Thank you.

---

### Post by grahammechanical on 2014-07-09
What version of Windows is this? If it is Windows 8 then Ubuntu cannot read the partition because when Windows 8 shuts down it actually hibernates and that prevents the partition from being read by Ubuntu.

The error message asks is the device a SoftRAID/FakeRAID? Do you know the answer? The message is also saying that the file manager cannot mount the partition and it gives 3 possible reasons: 

input/output error NTFS is inconsistent
there is a hardware fault
it is SoftRAID/FakeRAID hardware

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

TestDisk is in the Ubuntu software centre.

Regards.

---

