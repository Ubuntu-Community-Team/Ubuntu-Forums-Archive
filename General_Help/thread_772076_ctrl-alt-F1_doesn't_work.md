---
title: "ctrl-alt-F1 doesn't work"
date: 2008-04-28
forum: General Help
---

### Post by Jethro_uk on 2008-04-28
Hi all,

upgraded to HH, but since GG I have been unabled to get ctrl-alt-F1 to bring up a terminal. All it does is go black, and then I can't use ctrl-alt-F7 to get back to the X session.

This is now critical, as I need to use a terminal window to manually install my nVidia drivers ... in the event I can't do that, I can see myself having to remotely connect (using putty) and run it that way :-(

---

### Post by santaslittlehelper on 2008-04-28
If you can then maybe you should try to use either "Administration > Hardware Drivers" or envy to install the drivers?

If not try;
1. Boot into recovery mode and execute:
```
telinit 3
```
see if you can use ctrl + alt +f1 now.

2. Try switching your driver between either vesa or nv to see if it makes any difference.

I don't know or remember but this might be some old framebuffer bug.

---

### Post by Separ on 2008-04-28
I'm sure that you can do

```
/etc/init.d/gdm stop
```

to stick you on a terminal to install the nvidia drivers. At least I think that is what I did.

---

### Post by Joeb454 on 2008-04-28
If you can get into an X session in the first place you can just open up a terminal from there :confused:

It's in Applications > Accessories :)

---

### Post by Separ on 2008-04-28
the point is that the nvidia driver requires you to not be in an X session. Just in the console :p

---

### Post by Jethro_uk on 2008-04-29
> **Jethro_uk said:**
> Hi all,

upgraded to HH, but since GG I have been unabled to get ctrl-alt-F1 to bring up a terminal. All it does is go black, and then I can't use ctrl-alt-F7 to get back to the X session.

This is now critical, as I need to use a terminal window to manually install my nVidia drivers ... in the event I can't do that, I can see myself having to remotely connect (using putty) and run it that way :-(

Fixed it ! After 3 months ! It was the vesa/framebuffer bug.

---

