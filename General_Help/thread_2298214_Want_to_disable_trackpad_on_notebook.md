---
title: "Want to disable trackpad on notebook"
date: 2015-10-09
forum: General Help
---

### Post by michael-piziak on 2015-10-09
Xubuntu users on HP Notebook 2000

I want to disable the trackpad, and only have my mouse as input device - trackpad keeps moving things when I try to type and brush against it with my hand

---

### Post by howefield on 2015-10-10
There is often a hardware button on laptops (with an icon that resembles a mouse) for toggling the trackpad on/off. Some HP laptops have a button top left corner of the trackpad which toggle with a double tap, just have a look - you'll probably find it.. the Dell I'm using at the moment has a dedicated key next to the F12 button,

---

### Post by mikewhatever on 2015-10-10
The following could work:
```
synclient TouchpadOff=1
```

---

### Post by michael-piziak on 2015-10-13
> **mikewhatever said:**
> The following could work:
```
synclient TouchpadOff=1
```

that did it thanks!

so if i ever want to turn it back on, would i do synclient touchpadOnn=1

?

---

### Post by The_Forgotten_King on 2015-10-13
Should be something in settings...? On mine it had an option, otherwise do the ```
synclient TouchpadOff=1
``` To turn it on I think it would be ```
synclient TouchpadOff=0
```
Edit: Ups, solved already.

---

### Post by michael-piziak on 2015-10-13
> **The_Forgotten_King said:**
> Should be something in settings...? On mine it had an option, otherwise do the ```
synclient TouchpadOff=1
``` To turn it on I think it would be ```
synclient TouchpadOff=0
```
Edit: Ups, solved already.

I notice on reboot it turns trackpad back on

is this something i'll just have to turn off each time, or is there a permanent way to turn trackpad off on each reboot

the damn trackpad, i hit it with my palms while typing, and it always screws me up.

---

### Post by vasa1 on 2015-10-14
> **michael-piziak said:**
> I notice on reboot it turns trackpad back on

is this something i'll just have to turn off each time, or is there a permanent way to turn trackpad off on each reboot

the damn trackpad, i hit it with my palms while typing, and it always screws me up.

You can stick the code in your autostart file wherever that is.

There are also more subtle ways to prevent the annoyance: *grep -Ei* the output of *synclient* for "palm".

---

### Post by michael-piziak on 2015-10-14
> **vasa1 said:**
> You can stick the code in your autostart file wherever that is.

There are also more subtle ways to prevent the annoyance: *grep -Ei* the output of *synclient* for "palm".

I'm not that savvy with terminal.

But tell me what to type into terminal to stick the code into my autostart file.

This is an Xubuntu system.

---

### Post by yetimon_64 on 2015-10-14
You don't need to use the terminal to add an autostart entry in xfce, the GUI has a "services and startup" application you can directly add that command to. 

Go to, I think it's called, "Startup and Services" in xfce and then to the startup tab and add a new entry with the "New" button on the bottom of the window. For the command use "synclient TouchpadOff=1" and name the entry so you know what is when shown in the startup list. It should now turn the touchpad off each login to the desktop. Try a logout and then back in to see if the new entry works. Good luck.

---

