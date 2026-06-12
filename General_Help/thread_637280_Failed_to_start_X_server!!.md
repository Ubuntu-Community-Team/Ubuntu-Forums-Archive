---
title: "Failed to start X server!!"
date: 2007-12-10
forum: General Help
---

### Post by maria_smile on 2007-12-10
Hello everyone!
I am new to Ubuntu and Linux. I loaded Ubuntu a few days ago, i tried to install it,but there is  the following error message:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

When I hit yes it gives me:

"X Window System Version 7.2.0 
Release Date: 22 January 2007
X protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i 686
Build Date: 04April 2007
Before Reporting problems, check [http://wiki.X.org](http://wiki.X.org)
to make sure that you have the latest version.
Module loader Present
Markers: (--) probed, (**) from config file, (==) default setting,"
(++) from commande line,(!!) notice,(II) informational, (WW) warning,(EE)error,(NI) not implemented, (??) unknown

Fatal error:
Caught signal 11. Server aborting

I have tried sudo dpkg-reconfigure xserver-xorg, but it didnt work.. Any other ideas???
Any help would be appreciated.

---

### Post by Portable_Jim on 2007-12-11
What graphics card do you have installed on the machine?

---

### Post by maria_smile on 2007-12-11
ATi radeon X2300

---

### Post by ago on 2007-12-11
see if that helps
[http://ubuntuforums.org/showthread.php?t=497679&highlight=X2300](http://ubuntuforums.org/showthread.php?t=497679&highlight=X2300)

---

### Post by maria_smile on 2007-12-11
It doesn't work...

---

### Post by Portable_Jim on 2007-12-11
could you please post your xorg.conf
```
cat /etc/X11/xorg.conf
```

---

### Post by maria_smile on 2007-12-12
> **Portable_Jim said:**
> could you please post your xorg.conf
```
cat /etc/X11/xorg.conf
```

Sorry but I didn't understand what I have to do....:(

---

### Post by flamelab on 2007-12-12
In the console press 

or

```
cat /etc/apt/sources.list
```

or 

```
gedit /etc/apt/sources.list
```

It is a file (sources.list ) that holds links (repositories ) of servers that provide programs especially for your distribution .

Just copy paste whatever you see there on this thread and include everything in the code tag -->[img]http://ubuntuforums.org/images/uf/editor/code.gif[/img])just press this after you select all the text )

---

### Post by Portable_Jim on 2007-12-12
> **maria_smile said:**
> Sorry but I didn't understand what I have to do....:(
you could go to Places>>Computer>>Filesystem>>etc>X11 and double click on xorg.conf. Then copy everything in the text document (Ctrl+A then Ctrl+C) into the reply to this thread.

---

