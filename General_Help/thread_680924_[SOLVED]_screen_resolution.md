---
title: "[SOLVED] screen resolution"
date: 2008-01-28
forum: General Help
---

### Post by Dave Otter on 2008-01-28
I am running Gutsy Gibbon and want to change the screen resolution to 1280 x 760 but this option is not given though I did have it on Feisty Fawn
    Any help appreciated
                 Thanks

---

### Post by Dave Otter on 2008-01-28
sorry reqd resolution should read 1024x768

---

### Post by confused57 on 2008-01-28
What videocard/chipset does your pc have?

Also, check your xorg & see what driver your video device is using:
```
gedit /etc/X11/xorg.conf
```
just in case...it's an uppercase X, (one)(one)

---

### Post by Dave Otter on 2008-01-28
What videocard/chipset does your pc have?
   How do I find out?

---

### Post by confused57 on 2008-01-28
> **Dave Otter said:**
> What videocard/chipset does your pc have?
   How do I find out?
Open a terminal & enter:
```
lspci
```

---

### Post by IanShuttleworth on 2008-01-28
I find success about 80% of the time by running
```
 sudo dpkg-reconfigure xserver-xorg
```

Eventually it will ask you what resolutions to allow, and make sure you select the right driver.

---

### Post by Dave Otter on 2008-01-30
Thanks to all . Had to reinstall.Now sorted .

---

