---
title: "Broke my xorg.conf :( Help please!"
date: 2007-01-30
forum: General Help
---

### Post by nzk on 2007-01-30
I was installing the fglrx driver, and per the instructions on it's wiki, I had modified my xorg.conf. When I rebooted, the X-Server had crashed. I tried removing what I had put in, to no avail. I don't know what to do now. Can anyone help?

---

### Post by taurus on 2007-01-30
Can you boot into recovery mode from GRUB menu and change the Driver back to **vesa**?  That would at least let you run X again.

```
nano -w /etc/X11/xorg.conf
```

---

### Post by po0f on 2007-01-30
nzk,

Most guides suggest backing up xorg.conf before making changes to it.  Do you have a backup?  If not, boot into recovery mode and `dpkg-reconfigure -phigh xserver-xorg`.

---

### Post by nzk on 2007-01-30
> **taurus said:**
> Can you boot into recovery mode from GRUB menu and change the Driver back to **vesa**?  That would at least let you run X again.

```
nano -w /etc/X11/xorg.conf
```
yeah, im posting this from recovery mode with lynx. i'll try that thing.

---

### Post by nzk on 2007-01-31
> **po0f said:**
> nzk,

Most guides suggest backing up xorg.conf before making changes to it.  Do you have a backup?  If not, boot into recovery mode and `dpkg-reconfigure -phigh xserver-xorg`.

will that fix it?

BTW, how do I reload a page in lynx?

---

### Post by bg1256 on 2007-01-31
> **po0f said:**
>  `dpkg-reconfigure -phigh xserver-xorg`.

That will work, but it will erase any other changes you've made to your xorg file.  Try changing the driver name to vesa, and if that works, you will save the rest of your xorg configurations.

---

### Post by nzk on 2007-01-31
Okay, x is working. But now, the resolution is screwed up (the highest is like 1024x768) and the top gnome toolbar looks as if I had hit my screen with a hammer (black and weird).

I am installing the ati proprietary driver, then rebooting. hopefully that will work.

---

### Post by disturbedite on 2007-01-31
i just installed beryl (on kubuntu) yesterday.  i used to use compiz, but wasn't completely satisfied with kde integration/stability.  (its cuz i don't have a powerful/new video card with direct rendering, aiglx, not cuz of compiz).

i installed it via the guide on beryl's wiki for feisty.  it was pretty much the same approach as installing compiz.

something must have went wrong tho.  i scewed up x.  i could have restored a backup, but i knew what i had changed/added so edited xorg.conf via command line.  i tried removing/reverting all the info i added/changed but it didn't work.  it left me very concerned that removing/reverting the changes didn't fix it.  then i booted via kernel's safe mode.  (thank god).  i checked around online looking at other peoples' xorg.conf and realized that somehow the line "Load "i2c" under Section Module got removed.

i re-added that and x started fine.  beryl works nicely now.

---

