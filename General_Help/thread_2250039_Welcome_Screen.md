---
title: "Welcome Screen"
date: 2014-10-26
forum: General Help
---

### Post by rosswmcgee on 2014-10-26
How do I get back my unity greeter after installing Mate desktop? I get the mate greeter. No big deal but I am fussy. 

I followed one set of instructions but got bogged down on this. He says create a new

lighdm configuration file. I do not know how to do that. I use unity mostly but some times switch to mate. So even if I removed mate i would still have the greeter problem.


I installed mate on one of my Ubuntu 14.04 lts computers and do not have this problem. Every thing works. I just have been unable to duplicate it on my other ubuntu 14.04 computer.

Yes I can install it but then the greeter pages become mate and the terminal for instance become white instead of black, in other words its like mate takes over the computer

and ubuntu becomes the add on. I have used the recommended terminal commands. Back in the recesses of my mind I remember something about back ports as part of the

successful way of installing mate that did not cause the above problems, but I cannot remember how I did it.

---

### Post by CantankRus on 2014-10-27
Look in **/usr/share/lightdm/lightdm.conf.d** for a .conf file installed by mate.
My **/usr/share/lightdm/lightdm.conf.d/[COLOR="#FF8C00"]50[/COLOR]-unity-greeter.conf** file has a line 
```
greeter-session=**unity-greeter**
```


Check in files starting with a [COLOR="#FF8C00"]higher number[/COLOR] with the same line "**greeter-session=**". This will override the 50-unity-greeter.conf

eg some desktops install **/usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf**...
```
[SeatDefaults]
greeter-session=**lightdm-gtk-greeter**
```

[COLOR="#FF0000"]Comment[/COLOR] the **greeter-session** line..
```
[COLOR="#FF0000"]#[/COLOR]greeter-session=lightdm-gtk-greeter
```

---

