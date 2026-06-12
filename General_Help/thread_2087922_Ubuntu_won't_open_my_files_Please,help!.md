---
title: "Ubuntu won't open my files? Please,help!"
date: 2012-11-25
forum: General Help
---

### Post by Lightbunny on 2012-11-25
Hey ):P

I am really new here, like, I made this account right now, and I need some help. I have a micro SD card and he is really small, so I use an appropriate USB pendrive that opens all my files from SD card. I was trying to open it now, but when I plug the USB pendrive on my laptop, everything that appears is:

"Unable to mount 1.0 GB Filesystem

Error creating moint point: Input/output error"

How do I solve this problem? Please, it's really urgent!
:(

---

### Post by beboylips on 2012-11-25
```

sudo fdisk -l 

```

Locate your pendrive, copy the /dev/sdXX or whatever will be the link.

```

sudo mkdir /media/pendrive
sudo mount -t msdos /dev/sdXXX /media/pendrive 

```

---

