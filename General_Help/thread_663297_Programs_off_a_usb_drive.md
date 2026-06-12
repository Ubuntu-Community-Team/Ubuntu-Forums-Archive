---
title: "Programs off a usb drive?"
date: 2008-01-10
forum: General Help
---

### Post by lagitup on 2008-01-10
Is there a way to run a program in linux in general ubuntu in specific off a usb drive? (something simple like an html editor that can differentiate between an actual tag and a tpyo...)
Thanks all!
~lag

---

### Post by yurimxpxman on 2008-01-10
Are you saying that you want to install an application to the USB drive so you don't need to install it on each GNU/Linux machine you carry it to? If so, just copy the binaries to your USB drive. Eg, if you wish to carry Nvu on your USB disk, use:

```
sudo cp /usr/lib/nvu /media/mydisk
```

It's also important to note that the file system your drive uses makes a hug difference. You may not be able to execute the programs from a FAT32-formatted disk without changing the permissions every time you insert the disk.

---

