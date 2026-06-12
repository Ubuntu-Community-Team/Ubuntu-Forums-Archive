---
title: "pop up notification tells me to update a program that was removed/purged"
date: 2016-01-19
forum: General Help
---

### Post by J_Me on 2016-01-19
I removed/purged a program but I'm still getting a pop up notification to update that program! How do I fix this. Please tell me what extra information you need. Thanks

---

### Post by v3.xx on 2016-01-19
```
apt-cache policy **name-of-package**
```
what it say?

---

### Post by Bucky Ball on 2016-01-19
*Thread moved to **General Help**.*

Not related to ***Desktop Environments***.

Open a terminal and

> sudo apt-get autoremove

'A program' is not sufficient. Which?

---

### Post by J_Me on 2016-01-19
It's called 'flashplugin-installer'

---

### Post by grahammechanical on 2016-01-19
All you removed is the flash plugin installer which is also the method of updating flash ( I think). We cannot install Adobe Flash through the software center because it is  proprietary software but we can install an open source installer that  does the downloading and installing of Adobe Flash. It is this installer that you purged.

 Web sites will often say that Flash is out of date. And this is because Adobe stopped supporting the Linux version of Flash years ago.

Regards.

---

### Post by J_Me on 2016-01-19
The only reference to 'flash' that dpkg --get-selections shows is flashplugin-installer and nothing more. Should I look somewhere else. Thanks

---

### Post by J_Me on 2016-01-19
This pop up I'm getting is from the  'SYSTEM TRAY' which is why I originally posted this thread in the 'Desktop Environments sub forum'. To be clear I am NOT getting a update flash pop up while trying to watch a video using a web browser.

---

### Post by Bucky Ball on 2016-01-19
You could try installing Synaptics, search for 'flash', 'completely remove' any installed bits that show up ...

---

### Post by SeijiSensei on 2016-01-19
If you want to keep Flash on your system, then you'll need flashplugin-installer.  If not, then run "sudo apt-get remove -purge flashplugin-installer".

It's also possible you have something else installed for which flashplugin-installer is a dependency.

---

### Post by Dennis N on 2016-01-19
You should check if the flash plugin was removed or left behind  - removing or purging the installer may not remove the plugin. I assume you want it gone?

```
dmn@Kayleigh:~$ ls /usr/lib/flashplugin-installer
install_plugin  [COLOR="#FF0000"]libflashplayer.so[/COLOR]
```

libflashplayer.so is the actual plugin.

---

### Post by J_Me on 2016-01-20
@* There's nothing flashplugin-installer to remove or purge.[br]1[/br] [br]1[/br] @SeijiSensei >  It's also possible you have something else installed for which flashplugin-installer is a dependency  The only package on this PC I can think of that drags in a bunch of stuff with it is Wine. Otherwise I haven't intentionally installed anything that needs flash.[br]1[/br][br]1[/br]   @Dennis N The only thing in /usr/lib/ that has the word flash in it is[br]1[/br] [br]1[/br] ./x86_64-linux-gnu/libvisual-0.4/morph/morph_flash.so[br]1[/br] ./libreoffice/program/libflashlo.so[br]1[/br][br]1[/br]   I give up. I'm not wasting any more time on this, fumbling around in the dark when all I really need is a 'right click > ignore this specific package' option.[br]1[/br] [br]1[/br] Thanks anyway

---

### Post by Bucky Ball on 2016-01-21
Have you got ubuntu-restricted-extras installed? Anyway, by the by. If you don't want any more help with this please mark as solved so others also don't waste time dropping by to give any. Thanks and good luck. :)

---

