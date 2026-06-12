---
title: "Full disk encryption: help / advice on mounting at boot-up"
date: 2018-05-27
forum: General Help
---

### Post by cds60601 on 2018-05-27
Hi everyone

I finally took the plunge and encrypted my secondary drive with cryptsetup. Could use some help / advice on mounting 
the encrypted secondary drive on boot-up. 

Thanks in advance!!
Chris

---

### Post by cds60601 on 2018-05-28
Got it. No reason to respond ... Marking solved.

---

### Post by oldos2er on 2018-05-28
What is the solution? The information you provide will likely help others.

---

### Post by cds60601 on 2018-05-30
*The small print stuff:*

**Assumptions -**
1. Drive to be encrypted not be part of LVM.
2. cryptsetup has already been installed
3. You already know the device you wish to encrypt (I will be using /dev/sdb1 as an example)
4. You have already saved off any and all data on the drive you wish to encrypt - **_otherwise you will lose it all_**
5. You need to know how to use of sudo or su -

[B]Notes & WARNINGS -
[/B] You have already saved off any and all data on the drive you wish to encrypt - **_otherwise you will lose it all_**
This process I am presenting, worked for me -** YMMV**
Please see the referring links at the end for a more complete overview of other options and processes
as mine is a compilation from these link to suite my needs.
... and finally, You have already saved off any and all data on the drive you wish to encrypt - **_otherwise you will lose it all_**


*And now, for something completely different... The process:*

Create a key-file for authentication - you will want this if you intend to use auto mount on boot:
dd if=/dev/urandom of=/root/drive_key bs=1024 count=4 

Protect the key-file to be read only by root:
chmod 0400 /root/drive_key

Initialize the LUKS file system and use the key-file to authenticate instead of a password:
cryptsetup -d=/root/drive_key -v luksFormat /dev/sdb1

Create the LUKS mapping using the key-file:
cryptsetup -d=/root/drive_key luksOpen /dev/sdb1 data

Create your file system (I use ext4):
mkfs.ext4 /dev/mapper/data

Create your mount point on the system (some folks use /media):
mkdir /mnt/data

Mount the new file system at the mount point:
mount /dev/mapper/data /mnt/data

Create the mapper for fstab to use - edit /etc/crypttab:
# <target name>    <source device>        <key file>    <options>
data      /dev/sdb1  /root/drive_key  luks

Add the mount point to fstab:
/dev/mapper/data /mnt/data ext4 defaults 0 2

Reboot or use mount -a


Referencing links for futher reading:
1.  Linux Hard Disk Encryption With LUKS [https://www.cyberciti.biz/hardware/howto-linux-hard-disk-encryption-with-luks-cryptsetup-command/](https://www.cyberciti.biz/hardware/howto-linux-hard-disk-encryption-with-luks-cryptsetup-command/)
2. Automatically Unlock LUKS Encrypted Drives With A Keyfile [https://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](https://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)
3. How to Recover a LUKS Encrypted Disk [https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/#comment-3634](https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/#comment-3634)

---

