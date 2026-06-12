---
title: "I disabled my default screen..."
date: 2007-12-06
forum: General Help
---

### Post by milobos on 2007-12-06
I was messing around with my screen settings and I accidentally checked disable for my default screen. It only boots up in command line mode. I can get into my xorg.conf files, but I can't seem to enable my screen. Any help will be very much appreciated.

---

### Post by taurus on 2007-12-06
What happens when you run this command from a prompt?

```
startx
```

---

### Post by AntonGr on 2007-12-06
Don't know about how it is in Ubuntu or what is your distr, but if the command 'rc-update' is available type next :

```
rc-update add xdm default
```

That adds your screen to the boot-time.

---

### Post by taurus on 2007-12-06
> **AntonGr said:**
> Don't know about how it is in Ubuntu or what is your distr, but if the command 'rc-update' is available type next :

```
rc-update add xdm default
```

That adds your screen to the boot-time.

Looks like we have a Gentoo user here.

---

### Post by milobos on 2007-12-06
when I use startx in the command line I get:

(==) using config file: "/etc/X11/xorg.conf"
(II) module already built-in
(II) module already built-in
(WW) I810: no matching Device section for instance (BusID PCI :0:2:0) found
(WW) I810: no matching Device section for instance (BusID PCI :0:2:1) found
(EE) Screen 0 deleted because of no matching config section.
(EE) Device(s) detected, but none match those in the config file.

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X sever ":0.0"
        after 0 requests (0 known precessed) with 0 events remaining

---

### Post by taurus on 2007-12-06
You need to reconfigure your X again.

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by milobos on 2007-12-06
Thank you!!!!!

---

