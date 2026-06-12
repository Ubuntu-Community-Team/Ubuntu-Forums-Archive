---
title: "What is /lib/firmware?"
date: 2013-01-23
forum: General Help
---

### Post by Tinsnip on 2013-01-23
What does it mean to copy something as "/lib/firmware"?   I'm trying to get my laptop to notice wireless networks by downloading a new header and image, but the file I was told to download first said to do it as "/lib/firmware".   I don't understand this, what is a header and image anyway?

---

### Post by Yellow Pasque on 2013-01-24
You put the file in (i.e. copy it to) the /lib/firmware directory.

>  I don't understand this, what is a header and image anyway?
The image package has the kernel and the header package has the  development files needed if one needs to build new kernel modules (which you probably do).

---

### Post by prodigy_ on 2013-01-24
> **Tinsnip said:**
> What does it mean to copy something as "/lib/firmware"?   I'm trying to get my laptop to notice wireless networks by downloading a new header and image, but the file I was told to download first said to do it as "/lib/firmware".   I don't understand this, what is a header and image anyway?
You sound awfully confused. I take it you're trying to install a newer version of Linux kernel to see if it fixes your Wi-Fi issues. It might very well do that (e.g. if your laptop is brand new and the old kernel simply doesn't have the required drivers) but that's not a guarantee.

It wouldn't hurt if you provided some specifics about the problem you're trying to solve.

---

### Post by Yellow Pasque on 2013-01-24
Probably shouldn't have made a new thread... [http://ubuntuforums.org/showthread.php?t=2107810](http://ubuntuforums.org/showthread.php?t=2107810)

I'm going to guess that you were using proprietary video drivers and that's why you got dumped in the terminal when trying to use a newer kernel. BTW, if that happens again, hold Shift after BIOS/POST screen to access the GRUB menu and boot into the older kernel that worked. A reinstall is not needed (this ain't Windows!).

---

