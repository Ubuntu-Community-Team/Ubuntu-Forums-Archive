---
title: "Using truecrypt"
date: 2007-08-30
forum: General Help
---

### Post by PmDematagoda on 2007-08-30
I just installed truecrypt and I just want to know how I can encrypt my 128mb pen drive which has an NTFS file system using truecrypt.

---

### Post by anaconda on 2007-08-30
This might be of help.
[http://polishlinux.org/howtos/truecrypt-howto/](http://polishlinux.org/howtos/truecrypt-howto/)

currently truecrypt doesn't come with GUI, but some GUI:s can be downloaded separately.

PS. I would just put a truecrypt file in your USB stick. that would be the easiest. Or do you have any reason to encrypt the whole stick?

---

### Post by PmDematagoda on 2007-08-30
Currently I'm a noob when it comes to truecrypt, the GUI I have for truecrypt is forcefield. What's the difference between encrypting the whole drive and just putting a truecrypt file on the USB? Am I right in assuming that a file or drive encrypted by truecrypt is not readable by windows? 

P.S. I have enough and more time to spend on messing around so I don't mind the complicated or very long methods as well in addition to the simple ones.

---

### Post by anaconda on 2007-08-30
The file or drive encrypted with truecrypt in ubuntu will be readable in windows too. But ofcourse you will need to have truecrypt installed in your windows machine and you need to know the password.

the difference with truecrypt file in the USB or the whole USB encrypted is small. The truecrypt file is a filesystem in itself and it can be mounted to any directory. and there can be as many files as you like.

The advantage with having a truecrypt file in normal usb-disk is ofcource that you can keep some unencrypted data in your USB-stick too. Like the truecrypt install packkages for linux and windows. and you can also have your Keyfile or photo in the stick. (not recommended though)

---

### Post by PmDematagoda on 2007-08-30
Could you tell me how to encrypt a whole drive and how to put a truecrypt file?

---

### Post by anaconda on 2007-08-30
I havn't ever encrypted a whole drive, but the file is easy.
Just create a truecrypt file normally and copy it to your USB-stick.  Instructions for this are in the link I posted before..

---

### Post by kuja on 2007-08-30
> **PmDematagoda said:**
> I just installed truecrypt and I just want to know how I can encrypt my 128mb pen drive which has an NTFS file system using truecrypt.
I read something on the truecrypt website actually advising against installing it on flash drives .. something about the wear-leveling mechanisms that many of them employ making it possible for someone to break the encryption....

---

