---
title: "Encrypting external HDDs TrueCrypt tcplay"
date: 2016-08-25
forum: General Help
---

### Post by YQ002lc2 on 2016-08-25
I have a very large external HDD.
I would like to encrypt it with something like truecrypt, with multiple layers and passkeys...

But I see truecrypt is no longer supported or updated. 

I found tcplay in the repositories and this forum post [https://ubuntuforums.org/showthread.php?t=2228711](https://ubuntuforums.org/showthread.php?t=2228711) .  
I also don't know how to use it, but am unable to post there because the thread is closed. 

1. Can anyone make software recommendations for encrypting external hard drives with truecrypt -like functionality?
Preferably with an optional gui frontend like rsync & grsync
2. Can anyone provide an exhaustive detailed tutorial on how to encrypt external hdds with various software options?

---

### Post by TheFu on 2016-08-25
**dm-crypt** is the standard for whole-drive encryption on Linux. cryptsetup is the way to set it up, then the "disks" utility or many file managers know how to decrypt it. No specific GUI has been made, since it works as an OS extension.  Caja (is the file manager I use) knows how to ask for credentials. I suspect others will as well.

You can use 2FA with dm-crypt.  I use a Yubikey and passphrase myself. There are 8 slots, so different people can open the volume without sharing their passphrases.  I know it works with both internal and external drives too - using it now with a USB3 external SSD.

---

