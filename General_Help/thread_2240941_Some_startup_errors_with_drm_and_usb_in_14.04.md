---
title: "Some startup errors with drm and usb in 14.04"
date: 2014-08-23
forum: General Help
---

### Post by %cV4BU£r8Ofp&amp;# on 2014-08-23
When i start ubuntu some errors appear on the screen:
```

[   2.429487] usb 1-1.4: string descriptor 0 read error: -22
[   8.893307] [drm:cpt_set_fifo_underrun_reporting] *ERROR* uncleared pch fifo underrun on pch transcoder ...
[   8.893308] [drm:cpt_serr_int_handler] *ERROR* PCH transcoder A FIFO underrun
[  11.969580] usb 1-1.4: string descriptor 0 read error: -22

```

I have the lastest stable kernel (or maybe the second last) and Ubuntu 14.04 LTS. How do I solve this?

---

### Post by gordintoronto on 2014-08-23
Does the system work? If so, it's probably safe to ignore the errors.

This page might help your understanding: [http://askubuntu.com/questions/507302/updated-intel-display-driver-causing-errors-when-booting](http://askubuntu.com/questions/507302/updated-intel-display-driver-causing-errors-when-booting)

There are a couple of suggestions; I would try the "bootloader graphics" one first.

---

### Post by %cV4BU£r8Ofp&amp;# on 2014-08-26
I'll ignore the errors then. Thank you.

---

