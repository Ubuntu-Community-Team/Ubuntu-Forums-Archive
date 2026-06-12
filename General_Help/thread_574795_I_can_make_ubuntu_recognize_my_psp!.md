---
title: "I can make ubuntu recognize my psp!"
date: 2007-10-13
forum: General Help
---

### Post by kris2pe on 2007-10-13
Ubuntu can't recognize my psp!
Ver: Feisty
Response to possible questions:
Why not buy a card reader?
I don't want to! In fact Ubuntu should recognize it!

---

### Post by rainwalker on 2007-10-13
It recognizes mine...?
It mounts as "disk" at "/media/disk" for me

What do you mean when you say it can't recognize it?

---

### Post by hardyn on 2007-10-13
enable feisty backports.

there was a new hal layer developed for gutsy, it solved all of my USB camera related issues.  They may have added support for the PSP

its worth a try anwyay.

---

### Post by kris2pe on 2007-10-14
> **rainwalker said:**
> It recognizes mine...?
It mounts as "disk" at "/media/disk" for me

What do you mean when you say it can't recognize it?
Well when I try to plug my psp in to the usb port in XP it automatically recognizes it as ie removable media F:
or something like that. In Ubuntu's case it just ignores it!

> **hardyn said:**
> enable feisty backports.

there was a new hal layer developed for gutsy, it solved all of my USB camera related issues.  They may have added support for the PSP

its worth a try anwyay.

How do I do that?

---

### Post by Sef on 2007-10-14
> How do I do that? (Enable the backports)

Applications > Accessories > Terminal

then type this command or copy and paste it:

```
 gksudo gedit /etc/apt/sources.list
```


Look for these two lines:

# deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

Remove the # before each one.   That will enable them.   

Gutsy Gibbon will be out on Thursday, so you may want to wait and update to it then.

---

### Post by Brucevdk on 2007-10-14
Or instead of manually editing your sources.list simply use the configuration utility:
*System -> Administration -> Software Sources -> Updates Tab -> Check Backports*.

---

