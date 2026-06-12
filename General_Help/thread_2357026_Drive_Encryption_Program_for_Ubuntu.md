---
title: "Drive Encryption Program for Ubuntu?"
date: 2017-03-29
forum: General Help
---

### Post by jsc12345 on 2017-03-29
Now that I've settled in to Ubuntu, I want to encrypt my hard drive. I've tried using VeraCrypt, but the official one wouldn't boot and the one installed using the unofficial but recomended apt-repository doesn't have the option. Does anyone know of an app that can encrypt the entire hard disk?

---

### Post by TheFu on 2017-03-29
LUKS.  Easiest to select it during OS installation.
If you want to encrypt non-OS partitions, you can add LUKS after the fact.

There are many other ways to encrypt just your HOME (on an individual login basis) or a subdirectory tree on the file system too. Generally these are based on EncFS or EncryptFS. Both have security issues since each file is encrypted separately and the relative sizes can give away information about the type of file it is.

With most things like this, Ubuntu has a How-To guide and community help pages:
[https://help.ubuntu.com/community/FullDiskEncryptionHowto](https://help.ubuntu.com/community/FullDiskEncryptionHowto)
[http://askubuntu.com/questions/366749/enable-disk-encryption-after-installation](http://askubuntu.com/questions/366749/enable-disk-encryption-after-installation)
[https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)

I know that other distributions support an encrypted /boot/ partition, but Ubuntu doesn't make that easy, so most people (myself included) just use an unencrypted /boot/ and have everything else encrypted with LUKS.  **cryptsetup** is the primary command used, but after the install is over, most people will never use that command. Actually, they will probably never use it, ever.

Also - this is very, very, important - if you use encryption, be certain that you have excellent backups.  Data recovery for encrypted data is nearly impossible.  That is sorta the point of encryption.

And if you want added security, get a 2FA device to use when you want/need to unlock the drive.  I have a yubikey and use that with a passphrase. Been looking at an "OnlyKey" device for my next purchase.

---

### Post by jsc12345 on 2017-03-30
The official VeraCrypt won't open... Any Ideas?

---

