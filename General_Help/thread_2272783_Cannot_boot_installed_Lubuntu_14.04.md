---
title: "Cannot boot installed Lubuntu 14.04"
date: 2015-04-08
forum: General Help
---

### Post by Rolandl on 2015-04-08
Hi all: I installed ubuntu 1404 then reinstalled my windows xp but now I can't boot xp, I screwed it up somehow, but only xp shows in the boot menu twice and cannot boot ubuntu even from 2nd Master. I somehow screwed it all up. What can I do to enable the installed ubuntu boot? I've decided now to use only Ubuntu because IE doesn't even work well. too many problems with xp. Now am working from ubuntu cd.

Roland  :mad:

---

### Post by Vladlenin5000 on 2015-04-08
You shouldn't be using XP now in general, and particularly NOT for anything internet related. What you achieved by installing that unsupported Windows version after Ubuntu was that Windows removed the bootloader and installed its own. 

This contains instructions for recovering GRUB and the dual-boot: [http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu](http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu)

---

### Post by Vladlenin5000 on 2015-04-08
-Or-

You can try Boot-repair as suggested before in your older and unanswered thread: [http://ubuntuforums.org/showthread.php?t=2159552](http://ubuntuforums.org/showthread.php?t=2159552)

---

### Post by Rolandl on 2015-04-08
OK thanks Vladlenin. I will try your suggestion then get rid of xp. I got a lot to learn, basically taking it as a challenge not a problem.

Seems I've successfully reinstalled Ubuntu. Now to get rid of xp. best way to do that? is Piriform Recuva useful for that? can't from the windows install cd. Also, how can I find the partitions to see if windows is still in there? 
Thanks.

---

### Post by Vladlenin5000 on 2015-04-09
If your Ubuntu is booting now, just by opening GParted should show you a map of the partitions -> Check whether or not there's one or more NTFS partitions... There should be, provided you followed the usual steps for dual-booting. And after a successful reinstallation of Ubuntu you should also have a boot loader showing both options, Ubuntu and Windows.

---

### Post by Rolandl on 2015-04-09
looking in configuration manager disks I see 3 partitions. 

1/linux bootable, version 1- mounted at Filesystem Root 

2/extended partition (nothing else)

and 5/ linux swap. (version 2) -active. so this is where ubuntu is installed?

windows XP isn't shown. does that mean it's not in the hard drive? has been deleted?

Hi: a couple things please. I have installed grub boot repair no problem,  but when I entered 'boot-repair' in terminal it said 'command not found'. What I would like to do is find out if windows xp or pieces of it is still in there and delete it.
Also, as one good turn deserves another how can I give a donation to show my appreciation? and I am really happy that when I inserted a music cd Audacious opened and played it right away.
I am grateful for your help.

Ubuntu boots ok now. many functions don't seem to be working though. Am wondering, should I uninstall and reinstall? Is there a scanner to show me the condition of hard drive and ubuntu both? I'm lost. Thank you.

---

### Post by yancek on 2015-04-19
The information in your post from last week would indicate that you have Ubuntu on the first partition, the second partition is an Extended partition with no data which contains the swap partition which also contains no data.  It is only used when you need more RAM than physically installed on the computer.

What functions don't work.  Give a specific example or two and someone may be able to point you in the right direction.

To see partitions on your drive, open a terminal and type the following:  sudo fdisk -l(Lower Case Letter L in the command)
Under the System column, any partitions with HPFS/NTFS will be windows.  If you don't see any, you don't have any.

---

### Post by Rolandl on 2015-04-21
I've had nothing but a lot of problems since I began working with first linux mint and now ubuntu 14. Hardly anything works for me. It seems like you have to be a computer technician. am getting real tired of trying. can't even get my samsung printer connected. Are there any distributions that actually don't present a lot of problems for a non-technical beginner? am seriously thinking of trying another MS Windows distribution.

---

### Post by Vladlenin5000 on 2015-04-21
Linux isn't a free clone of Windows. Any distro is hard for those not wanting to change their way of thinking.
That said, software coded for one OS won't run on another (some may due to a compatibility layer called WINE) and devices officially supported in Windows may work partially or not at all.

I suggest you open different threads for any specific issue. Saying "hardly anything works for me" is actually saying nothing at all.

What doesn't work exactly? An OS - any OS - has the only purpose of allowing the users to run software in a given machine. Different OSs may require different software but the ned result is roughly the same. What is that you are unable to do in Ubuntu that you could do in Windows? Honestly, I see no difference in accessing apps (almost always the same) and your contents (the same) with one or the other...

---

### Post by Rolandl on 2015-04-21
Hi Beans. I just now tried what you suggested twice to make sure I got it right. nothing opened.
Thank you anyway.

I just tried this again too. >> GParted: command not found.

---

### Post by Vladlenin5000 on 2015-04-21
Post #10

GParted is the name of the tool and is graphical, i. e., you search it in the dash like "gparted" (or even less). Available in a live sessions but won't be installed by default. If you need it after the system is installed then you need to install GParted first. It was just a suggestion. The commands in post #10 will do just fine for the purpose of finding which and what partitions you currently have. Again, if there's no mention of NTFS then you don't have any Windows.

---

### Post by Rolandl on 2015-04-22
I got it thru 'disks' in Accessories. 

Does it mean there are no windows xp files left in the computer that are accessible?

How are the partitions different from each other? in contents? any suggested study info. I can goto?

Hard drive partition 1 says: linux bootable (5.0 % full). dev/sda1.   contents  ext.4 (version 1.0) mounted at Filesystem root.
 size: 158GB - 151GB free.

partition 2: says 'extended partition' device dev/sda2  1.5GB

partition 5: dev/sda5, linux swap version 1 active  1.5GB (What does linux swap mean?)

I just downloaded and tried to open beginners info file from [http://linuxquestions.tradepub.com/free/w_mach01/](http://linuxquestions.tradepub.com/free/w_mach01/).
It wouldn't open. I'm getting nowhere fast. Can't get printer going nor open downloads. terminal usually doesn't give me anything. wonder what's going on. 
I have a disk for solydxk installation. anyone have success with that?
I guess you guys are getting tired of trying to help me too.  But I do appreciate your efforts. don't wanna go back to MS if I don't have to.

Could someone tell me where to find the URI for my Samsung ML-1665 mono laser printer? I saved and tried to install unified linux driver-3.00.65.tar.gz, and uld_v1.00.06.tar.gz, but it keeps asking for the URI. Is that the link to the on-line file?

I apologise for being so slow to let you know this issue has been resolved. thanks.
Roland

---

