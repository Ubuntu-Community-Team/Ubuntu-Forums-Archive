---
title: "Very slow boot times"
date: 2007-05-31
forum: General Help
---

### Post by smasterson on 2007-05-31
I have a Dell Inspiron 5160 with Fiesty 7.04 on it and it boots in less than 1min 30 sec. It is a 3.2GB intel w/Nvidia FX 5200 go video card. I have 2 desktops with intel chipsets (1) intel 815, (1) intel 945 with ATI Radeon 9000 & 9600 Pro AGP video cards and they both take between 4-5 min. to boot up from progress bar.I've reinstalled several times with no change. Ifound a fix to help boot laptop faster but not desktop. Does anyone know of a fix for this? Any help would be much appreciated. Thanks in advance.

---

### Post by taurus on 2007-05-31
Perhaps you should edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
and remove the **quiet** at the end of an entry for kernel.  Then, you can see which process takes the longest to start.

---

### Post by smasterson on 2007-05-31
Thanks, I'll try that as soon as I get home

---

### Post by loathsome on 2007-05-31
If it's the «configuring network interfaces» step that hangs, I've got the solution ;) Just scream out if that's the case.

---

### Post by smasterson on 2007-06-01
> **taurus said:**
> Perhaps you should edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
and remove the **quiet** at the end of an entry for kernel.  Then, you can see which process takes the longest to start.

taurus,

I removed quiet from the end of the entry for kernel and it didn't change anything. I'm also dual booting with debian etch. Could the ati card be the problem as it doesn't do this with the laptop with the nvidia card?

---

### Post by tehBoris on 2007-06-01
You need to also remove the splash option from menu.lst.

---

### Post by smasterson on 2007-06-01
Sorry, I really hate to be annoying and stupid, but I removed **quiet** and **splash** and I still get the orange progress bar that hangs at the beginning for 4-5 min. I am a noob and I haven't been using linux near as long as I've been a member of the forum. Sorry for being a pain in the a**  :(

---

### Post by loathsome on 2007-06-01
Try pressing CTR+ALT+F6/F8 when usplash is loading.

---

