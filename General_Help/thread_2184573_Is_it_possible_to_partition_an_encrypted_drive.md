---
title: "Is it possible to partition an encrypted drive?"
date: 2013-10-29
forum: General Help
---

### Post by mathieu-mgkgroup on 2013-10-29
My laptop came shipped with windows 8, I quickly blew it away and installed ubuntu 13.04 on there, and opted in to encrypt the harddrive on startup. I didn't think this would ever be a problem! Now there's some software that unfortunately I need windows to run and I would like to set out a small partition for it.

I installed gparted to do the task, I've always used it in the past, and quickly ran into the issue of my harddrive being encrypted. Understandably, I would rather not back up and blow away my ubuntu partition to install it all over again, so I'm wondering if it's possible to partition my hdd without doing that. That is to say, keep my current installation in tact and still partition a portion for windows.

Or am I screwed? haha

Thanks!

---

### Post by vonvic on 2013-10-29
Use Wine.  It may or may not work depending on the program.

---

### Post by oldfred on 2013-10-29
I actually do not know anything about encryption nor LVM. But question comes up enough I saved links. I think they still are current.

 Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.
How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)
Ubuntu 13.10 Linux Disk Encryption Performance Full Disk, /home & unencrypted comparison
[http://www.phoronix.com/scan.php?page=article&item=linux311_disk_encryption&num=1](http://www.phoronix.com/scan.php?page=article&item=linux311_disk_encryption&num=1)
settings and lots of info:
sudo tune2fs -l /dev/sda1
Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)
chroot & reinstall grub encrypted LVM
[http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/](http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/)

---

### Post by Impavidus on 2013-10-29
You can also try a virtual machine.

---

### Post by mathieu-mgkgroup on 2013-10-29
Vonvic I am well aware of wine, I've been using ubuntu since 7.04. One of the two programs I need actually says it has a platinum rating, but I can't even get it to install, the other program (which I need much more than the first) has a garbage rating, on all versions.

Impavidus, I thought about a virtual machine but I'll be using this software for live performance (DJing), where what what matters most is the sound quality and the latency of all the hardware and software. I haven't ruled it out completely, but that's more of a last resort. However, the other piece of software is what I used to write music, so that is always a possibility.

oldfred, thanks! I'll be looking through these articles in the morning and let you know if they were successful.

---

