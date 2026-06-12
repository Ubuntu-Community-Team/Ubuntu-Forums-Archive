---
title: "Taking screenshots with fbgrab"
date: 2007-10-11
forum: General Help
---

### Post by vasiliymeshko on 2007-10-11
Hello. I'm trying to use fbgrab to take screenshots from virtual terminals but unfortunately anything I do results in the following:

```
Error: Couldn't open /dev/fb0
```

Any help would be greatly appreciated.

---

### Post by vasiliymeshko on 2007-10-17
Bump.... Anyone?

---

### Post by vasiliymeshko on 2007-11-12
Bump, and resurrected.

---

### Post by gmogmo on 2008-02-29
Hi!

You have to:
1. Have frame buffer support compiled into your kernel (default in ubuntu)
2. The virtual terminal has to use the frame buffer sub system (also default in ubuntu, but it depends on your hardware). 

I.e. if you have graphical boot progress, you have 1 and 2. 

Please note that the /dev/fbX device you are using need to exist (normally handeled by udev), and you might be on a system using /dev/fb1 (unlikely though), if so read the man page:

man fbgrab

---

