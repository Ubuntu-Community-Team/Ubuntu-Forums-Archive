---
title: "Encrypt external usb drive"
date: 2016-07-07
forum: General Help
---

### Post by 3dmatrix on 2016-07-07
I wish to Encrypt my external usb hard drive. 
I wish to use a tool that is easily available in repo of most disros. 
So that if in future, I wish to change over to some other distro, it should work there too.

---

### Post by banceu_sergiu_ione on 2016-07-07
cryptsetup 

Check 1st you don't have it already install, if not install it.

You can also use the Disks, unmount the disk you want to encrypt and  when format it ( save your data 1st or you will lose it ), chose as Type : 'Encrypt, ...........'

If you want more, have a look for [cryptsetup]("https://wiki.archlinux.org/index.php/Dm-crypt/Device_encryption").

---

### Post by 3dmatrix on 2016-07-23
> **banceu_sergiu_ione said:**
> cryptsetup 

Check 1st you don't have it already install, if not install it.

You can also use the Disks, unmount the disk you want to encrypt and  when format it ( save your data 1st or you will lose it ), chose as Type : 'Encrypt, ...........'

If you want more, have a look for [cryptsetup]("https://wiki.archlinux.org/index.php/Dm-crypt/Device_encryption").

Do we have a GUI interface for that ?

---

