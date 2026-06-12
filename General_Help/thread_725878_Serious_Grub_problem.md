---
title: "Serious Grub problem"
date: 2008-03-16
forum: General Help
---

### Post by satjat on 2008-03-16
I am having what seems to be a serious problem.
I get the GRUB error 17 on boot and the system is frozen.
I got the super grub disk and tried to manualy setup.
the root(hd0,0) command yielded an error:

Filesystem type unknown, partition type 0x83

this is my normal boot partition, how can this be Unknown type?
Is there any chance to rescue my data?

Thank you all

---

### Post by sandysandy on 2008-03-16
have a look at these links

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

to quote GNU Grub page
> 
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 


regards

---

### Post by satjat on 2008-03-16
I managed to boot from a livecd and did fsck to the hard disk.
It seems like fixed since I can browse the files from the livecd but there are two mysterious problems

One of my user home directories appears as a file, not a dir

The vmlinuz image at root is a broken link to a /media/disk-1/kernel.... which does not exist as a directory. There is no /boot directory on this disk.

If I resort to reinstalling is there any way to preserve settings and data plus installed apps for the users that I can find on the disk? For the user that has the home dir turned into a file?

Can I recreate the /boot directory somehow so that I skip reinstalling? Will the "weird" user still be lost?

Lastly I believe that the filesystem was ext3 while now it is ext2fs, is there any case it got changed or I am not remebering correctly it being ext3?

Excuse me for asking so many questions but I feel lost and there are valuable data in the disk.

---

### Post by louieb on 2008-03-16
is this the same hard drive you asked about in this thread? [URL="http://ubuntuforums.org/showthread.php?t=675002"]Hard disk damaged 
[/URL] The 1st thing to do is get whatever data you can copied off to another drive. I like using  [Knoppix Linux]("http://www.knoppix.net/") or [Puppy Linux]("http://www.puppylinux.com/") for doing the copying. 

Sounds like you have a hardware problem. Either the hard drive or motherboard.  Until you can rule that out, not much else can be done.

---

