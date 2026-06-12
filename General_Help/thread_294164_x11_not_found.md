---
title: "x11 not found"
date: 2006-11-06
forum: General Help
---

### Post by naseem on 2006-11-06
hy!
i'm in big trouble
I fallowed the guide on beryl on edgy, tried to install nvidia beta drivers
then on reboot si says X: cannot start /etc/x11/x no file or dir. aborting
What to do? :-?

---

### Post by Iarwain ben-adar on 2006-11-06
Hi,
it is 
/etc/X11/X
with uppercase letters ;)


Iarwain

---

### Post by naseem on 2006-11-06
YEs it's /etc/X11/X
and on reboot it just pop ups this notice and after I give ok, black screen with cursor...](*,)

---

### Post by taurus on 2006-11-06
Can you get to a console with <Ctrl><Alt>F2 at all?  Otherwise, boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

