---
title: "LUKS boot script"
date: 2006-10-18
forum: General Help
---

### Post by Jebenko on 2006-10-18
Hello,
   I created a encrypted /home with LUKS using this guide: 
 
 [https://help.ubuntu.com/community/EncryptedFilesystemHowto3](https://help.ubuntu.com/community/EncryptedFilesystemHowto3)
 
 Alll works fine. Just one thing not.
 
 This script: 
 cat /etc/init.d/cryptinit
 
 #! /bin/sh
# if this script is executed when home is opened, tries to close it;
# otherwise, tries to open it, for three times, then continue without
# opening it
if [ -b /dev/mapper/home ]; then
     /sbin/cryptsetup luksClose home
else
    i=3
    while [ $i -gt 0 ]; do
        let "i -= 1"
         /sbin/cryptsetup luksOpen /dev/sda1 home && i=0
    done
fi
  should automatically mount the /home partition after entering the correct LUKS password at boot. Instead, i get a sh shell and have to manually mount the partition with:
 
 mount /dev/mapper/home /home
 
 and then 
 
 init 2
 
 to booot up the system.
 
 Can someone tell what should be changed in this script to make it work?
 
 Thanks in advance.  
 
 J

---

