---
title: "Have to login twice using dmcrypt/luks"
date: 2020-01-22
forum: General Help
---

### Post by bobhesketh on 2020-01-22
I use dmcrypt/luks and pam to encrypt a partition and automatically unlock it at login. This was working fine on 19.04, but since upgrading to 19.10 I have to login twice to get this to work.

What I mean by this is that when I login the encrypted partition isn't unlocked, but if I log out and back in again, it does get unlocked.

Thanks

---

### Post by TheFu on 2020-01-22
LUKS isn't part of the login. It is unlocking the disk storage. Nothing more.  Unlocking the disk happens due to a reboot or shutdown.

Then comes the actual login. 

The effort to use LUKS says you care about security, perhaps using a hardware token in challenge-response mode would be worth while?  LUKS has 8 slots for different credentials/methods to unlock the storage.

---

### Post by bobhesketh on 2020-01-24
Thanks for the reply. I've been using this encrypted partition for many years, initially on Gentoo and latterly on Ubuntu. It unlocked fine with 19.04 - password input at the login screen unlocked the drive, ready for use. With 19.10 I have to login, logout and login again for it to work.

---

### Post by TheFu on 2020-01-24
> **bobhesketh said:**
> Thanks for the reply. I've been using this encrypted partition for many years, initially on Gentoo and latterly on Ubuntu. It unlocked fine with 19.04 - password input at the login screen unlocked the drive, ready for use. With 19.10 I have to login, logout and login again for it to work.

I've never seen that, unless using encfs and HOME directory-only encryption. That was deprecated for a number of issues. LUKS has always required unlocking the storage first on Ubuntu, then the login screen would be shown.  The LUKS credentials have nothing to do with login credentials.  

cryptsetup is the CLI interface to control LUKS on Ubuntu.  I've been using LUKS for about a decade.

---

