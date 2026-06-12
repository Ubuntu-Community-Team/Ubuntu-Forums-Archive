---
title: "KFTPGrabber fails to open"
date: 2007-01-07
forum: General Help
---

### Post by TheMatt on 2007-01-07
I have a small little problem that I am sure there is a quick fix to, but I am unsure of what it is. I set KFTPGrabber to minimize to the system tray when I closed it in the options. When I closed it and opened it back up again later, however, It showed the Loading symbol (the rotating hourglass) in the taskbar for about 30 sec., and then just went away. It does this every time I try to open it. An instance of KFTPGrabber opens whenever I try to open it. I tried this with no luck.
```
~$ sudo killall kftpgrabber
```
Any suggestions would be appreciated. Thanks.

---

### Post by tweedledee on 2007-01-09
> **TheMatt said:**
> I have a small little problem that I am sure there is a quick fix to, but I am unsure of what it is. I set KFTPGrabber to minimize to the system tray when I closed it in the options. When I closed it and opened it back up again later, however, It showed the Loading symbol (the rotating hourglass) in the taskbar for about 30 sec., and then just went away. It does this every time I try to open it. An instance of KFTPGrabber opens whenever I try to open it. I tried this with no luck.
```
~$ sudo killall kftpgrabber
```
Any suggestions would be appreciated. Thanks.

Try deleting (or renaming) the config files in ~/.kde/share/apps/kftgrabber.  You'll lose all your settings, but it may be that something weird got written there.

---

### Post by TheMatt on 2007-01-10
Thanks for the response. That didn't work unfortunately. Any other suggestions?

---

### Post by tweedledee on 2007-01-13
> **TheMatt said:**
> Thanks for the response. That didn't work unfortunately. Any other suggestions?

Reinstall it (in Synaptic)?

---

### Post by TheMatt on 2007-01-13
How would I reinstall it via the command line (what are the commands)? I am havingtrouble with Adept now. I don't have synaptic since this is Kubuntu.
[http://ubuntuforums.org/showthread.php?t=331631](http://ubuntuforums.org/showthread.php?t=331631)

---

### Post by tweedledee on 2007-01-13
> **TheMatt said:**
> How would I reinstall it via the command line (what are the commands)? I am havingtrouble with Adept now. I don't have synaptic since this is Kubuntu.
[http://ubuntuforums.org/showthread.php?t=331631](http://ubuntuforums.org/showthread.php?t=331631)

Not the most elegant, but it works:
```
sudo apt-get remove kftgrabber
sudo apt-get install kftgrabber
```

The only potential problem is that if kftgrabber is a standard component of kubuntu, you'll lose kubuntu-desktop when you remove kftgrabber.  That's not a big deal, that package doesn't do anything, and you can always re-install it as well (all it does is point to all the standard kubuntu packages so you can grab them in one shot).

---

### Post by jeremy on 2007-01-13
> **tweedledee said:**
> The only potential problem is that if kftgrabber is a standard component of kubuntu, you'll lose kubuntu-desktop when you remove kftgrabber.

kftgrabber is not a standard component of kubuntu.

---

