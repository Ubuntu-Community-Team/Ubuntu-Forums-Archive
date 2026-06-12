---
title: "GUI not loading after change to xorg.conf"
date: 2008-01-20
forum: General Help
---

### Post by JPotter on 2008-01-20
I am one month into regular usage of linux, so keep in mind that I am not an expert.  

I have a Logitch mx518 mouse; I wanted to use all of the buttons. After searching the forums I came across this HOWTO:

```
[http://ubuntuforums.org/showthread.php?t=65471&highlight=mouse+buttons+logitech](http://ubuntuforums.org/showthread.php?t=65471&highlight=mouse+buttons+logitech)
```

It illustrates some edits to xorg.conf.  After executing all of the changes and rebooted my UI it came back up in fail-safe mode.  I followed the instructions in the fail-safe xorg.conf to bring back a normal version using:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

After rebuilding xorg.conf with this command my boot process won't go beyond the splash screen.


How can I bring my UI back?

---

### Post by jleaker01z on 2008-01-20
Boot up

Press ctrl+alt+f1

Login

type "cd /etc/X11"
type "dir"
Find your old xorg.conf  (likely either xorg.conf.backup or xorg.conf.old)
type "sudo rm xorg.conf"
type "sudo cp xorg.conf.backup xorg.conf" (xorg.conf.backup=your old xorg.conf file, whatever it is)

Reboot

---

### Post by erfahren on 2008-01-20
that howto really should've had you backup your /etc/X11/xorg.conf before editing it - "water under the bridge"

the one you edited still exists - when you reconfigure it the utility automatically makes a backup

so in the login screen - go to "Sessions" and login failsafe mode (you already may be there) - at the command pronpt enter (list the directory's contents):
```

ls /etc/X11

```
the backup file will be something like "xorg.conf.xxxxxxx" where "x" are numbers - copy that over your current one:
```

sudo cp /etc/X11/xorg.conf.xxxxxxx /etc/X11/xorg.conf

```
Now (you're not done) - open it up in "nano" (command line text editor) and remove the changes or entries you originally made when going by that howto
```

sudo nano /etc/X11/xorg.conf

```
hit Ctrl+X to save - and try to startx

---

### Post by rosegarden78 on 2008-01-20
> **jleaker01z said:**
> Boot up

Press ctrl+alt+f1

Login

type "cd /etc/X11"
type "dir"
Find your old xorg.conf  (likely either xorg.conf.backup or xorg.conf.old)
type "sudo rm xorg.conf"
type "sudo cp xorg.conf.backup xorg.conf" (xorg.conf.backup=your old xorg.conf file, whatever it is)

Reboot

Thank you I had another thread dealing with this issue.

---

### Post by JPotter on 2008-01-20
Thank you both for your suggestions, I've been off fixing my idiot mistake. I did get Gutsy out of fail-safe mode.  Now, on to breaking it again! (with backups this time)

---

### Post by rosegarden78 on 2008-01-22
There's a thread look for How to Restore Xorg if you still need help.  It looks something like dpkg reconfigure a xorg I think ...

---

