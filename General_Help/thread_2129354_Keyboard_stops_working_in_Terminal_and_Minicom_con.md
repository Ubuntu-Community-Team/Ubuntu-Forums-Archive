---
title: "Keyboard stops working in Terminal and Minicom config issues"
date: 2013-03-26
forum: General Help
---

### Post by mikeulator on 2013-03-26
I'm quite new to Linux and stumbling with these issues.

Haven't been able to find anyone with my exact keyboard issues online.  Whenever I run an app in the terminal (ssh or minicom) the keyboard will stop working.  For SSH (which is on my laptop) I can ssh to my home linux box and start something up... but after a while it stops working.  I'm not sure if it's when the screen locks or not.  With minicom, it wont let me type once connected.  I can do the Ctrl+A and any of the minicomp commands but I can't type at the prompt.  That's if I get one, I only seem to get a prompt if I connect via minicom and then reset the Cisco ASA 5505 appliance and let it bootup.  At first I thought maybe it was the USB keyboard plugged in via an IOGear KVM but I plugged in a PS2 keyboard and had the same issues.  Earlier I tried launching minicom with sudo and when it failed and took me back to the terminal, I couldn't type anything.  The cursor freezes while I'm typing and when I stop it goes back to blinking but doesn't put any characters at the prompt.

And for other issues with minicom.  It now will not load using the minirc.dfl file.  It keeps loading with a bad configuration file but I can't find out where those settings are coming from.  I removed minicom and deleted any .dfl files associated with it, as well as any other files that a "minicom" word search in the filesystem yielded.  After reinstalling it's doing the same thing.  It wont even load a custom configuration file if I make one.  If I pass it as the parameter when launching minicom it loads the "factory default" settings for minicom.  It doesn't matter how many times I run "sudo minicom -s" and make the right changes, then save as dfl, it wont read from it.  If I gedit the minirc.dfl file it has all the right settings!  This happened in the middle of it working.  I had changed the Hardware/Software modes to Yes's and No's to get the keyboard to work.  Also, while trying to troubleshoot issues I came across a site that said if you get gibberish across the screen to remove everything in the "Init String" in Modem and Dialing Parameter Setup of the minicom menu.  Perhaps clearing that out did this?  Putting the string back in (I took a screen grab) doesn't seem to fix it.  I don't know if it was because I changed the baud (to fastest), turned software flow control on, or deleted the Init string.   I can't find a way to completely remove minicom so I can reinstall, or force it to reset itself back to default settings.

Rebooting did not solve :P

I'm running 12.04 64bit with all the updates.  Installed minicom through software center.

Thanks.

---

### Post by mikeulator on 2013-03-26
Well I'm not sure what happened now.  When I go thome today there were 20 or so updates for me so I installed them.  I then uninstalled Minicom again, cleared out my tmp folders just in case, rebooted and then reinstalled.  It was STILL loading some random configuration and not the default.  I saved off a custom config file again and this time I got it to load.  I was also able to type in the terminal for the appliance!  This random keyboard thing is annoying.  If anyone has any ideas on that I would appreciate it.  Also if you have any on this cached settings that minicom is using...

---

