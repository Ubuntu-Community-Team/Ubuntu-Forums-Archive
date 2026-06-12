---
title: "Ubuntu starts timidity at boot, but it should not."
date: 2017-09-22
forum: General Help
---

### Post by bartveurink5 on 2017-09-22
with ps aux i do see the following:
```
timidity  1028  0.0  0.3 126152 12160 ?        S    12:24   0:00 /usr/bin/timidity -Os -iAD

```

When i want to start the program, below. It does not work, because timidity is already loaded.
```
timidity -iA -Os -B2,8 &
```

So i had to kill the first process what ps aux shows. Then start timidity on the right way and then sounds works. Every time i reboot i had to kill the process first. Thats why i dont want to load it at boot.

I did add and also remove applications in the "Startup Applications Preferences". Did ubuntu remove it wrong?
For trying to get music in a game, i did search on the web. I did try some commands with timidity. But in the configuration files cant i find a line with timidity that causes to start it at boot.

Can someone help me with this? I am desperate.

---

### Post by ajgreeny on 2017-09-22
I think that is normal as my system is the same.
timidity  1173  0.0  0.1 126152 12332 ?        S    10:20   0:00 /usr/bin/timidity -Os -iAD

If I use command ```
timidity Music2/file.mid
``` where I have several midi files it plays them without a problem.
I also have the added **timidity-interfaces-extra** package installed to get the few simple GUIs available from that using **timidity -ig** for the gtk version and **timidity -ik** for the Tcl/Tk GUI.

---

### Post by bartveurink5 on 2017-09-22
I can play midi files, but Age of Empires dont play music.
When I delete timidity in /etc/init.d/ then i start after reboot "timidity -iA -Os -B2,8 &". Now Age of Empires plays music.
If I kept timidity in /etc/init.d there is no music.

---

### Post by ajgreeny on 2017-09-22
I know nothing about "Age of Empires"; is it a game or something else that uses midi files as the sound source?

---

