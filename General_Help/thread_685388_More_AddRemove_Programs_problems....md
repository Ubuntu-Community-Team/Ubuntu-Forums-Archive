---
title: "More Add/Remove Programs problems..."
date: 2008-02-02
forum: General Help
---

### Post by NEUR0M4NCER on 2008-02-02
I've had problems with gnome-app-install before, and was bothered by it so much that I did a fresh Ubuntu install (as documented in this thread: [[COLOR="RoyalBlue"]gnome-app-install closes at 'Loading Programs'[/COLOR]]("http://ubuntuforums.org/showthread.php?p=3446299#post3446299")). Seems it's not working again, and this time I don't want to do a fresh install, 'cause there's so much stuff on here now.

So here's what I get when in a terminal:

```
neur0m4ncer@neur0m4ncer-desktop:~$ sudo gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 30, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/AppInstall/activation.py", line 435, in main
    from AppInstall import AppInstall
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 64, in <module>
    import dbus
  File "/var/lib/python-support/python2.5/dbus/__init__.py", line 96, in <module>
    from dbus._dbus import Bus, SystemBus, SessionBus, StarterBus
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 45, in <module>
    from dbus.bus import BusConnection
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 43, in <module>
    from dbus.connection import Connection
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 38, in <module>
ValueError: bad marshal data

```

I can't find anything relating to 'Bad Marshal Data' as-well as Add/Remove - there was a post somewhere about corrupt python instructions, but it didn't seem relevant...

Synaptic still works, as does apt, but I don't like the idea of something not being 'right' on my 'puter so if anyone's got any ideas, i'd be very grateful. Let me know if you need any further info to diagnose this annoyance :)

Regards

---

### Post by SpiderGorilla on 2008-02-02
There's a lot that can go wrong from Fresh Install to this sort of thing. You installed apps, right? What method did you use to install everything? Because right now, Ubuntu is pushing towards using Add/Remove and/or Synaptics Package Manager in lieu of apt-get'ing or self-compiling, both of which have a tendency to break dependencies if you aren't aware of every last dependency needed.

I'm just curious as to which version of Python you've got on your system. Using nothing but the regular methods (save for some black terminal magic to force DVDs to play), I've got the following Python installed:

Python 2.5.1 (r251:54863, Oct  5 2007, 13:50:07) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2

Have you got a newer or older version?

Also -- your previous version looked more like an issue with compiz-fusion rather than python, which appears to be the current issue.

I'm not saying I can fix it, but maybe I can ask enough of the right questions for someone with a better idea to come through and get everything back on track for you.

---

### Post by NEUR0M4NCER on 2008-02-03
I'm afraid i've used every method to install stuff - Synaptic, Apt, Add/Remove, Self Compile... Guess I should be more careful.

Python appears to be the same version as yours:
```
neur0m4ncer@neur0m4ncer-desktop:~$ python
Python 2.5.1 (r251:54863, Oct  5 2007, 13:36:32) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.

```

So yeah, i'm an install fiend - even put K & X on to see what they were like (not a fan), but the Add/Remove issue began before I installed them. Would (or should) K's Adept work properly whilst running (Gnome) Ubuntu?

Thanks in advance!

---

### Post by NEUR0M4NCER on 2008-02-06
No - i've got no idea either. I suppose Hardy's out in a couple of months, i'll just have to see if the upgrade solves the problem.

---

### Post by NEUR0M4NCER on 2008-02-07
... but it'd be cool if anybody had any thoughts about this problem?


Cheers

---

### Post by Ink-Jet on 2008-02-07
What's this about using Add/Remove + Synaptics over apt-get itself?

I always thought they were just front-ends for apt.

---

### Post by NEUR0M4NCER on 2008-02-07
... well yeah, that's what I thought, but apt-get works, Synaptic works... Add/Remove doesn't. Go figure. Apparently, it's something to do with Python, but as much as i've learned about Linux in the last six months, I have no idea how to go about checking or repairing these things.

---

### Post by toomuchcomputertime on 2008-02-08
Can anyone help on this issue. I can't use the add and remove programs (in the application menu). It all goes fine until I click apply. After that, it just locks up. I am new at linux.

---

### Post by NEUR0M4NCER on 2008-02-08
Further to the original issue, the update manager panel icon doesn't work properly either; for a while it only worked with right-click > install all updates, but doesn't work at all now.

Thought this might help any possible diagnosticians out there...


Regards

---

### Post by Bablefish on 2008-02-08
also check out [www.getdeb.net](www.getdeb.net)

---

### Post by NEUR0M4NCER on 2008-02-09
... is that actually a suggestion, or are you just advertising? If you read the posts above, you'll see that I can still install and un-install stuff, I just can't do it through Add/Remove Programs.

Thanks anyway

---

### Post by NEUR0M4NCER on 2008-02-14
Still having no joy with this problem - guesses welcomed :)

---

