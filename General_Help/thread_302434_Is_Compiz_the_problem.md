---
title: "Is Compiz the problem?"
date: 2006-11-18
forum: General Help
---

### Post by championchap on 2006-11-18
I installed Compiz on my Dapper installation of Ubuntu yesterday, following the ubuntuguide instructions and since then I've noticed a couple of problems.

Amarok isnt opening, not really anyway.. the splash screen comes up and its there in the processes menu.. But I cant see it anywhere.

I also installed Firefox 2.0, and this next problem may be down to that.
On some websites, when I log in the browser just closes itself without warning.

Any thoughts on this guys?

---

### Post by lolocaust on 2006-11-18
Try running a non-xgl session (by disabling the startup scripts in "sessions" if that's what you're using) and see if the same things happen.

---

### Post by championchap on 2006-11-18
Ok, done, and still the problems remain.
Also, I noticed that when i tried to log out my system froze up.

Seriously guys any help to resolve this would be greatly appreciated.

---

### Post by Azakus on 2006-11-18
I've noticed that Beryl and Compiz both freeze on logoff. Since I'm the only one using the computer and I only logoff to dual-boot into Windows for games, I just do ```
sudo shutdown -r now
``` to restart.
I think the problem is Compiz going into paranoid mode when you try to logoff. Try killing compiz before logoff and see if it will work.

---

### Post by championchap on 2006-11-18
Ok, well the loging off dosnt seem to be much of an issue anymore.

But firefox is still giving me grief, im thinking its a problem with 2.0 to be honest. Might just have to revert back to 1.5.

Oh, and here is where I show my n00b side, but is there a system tray like in Windows?
I'm fairly sure Amarok is just hiding itself in a system tray.. but i cant see it.
See, when i first installed ubuntu i went about playing with pannels.. a lot.
And i accidentally removed the default bottom one.

So i built my own one to fufil all the needs i thought i have.

So where might Amarok be hiding? and how can i get him to show his pretty little face again?

Edit: Ahh sorry guys, I was just being stupid.. found the system tray.. just wasnt called what I expected. Thanks anyway guys! Sorry for the trouble

---

### Post by Azakus on 2006-11-19
I found another rather nasty way to really logout, and not shutdown the computer. Try ```
pkill X
``` That will kill the X server and send you back to the login screen. You'll get a crash report when someone logs in, but its just X telling you that you killed it.

---

### Post by David Corrales on 2006-11-19
You can also use ctrl+alt+backspace to kill the X server directly.
About amarok, could you try starting it from a console since you get a lot more output useful for troubleshooting.

---

