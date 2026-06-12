---
title: "help disabling the &quot;lock computer&quot; button on my Remote Wonder II"
date: 2007-11-28
forum: General Help
---

### Post by pombe on 2007-11-28
Hi all.

I'm running Mythbuntu, which is based on Xubuntu apparently, for my home theater PC.   I am navigating through the menus using only an ATI Remote Wonder II. This works like a charm for the most part except there is one button that, when pressed, locks the desktop.   This is kind of a pain in the butt because I then have to plug a keyboard into the machine and unlock the thing again.   Not a massive problem, but one that is going to bug me until I fix it...  

I cannot figure out a way to disable the button directly.  I've used xev and .Xmodmap to change a bunch of other buttons on my remote.  However, there is something special about this button as it doesnt give a keycode in xev.

The actual process that runs when I press this "lock" button looked like it was "xflock4" which is bound to Alt-Ctrl-Del in the keyboard shortcuts (has the exact same locking behavior).  however, if I disable this shortcut then pressing Alt-ctrl-del on the keyboard does nothing, but the "Lock" button still works.   If I remove xflock4 from its directory /usr/bin/ and the same thing happens.  keyboard shortcut doesn't work, "Lock" button still does its thing.

Anyone have any ideas for what to try next?  I've reached the end of my somewhat limited knowledge, and google hasnt been any help so far...

Thanks

Corey

---

### Post by Jonsson84 on 2007-12-22
i have exactly the same problem, although i'm using ubuntu 7.10 and a remote wonder 1.

i found this thread but the advise to "chmod o-x /usr/bin/gnome-screensaver-command" doesnt work either..
( [http://www.linuxquestions.org/questions/linux-general-1/how-do-i-disable-lock-screen-in-gnome.-530035/](http://www.linuxquestions.org/questions/linux-general-1/how-do-i-disable-lock-screen-in-gnome.-530035/) )

would appreciate any tips that can help to dissable the lock button.

/Jonsson

---

### Post by p_quarles on 2007-12-22
It sounds like the lock button is using a different locking application from the one being used by the keyboard shortcut. Try running this and pasting the output:
```
ls /usr/bin | grep lock
```

---

### Post by Jonsson84 on 2007-12-22
```
andreas@HTPC:~$ ls /usr/bin | grep lock
flock
hal-is-caller-locked-out
hal-lock
oclock
xclock
```

---

### Post by p_quarles on 2007-12-22
It doesn't look like there's any other specific program, then. I think hal-lock may be involved, but it's a low-level system tool and you don't want to mess around with that. 

The mythbuntu wiki suggests a way to turn off the screensaver, and I believe that the same application controls screen locking. See if you can disable the locking option in the gnome-screensaver-preferences dialogue. Here's the link:
[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

---

### Post by Jonsson84 on 2007-12-22
> **p_quarles said:**
> It doesn't look like there's any other specific program, then. I think hal-lock may be involved, but it's a low-level system tool and you don't want to mess around with that. 

The mythbuntu wiki suggests a way to turn off the screensaver, and I believe that the same application controls screen locking. See if you can disable the locking option in the gnome-screensaver-preferences dialogue. Here's the link:
[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

I tried to turn off the screensaver that way but it didnt work, but then i found a guide to stop and disable the screensaverprogram.. I just used the first 2 steps in this howto and it worked, no more lock when button is pressed..=)
[http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557)

Ofcourse i dont have any screensaver now but i dont care, XBMC that i use has its own anyway. =)

Thank you p_quarles for your help

---

