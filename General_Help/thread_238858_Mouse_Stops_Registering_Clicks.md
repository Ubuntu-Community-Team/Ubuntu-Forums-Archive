---
title: "Mouse Stops Registering Clicks"
date: 2006-08-18
forum: General Help
---

### Post by socrplyr on 2006-08-18
I inherited a Dell 4400 PC from a previous user in my lab.  I installed Ubuntu pretty much as soon as I got it, but I am having problems with the mouse.  when I first log into gnome everything works great. then after being logged in for a while the mouse stops registering clicks.  the pointer still is able to be move around the screen although hovering over things like the buttons no longer causes them to highlight or display the name.  There seems to be no commonality when this happens, other than possibly time.  The mouse is a standar Dell branded MS mouse w/ scroll wheel (not optical) plugged into a PS/2 port.  To fix the problem if i kill the gnome session with the keyboard and then log back in it works fine again for a while then does it again.

Any ideas?

Thanks,
Josh

---

### Post by linuxbz on 2006-08-19
Have you tried using a different mouse? I recently had trouble with a mouse doing multiple clicks when I middle-clicked. I replaced the mouse and have no problems anymore.

---

### Post by socrplyr on 2006-12-13
Actually there is now a definite correlation between the mouse stopping working and rdesktop.  It only occurs when I am running rdesktop.  I am not sure, but it might have something to do with the screen saver coming on.  This problem is definitely reproducible with a fresh install on this machine.  I do not have another to try it out on.
Josh

---

### Post by maczap on 2006-12-31
This is also happening to me. The mouse functions properly under xfce and fails after a few minutes of use under gnome.

I am using xubuntu 6.1 and have added gnome as a package.

Have not tried loading ubuntu 6.1 so hope that helps someone else figure out what may be going wrong.

GoodLuck
Severin Swensen

---

