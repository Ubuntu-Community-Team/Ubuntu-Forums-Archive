---
title: "Need help to reinstall XP over Xubuntu Dapper"
date: 2007-08-24
forum: General Help
---

### Post by greg_suomi on 2007-08-24
HI,

I ve been using Xubuntu 6.06 and XP for some time in dual boot.
I installed them the usual way, XP first then Xubuntu. It s been perfect
until I updated drivers for Terratec dm6 fire sound card. The sound card 
went away, then after that even the CD drive disappeared and now the USB mouse. 
I even tryed to follow MS on-line instruction about how to delete line in registry. It was
a mistake...

Now, It seems it would be best to just reinstall XP.
How can I do it without having to format my linux partition so that GRUB would still
exist, using same dual boot ?

Thanks,

gregoire.

---

### Post by 505 on 2007-08-24
Just install XP from the CD, and choose to install it on the same partition as the current installation of XP. It will leave the partition of Xubuntu alone, but will overwrite Grub. After the installation is complete, use a (X)ubuntu live disk to restore Grub.

---

### Post by tompickles on 2007-08-24
Just wondering how you would restore GRUB using the Live CD?

---

### Post by greg_suomi on 2007-08-24
> **tompickles said:**
> Just wondering how you would restore GRUB using the Live CD?

Yes, this is a good issue!

EDIT:
it seems to be good:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I let you know how it goes!

EDIT2
It worked like a charm with SGD. 
Thanks!

---

