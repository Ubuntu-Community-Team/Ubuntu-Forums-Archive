---
title: "ubuntu randomly logs out after upgrading to 13.04"
date: 2013-08-18
forum: General Help
---

### Post by matrooswolf on 2013-08-18
Hi,
I recently upgraded to 13.04 and since then my desktop, seemingly randomly, logs me off and goes back to the login screen.

This goes very fast. There is no message or warning, no freeze (or it should be for a tiny fraction of a second).
After logging in all programs are closed.
It seems random. Sometimes after 5 minutes with only firefox running. Sometimes after hours with plenty of programs running. Sometimes after being away and simply moving the mouse.

I problably could do a clean install, but I would rather know what is happening and how I can fix this, but I have no idea where to begin to debug this.

Anybody any ideas how I could find the cause?

---

### Post by Frogs Hair on 2013-08-18
This can be graphics card and driver related . System Log/ Xorg.0.Log may offer some clues.

---

### Post by matrooswolf on 2013-08-18
Hi Frogs,
thanks for your reply. And what should I be looking for? in Xorg.0.Log?

---

### Post by Frogs Hair on 2013-08-18
Warnings or failures would be a good place to start . An example would be video driver modules not loading properly or failing .

---

### Post by matrooswolf on 2013-08-19
I see no errors (EE) in the file, only these warnings:```
[    41.910] (WW) Falling back to old probe method for vesa
[    41.910] (WW) Falling back to old probe method for modesetting
[    41.910] (WW) Falling back to old probe method for fbdev
```

---

### Post by Frogs Hair on 2013-08-19
Are you using the default graphics drivers or did you install proprietary drivers from additional drivers ?

---

### Post by philinux on 2013-08-19
Run this in a terminal. 

copy the resulting link when you post back

```
pastebinit ~/.xsession-errors
```

---

### Post by matrooswolf on 2013-08-20
Hi Frogs,
I use the default graphics driver

Hi philinux,
This is the result:

[http://paste.ubuntu.com/6005796/](http://paste.ubuntu.com/6005796/)

*verbinding is geweigerd* means *connection refused*
*kan gedeeld objectbestand niet openen: Bestand of map bestaat niet* means *cannot open shared object file: file or folder does not exist*

---

### Post by philinux on 2013-08-20
Have a look in system settings - software and update- additional drivers. Try the recommended if any.

---

### Post by matrooswolf on 2013-08-21
Hi philinux,
I had a look, but there are no recommended additional drivers. This is my graphic chipset: Intel® G33 x86/MMX/SSE2

---

### Post by matrooswolf on 2013-08-30
Apparently /boot/grub/menu.lst was not automatically updated so it still loaded an old kernel (3.0.0). I have deleted menu.lst and generated a new menu.lst with the latest kernel (3.8.0).
Maybe the problem is fixed now. So far no crashes.

---

