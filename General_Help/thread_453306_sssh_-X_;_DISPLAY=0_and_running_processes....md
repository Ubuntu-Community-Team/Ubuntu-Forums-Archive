---
title: "sssh -X ; DISPLAY=:0 and running processes..."
date: 2007-05-24
forum: General Help
---

### Post by adieb on 2007-05-24
Hey there,

when i run firefox over a ssh -X session on my laptop, while the real process is located on my desktop maschine; is it possible to open a new firefox window on the desktop maschine? if i try to start per clicking on the icon or typing "firefox" in console, it just says i should close all runnning firfox windows, to start a new one.

well, i dont want to do that. is it not possible to open some kind of new instance?


another thing i´d like to know is:

can i "call back" a running process that is running under anouther DISPLAY?
for example change the DISPLAY variable while the process is still running? if yes, can i even do that when there is a ssh -X session "between" ?

....

i hope everybody understood what i mean although strange sentences ;-)

---

### Post by thelinuxguy on 2007-05-24
> **adieb said:**
> 
can i "call back" a running process that is running under anouther DISPLAY?
for example change the DISPLAY variable while the process is still running? if yes, can i even do that when there is a ssh -X session "between" ?


Are you looking for xmove? I haven't used it but the description looks like it.
([http://www.hermann-uwe.de/blog/how-to-hijack-an-already-running-x11-application-via-ssh-x](http://www.hermann-uwe.de/blog/how-to-hijack-an-already-running-x11-application-via-ssh-x))
```

apt-cache show xmove

```

---

### Post by adieb on 2007-05-25
hey, thanks a lot, it seems to be the right program. have not tested it yet, because still looking for a  howto or something, the man page is quite good, but still some problems ;-)

i am going to post if i find a good howto

---

### Post by hartz on 2007-05-25
I asked the same question back here: [http://ubuntuforums.org/showpost.php?p=2225775&postcount=1](http://ubuntuforums.org/showpost.php?p=2225775&postcount=1)

Unfortunately it requires that you have xmove running before you start up your X clients, but still this is a solution!!!

---

