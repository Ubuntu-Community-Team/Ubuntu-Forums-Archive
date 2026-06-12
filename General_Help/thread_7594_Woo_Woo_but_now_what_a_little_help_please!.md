---
title: "Woo Woo but now what? a little help please!"
date: 2004-12-09
forum: General Help
---

### Post by tigerb on 2004-12-09
First of all I am VERY new to Linux and my first Knoppix LIVE CD was OK but no sound......then I got lucky as I found Ubuntu! The LIVE CD just blown me away, I can connect to the web without doing anything and I can hear system sounds.... I like what I see and ready to install, where do I start? Oh how come I could not play mp3s and mpeg files? is it due to the limitations on LIVE CD? or do I need to install plug-ins, will the REAL installation ISO CD solves all these minor problems? I still have a lot to learn about using Linux/Ubuntu......but I got the time and hopefully soon one day I will be able to contribute positively to this great ORG. Woo Woo.

Keep up the good work - those who bring sunshine into the lives of others cannot keep it from themselves. :-D

---

### Post by kamstrup on 2004-12-09
I honestly don't know if you are able to install from the live cd, but I don't think so. Grab the Ubuntu installation cd from [http://www.ubuntulinux.org/download/](http://www.ubuntulinux.org/download/) You probably want the file called warty-release-install-i386.iso . Burn this to a cd (as I guess you've done with the LiveCD?).

mp3's didn't work for me right after installation, but after a few minutes of downloading appropriate programs it did. As did mpeg's.

Post back if you have any problems. Cheers!

---

### Post by tigerb on 2004-12-09
Thanks kamstrup. OK I already installed Ubuntu on my secondary HD, no problem so far....what/where do I need to go to download those programs/patches you mentioned? Thanks again for your help. One more thing, with the live CD, I could aceess all my HD/partitions (from W2K), but after installation of Ubuntu, I don't seem to be able to locate my other HD/partitions (W2K)? Where do/what do I need to find them? and also why is it always saying I am not the the owner and could not change??? Many thanks...... 8-[

---

### Post by robotboy on 2004-12-09
[QUOTE=tigerb]Thanks kamstrup. OK I already installed Ubuntu on my secondary HD, no problem so far....what/where do I need to go to download those programs/patches you mentioned? Thanks again for your help. One more thing, with the live CD, I could aceess all my HD/partitions (from W2K), but after installation of Ubuntu, I don't seem to be able to locate my other HD/partitions (W2K)? Where do/what do I need to find them? and also why is it always saying I am not the the owner and could not change??? Many thanks...... 8-[[/QUOTE]

I haven't used the live CD, but I'd assume that it autodetects your harddrives and partitions and makes links to them on the desktop. The typical way to access a partition under linux is to mount it. Devices (such as harddrives) are stored under the /dev filesystem with /dev/hda being the first harddrive found in the system and /dev/hdb being the second. If you want to see the partition table for each harddrive you can open a terminal, su to root, and type fdisk -l /dev/hda and fdisk -l /dev/hdb. It should list the partitions found on each drive. One of them should either say NTFS or FAT32. That's your windows partition. You can mount (meaning assign it to a directory) it by looking at the partition number printed by fdisk (i.e., hda1, hda2, etc...) on the left and using it with the mount command like so.

mkdir /mnt/win32
# for NTFS
mount -t ntfs /dev/hda1 /mnt/win32
# for FAT32
mount -t vfat /dev/hda1 /mnt/win32
# Make sure you change hda1 above to reflect the drive you want to mount

You can then browse to /mnt/win32 with your favorite filebrowser and access the files. You can also setup the partition to be mounted automatically at boot time by adding an entry to /etc/fstab. As an aside, you can also mount other linux partitions this way. Anyway, I hope this explanation isn't too technical. There are a few basics with Linux that you need to learn to get around and mounting drives is one of them. See also.

[http://www.linuxforum.com/linux_tutorials/14/1.php](http://www.linuxforum.com/linux_tutorials/14/1.php)

Your last question about ownership is a little vague, but I will tell you that if you're logged in as a regular user (as you should be) and not root, that you have limited permissions on which parts of the filesystem you can and can't change. A mounted filesystem such as your Windows drive is going to be owned by root, so you won't be able to change it as a regular user. This is a good thing overall because it increases the security of the system. If the drive is NTFS, it'll only be available as a readonly drive anyway because Linux support for writing to NTFS drives isn't stable enough for general use yet.

---

### Post by tigerb on 2004-12-10
Thanks for the answers/link, Robotboy, I guess I will have a lot to read/learn.. :roll:

---

### Post by kamstrup on 2004-12-13
Everything is installed via the Synaptic package manager. You will find it under Computer->System Configuration->Synaptic.

Synaptic enables you to download the original Ubuntu software. You can acces an much greater resource called "universe" if you enable it in Synaptic. You can do this under "preferences->repositories" or what it might be called. Enable the sektion called "universe" with binary packages.

After enabling universe use the search function within Synaptic, and search for "mad", and select the package "gstreamer0.8-mad" for installation (doubleclick). Now click "Apply".

This ought to enable mp3-playback.

Regarding your Windows drives I suggest reading this thread [http://www.ubuntuforums.org/showthread.php?t=1886&highlight=ntfs](http://www.ubuntuforums.org/showthread.php?t=1886&highlight=ntfs) which should provide some hints.

NOTE: If you mount filesystems under /mnt they will not show up in "Computer". Instead mount them in the /media directory.

FSTAB: When people are refencing to "fstab", it is the file /etc/fstab. You can edit it by typing "sudo gedit /etc/fstab". Typing "sudo" in front of commands enables the super user mode.

---

### Post by heema on 2004-12-13
u could check out also the unofficial starter guide as it tells you how to do anything  :)

[http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html)

---

### Post by slavic9117193 on 2007-05-15
> **tigerb said:**
> Thanks kamstrup. OK I already installed Ubuntu on my secondary HD, no problem so far....what/where do I need to go to download those programs/patches you mentioned? Thanks again for your help. One more thing, with the live CD, I could aceess all my HD/partitions (from W2K), but after installation of Ubuntu, I don't seem to be able to locate my other HD/partitions (W2K)? Where do/what do I need to find them? and also why is it always saying I am not the the owner and could not change??? Many thanks...... 8-[


[Girls Debt Consolidation chemistry photosynthesis music](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

