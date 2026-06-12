---
title: "I Can't Get the GUI Running Once I Stop It..."
date: 2008-02-12
forum: General Help
---

### Post by kmullinax on 2008-02-12
So I was trying to play around with "readahead" last night and part of the instructions require you to log out, CTRL+ALT+F1 into the terminal, log in, enter some code and then ALT+F8 to get back into Gnome.

My problem is: Ubuntu starts up great, and I can log into Gnome and everything just fine.  However, once I log out and switch to terminal mode, pressing ALT+F8 doesn't work.  It tries to start Gnome and then just stops.  It doesn't freeze, because I can still CTRL+ALT+F1 back to the terminal, but it won't load the GUI, and I eventually have to reboot the computer.

Am I doing something wrong?

---

### Post by yabbadabbadont on 2008-02-12
Alt-F7 is the correct key combination to return to the GUI.

---

### Post by x1a4 on 2008-02-12
Have you changed on which VT the X server is running?  If not, it should be Ctrl+Alt+F**7**.  If that's not it, the X server should give you an error.  What is it?

---

### Post by kmullinax on 2008-02-12
Ok, well that works with ALT+F7.
Huh.
Thanks!  At least I can get back into Gnome...:)
So now I'm confused.
The instructions I was following were saying to log in at the terminal and then press ALT+F8 to start up the GUI *without logging in again.*
So maybe that's where the problem is?
Is ALT+F8 supposed to start up Gnome without needing to log in if you're already logged in from the terminal?

---

### Post by yabbadabbadont on 2008-02-12
Nope.  What can be done though, is to start a new instance of X on tty8.  Then switching to Alt-F8 would change to that new instance.  Some people do this with fullscreen games and such.

---

### Post by x1a4 on 2008-02-13
When you press Ctrl+Alt+F# you are not closing anything, you're simply switching virtual terminals (VTs).  If you switched from an X session it continues to run.  

Back in the day when mainframes were king, they had many of so called dumb terminals (keyboard & display) attached to them, and needed a software way to differentiate between the different terminals as each user was doing something different.  As the years went by, this piece of code remained in Unix (and later Linux as well) systems and translated into so called virtual terminals.  By default *buntu has 7 VTs.  The first 6 running getty's (consoles) and the seventh an X display.  You are of course free to change that.  I, for example, am running consoles on VT1-4, X on VT5-7, VT8&9 free for friends' and family's accounts when they come to visit, user logs on VT10, daemon logs on VT11 and kernel logs on VT12.  

There can be twice as many VTs as there are function keys on the keyboard.  I have 12 so can have 24 virtual terminals.  The first 12 accessed using LCtrl+LAlt+F1-12 and the other 12 using LCtrl+RAlt+F1-12.  

To change a virtual terminal using the command line execute **chvt #**.  Where # is the number of the VT you wish to change to. **chvt** is short for change virtual terminal and is the program that's called when you press Ctrl+Alt+F#

---

### Post by kmullinax on 2008-02-15
Wow, that explains a LOT.  Thanks for the useful information!

---

### Post by x1a4 on 2008-02-16
> **kmullinax said:**
> Wow, that explains a LOT.  Thanks for the useful information!

You're welcome.  Be sure to mark this thread solved.

---

