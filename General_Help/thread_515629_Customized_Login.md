---
title: "Customized Login"
date: 2007-08-02
forum: General Help
---

### Post by dmfield on 2007-08-02
I'm not sure if there is a gui, which will let me do this, I think not, however i'm looking for a solution to an issue..

**Scenario**

[INDENT]I have a Dell 1501 with an ATI 200m (Didn't buy it with Ubuntu installed) with the Laptop i got an external flatscreen, which i am able to make use of quite happily using  the "BigDesktop" setup within the /etc/X11/xorg.conf so i power on the laptop, and away we go.. Dual head display.. Nice..

however, when i go into work, the dual screen still kicks in, just with physical monitor there..
[/INDENT]
[B]
What would i like to do?[/B]

[INDENT]I would like to setup a script, which runs instead of whatever starts GDM up 

The script would perform the following task...

Ask the question "Do you wish do use the Dual Head display?" (Y/N)

If i say yes, copies /etc/X11/xorg.conf.dualhead over the existing xorg.conf
If i say no copy /etc/X11/xorg.conf.single over the existing xorg.conf

Then launch GDM, and allowing me to login..

I'm actually not fussed if i have to login at a text prompt, then the above script runs, or the script runs, and then get a gui login page..
[/INDENT]

**My Questions?**

[INDENT]Is it possible to run a choice script, in place of the GDM script, without having logged it?
If so, what file do I have to edit in order to stop GDM running, and call my script instead?

If not, how do i stop GDM working on login, drop to a Text prompt?
Where would i put the script to run after i login? ~./baschrc ?
[/INDENT]
**Some Further details**

OS - Ubuntu 7.04 x86_64
Graphics Card = ATI 200m
GDM


:)As usual any assistance would be appreciated assistance.. And if anyone thinks they know a better way, i'm open to suggestions...

---

### Post by dmfield on 2007-08-02
Some additional information:

I have switchconf working

i have /etc/switchconf/dual/etc/X11/xorg.conf for dual screen setup
I have /ext/switchconf/single/X11/xorg.conf for single screen setup

so:

sudo switchconf dual               # Puts the Dualscreen config into operation after a CTRL ALT BACKSPACE

sudo switchconf single             # Puts the maching into a working single screen system after a CTRL ALT BACKSPACE

So maybe i'd be better off dropping to a prompt for the login, and then when i login as the default user, it offers me a choice, and then runs one of the two, then

sudo /etc/init.d/gdm start

Any takers?

---

