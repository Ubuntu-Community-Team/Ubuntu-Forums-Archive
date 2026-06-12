---
title: "My personal files had disappeared from an internal error"
date: 2012-12-20
forum: General Help
---

### Post by dimas869 on 2012-12-20
I am using ubuntu 12.04 and after my system crashed a couple of time the configuration of my desktop had come to the default setting (the backgrown and the unity bar icons) and my personal files had disapeared and also my firefox browser don show the bookmarks and so on.
the system had given me a error report which i am postting too

i would really appreciate any help

---

### Post by irv on 2012-12-20
It looks like you are booting into 2D mode after crashing. Try rebooting and as your computer boots up hold shift key down to show the grub menu. Select recovery mode and do a repair on installed apps. See if this will fix the problem.
How long has it been since you installed Ubuntu? If it has been a short time you could do a fresh install, but save any files you want to a backup.
I have been keeping all my personal files on Ubuntu One so I never lose them. All my emails are online so it is easy for me to do a reinstall.

---

### Post by dimas869 on 2012-12-27
hello IRV, thank you for the advise but i did tryed to use the repair broken packages from the Grub Menu but it seems like doesnt do anything.

---

### Post by irv on 2012-12-27
I am sorry to say this happen to me one time and I got tired of trying to fix it, so I just did a re-install of the OS and got back running and everything just worked fine. I did have all my personal files backed up and most of them were in the cloud. If any one else out here has something you can try, otherwise you might have to do the same thing. Sorry I Couldn't have been more help.

---

### Post by dimas869 on 2012-12-29
thank you very much man, i am going to wait a little as i have years of work on those files though

anyway...when i used a Grub menu the system only throwed me two lines so i dont know if i missed to do something else...perhaps...to write a command?

---

### Post by oldfred on 2012-12-30
It sounds like you /home got corrupted and it rebooted with a new default (empty) /home.
Is  your /home a separate partition that you can run e2fsck on?

Post this.

        sudo cat /etc/fstab
    sudo fdisk -lu

---

### Post by dimas869 on 2012-12-30
> **oldfred said:**
> It sounds like you /home got corrupted and it rebooted with a new default (empty) /home.
Is  your /home a separate partition that you can run e2fsck on?

Post this.

        sudo cat /etc/fstab
    sudo fdisk -lu

thank you for your replay, i do really apreciate it. i dont understand how the partitions took place so i guess the system did when found the corrupted issue

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=11bcb302-bb34-4fcd-8338-94a8d83f1543 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0


sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000db936

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   308518911   154258432   83  Linux
/dev/sda2       308520958   312580095     2029569    5  Extended
/dev/sda5       308520960   312580095     2029568   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 2078 MB, 2078277632 bytes
255 heads, 63 sectors/track, 252 cylinders, total 4059136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc85773ac

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

---

### Post by oldfred on 2012-12-30
You do not have a separate /home, but since swap is encrypted, you probably have an encrypted /home. If the encrypted data is not unencrypted when you boot then you get the default.
I do not know encryption, but did you change passphrase or are not using passphase to unencrypt /home?

       [https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)

---

### Post by vanadium on 2012-12-30
From the output you show, you probably have setup an encrypted home folder. It may thus be that the problem is with the encryption, or with the encrypted volume. You might want to try this: [http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

