---
title: "Eject usb-device using UUID."
date: 2013-05-04
forum: General Help
---

### Post by sebastian.s on 2013-05-04
A simple question, is it possible to eject a usb-device by specifying its UUID insted of the device file? So insted of doing this:

```
eject /dev/sdb
```

You would do this:

```
eject 31AA-99B8
```

I have read the manual page but could not find any options for this, but i would like to ask here just to ne sure.

---

### Post by Cheesemill on 2013-05-04
You should be able to use...
```
eject /dev/disk/by-uuid/31AA-99B8
```

---

### Post by sebastian.s on 2013-05-05
Ah just perfect! thanks man :) I didn't know these types of files was there, i really need to explore the /dev filesystem some more.

---

