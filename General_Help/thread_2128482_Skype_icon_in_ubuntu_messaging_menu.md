---
title: "Skype icon in ubuntu messaging menu"
date: 2013-03-23
forum: General Help
---

### Post by firekage on 2013-03-23
Hi.

I would like to ask for your help. I ran into strange problem. I use Ubuntu 12.10 and can't get skype or skype-wrapper to work wint ubuntu messaging menu. I installed skype-wrapper, i allowed skype to use skype.py scripts, in dconf-editor i have "skype" show where it should be, but there is no skype icon in ubuntu messaging menu - there is only green skype logo in unity taskbar. I would like to place skype to a place where there is also thunderbird, but i just can't do it. Do you see envelope? I would like to insert it there.

Could you help me? On the web i read that after installing skype-wrapper we can remove sni-qt in order to remove green skype icon, but when i do it, i don't have skype icon at all - no in unity taskbar, no in unity messaging menu - envelope.

---

### Post by kostkon on 2013-03-23
Unfortunately for you, 12.10 saw the introduction of a new api for the messaging menu; and obviously, any application that wishes to show it's icon in that menu, needs to be ported to this new api.

skype-wrapper hasn't been ported yet, so there is not chance you will make it work in 12.10 :(

Nevertheless, you can subscribe yourself, if you wish, to [the bug report that keeps track of the progress of the porting to the new api]("https://bugs.launchpad.net/skype-wrapper/+bug/1040259").

---

### Post by firekage on 2013-03-24
Thank You. I didn't know that - i used ubuntu from 11.10 to 12.04 with update and it worked, but after i updated it to 12.10 this function is broken. I thought that i broke it down.

---

### Post by firekage on 2013-03-25
The icon is back...i thing that i was missing one of the indicator for Unity menu. Now i have skype near thunderbird in Ubuntu "envelope". I was missing:

```
Indicator-applet is an applet to display information from
various applications consistently in the GNOME panel.
```

and 

```
Indicator-appmenu  This package provides support for application menus.
```

also

```
dicator-applet-complete is an applet to display information from
various applications consistently in the GNOME panel.
```
```
Indicator-applet-appmenu is an applet to display information from
various applications consistently in the GNOME panel.
```

---

