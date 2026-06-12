---
title: "Mounting root.disk inside Windows?"
date: 2008-05-28
forum: General Help
---

### Post by mfearby on 2008-05-28
Is there a way to mount the root.disk file in Windows so that I can, for example, copy replacement *.conf files into the disk image, then unmount it (all automated via the command-line)?

My scenario is this: I'd like to be able to deploy Ubuntu Wubi installs to lots of classroom machines using Altiris (I have this working fine so far) except that on one machine, the teacher's computer, I'd like to insert a different xorg.conf into the root.disk file so that the display resolution is low enough for the data projector to cope with the image.

I might be asking a bit much, but I thought I'd ask if it can be done. If not, I'll probably have to prepare a different Wubi install and copy that one to the teacher's PC only.

Thanks

---

### Post by ago on 2008-05-29
Yes there are ext2 browsers for windows that can also look into loop files. If you search this forum you should be able to find some references.

---

### Post by HuntMike79 on 2008-05-30
Is it also possible to do this the other way around? Look at the files on the NTFS partition within Ubuntu iself (when running from the loop files)?

---

### Post by ago on 2008-05-30
Yes the windows partition where you installed wubi is available as /host
The others can be mounted separately

---

### Post by HuntMike79 on 2008-05-30
> **ago said:**
> Yes the windows partition where you installed wubi is available as /host
The others can be mounted separately

Awesome, thanks. :)

---

