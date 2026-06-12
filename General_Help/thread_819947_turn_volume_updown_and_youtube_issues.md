---
title: "turn volume up/down and youtube issues"
date: 2008-06-05
forum: General Help
---

### Post by rock4christ on 2008-06-05
1.im not sure how to turn volume up or down is there a volume option somewhere, and/or a way to make my fn + page up/page down/end cause volume up/down/off respectively? im on a Dell Inspiron 5100

2.when I use youtube, I cant pause or change volume, and the loading circle stays in the center of the vid even while playing. I noticed that youtube works fine when embedded on one of my favorite sites.

---

### Post by iaculallad on 2008-06-05
> **rock4christ said:**
> 1.im not sure how to turn volume up or down is there a volume option somewhere, and/or a way to make my fn + page up/page down/end cause volume up/down/off respectively? im on a Dell Inspiron 5100

Navigate to System->Preferences->Keyboard Shortcuts,  Select the action you want to change and then type the key combination you want to assign for it.

> **rock4christ said:**
> 2.when I use youtube, I cant pause or change volume, and the loading circle stays in the center of the vid even while playing. I noticed that youtube works fine when embedded on one of my favorite sites.

Try installing libflashsupport

```
sudo apt-get install libflashsupport
```

---

### Post by rock4christ on 2008-06-05
> **iaculallad said:**
> Navigate to System->Preferences->Keyboard Shortcuts,  Select the action you want to change and then type the key combination you want to assign for it.



Try installing libflashsupport

```
sudo apt-get install libflashsupport
```im on xubuntu, not ubuntu. where would keyboard shortcuts be in xubuntu? and libflashsupport didn't help.

---

### Post by iaculallad on 2008-06-05
> **rock4christ said:**
> im on xubuntu, not ubuntu. where would keyboard shortcuts be in xubuntu?

I guess that would be located on Settings->Window Manager Settings->Keyboard Settings.

---

### Post by rock4christ on 2008-06-05
> **iaculallad said:**
> I guess that would be located on Settings->Window Manager Settings->Keyboard Settings.there is no option for changing volume

---

### Post by rock4christ on 2008-06-05
bump

---

### Post by iaculallad on 2008-06-05
> **rock4christ said:**
> bump

Here, I did some research for you and it seems that amixer could do the volume keyboard shortcut thing for XFCE. Jump on to this [link]("http://alvonsius.wordpress.com/2007/01/08/xfce-volume-controlling-with-keyboard/") and perform the said procedures.

---

### Post by rock4christ on 2008-06-05
ok, but how do I add the shortcut to the theme?

---

### Post by rock4christ on 2008-06-06
bump

---

### Post by iaculallad on 2008-06-06
If what you mean is how to add the volume control on the panel:

Right click on the panel and select "Add New Item", a window will display where you can select/double click the Volume Control (under System and Hardware) from the shown items. From there, you can now see a speaker icon on the right-topmost side of your panel.

---

### Post by rock4christ on 2008-06-06
ok. i did that, but I cant figure out how to add keyboard shortcuts, i only see how to edit pre existing ones.

---

### Post by x1a4 on 2008-06-06
Settings > Settings Manager > Keyboard > Shortcuts Tab

---

### Post by rock4christ on 2008-06-06
ok. what should I name the commands?

---

### Post by x1a4 on 2008-06-06
Depends on your soundcard and how you have it configured.  There are two tools you may want to try: **aumix** and **amixer**

aumix examples:
```
aumix -v+10
```
will increase main volume by 10
```
aumix -v-10
```
will decrease main volume by 10
```
aumix -v0
```
will mute
```
aumix -b+10
```
will increase bass by 10
```
aumix -l+10
```
will increase line by 10
```
aumix -1+10
```
will increase line 1 by 10, -2+10 line 2 and -3+10 will increase line 3 by 10
```
aumix -w+10
```
will increase PCM by 10

see the aumix manpage for details

amixer example:
```
amixer -c 1 -- sset Master playback 40%
```
will set the main volume of the second card to 40%.

see the amixer manpage for details

You have to install the aumix package to use aumix, and I think (although I'm not certain) you have to install the alsa-utils package to use amixer

---

### Post by Alistair George on 2008-08-16
Using Ubuntu 8 I find the system max volume is quite a bit lower than what I get out of WinXP on the same machine.

Any others having same issue - it has to be on same machine to be relevant eg Winxp on one partition and Linux on another or similar.
Cheers,
Alistair.

---

