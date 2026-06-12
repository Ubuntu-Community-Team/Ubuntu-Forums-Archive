---
title: "gdm freeze after each logout"
date: 2006-10-30
forum: General Help
---

### Post by mitjab on 2006-10-30
Every time i logout gdm freeze. Every time when i logout from gnome and i must see gdm i see white screen. 

why?

---

### Post by mwolfe on 2006-11-15
i have the same problem here.. when i click the button that usually brings up a dialog box where i can logout, shutdown, restart etc, it just logs out and then freezes up with a blank screen.. It used to do this sometimes but now it always does it..

Can't figure out how to fix it. Any ideas?

---

### Post by Falcorian on 2007-01-18
I get the same problem in Ubuntu Edgy. When I logout I sometimes get a white screen (although the login text box appears, and is slightly lighter than the surrounding white). I can't type in the box though, or do anything else with the screen.

I can however switch to one of the background terminals using ctrl+alt+F1, sort of. When I do this instead of the terminal, I get a blue square where the 640X480 (or whatever size the text area normally is) with orange stripes that flashes. I then can not switch to any other terminals, or back to the login screen (which is all white anyway). I can't restart x using ctrl+alt+backspace.


Any ideas? I wish I could tell you when it pops up, or what programs have been installed since, but I can't, it happens sometimes, and I don't remember when it started, and can't reliably reproduce it.

EDIT: I'm trying the bug fix here: [https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/50535](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/50535)
I'll keep you posted. ;)

---

### Post by MattJ100 on 2007-02-05
Any luck? I get the EXACT same problem as you, Falcorian, just as you describe.

I have an ATI Radeon, and the Edgy xorg-driver-fglrx driver installed. I never had this problem with Dapper, but then I never got my ATI card working in Dapper :P

Telling GDM to restart X did not seem to help for me, this could be because on my PC multiple users are frequently logged in at once. The last one to log out (and therefore the one that gets taken back to GDM) experiences the freeze of the whole PC.

---

### Post by Ramses de Norre on 2007-02-05
I've got the same white screen sometimes when I log out of gnome. Not always though and if it does occur my whole machine freezes up and I need to hard reset.

I'm on edgy with an ati x600 and the fglrx driver from the repos.

---

### Post by krantix on 2007-02-09
happens to mee to... 

it must have something to do with ATI... mine is a Mobility Radeon 9000

(i've managed to have beryl+XGL working fine)...

to avoid gdm freeze i usually exit with CTRL-ALT-backspace

and then login again from there...

---

