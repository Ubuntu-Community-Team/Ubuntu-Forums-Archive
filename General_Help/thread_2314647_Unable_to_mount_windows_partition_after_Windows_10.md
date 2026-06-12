---
title: "Unable to mount windows partition after Windows 10 upgrade"
date: 2016-02-22
forum: General Help
---

### Post by crew-j on 2016-02-22
Am running ubuntu 14.04 on dell laptop, formerly Windows 7. 

After upgrading to Windows 10, I am getting 'unable to mount /dev/sda3.... windows in an unsafe state, windows is suspended, which it isn't having been closed down properly. Try mount in read only mode. 
U
My linux knowledge is limited, and I have tried all combinations of mount that I can think of, without success, as well as trying to include line in mtab - probably illegal. 

Any advice appreciated.. 


(Used to be mounted automatically, and openable by file manager)

---

### Post by yancek on 2016-02-22
It used to be mounted automatically because it was windows 7 and now you have windows 10.  windows 8 and newer have always on hibernation and no Linux system will mount a hibernated partition.  You need to do what the message says and turn off the fast boot or fast start and hibernation options.  The new versions of windows do hibernation to make it appear they are booting faster.

---

### Post by goofprog on 2016-02-22
Sometimes Linux has a problem with NTFS, the file system for most of the Windows OS, so what I did was plugged the hard drive into a Windows computer to fix the problem with the file system.  Or maybe boot into windows repair mode and extract your files via console.

---

### Post by QIII on 2016-02-23
That might actually make things worse.  If files are changed, even with the drive removed, and Windows restarted,  file corruption may occur.  The appropriate answer was given: be sure the partition is fully unmounted rather than in Windows' gimmick hibernated "off" state.

Linux has no difficulty with NTFS partitions.  It won't mount the partition still mounted by Windows.

---

