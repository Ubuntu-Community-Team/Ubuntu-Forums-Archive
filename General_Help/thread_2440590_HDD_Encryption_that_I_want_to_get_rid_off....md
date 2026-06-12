---
title: "HDD Encryption that I want to get rid off..."
date: 2020-04-12
forum: General Help
---

### Post by andysharpie on 2020-04-12
Hello world!
I am working with an Ubuntu 16 system installed on an HP Pavilion dm4 laptop. When the system was first installed, the hard drive was encrypted. As is the usual story, having *two* passwords to log in is tiresome, and I am trying to get rid of the encryption. I read other posts around the web on this topic, and the overwhelming solution is  either to re-install, (which I want to avoid), or to set a new password. Simply put, I don't know how to re-set that password. Any hints?
Thanks in advance.

---

### Post by CelticWarrior on 2020-04-12
Setting a new password just sets a new password. If you want to remove encryption then you need to reinstall, actually backup first and then reinstall.

---

### Post by wildmanne39 on 2020-04-12
Please use normal fonts unless you want to call attention to just a small portion of text.


Thanks

---

### Post by HermanAB on 2020-04-13
You can change the disk password (or add another one) with cryptsetup.  A little bit of googling and man page reading will show you how.

Note that you only need to enter the disk password when you reboot.  Therefore the easy solution is *not* to reboot.  Use Suspend instead.

---

