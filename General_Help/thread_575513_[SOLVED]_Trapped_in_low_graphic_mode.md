---
title: "[SOLVED] Trapped in low graphic mode"
date: 2007-10-14
forum: General Help
---

### Post by OsakaWilson on 2007-10-14
On my Acer Aspire 5100, I connected to a VGA to RCA converter (Buffalo PCast) and hurray, it worked. However it went into non-graphic mode on the next startup and is stuck there. 

This is my linux nightmare--it is dark, I am alone, and there is only a command line. 

I'm using 7.04 for 64 bit. How can I have my beautiful GUI back?

---

### Post by por100pre1 on 2007-10-14
Try to login and then do this:

```
startx
```

if that doesn't work try this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and follow the instructions...

```
sudo reboot
```

---

### Post by OsakaWilson on 2007-10-14
Well, that did it. It was the second part, not the startx. 

Thank you very much for your help.

---

