---
title: "X Problem"
date: 2007-03-08
forum: General Help
---

### Post by Eminem on 2007-03-08
I just finished installing Ubuntu on a 4GB partition. All went well until I wasn't able to boot into the OS because of a "X Server Problem" or something of that sort. It asked me to check for a version of some sort in wiki.x.org or something.

I have an ATI Radeon 7000 Graphics Card, any help?

---

### Post by taurus on 2007-03-08
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
Use **vesa** as a driver for your graphic card until you get X running.  Then, you can install an ATI driver for it.

Reboot your machine with

```
shutdown -r now
```

---

### Post by cfyves on 2007-03-13
I just wanted to post to say that I've recently installed Ubuntu 6.06 on a server I'm rebuilding.

I have had problems with xserver and this seems to have solved my problems.

This forum is certainly a great ressource.

:)

---

