---
title: "Where is the WINE c:\ drive?"
date: 2007-08-27
forum: General Help
---

### Post by telovoyagarcar on 2007-08-27
I am using Mandriva.. in a friends home.
I just installed WINE but can't find the c drive.
/home/<username>/.wine/drive_c does not exist.
If i do a search for .wine folder, nothing comes up.
I can use "wine" command.. i just used it to install something in a terminal..
what can i do?

---

### Post by LaRoza on 2007-08-27
[http://www.mc1soft.com/linux/installing_wine.htm](http://www.mc1soft.com/linux/installing_wine.htm)

Maybe this will help, the C drive directory can be else where.

---

### Post by telovoyagarcar on 2007-08-27
> **LaRoza said:**
> I don't have Ubuntu in from of me, so I may be wrong.

go to your home folder (in Nautilus, not Terminal), press Ctrl + h.

Look in the .wine folder, it should be in there somewhere.

Please read my WHOLE question... thanks

---

### Post by aldenhg on 2007-08-27
Run winecfg. It'll automagically set up all of the paths you need to make wine work properly. It also lets you edit some settings and set up the sound. If you intend to play any games or play music I suggest you go with the OSS sound dirver - I've had problems with ALSA.

---

### Post by maybeway36 on 2007-08-27
~/.wine/drive_c

---

