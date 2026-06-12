---
title: "Grub rescue : invalid arch independant ELF magic"
date: 2016-11-26
forum: General Help
---

### Post by 20sylknight on 2016-11-26
Hi people,

First, thanks a lot for anyone who helps me.
I installed Linux for first time yesterday to learn how to use it. I got some problems whit grub very quickly, windows not displaying on boot, I used sudo grub-update to fix the problem. After going back to W10 and trying to boot again to linux, I had a "invalid arch independant ELF magic" and grub rescue displaying. I used my usb live to try boot-repair but this one tells me "[COLOR=#000000][FONT=Arial]Please enable a repository containing the [grub2] packages in the software sources of unknown Linux (sdb5). Then try again."
Here is my boot info : [/FONT][/COLOR][http://paste2.org/hY6VN6Uh](http://paste2.org/hY6VN6Uh)[COLOR=#000000][FONT=Arial]
More info : 
W10 is installed on legacy so does ubuntu
My MB is UEFI or Hybrid UEFI Legacy
Both OS are installed on SSD
There is nothing important on my Linux partition, I just need to keep W10
My knowledge concerning linux is extremely limited as I installed it to learn.
English is not my native language, please excuse my mistakes.

Thanks a lot, I'm kind of desperate.[/FONT][/COLOR]

---

### Post by yancek on 2016-11-26
At least part of the problem is related to the fact that you left your windows hibernated which will cause problems.  You will see in the boot repair output numerous lines such as below:

> The NTFS partition is in an unsafe state. Please resume and shutdown
 	Windows fully (no hibernation or fast restarting), or mount the volume
 	read-only with the 'ro' mount option. 

You need to shut off hibernation and fast start or fast boot before trying anything else.

---

### Post by 20sylknight on 2016-11-26
Thanks yancek
There is a fast boot option in my msi bios, I enabled it, it doesn't change anything.

---

### Post by oldfred on 2016-11-26
Fast boot in UEFI is different than the fast start up in Windows.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

Grub will not boot a Windows install that is hibernated nor if it needs chkdsk. Best to have a Windows repair/recovery drive.
You may be able to temporarily install a Windows boot loader, fix Windows and then use Boot-Repair to reinstall grub.

---

### Post by 20sylknight on 2016-11-26
Ok, I wiped completely the SSD and re-installed it all. Its feels like a failure, but when I tried to repair windows' wbm with the live WD cd it refused for some obscure reasons to me. Solved...

---

### Post by oldfred on 2016-11-26
Glad you resolved it.

But one advantage of UEFI is then you can always direct boot a system from UEFI, if grub does not boot it. And Windows updates may keep turning on fast start up or Windows often needs chkdsk. And in those cases you must directly boot Windows. 
Either way best to have Windows repair/recovery disk.
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

