---
title: "Screen display problems?"
date: 2007-07-30
forum: General Help
---

### Post by iAndrew on 2007-07-30
I've searched for this, but I'm pretty sure all the similar topics weren't even related to this.

When I boot ubuntu, it loads. The loading screen finishes, then you see the text from the kernel?

Anyways. When I finally get past it, my LCD screen displays a message:

MODE NOT SUPPORTED.

H = 63.5khz (I think) and V = 60 hz.

Is this with screen display?

If so is there a way to fix this problem through windows?

---

### Post by ago on 2007-07-30
press alt+f2 and run:

sudo dpkg-reconfigure xserver-xorg

or edit manually /etc/X11/xorg.conf

---

### Post by iAndrew on 2007-07-30
Nice 2100 posts. Anyways, I'm about to try it.
-----------------

Okay, I've tried it.

When I type that in I get a bunch of menus and screens that want information.
I'm not really the computer guy, but I do know basic stuff about my graphics card, but not about my keyboard and pci busses, etc.

If there is a way to solve something like this please help.

-Andrew

---

### Post by tuxcantfly on 2007-07-30
Just select the defaults for the keyboard/mouse and it should work fine; the issue appears to be that it didn't properly detect your monitor, so look carefully at the section when it asks about your monitor. Also, if you don't want to have to answer too many questions, this will do the process automatically (though manually doing it might work better):
```

sudo dpkg-reconfigure -fnoninteractive xserver-xorg
```

Also if you have an nvidia card, this might work better:

```
sudo apt-get update
sudo apt-get install nvidia-glx-new
sudo nvidia-glx-config enable
```

---

### Post by iAndrew on 2007-07-31
There is no default for keyboard/mouse I have to type itin.

It displays ________________________. That basically.

EDIT---------------------------------------------

Oh, okay I've read your post more thoroughly. Thanks. Time to try it.

---

