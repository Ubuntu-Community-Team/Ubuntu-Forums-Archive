---
title: "Terminal Not Working!!"
date: 2006-08-26
forum: General Help
---

### Post by simoncoul on 2006-08-26
I installed the kiba dock (which rocks btw), but now when I go to launch the terminal it says "starting terminal" in the bar at the bottom and then it goes away and nothing happens.   This is making it very hard to do thing lol, so if someone could help me out that would be great!

Thanks

---

### Post by croak77 on 2006-08-27
What is kiba dock? You can't launch any terminal from Ubuntu? Alt-F2, type gnome-terminal.

---

### Post by peabody on 2006-08-27
> **simoncoul said:**
> I installed the kiba dock (which rocks btw), but now when I go to launch the terminal it says "starting terminal" in the bar at the bottom and then it goes away and nothing happens.   This is making it very hard to do thing lol, so if someone could help me out that would be great!

Thanks

When all else fails, press Alt+F2 and type xterm.  xterm is always available.  From within that terminal type gnome-terminal and press return.  Tell us what it says.

---

### Post by adam.tropics on 2006-08-27
If you are using the quinn repo, and haven't done so since recent updates to libvte4, you may want to open xterm and run

sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4

worked for me anyway..

---

### Post by simoncoul on 2006-08-27
I am unable to run the terminal from ubuntu and the dock.  I tried xterm and it doesn't do anything when I enter gnome-terminal, xterm just closes, when I try to launch it from ubuntu at least something shows up at the bottom.   And I did repair the quinn repo thing already.

Any other ideas?

Thanks

---

### Post by peabody on 2006-08-27
xterm just closes?  That's definitely not good, something sounds wonky on your system.  Are you able to launch anything else from xterm?  firefox for instance?

---

### Post by simoncoul on 2006-08-27
yes I can launch things from xterm, and everything else launchs is there a way to uninstall and reinstall terminal maybe a package is broken ( but I checked in synaptic and it said nothing was borken).

Thanks

---

### Post by simoncoul on 2006-08-27
Alrite I did that and now it is working!   Removed "gnome-terminal" & "gnome-terminal-data" then installed them again and it worked after an X restart!

Thanks for the help!

---

### Post by mwpmwjcp on 2008-01-23
My gnome-terminal is also broken. xterm still works

I tried completely removing gnome-terminal and gnome-terminal data in the synaptic package manager, restarting the computer and then reinstalling and it still doesn't work. I see the starting terminal notification in my task bar and then it just disappears... 

Any suggestions?

---

### Post by mwpmwjcp on 2008-01-23
I restarted a couple of times due to nvidia issues and suddenly gnome-terminal is working again...

Thanks anyway...

---

