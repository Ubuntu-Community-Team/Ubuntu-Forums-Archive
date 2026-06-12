---
title: "Hangs on Desktop enviornment startup"
date: 2007-07-01
forum: General Help
---

### Post by sublimation on 2007-07-01
So I was running ubuntu under Xgl with Compiz-Fusioin running. Has been running quite well for sometime. I was playing some music, running VMWare, and surfing. 

Apparently this was all a little too much, as my system stalled. :(
I used ctl-alt-backspace to kill X and return to login, and now it hangs whenever I start up. I can run fine when I disable startup services, but I haven't been able to get it to run normally since. It always hangs with the Ubuntu splash screen when it's supposedly loading Metacity. 

Any tips for how to get my desktop up and running again?
All suggestions are greatly appreciated

---

### Post by DagMan on 2007-07-01
Have you started out with turning off compiz yet?

---

### Post by Crafty Kisses on 2007-07-01
> **sublimation said:**
> So I was running ubuntu under Xgl with Compiz-Fusioin running. Has been running quite well for sometime. I was playing some music, running VMWare, and surfing. 

Apparently this was all a little too much, as my system stalled. :(
I used ctl-alt-backspace to kill X and return to login, and now it hangs whenever I start up. I can run fine when I disable startup services, but I haven't been able to get it to run normally since. It always hangs with the Ubuntu splash screen when it's supposedly loading Metacity. 

Any tips for how to get my desktop up and running again?
All suggestions are greatly appreciated

Try booting in verbose mode, to see where it hangs.

---

### Post by sublimation on 2007-07-01
::UPDATE::

Starts in KDE fine, though since I have nothing set up in KDE there's no network support etc. All attempts at starting in X fail. It always fails when the Ubuntu splash screen lists metacity as loading. But in my X it typically doesn't load metacity at all... and I just have to wait a couple of minutes for the compiz start script to run. 

now running in failsafe Gnome. 

How do I run it in verbose to find out where it hangs?

---

### Post by sublimation on 2007-07-01
tried to run verbose via <ctl><alt>F1 while loading xgl. resulted in a crash. 
Functionally all I have right now is failsafe gnome. Can I do a reinstall of Gnome or Xgl? should I simply go with uninstalling compiz? How do I return metacity to handling windows by default?

---

### Post by sublimation on 2007-07-01
uninstalled compiz, uninstalled and reinsalled xgl. Now both gnome and xgl hang differently. Instead of sitting at the splash screen, it now seems as though it loads completely, but when it does my screen goes completely blank. 
Hard to say if it is running, just with no display.
now that we're running into hardware issues, I'll mention I'm on a HP inspiron dv8000 laptop with an ATI graphics card that's currently running fine off the restricted driver (in failsafe gnome).

going to try and determine if anything can be run while the screen is blank.
then sleep :D
I'll check back tomorrow

---

### Post by DagMan on 2007-07-01
is it a blank black screen or a blank white screen?

---

### Post by sublimation on 2007-07-02
Blank black screen. It's not the "white screen of death" I'd fixed that problem earlier. 
It appears as it does when Ubuntu has shutdown issues, and simply doesn't tell the hardware to turn off.

---

