---
title: "backups and encryption"
date: 2008-04-25
forum: General Help
---

### Post by jerome1232 on 2008-04-25
Ubuntu i386 8.04

Ok so I created a backup of my /home using

```
tar cvfz - /home | split -b 4G backup.tar

```

So i get my archive split into DVD sized files named backup.tar.aa, backup.tar.ab etc... now I would like to encrypt them and write them to DVD, I'm worried that *if* i were to have to reinstall ubuntu and get the files off the dvd, i won't be able to de-encrypt them.

just to see i created a key, encrypted a small file, backed the key up to a file, deleted the key from my keyring, then attempted to de-encrypt the file. It just begins decrypting then tells me i probably don't have the key, tried restoring the key by importing the .asc file back into my keyring and it doesn't seem to want to import back in. I had even published my key to the key servers and i just can't seem to get this key back. so my question is how does one go about backing up a key and restoring it back into the keychain?

---

### Post by jerome1232 on 2008-04-26
Okay well I figured out I'm just retarded and there's an option "backup key rings" I just select the key rings I want backed up and it puts them in a .tar file, restoring them is a matter of untaring/click and drag. So how can the keys be securely stored, doesn't seem to do much good to have the unencrypted key backups sitting on the dvd with the encrypted data... perhaps this should be in the security section really

---

### Post by bingoUV on 2008-04-26
I presume the tar file of keys will be very small (much less than 1MB?). You could easily find a secure, password protected online storage for such data.

---

### Post by Zack McCool on 2008-04-26
I wouldn't store them on the same disc.  I would use a USB dongle or a floppy.  It doesn't make sense to encrypt the key, as at some point you need to have an unencrypted key to be able to unlock the others.

---

### Post by jerome1232 on 2008-04-26
Ok thanks so the solution would be just to store the archived key on separate media :)

---

