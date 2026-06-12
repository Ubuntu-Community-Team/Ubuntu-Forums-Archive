---
title: "i need help running Ubuntu"
date: 2007-09-09
forum: General Help
---

### Post by BulletREaper713 on 2007-09-09
when i run this os i get the start screen and then it tells me error xo rsomething cant find any screen what do i do?

---

### Post by 1337455 10534 on 2007-09-09
Was it X.org? You mite have to reset it, although you'll have to ask a higher power than me to do that.
Sure your hardware is fine?

---

### Post by merlinus on 2007-09-09
Try this:

Start in recovery mode, and at the command line:

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
or reboot.

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

---

