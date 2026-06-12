---
title: "Live USB with persistence, once setup how to lock down?"
date: 2014-08-28
forum: General Help
---

### Post by Atomic Dog on 2014-08-28
I have a live USB stick with a persistent file up and running and all setup the way I want (xubuntu flavor).  How, or is it possible to lock it down so no further changes can be made?  I would like it to always return to the original state when restarted -kind of like how pxe boot works for a bunch of our thin clients.

I have a situation where I need to temporarily convert some workstations for a project and this would be ideal for me.  I have searched, but any time I use the word persistent, I get a ton of results about how to create, not how to lock it down so no changes can be made (or any changes made are temporary).  Any ideas are very welcome.  Thank you!

---

### Post by yancek on 2014-08-28
From another Linux system booted, plug in the flash drive and then locate it, probably under /media.  You can then generate an iso file of it which will be read-only with the mkisofs, genisoimage commands.  Probably also with grub-mkrescue.  You should be able to put it on another flash drive with something like unetbootin.  These are standard methods for creating iso files, lots of tutorials on using mkisofs/genisoimage.  I've never tried it with a system with persistence so don't know if it will work.

---

