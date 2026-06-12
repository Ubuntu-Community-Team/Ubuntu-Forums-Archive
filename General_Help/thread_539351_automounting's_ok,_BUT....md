---
title: "automounting's ok, BUT..."
date: 2007-08-31
forum: General Help
---

### Post by jf/ on 2007-08-31
is it possible to do the following, and if so, how?
- disable that popup that takes place after a drive is recognized. I don't need that!
- set it up so that my normal user can umount (and not just root)

---

### Post by chewearn on 2007-08-31
> **jf/ said:**
> is it possible to do the following, and if so, how?
- disable that popup that takes place after a drive is recognized. I don't need that!
If you are using Gnome desktop, goto:
Top Panel Menu > System > Preferences > Removable Drives and Media

> - set it up so that my normal user can umount (and not just root)
Sorry, not sure what you meant here.  I can umount removable drives / disc without root.

---

### Post by ajgreeny on 2007-08-31
What sort of drives are you talking about, USB?  These are usually automounted and you should be able to stop the query about what you want to happen (see astalavista above).  Usually any automounted drive plugged in to a USB port will also unmount without root privileges just by right clicking on the icon on desktop.  I assume this is not so in your case, but can't imagine why.

---

### Post by jf/ on 2007-08-31
> **AstalaVista said:**
> If you are using Gnome desktop, goto:
Top Panel Menu > System > Preferences > Removable Drives and Media


ah, gotcha. Thanks!

> Sorry, not sure what you meant here.  I can umount removable drives / disc without root.

sorry, folks, apparently you can do the unmount *graphically*. I am talking about doing it from the shell (and heck, pls, no sudo just to do that pls. Why should I? this is silly - GUI no sudo needed, xterm sudo needed?)

```

$ umount /media/disk/
umount: /media/disk is not in the fstab (and you are not root)

```

I've tried to include the entry in fstab, but when I do that, the disk no longer automounts...

---

### Post by jf/ on 2007-09-03
> **jf/ said:**
> ah, gotcha. Thanks!



sorry, folks, apparently you can do the unmount *graphically*. I am talking about doing it from the shell (and heck, pls, no sudo just to do that pls. Why should I? this is silly - GUI no sudo needed, xterm sudo needed?)

```

$ umount /media/disk/
umount: /media/disk is not in the fstab (and you are not root)

```

I've tried to include the entry in fstab, but when I do that, the disk no longer automounts...
uh.. anybody any comments?

---

### Post by jspangler on 2007-09-09
I have the same problem with a 320 gb hard drive. It's formatted ext3. It mounts automatically, but I can't use graphical unmount (it says can't unmount).

---

### Post by zazery on 2007-09-17
> **jf/ said:**
> uh.. anybody any comments?

I was wondering the same thing. After a bit of searching I figured out you can unmount it with the following command.

```
eject /media/card_name
```

---

