---
title: "Trying to speed up my boot time"
date: 2008-01-07
forum: General Help
---

### Post by ~LoKe on 2008-01-07
Well, I'm trying to trim down my boot time by a couple more seconds, but I'm not sure which of the remaining processes I can get away with removing.  Attached is my most recent boot chart.

I'm curious about dkms_auto, console-kit(which I've disabled in sysv-rc-conf...), klogd/syslogd, rmpq, and libusual.  Basically, if someone could tell me which services I could disable, I'd appreciate it!

Also, in Feisty I could disable some of the tty's, but the old "fix" doesn't work in Gutsy or Hardy.  How would I do it?

---

### Post by ~LoKe on 2008-01-07
No ideas?

---

### Post by Arthur Archnix on 2008-01-14
Disabling tty's has been changed in Gutsy. You'll find them in /etc/event.d
```
cd /etc/event.d && ls | grep tty
```

To disable a tty simply rename it tty#.bak. E.g., 
```
sudo mv tty2 tty2.bak
sudo mv tty3 tty3.bak
```
And so forth. On your next reboot, those tty's you renamed will be disabled. I'm sure you know, but it's a good idea to keep at least one tty available for troubleshooting.

---

### Post by kool_kat_os on 2008-01-14
Here is a great thread:
[http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903)

---

### Post by ~LoKe on 2008-01-14
> **Arthur Archnix said:**
> Disabling tty's has been changed in Gutsy. You'll find them in /etc/event.d
And so forth. On your next reboot, those tty's you renamed will be disabled. I'm sure you know, but it's a good idea to keep at least one tty available for troubleshooting.

Thanks!  I'm leaving two available just in case.  I need at least one to startx (I've got GDM disabled).  I'll see if I really need the second later.

---

### Post by Arthur Archnix on 2008-02-28
Looks like that may have been bad advice. Sure enough you can't switch to those terminals once they've been moved like that, but they're still running and using up ram. Just do sudo ps ax to see for yourself...
```
sudo ps ax
```
The way to get them gone for real, it turns out, is to ignore the whole moving them / renaming them nonsense, and open up the tty files in /etc/event.d
```
cd /etc/event.d && ls | grep tty
```
To disable tty2, (and you just have to repeat this for the rest), open up the tty2 file:
```
gksudo gedit tty2
```
And comment out the lines that say "start". So, you're file would look like this:
> # tty2 - getty
#
# This service maintains a getty on tty2 from the point the system is
# started until it is shut down again.

#start on runlevel 2
#start on runlevel 3

Repeat as desired, reboot to take effect.

---

