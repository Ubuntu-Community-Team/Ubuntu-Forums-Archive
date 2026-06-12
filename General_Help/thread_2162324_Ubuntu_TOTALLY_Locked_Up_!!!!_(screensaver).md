---
title: "Ubuntu TOTALLY Locked Up !!!! (screensaver)"
date: 2013-07-14
forum: General Help
---

### Post by Lewis Balentine on 2013-07-14
damned screen saver again.
I I am running the version of Ubuntu that came with unity.
I replaced that awful UI with gnome immediately.
So there is no handy way to tell the version.

Problem has always been the unwanted, unneeded and totally irritating screensaver.

Tonight I saw a post how how to remove it using "sudo appget ...."

So I did that.

Now it has gone into screensaver mode and will not accept any user input what-so-ever.
I have an long running app on that machine and now I am going have to pulll the plug and corrupt the data.

Here is the Question:
Once I get the machine  restored how can I safely and COMPLETELY remove all screensavers?

---

### Post by buzzingrobot on 2013-07-14
Gnome Shell has no screensaver installed by default.

What it does have is a "Lock"  screen that can be toggled on or off or otherwise adjusted in system settings.

The version of Gnome you are running can be seen via "Details" in settings.

When you removed the "screensaver", what, exactly, did you enter on the command line? Did you notice if that action also deleted other, dependent, packages? (Warnings would have been displayed.)

---

### Post by Lewis Balentine on 2013-07-14
I am getting old and senile.
If I could have remembered exactly what i typed then I would have put that in the post above.
I got the version after I shut reset the machine.
It is gnome-fallback.
I also found the controls for screen blanking under System Settings, Brightness and Lock.
I would expect to find it under Display or Power or something along those lines --- not something that begins with brightness.

Anyway it is totally disabled now.
I am starting to use ubuntu to run draftsight scripts on a vmware virtual machine.
They actually run better in that environment with 2 CPUs that under Windows7 on the host machine with 4 CPUs (go figure).
Anyway I like to be able to observe the progress without constantly moving the mouse around so the screen lock is a major inconvenience.

---

### Post by buzzingrobot on 2013-07-14
There's a little app called Caffeine that apparently can be used to temporarily disable screensavers and such.  No idea if it would work for your setup, tho.

I'm not on Gnome at the moment, and haven't used gnone-fallback, but I *think* I remember a lock setting in the Privacy settings, as well.

---

### Post by MrSteve on 2013-07-14
the way i stopped the screen lock was to install xscreensaver
after setting xscreensaver up i removed the gnome screen saver (lock screen)

12.04 LTS has been running fine on 2 home systems since ...

---

