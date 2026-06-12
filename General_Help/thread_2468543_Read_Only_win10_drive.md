---
title: "Read Only win10 drive"
date: 2021-11-02
forum: General Help
---

### Post by nighttripper on 2021-11-02
I have found plenty of answers on how to fix this error.  But they all assume that the win10 disk works.  They all say to run win10 and stop fast login and hibernation.  But what do you do if win10 will not run?  How can I read and WRITE to a win10 hard drive when it is in read only mode?

Night

---

### Post by grahammechanical on 2021-11-02
If you have a Windows 10 boot problem you might find the answer on a Microsoft support site. If you have a working Ubuntu you might try finding a Windows 8/10 evaluation ISO image. Burn that to a USB stick and see if that loads and read and writes to the Windows 10 file system on the hard drive. Were you supplied with a Windows 10 repair disc?

Regards

---

### Post by oldfred on 2021-11-02
lf UEFI install can you not directly boot Windows from UEFI menu.
Grub only boots working Windows, but UEFI entry then often works.

---

### Post by QIII on 2021-11-02
Just for the sake of clarity, could you explain exactly what you mean by "win10 will not run"?

Is it, as suggested above, that you cannot boot Win10?  Is this a dual boot arrangement?

---

### Post by nighttripper on 2021-11-02
I'm running Ubuntu 20 and trying to repair a friends win 10 disk.

Night

---

### Post by nighttripper on 2021-11-02
The windows computer will not boot.  So I popped the drive out and connected it to my Ubuntu 20 computer.  No this is not a dual boot.

Night

---

### Post by QIII on 2021-11-02
Then you are pretty much out of luck.  If a Windows drive is not properly unmounted, most Linux distros will treat it as read-only -- because Windows sets it that way.  The problem is that if a file is modified/added outside of Windows on an unmounted device, those modifications will not have been tracked by Windows, the state of the drive will not match what was recorded at shut down, and that will cause Windows to fail.

If Fast Boot is not disabled, Windows does not actually "shut down".  It enters a hybrid hibernation state and expects to restart where it left of.  Fast Boot is a bit of trickery employed by Microsoft to make you think it is "booting" faster.  It is not.  It is recovering from hibernation.

When Linux treats your Windows partitions as read-only, it is protecting you, your OS and your data.  This is a wise feature.  It allows you to recover data if needed without messing things up.

You would be better off visiting a Win10 support forum to work out why your Win10 machine is not booting.

---

### Post by Holger_Gehrke on 2021-11-02
In addition to what QIII said: Linux is good at a lot of things but fixing a broken NTFS is **not** one of them. There simply are no tools to do this. So whenever an NTFS looks like something is wrong Linux will mount it read only and the consensus on this forum - and any others on which I've looked - is to fix NTFS problems using Windows.

Holger

---

### Post by ActionParsnip on 2021-11-02
Boot Windows install media. Drop to recovery console using the CD (or USB) then run a chkdsk. This may help.

---

