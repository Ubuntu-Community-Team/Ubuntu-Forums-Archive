---
title: "Installing and running Groupwise libstdc++.so.5 problem"
date: 2008-06-17
forum: General Help
---

### Post by wess126 on 2008-06-17
Dear Friends,

I have recently installed groupwise for Linux version 6.5.7 using information from the following thread

[http://ubuntuforums.org/showthread.php?t=51893](http://ubuntuforums.org/showthread.php?t=51893)

Everything went fine until I tried to run groupwise using the following command:

/opt/novell/groupwise/client/bin/groupwise 

I then get the following error

/opt/novell/groupwise/client/bin/groupwise: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I did a google search to find a solution see below

[http://www.joewein.de/sw/swnotes002.htm](http://www.joewein.de/sw/swnotes002.htm)

I created the symbolic links to libstdc++.so.5 and I still get the same error.

I am running a Dell GX620 machine with Ubuntu 7.10 installed as a dual boot with win32 XP.

If someone could direct me to a tutorial or help out with some suggestions I would greatly appreciate it.

Many thanks,
Wes

---

### Post by chunchengch on 2008-06-17
> **wess126 said:**
> ...I created the symbolic links to libstdc++.so.5 and I still get the same error...

I think there is no libstdc++.so.5 in /usr/local/lib, try this:

1. delete the symbolic link you created

[COLOR="Red"]$ sudo rm -r /usr/lib/libstdc++.so.5[/COLOR]

2. install package libstdc++5

[COLOR="Red"]$ sudo apt-get install libstdc++5[/COLOR]


now the groupwise should work.

---

### Post by wess126 on 2008-06-17
cool, got it to work but Groupwise just hangs. We are having a new roll out in a couple of months so will upgrade then. for now I am back to using our webmail interface.

Shot alot.

---

### Post by clparker on 2008-07-06
We had to get rid of the Java Virtual Machine that comes with GW, and I had to copy some Java Package that we installed from Synaptec to the GW folder.

---

### Post by mist_01 on 2008-08-10
I am a linux noob, but I found that installing "gtk-qt-engine" fixed the problem for me.

---

