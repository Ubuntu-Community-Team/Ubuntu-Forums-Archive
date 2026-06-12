---
title: "Unable to smartctl on external USB drive - &quot;Aborted by the host&quot;"
date: 2013-12-18
forum: General Help
---

### Post by kgandhiok on 2013-12-18
Hi,

I'm running an hp laptop with windows 7 and Ubuntu 13.10 dual boot. I  wanted to check the sectors of my Seagate external 1tb USB drive using  smartctl. About 30 minutes after starting the test, I did command  smartctl -c /dev/sdb to check the status of the test. I was given  "Self-test status as - The self test routine was aborted by the host". I  don't understand how the test was aborted because I didn't abort it. 

Is it possible that Seagate has some bug that does not allow  smartmontools? Should I use some other method to check my external  drive? Can I use fsck to check and repair external drives?

Any help regarding this would be much appreciated. Thanks!

---

### Post by tfrue on 2013-12-18
What file system type is formatted with the external drive? Be it NTFS, ext4, vfat...? fsck will work, but it will not work for NTFS file systems.

Here is a link to an article that might help: [http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/](http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/)

If the external drive is NTFS, then you can boot into your Window's partition and use chkdsk, or read this article for GUI version of chkdsk: [http://windows.microsoft.com/en-US/windows-vista/Check-your-hard-disk-for-errors](http://windows.microsoft.com/en-US/windows-vista/Check-your-hard-disk-for-errors)

The article covers how to do this in Vista, but should be the same for 7.

---

### Post by kgandhiok on 2013-12-18
Thanks, yeah my external drive file system is NTFS, and I also remember reading something like it isn't recommended to use fsck for external / mounted drives because that would destroy all the data on the drive. I have used /forcefsck to check my Ubuntu file system on reboot, that worked fine. 

Well, yeah I know I can enter windows and check the external drive for errors, but I don't want to enter windows.. *lol*... I mean, I want to be able to do everything out of Ubuntu itself. 

I did install the smartmontools package in order to run check disk on Ubuntu, but everytime I run it, the check gets aborted by itself. I remember earlier Ubuntu releases had a 'Disk Utility' in the system administration where one could check the health of their disk drives, but I can't seem to find that in the release that I have (13.10).

---

### Post by kgandhiok on 2013-12-18
> **kgandhiok said:**
> I remember earlier Ubuntu releases had a 'Disk Utility' in the system administration where one could check the health of their disk drives, but I can't seem to find that in the release that I have (13.10).

Sorry, I just found the 'disk utility' in 13.10, it's called 'disks' (my bad), it has a smart GUI disk check system. So I was able to run the disk check from there... I still wonder why the check didn't run from the terminal...

---

### Post by tfrue on 2013-12-18
Darn naming schema's will never grow old lol. All I've had is trouble with 13.10, though I am using Server 13.10, but I will go back to 13.04. I just don't want to do all the moving of my files. Actually, I've been having the same problem with mounting drives, getting logical block errors, partitioning and formatting drives using Linux, but all I have is the terminal, which is fine, but I have yet to find a command line partitioning tool for NTFS drives in Linux. But glad to hear all went well!

---

### Post by kgandhiok on 2013-12-18
:) I guess not! 

So far I've only been able to run 13.10, all other releases gave me errors when I tried installing proprietary drivers for AMD graphics, lesson learned... next time I'll get nvidia...*lol*

Although I was able to disk check from 'disks', I'm on the lookout for a way to get this done using CLI. I will do some reading on these forums and google and if I find something will post it here. I hope all works fine for you!

---

### Post by tgalati4 on 2013-12-18
I was under the impression that *smartctl* had limited capbabilty for accessing SMART commands through USB.

---

### Post by kgandhiok on 2013-12-19
Oh! Do you know a better, more effective way to disk check external drives (NTFS) on ubuntu?

---

### Post by philinux on 2013-12-19
Maybe it has something to do with this.

[http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices](http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices)

---

