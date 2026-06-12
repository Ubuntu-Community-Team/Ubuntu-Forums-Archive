---
title: "Usplash / Bootsplash : same things required on a custom kernel ?"
date: 2005-10-17
forum: General Help
---

### Post by Spear on 2005-10-17
Hi !

I use a custom kernel, a 2.6.10. I'd like to use the nice Usplash. But, one thing i don't find nor understand, is about it's prerequisites : are these the same required as for bootsplash ?

Is usplash an advanced version of bootsplash or not ? I checked Usplash readme  but it tells nothing about what's required to use it ...

So, what's required for usplash to be used ? Kernel option changes (same as for bootsplash ?) ? Patches ?

Thanks !

---

### Post by seldenthuis on 2005-10-17
I don't know what the prerequisites for bootsplash are, but usplash needs to have vga16fb framebuffer support enabled in your kernel.
As far as I know the only kernel option you need then is 'splash'.

BTW: You can still use the vga=... kernel option, but only with vga16fb. Any other framebuffer won't work with usplash and will probably only give you a blank screen in the console.

---

### Post by Spear on 2005-10-18
I contacted the development team :
all that is required in the kernel is framebuffer & initramfs, that's all.
Thanks !

---

### Post by felipe on 2005-10-18
this worked for me:

[http://www.ubuntuforums.org/showpost.php?p=416280&postcount=3](http://www.ubuntuforums.org/showpost.php?p=416280&postcount=3)

---

