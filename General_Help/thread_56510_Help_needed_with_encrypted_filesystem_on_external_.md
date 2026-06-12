---
title: "Help needed with encrypted filesystem on external harddrive"
date: 2005-08-12
forum: General Help
---

### Post by Pig Monkey on 2005-08-12
I have an external usb hard drive that I would like to create an encrypted file system on. I've already followed the first part of [this guide](https://wiki.ubuntu.com//EncryptedFilesystemHowto) ("Using dm-crypt"). It seemed to work fine, so I turned the drive off and walked away.
Later, I came back, turned the drive on, and tried to *mount /crypt*.
It returned this error:
```
mount: wrong fs type, bad option, bad superblock on /dev/mapper/crypt,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
After a little digging I discovered that the hard drive was now at /dev/sdb1, instead of /dev/sda1 (which is where it was originally).

Is there anyway I can make the drive always appear at the same place, so I don't have to edit crypttab everytime I plug the drive in?

(Note that the drive never changed USB ports.)

---

