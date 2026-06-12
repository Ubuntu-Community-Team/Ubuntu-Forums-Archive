---
title: "Calling Gnome-Do Alongside Unity Dash with Persistence"
date: 2013-07-11
forum: General Help
---

### Post by jamesisin on 2013-07-11
I have set up several machines running Ubuntu 13.04 and have followed some instructions for getting Gnome-Do to play nicely alongside Unity's Dash.  The trouble is the key-binding I set up for Gnome-Do (super-space) works until I reboot.  At which point it returns to disabled and I have to reassign the key-binding again.

What gives?  How can I ensure this remains persistent?

(Here are the instructions for those interested (just the gnome-do and ccsm parts):  [http://trumbitta.github.io/posts/unity-and-raring-tamed/](http://trumbitta.github.io/posts/unity-and-raring-tamed/) )

---

### Post by jamesisin on 2013-07-13
I have one machine which I upgraded from 12.04 --> 12.10 --> 13.04.  I installed Gnome-Do and set its key-binding before the upgrade.  I didn't make the CCSM change until just now (because it started spawning both when I called GD).  However, this particular machine keeps the GD key-binding persistent.  Why?

---

### Post by jamesisin on 2013-07-17
Just me and the crickets?

---

### Post by jamesisin on 2013-07-20
Ok, so I do not have an explanation only the solution.

If you find that your Gnome-Do will not retain the keyboard shortcut of super+space, set the shortcut to ctrl+space and reboot.  When you log in again GD will be persistently using the super+space shortcut.

What?

Yup.

---

### Post by jamesisin on 2013-07-20
My complete write-up...

[http://jamesisin.com/a_high-tech_blech/index.php/2013/07/gnome-do-and-unity-harmoniously/](http://jamesisin.com/a_high-tech_blech/index.php/2013/07/gnome-do-and-unity-harmoniously/)

---

### Post by jamesisin on 2013-10-27
It reverted later for no apparent reason.  If anyone has any solutions, let me know.

---

### Post by stinkeye on 2013-10-27
I don't use gnome-do but do use kupfer which is much the same minus the mono.
I can use the commands plugin to set a super+space shortcut.
Survives a reboot.

Im using Saucy.
Be warned though, I have found previously, shortcuts set in the commands plugin to just disappear for no reason
and using  super+space seems to have focus issues when the kupfer window is brought up.
ie typing is not being sent to the kupfer window.

Dont use the key combo myself....prefer  Rctrl+menu.

[COLOR="#FF0000"]EDIT[/COLOR] I can solve the focus issue by using wmctrl to focus kupfer. 
eg the ccsm command....
```
kupfer && sleep 0.1 && wmctrl -a kupfer
```
Something for you to have a look at anyway.

---

### Post by jamesisin on 2013-12-09
I have started using ctrl-space to summon Gnome-Do.  Thanks for offering Kupfer though it looks that it may have been abandoned (the developer site link in Software Center is 404).

---

