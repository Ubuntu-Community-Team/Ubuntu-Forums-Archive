---
title: "cannot get scanner working"
date: 2008-06-10
forum: General Help
---

### Post by workshop1702 on 2008-06-10
hi asked this question a couple of months ago only got two replies which got me nowhere. my scanner is supported acording to info i found on the net but it wont work . this is what it says failed to open device artec-eplus48:libusub:006:002:invalid argument. realy doneed to get it working or will be forced back to windows . ubuntu is great but there are so many problems to get everything working and its so hard to get a reply.please someone help . thanks andrew:confused::confused::confused:

---

### Post by tbonemc on 2008-06-22
i have the same scanner and had the same problem.  you need to install the driver from the cd that came with the scanner.

put the cd in you cd drive, open a terminal, and type the following:

```
sudo mkdir /usr/share/sane/artec_eplus48u
sudo cp /media/cdrom0/WINXP/Artec48.usb /usr/share/sane/artec_eplus48u/Artec48.usb
```

It should work after that :)

---

