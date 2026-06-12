---
title: "Encryption: Files emptying themselves"
date: 2013-01-12
forum: General Help
---

### Post by Tralce on 2013-01-12
Set up encryption on a USB drive and put some files on it yesterday. Today, I plug in and log in, and most of the files are now empty, or literally 0-byte. Ideas?

---

### Post by Tralce on 2013-01-18
No ideas? That's ok. I'm gonna just go over here... and cry...

---

### Post by Impavidus on 2013-01-19
Did you properly unmount the drive before unplugging it?

---

### Post by Tralce on 2013-01-21
Yes.

---

### Post by black veils on 2013-01-23
how did you setup the encrypted usb stick/hdd ?

this is what i did [http://ubuntuportal.com/2012/03/tips-easy-way-to-encrypt-usb-flash-drive-on-ubuntu.html](http://ubuntuportal.com/2012/03/tips-easy-way-to-encrypt-usb-flash-drive-on-ubuntu.html)

1.  install **cryptsetup**

2.  plug in the usb stick, make sure to have a backup of contents as this process will erase everything.

3.  open **disk utility**, choose the correct device from left pane, check it is correct in the right pane. then select **unmount volume**.

4.  select **format volume**, to format the usb stick.

5.  type: ext4, check **take ownership of filesystem**, check **encrypt underlying device**.

6.  choose a password.. a strong one would make sense - random letters and numbers.

---

### Post by Tralce on 2013-01-23
Well, this is weird. That's almost exactly the same process I used before, except the installing of cryptsetup. I installed cryptsetup and ran through the process once again, and it seems to be working ok now. I'll mark this as solved for now. Thanks!

---

