---
title: "Can't log into encrypted drive"
date: 2015-10-12
forum: General Help
---

### Post by adrinkrahene on 2015-10-12
Can't log into encrypted drive after running anti-virus. I was working with 2 terminal and mixed up the term program that should have been running the anti-virus. Now when I start my computer it take me  to c-mos via a message that states "Invalid signature detected. Check secure boot policy in set up" this error message is not helping because I don't know what I am suppose to check for. If anyone can help or have any ideas I would thank them in advance. Any help at all!

---

### Post by oldfred on 2015-10-12
That message is from UEFI. You have secure boot on, but perhaps your install is standard UEFI or even just BIOS/Legacy/CSM?
Try turning off Secure boot in UEFI.

---

### Post by adrinkrahene on 2015-10-18
forgive the delay in replying (other problems) Thank you will try and report back.

---

### Post by adrinkrahene on 2015-10-18
Looks like that has gotten me to where I can start to see the problem ( Not that I understand it!)

Message follows

Gave up waiting for root device. Common problems:
 - boot args (cat /proc/cmline)
  -Check rootdelay= (did the system wait long enough?)
  -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; is /dev)
ALERT! /dev/mapper/ubuntu--vg-root does not exist Drooping to shell!

Again Many Thanks in advance.

---

### Post by oldfred on 2015-10-18
You may then have a corrupted partition. Not sure with LVM and encryption whether repairable or not. Do you have good backup? 
With encryption recovery of even minor issues can be a problem and good backups are essential.

One of these links may help.
 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

 fsck on encrypted LUKS 
[http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk](http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk)

---

### Post by adrinkrahene on 2015-10-18
Looks like that has gotten me to where I can start to see the problem ( Not that I understand it!)

Message follows

Gave up waiting for root device. Common problems:
 - boot args (cat /proc/cmline)
  -Check rootdelay= (did the system wait long enough?)
  -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; is /dev)
ALERT! /dev/mapper/ubuntu--vg-root does not exist Drooping to shell!

Again Many Thanks in advance.

---

### Post by adrinkrahene on 2015-10-18
Thank you, I will check the links provided.
The only backup would be on the drive itself. 
Sound like the anti-virus may have cause 
that having root access. (bummer)

---

