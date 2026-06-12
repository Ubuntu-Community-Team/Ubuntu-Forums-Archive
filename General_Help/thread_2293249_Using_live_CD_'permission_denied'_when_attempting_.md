---
title: "Using live CD 'permission denied' when attempting to access ext4 external drive"
date: 2015-09-03
forum: General Help
---

### Post by C_Mac on 2015-09-03
Hello

I am an extremely new user so pardon my lack of vocabulary pertaining to Linux and Ubuntu. I have an old windows 7 machine with an NTFS file system and I would like to transfer some files over to an external drive with an ext4 file system encrypted with LUKS. I booted to a live CD of xubuntu 14.04, plugged in my external drive, and entered my passphrase. The message I received was 'permission denied.' Next I installed the disk utility from the Ubuntu Software Center, re-plugged the external drive and unlocked it through the disk utility. It shows that the drive is unlocked, but when I try to access the files I again get the message 'permission denied.' I checked the external drive by plugging it into my permanent xubuntu machine and everything seems okay; I am able to mount and access all my files.  


Any help would be great, and if you could possibly ELI5 with the technical language I would be super appreciative.

---

### Post by powder on 2015-09-03
Mount the drive and then check the permissions with:
```
ls -l /media/$(logname)
```

---

### Post by C_Mac on 2015-09-04
[solved]

I just did a work around. Formated an old usb drive to FAT32, populated the needed files on it from the windows 7 machine, and plugged it into my linux machine to transfer to the ext4 drive. Not an elegant solution but it worked.

---

