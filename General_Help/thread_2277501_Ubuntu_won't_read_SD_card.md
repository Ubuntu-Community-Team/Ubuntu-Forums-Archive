---
title: "Ubuntu won't read SD card"
date: 2015-05-09
forum: General Help
---

### Post by dadaq on 2015-05-09
How can I get Ubuntu to read my SD card. Ubuntu won't read my SD card that's on my laptop and when I plug in my SD card reader, it does not see that as well.

---

### Post by tgalati4 on 2015-05-09
Welcome to the forums.

Open a terminal and post the output of:

```
lsusb
```

Plug the SD card in the laptop and post the following:

```
dmesg | tail -50
```

Do any SD cards work with either your laptop or card reader?

---

