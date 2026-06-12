---
title: "top and bottom menu bar gone."
date: 2008-06-21
forum: General Help
---

### Post by erb2k915 on 2008-06-21
I don't really know how this happened. One day i turned on my computer, and the bars at the top and bottom of the screen are gone, and i don't know how to get them back. I tried pressing alt+f2 to open up a terminal, but it didn't work.

---

### Post by avtolle on 2008-06-21
Once you are on an installed system, to get to a terminal, it is CTRL+ALT+Fn, where 1=>n<=6. Were they deleted, or for some strange reason, did they autohide? To check the latter possibility, move your cursor (mouse arrow) to the extreme left or right top (or bottom) corners of your screen, and see if anything is reported.

---

### Post by erb2k915 on 2008-06-22
ok i got the terminal working, but i dont really know what to type to get it working. i tried the autohiding thing, that didn't work.

---

### Post by lfaraone on 2008-06-22
Please see [http://ubuntuforums.org/showthread.php?t=101657](http://ubuntuforums.org/showthread.php?t=101657)

---

### Post by johngml on 2008-06-22
I too have the same problem. It has happened before after installing the recommended updates. It works okay until you reboot  then bars are gone. Last time I wiped the disc and reinstalled thinking it was one of the programs I had on there but I reinstalled Hardy with just the contents of the disc. I did uninstall Evolution using Synaptic as it serves no purpose to me and I installed Thunderbird but other than that it is bog standard. Again I have installed the updates and the problem has returned.

---

### Post by johngml on 2008-06-22
> **ffm said:**
> Please see [http://ubuntuforums.org/showthread.php?t=101657](http://ubuntuforums.org/showthread.php?t=101657)

Had a look at it but cannot see how it refers to our problem. In any case as a beginner to Ubuntu it is written in a way I cannot understand anyway. Is there a simple way to restore it to how it was before whatever update screwed it up ?  As I don't know which update causes the problem i was wondering if it is wise to disable all of them. I know updates are meant to keep your computer secure but if they screw it up so you cannot use it then is there any point ?

---

### Post by johngml on 2008-06-22
I have been looking around the other forums and it looks like removing Evolution screws up the computer. Following instructions I got elsewhere I pressed Control-Alt-F2 and used the sudo apt-get install ubuntu-desktop command. It then proceeded to download several files including Evolution and when it was finished I rebooted. Everything looks as it was except Evolution has returned. As the command issued referred only to Ubuntu I have to assume that Evolution is part of the OS as it appears to screw it up if it is removed.

Hope this helps.

---

### Post by fooman on 2008-06-22
> **erb2k915 said:**
> ok i got the terminal working, but i dont really know what to type to get it working. i tried the autohiding thing, that didn't work.

open the terminal and type:

```
gnome-panel &
```

hope that helps.

---

### Post by erb2k915 on 2008-06-22
oh wow that must have been the problem i just uninstalled evolution because i use thunderbird.

---

### Post by erb2k915 on 2008-06-22
yeah reinstalling evolution worked

---

