---
title: "Broken NTFS partition - Windows doesn't boot up"
date: 2015-01-14
forum: General Help
---

### Post by dimitar4 on 2015-01-14
Hello dear Ubuntu fellas,

Been using Ubuntu quite a while on my desktop and am so much satisfied with it. But now I've encountered a problem.

Dual booting Ubuntu 14.10 with Windows 7. Although I mainly use Ubuntu, sometimes I need Windows - League of Legends (dammit). Today I experienced problems with booting into Windows. Nothing seems to help. 

Windows and Ubuntu are on one hard disk, different paritions. Using second and third HDD for data.

When I try to reach the NTFS partition via Ubuntu an error shows up:

```
Error mounting /dev/sda1 at /media/dimitar/Windows: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda1" "/media/dimitar/Windows"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

When I try to boot into Windows - 0x0c000001.

Both are 64 bit installations if that's important. Using Burg if that's of somebody's use.

Tried almost everything. I don't want to reinstall Windows, because I sometimes (in emergency cases) use it for work and got important files on the partition. 

Any ways of at least recovering those files via Ubuntu?
Any ways of saving this Windows installation?

Your best,
Dimitar

---

### Post by DuckHook on 2015-01-14
First and foremost, do a backup of your Ubuntu data *right now*. Your HDD may be dying. It's too bad you did not back up your Windows data, but no point in dwelling on regrets either. I'm betting that you will be doing regular backups from now on.

You can run a *chkdsk* using the Windows recovery disk. Always do that with problem NTFS partitions created by Windows. Else, follow instructions [here]("http://ubuntuforums.org/showthread.php?t=1907603&p=11604167#post11604167") ...and render proper obeisance to master *oldfred*.

...and stop using BURG which has been abandoned for years.

Apologies for curt instructions but I'm leaving momentarily and won't be back for some time. Won't be able to help of many hours. Hoping someone will dive in here. If you attract *oldfred*'s attention, you will be in good hands.

---

### Post by ineuw on 2015-01-14
The message indicates that you might be running a RAID software???

First, try to analyse and possibly correct the disk access problem from Ubuntu using Gparted. That won't correct the boot problem, it only determines and possibly fixes NTSF disk access. If NTFS access from Linux is repaired and the data is readable, you need to have on hand a Linux/Ubuntu 64bit Boot-Repair disk (available from Sourceforge) AND a Windows 7 64 bit repair disk from Microsoft. They need to be downloaded as ISO's and either burnt into separate CD's, or installed on USB keys. This is required because when Windows boot is repaired, you loose access to Ubuntu. First you repair Windows boot, and then the Ubuntu boot which reinstalls Grub. I hope this helps.

---

### Post by oldfred on 2015-01-14
The error message is a generic, Linux NTFS driver cannot mount.
It can be any or all of the issues.

Most common is minor corruption that chkdsk may fix, or Windows was left hibernated which also prevents the Linux NTFS driver from mounting the NTFS partition.

You can force mount in read only mode if you have to backup data that you cannot otherwise read. But best to run Windows repairs first.

Last case is that hard drive is failing, and then use Disks or Disk Utility to run Smart data to see if drive has major issues. Often then backups are only recourse.

---

