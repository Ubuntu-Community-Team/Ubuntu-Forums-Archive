---
title: "ZSNES not loading mouse error?"
date: 2008-01-05
forum: General Help
---

### Post by bhuthogg on 2008-01-05
here's the error I am  getting

Any help appreciated 

brian@brian-desktop:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/brian/.kde/socket-brian-desktop.
can't create mcop directory
brian@brian-desktop:~$ 

Thanks

---

### Post by rubicon on 2008-01-05
Believe me, mouse isn't your problem.
```

Starting Mouse detection.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

```

This is what I have when run ZSNES from console. I believe this is normal. However, it seems that 
> 
Creating link /home/brian/.kde/socket-brian-desktop.
can't create mcop directory

is not good.

---

### Post by bhuthogg on 2008-01-05
Creating link /home/brian/.kde/socket-brian-desktop.
can't create mcop directory hmm i dont have kde i just have regular ubuntu 7.10

---

### Post by rubicon on 2008-01-05
Hey. [http://ubuntuforums.org/showthread.php?t=582289](http://ubuntuforums.org/showthread.php?t=582289)

---

### Post by bhuthogg on 2008-01-06
> **rubicon said:**
> Hey. [http://ubuntuforums.org/showthread.php?t=582289](http://ubuntuforums.org/showthread.php?t=582289)

mkdir -p $HOME/.kde/socket-$HOSTNAME/mcop


That fixes it :D

Thanks

---

