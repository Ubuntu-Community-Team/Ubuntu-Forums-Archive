---
title: "After upgrade to 16.04, no USB Mouse"
date: 2016-08-07
forum: General Help
---

### Post by herlann-weiss on 2016-08-07
I recently upgraded my Intel NUC BOXD54250WYKH1 from 14.10 LTS to 16.04 LTS. While everything worked flawlessly previously, now I have no USB mouse (as in, there is no pointer whatsoever).  In attempting to solve this problem I've done my homework and done the following:

1) Restarted/rebooted the system
2) Reboot with/without USB mouse connected
3) Tried 2 different wired USB mice (formerly with 14.10 both worked).  Both still work on other computer.
4) Uninstalled Natural Scrolling (was a nice-to-have, removed it just in case there were incompatibilities)
5) Booted into older 3.13 kernels
6) Checked the BIOS for USB Legacy checkmarked
7) All software up to date, both thru Software Updated and apt
8) Plugged the USB mice into different ports
9) Tried the fix outlined here: "http://askubuntu.com/questions/763511/usb-mouse-not-working-after-installing-ubuntu-16-04-persistent-fix" 
10) Various hardware detail programs such as hardinfo oulined here: [http://askubuntu.com/questions/31618/how-can-i-find-my-hardware-details](http://askubuntu.com/questions/31618/how-can-i-find-my-hardware-details) show that there in indeed a USB mouse recognized by the system
11) removed gnome-software-center because somebody reported some problems on Fedora (sounds silly but it was a just-in-case experiment)
12) Tried disabling Apport

I think that pretty much covers everything I've tried.  I've been using Ubuntu since 09, so please hit me with the heavy stuff, I'm ready.

I'd like to point out that, apple USB keyboard is ok, networking is ok, sound is ok, streaming youtube and videos ok.  Everything seems normal except the USB mouse.  The USB mice are generic hardwired GE branded mice that you buy for $8 at Target.  There are no other extraneous operating systems on the computer.  Also, I have a 3dConnexion spacenavigator that /usr/bin/spacenavd complains with an "System program problem detected" boilerplate error only if it's unconnected at boot time, no complaints if it's connected (confirmed that it works in Blender).  I don't think this should be related but thought to mention just in case.

Additionally, mouse pointer appears for a few seconds during the login screen, but is unresponsive and disappears altogether.  Once logged in, mouse pointer is not present, and it does not seem to be a case of phantom/invisible pointer but functional: clicking all over the place has no effect.  Also, the mouse LED light is on while plugged in.

I have created (thankfully) a copy of the / partition on a backup USB drive in case I have to roll back to 14.10 utilizing gparted in a live USB session, but I'd really like to fix the mf'er since almost everything seems ok, except for this one critical issue.

Your kind help is much appreciated.

---

### Post by herlann-weiss on 2016-08-08
also I tried recording some events using xev, but still nothing.

---

### Post by herlann-weiss on 2016-08-08
also the mouse works while browsing all the BIOS menus, so it is definitely not a hardware issue.

---

### Post by jamesisin on 2016-08-08
Try creating a new user to see if a fresh profile functions.  Probably won't because your login screen isn't working but can't hurt to test.

---

### Post by herlann-weiss on 2016-08-08
I just created a new user and can confirm that this does not fix the problem.  There is no mouse with other users, nor with the guest account.

I did notice that by coincidence when the mouse pointer disappears during login, the volume top right pane (I forget what it's actually called) shows the red x muted figure.  Weird. To be clear, the sound is actually working normally, and is not actually muted. It just momentarily displays the muted popup notification thingy. It never used to do that before in 14.10.

---

### Post by herlann-weiss on 2016-08-08
I also tried installing KDE using sudo apt-get install kubuntu-desktop, however it finishes with broken package errors, and when I try to log into kde (which becomes available at the signin screen) the mouse is still unresponsive (and due to broken packages, KDE doesn't load properly, plus the USB keyboard is unresponsive). So basically I've narrowed down that the mouse is dead at the log-in screen, and forever after.  What does this mean?

---

### Post by herlann-weiss on 2016-08-09
alright peeps, if there's no solution I'll have to skip 16.04 and go back to 14.10 if there no ideas forthcoming.

---

### Post by herlann-weiss on 2016-08-10
also, mouse works in the 16.04 live usb environment.... wtf

---

### Post by herlann-weiss on 2016-08-10
Ok I give up.  I'm reverting back to the backup.

---

