---
title: "[SOLVED] Truecrypt on a USB stick not writeable?"
date: 2008-04-18
forum: General Help
---

### Post by zymurgist on 2008-04-18
I've got an FAT32 USB stick (memorex 4-gigger) which mounts just fine in Gutsey 7.10. I've installed TrueCrypt on it and it works great ... from Windows! On Ubuntu I am unable to write anything to the encrypted volume, whether as a user or root (I can write to non-encrypted parts of the key).

I've seen references to a '-u' parameter to give users write permission when this is mounted .. it usually referred to as 'truecrypt -u ...' but my version of truecrypt (5.1a) doesn't support that parameter.

In searching the forums, there isn't a lot of info on this .. so Im' wondering maybe I am doing something fundamentally wrong?

---

### Post by LeoSolaris on 2008-04-18
Uhh    you encrypted it to keep it from being read...  meaning it is locked till you enter the password with the proper encryption settings from TrueCrypt. 

You can put TrueCrypt on Linux by the way, and if you use the same password (and keyfiles if you used that option) you should be able to access your data from Linux. Without TrueCript, it's a piece of plastic. That's the point of encrypting it, to keep the data safe.

(I use TrueCrypt to do the same thing, and unless I put TrueCrypt and EXT reader on my XP, I would not be able to access a couple of my SD cards.)

Leo

Ok I see what you meant. You installed TrueCrypt on Linux and it is still not reading your USB drive. Have you checked TrueCrypt's website? There maybe a fundamental difference between the Linux and the Windows versions that do not allow interoperability. I'll check and get back to ya.

I checked their site and according to them, the only way you should have been able to encrypt it was by partition, which should leave it open for you to access from any instance of TrueCrypt. Contact them, it may be a bug.

---

### Post by zymurgist on 2008-04-19
Leo, I appreciate your response but I still don't think you quite understand my problem (or I didn't explain it very well).

I am able to view the USB stick in Ubuntu, and proceed to mount the truecrypt volume and enter my password. I am able to view all the files I encrypted, but I cannot change or write anything (even as root). I get an error that I do not have permission to do so. 

Interestingly, I have a similar problem with my SD memory cards. I can view their contents, but not change anything UNLESS I do it as root.

---

### Post by zymurgist on 2008-04-20
My problem is solved. 

I booted to Windows, created a new encrypted volume on my USB key, this time formatting it as NTFS. The NTFS option is not available on Ubuntu's Truecrypt. 

Rebooted to Ubuntu, and I have full access to it.

---

