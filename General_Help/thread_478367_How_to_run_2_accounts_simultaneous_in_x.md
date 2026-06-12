---
title: "How to run 2 accounts simultaneous in x?"
date: 2007-06-19
forum: General Help
---

### Post by nalinde on 2007-06-19
Well as my headline states, how do i run 2 accounts in X?

Let me refine this a bit;
As i'am sitting and surfing in one account i want to be able to push ctrl + alt +F2, log in to my other account and then be able to also run that account in a graphical environment so i can surf with my precious Firefox and other stuff. Now... HOW can i do that ... Pleas help me...!

---

### Post by dreadlord_chris on 2007-06-19
> **nalinde said:**
> Well as my headline states, how do i run 2 accounts in X?

Let me refine this a bit;
As i'am sitting and surfing in one account i want to be able to push ctrl + alt +F2, log in to my other account and then be able to also run that account in a graphical environment so i can surf with my precious Firefox and other stuff. Now... HOW can i do that ... Pleas help me...!

In KDE I click my Kmenu > My user name > Start a new Session. This brings me to the login screen - to go back to my other session I hit ctrl-alt-f7

Pretty sure it's something similiar in GNOME

---

### Post by energiya on 2007-06-19
> **dreadlord_chris said:**
> In KDE I click my Kmenu > My user name > Start a new Session. This brings me to the login screen - to go back to my other session I hit ctrl-alt-f7

Pretty sure it's something similiar in GNOME

Yes, there is. You could also use the nested window...

---

### Post by Rui Pais on 2007-06-19
hi, 
check [my suggestion]("http://ubuntuforums.org/showpost.php?p=2791398&postcount=6") and others on this thread [here]("http://ubuntuforums.org/showthread.php?p=2792688").

hth.

---

### Post by nalinde on 2007-06-19
Awesome!! Thanks for all the awnsers guys/girls!

Tested the fast switch applet and it seemed like an nifty little app.
Also tried the alternative with modifying the gdm.conf with less scucess.
The thing is that my X seems to crash when i switch back from the "originate" account.
Guess it's the Nvidia-drivers, version 100.14.09? that don't manage it..

Anyways thanks for the support..

---

### Post by dreadlord_chris on 2007-06-19
> **nalinde said:**
> Awesome!! Thanks for all the awnsers guys/girls!

Tested the fast switch applet and it seemed like an nifty little app.
Also tried the alternative with modifying the gdm.conf with less scucess.
The thing is that my X seems to crash when i switch back from the "originate" account.
Guess it's the Nvidia-drivers, version 100.14.09? that don't manage it..

Anyways thanks for the support..

I'm using the latest NVIDIA drivers (GeForce 7300) - lately I've been running 1 session in KDE as my normal desktop & 1 Enlightenment session with an XP virtual session running full screen in it. I have no problems switching back and forthy between any of them (e17 occasionally crashes - but that's what I get for running svn snapshots, besides it recovers nicely)

So, I don't think it's that the drivers won't/don't handle it.....

---

### Post by louieb on 2007-06-19
Feisty has a problem with Ctrl+Alt+F# switching.  Both my laptop and desk will freeze up from time to time. and I am running  a vanilla install on both. There is a but report on it.   [Bugs in Ubuntu]("https://bugs.launchpad.net/ubuntu")
BTW: Haven't had any problems using c+a+f switching in Dapper.

---

### Post by Rui Pais on 2007-06-20
> **dreadlord_chris said:**
> I'm using the latest NVIDIA drivers (GeForce 7300) - lately I've been running 1 session in KDE as my normal desktop & 1 Enlightenment session with an XP virtual session running full screen in it. I have no problems switching back and forthy between any of them (e17 occasionally crashes - but that's what I get for running svn snapshots, besides it recovers nicely)

So, I don't think it's that the drivers won't/don't handle it.....

he he, i'm running this with e17(me) and gnome (wife,kid). 
The only times i had problems (black screens) is when i activate bling on e (a simple F1 solves the issue) or composite managers on gnome...

but maybe nalinde is right about the latest nvidia drivers, i still use 1.0.9755 here. 
I will check in my tests installation before any upgrade to nvidia drivers.

---

