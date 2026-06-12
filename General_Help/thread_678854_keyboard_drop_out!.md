---
title: "keyboard drop out??!"
date: 2008-01-26
forum: General Help
---

### Post by kooldino on 2008-01-26
So for the second time since last night, I've been using my machine (last night on firefox and today on Pidgeon) when all of a sudden, the keyboard will stop responding.  Typing on the keyboard does nothing, the Num and Caps lock keys won't toggle the status LED...nothing.  However, the mouse and everything else work just fine.

If I log out, everything will work just fine from then on.

What in the world??

---

### Post by espressopigeon on 2008-01-26
It might be that the keyboard is broken. Have you had it very long?

---

### Post by kooldino on 2008-01-26
Maybe about a year.  Keyboards generally last me eons.  My gut tells me this isn't a hardware issue.

---

### Post by kooldino on 2008-01-27
Definitely not a hardware issue.  It happened again, and a CTRL+ALT+F2 brought me to a functional terminal.  When I did a CTRL+ALT+F7 to return to KDE, I still had no keyboard input.  It also didn't allow me to resize windows.  I have a feeling that this is some kind of compiz issue.

I tried to do a kwin --replace from my  CTRL+ALT+F2  terminal, but it couldn't communicate with the X server.

---

### Post by geraldm on 2008-01-28
If the keyboard was a USB type, then there might be a device disconnect on that port.
Check the file /var/log/messages /var/log/syslog for an error message on the disconnect.
If there is such a message, try plugging the keyboard onto a different USB bus.

Gerald

---

### Post by kooldino on 2008-01-28
If the pot dropped out completely, the status lights would turn off altogether instead of sticking.

Again, I really don't think it's a hardware problem.  Especially considering that CTRL+ALT+F2 will actually get me to a tty...

---

### Post by 47_MasoN_47 on 2008-01-28
I had an old Dell do something similar to that with USB keyboards.  I just put a PS2 keyboard on it instead and it worked fine.  It doesn't sound like it's completely hardware related, but if you have a PS2 keyboard you may want to try that out just to see if it does the same thing or if it is only USB.  That would at least narrow down the problem.

---

### Post by kooldino on 2008-01-31
Still happening...still not a hardware issue.  If it were, CTRL+ALT+BACKSPACE wouldn't work to restart X, and neither would CTRL+ALT+Fx.

This is driving me insane.

---

### Post by kooldino on 2008-02-11
Confirmed that this is 0% hardware related.

I logged into KDE, and hit Super+E (which I have bound to dolphin) and nothing happened.  I then noticed that my keyboard "dropped out" yet again.  

So I clicked through the System Settings menu and disabled "Restore Previous Session on login".  

I then logged out.  While the machine was logging itself out (and killing processes) suddently my dolphin windows popped up.  In other words, it recognized my Super+E keystrokes but didn't act upon them.  

I logged back in, went into /home/me/.kde/autostart and removed the script I had in place to do a "compiz --replace" on login.  

I'm guessing that when my sessions were being saved, this script was forcing compiz to run twice.  Somehow this was freaking things out, especially when it came to the Superkey which it monitors.

I then set it back to restoring my last session upon login.  This should work, but if it doesn't, I'll  autostart compiz during each login, and then disable compiz from being included in the session restore.

---

### Post by kooldino on 2008-02-11
Also, solving this issue also solved another issue I had...

[http://ubuntuforums.org/showthread.php?t=660226](http://ubuntuforums.org/showthread.php?t=660226)

---

