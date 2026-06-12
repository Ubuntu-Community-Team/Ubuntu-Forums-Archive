---
title: "After updating/restarting Feisty today, /dev/sdb1 has vanished!"
date: 2007-04-13
forum: General Help
---

### Post by marc_th on 2007-04-13
I'm Linux novice who, after happily using Edgy for many months, decided to install Feisty 7.04 Beta earlier this week.  And the upgrade went very well--during the LiveCD installation I recreated the sda2  (ext3 => /) and sda3 (swap => none) partitions to make sure I had a clean install.  After booting into Feisty and installing all the updates, all was good.  Grub still allowed me to boot up into my XP NTFS partition and Feisty mounted the /dev/sda1 NTFS and /dev/sdb1 EXT3 partitions under the /media folder.

Life was wonderful before I updated and rebooted my computer 1/2 and hour ago, when /dev/sdb1 vanished!  I almost had a heart-attack, /dev/sdb1 is my 300GB SATA drive with an ext3 partition containing all my personal/business data.  The message that was logged in /var/log/fsk/checkfs was:

[FONT="Courier New"]Log of fsck -C -R -A -a 
Fri Apr 13 16:46:42 2007

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda4: 18540 files, 196488/1555536 clusters
fsck.ext3: No such file or directory while trying to open /dev/sdb1

/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8[/FONT]

I booted up into WinXP and was able to access the drive and all the files on it using some ext2/etx3 driver I installed--I assume the drive is fine.

Booting back into Ubuntu, /dev/sdb1 no longer exists.

My fstab file looks like this:[FONT="Courier New"]

# /dev/sda2
UUID=6c034462-f0f6-4bf0-a9c6-52da6b42769d / ext3 defaults,errors=remount-ro 0 1

# /dev/sda1
UUID=62201BC8201BA1D9 /mnt/Windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1

# /dev/sda4
UUID=1CDF-9F8D none vfat defaults,utf8,umask=007,gid=46 0 1

# /dev/sdb1
UUID=7c907bd9-8752-4d7a-893a-3838fe8b0be1 /mnt/Archives ext3 defaults 0 2

# /dev/sda3
UUID=462935f4-a54e-421b-b8d7-b7a7354c45cf none swap sw 0 0

# /dev/hdd
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0[/FONT]

Anyone have any ideas why /dev/sdb1 disappeared?  I don't know where to begin fixing this except by reinstalling the OS again from scratch or moving back to Edgy.

---

### Post by marc_th on 2007-04-13
Bump. Sorry, I'm waiting for a helpful reply before I quit and try a reinstall.

---

### Post by wthanna on 2007-04-13
This is probably related to the kernel problem discussed in the following thread

[http://ubuntuforums.org/showthread.php?t=408253](http://ubuntuforums.org/showthread.php?t=408253)

I had a similar problem, but it appears a new kernel is now in the repositories that corrects the problem.  Try booting to an older kernel and updating again.

---

### Post by marc_th on 2007-04-13
So okay, I'm being impatient.  I booted up the Ubuntu Feisty LiveCD and noticed that /dev/sdb1 was there.  Further, I was able to mount it and access all my files.  This is evidence that the HD is fine.  Therefore, am I to assume that the last Feisty updates messed up my Ubuntu? Should I reinstall Feisty from scratch? Revert back to Edgy?  Why would reinstalling Feisty help?  I have a fresh install; all I did was uninstall Evolution, install Thunderbird, Amarok, Eclipse, Beryl, VLC and some codecs.  I also edited my fstab to not mount my windows drive and to mount sdb1 to the /mnt folder as opposed to the /media folder.  I don't know what to do.

---

### Post by wthanna on 2007-04-13
.... see my first reply....  this is a problem with a recent kernel update.. if you did  not remove the previous kernel you were using, just select it when GRUB loads, and boot the previous kernel.  An updated kernel should be showing up in whatever repository you are using soon, if it is not there already.

---

### Post by marc_th on 2007-04-13
wthanna, you are right. This thread is done.  I was able to boot up using the previous kernel and my drive is back and healthy.  Thank you very much.

---

### Post by wthanna on 2007-04-13
Glad to be of some help!  It's not often that I have an answer to people's problems, but I've been helped so much by others on this forum that I try to help others that I can when I see the chance.  This forum is what makes Ubuntu the best distribution you will find!

---

### Post by marc_th on 2007-04-13
What's not very interesting about all of this is how or why some flawed code was released as an update. What fascinates me is how easily (ok with a little help)  I could revert back to a stable system, how quickly the update was pulled and how quickly a new update was reissued.   

How cool is that?

---

### Post by wthanna on 2007-04-14
.. it was definitely a problem.. but also a good example of how well open source software can work.. how quickly help can be found... patches or fixes released.. We didn't have to wait on some giant, slow moving corporation on "Patch Tuesday"..    I'm not trying to "minimize" the problem.. just pointing out how well this "community" works and responds to problems when they do happen.  I am more "Wowed" here every day.. and feel more and more that Ubuntu will be an unstoppable force for a long time to come.

---

