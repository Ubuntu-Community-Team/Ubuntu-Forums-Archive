---
title: "xorg.conf messed up"
date: 2006-12-29
forum: General Help
---

### Post by Ted D. on 2006-12-29
Unfortunately, I have messed something up in xorg.conf and X is not letting me in. I did save my xorg.conf.old but I don't know how to restore it. Don't know how to restore my old xorg.conf even in recovery mode. Need assistance, please, to get X up and running.
Ted D.:confused:

---

### Post by heinouskyle on 2006-12-29
Use:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by NeoLithium on 2006-12-29
To RESTORE your xorg....you might have saved it a differnet way. try this first:
```
cat /etc/X11/
```
And see what your backup xorg.conf is saved as. Then, all you have to do, is:
```
cp /etc/X11/<backup xorg name> /etc/X11/xorg.conf
```

Usually it's xorg.conf.bak, but I'm not sure how you saved it, checking the directory should let you know what its been saved as.  Good luck!

---

### Post by Ted D. on 2006-12-29
> **NeoLithium said:**
> To RESTORE your xorg....you might have saved it a differnet way. try this first:
```
cat /etc/X11/
```
And see what your backup xorg.conf is saved as. Then, all you have to do, is:
```
cp /etc/X11/<backup xorg name> /etc/X11/xorg.conf
```

Usually it's xorg.conf.bak, but I'm not sure how you saved it, checking the directory should let you know what its been saved as.  Good luck!

These look like terminal commands. How do I enter terminal commands in recovery mode?

---

### Post by NeoLithium on 2006-12-29
You betcha :)  Cat should display the whole contents of /X11 to you, and that way you can see what is similar to xorg.conf, in case it actually is xorg.conf.bak, or whatever it might be, the 2nd command overwrites the original, backup copy on top of the fault one, and then you should be back to the original before it was messed up.

---

### Post by Ted D. on 2006-12-29
Tried suggestion un recovery mode but for some reason /X11 doesn't show up. Any other ideas? Ted D.

---

### Post by NeoLithium on 2006-12-29
Did you go /X11 or /etc/X11? You you need to include the /etc/ first

---

### Post by scrooge_74 on 2006-12-29
> **Ted D. said:**
> Unfortunately, I have messed something up in xorg.conf and X is not letting me in. I did save my xorg.conf.old but I don't know how to restore it. Don't know how to restore my old xorg.conf even in recovery mode. Need assistance, please, to get X up and running.
Ted D.:confused:

Login from terminal window CTRL+ALT+F1

To restore old xorg.conf you should type

sudo cp /the_path_to_your_xorg.backup /etc/X11/xorg.conf

That should do it

---

### Post by Ted D. on 2006-12-30
No luck. Decided a reinstall -yuk!

Nevertheless I appreciate your help. I gotta lot of learning to do.

Thanks Ted D.

---

### Post by bapoumba on 2006-12-30
> **Ted D. said:**
> These look like terminal commands. How do I enter terminal commands in recovery mode?
In recovery mode, you are in a terminal, and you are root. Are you sure you are in recovery mode (you get there from grub menu)  ?
And to see what's in a file :
```
ls /etc/X11/
```

---

### Post by Ted D. on 2006-12-30
> **bapoumba said:**
> In recovery mode, you are in a terminal, and you are root. Are you sure you are in recovery mode (you get there from grub menu)  ?
And to see what's in a file :
```
ls /etc/X11/
```
 Hi,
Yes I selected the recovery mode in grub. In recovery I could get to /etc/  but when I asked for /etc/X11, It told me no such dir existed. Did a ls of /etc/ but could find no X11. Perhaps the dir had been renamed although I cannot reckon why that would be.
Ted D.

---

### Post by scrooge_74 on 2007-01-01
and when in /etc and you give ls, what dirs you have?

---

### Post by Ted D. on 2007-01-04
> **scrooge_74 said:**
> and when in /etc and you give ls, what dirs you have?
Can't give you the ls info because I have already reinstalled. Too bad, because I might have learned something more from you. Thanks for your interest.

---

