---
title: "Ctrl+Alt+F2 = Black Screen"
date: 2007-04-02
forum: General Help
---

### Post by Pru on 2007-04-02
I reinstalled Ubuntu Edgy this morning and now when I press ctrl+alt+f2 so I can install my graphics drivers it goes to a blank screen.

I never had this problem before, i tried reinstalling again but that didn't do anything. Please help, I don't even know what to google for

---

### Post by FluffyElmo on 2007-04-02
Hit *Ctrl+Alt+F7* and it should take you back to your desktop. Ctrl-Alt-F2 should show you a login prompt at least, *Ctrl+Alt+Any Function* key will open a new text terminal.  F7 is the terminal where the desktop launches...

---

### Post by Pru on 2007-04-02
That's what used to happen untill I reinstalled it. 

It used to ask me for log in details but now it's just a black screen and ctrl+alt+f7 wont work when it's gone black.

---

### Post by FluffyElmo on 2007-04-02
What video chip-set do you have? Here is a similar sounding issue with an i810 chipset:
[http://ubuntuforums.org/showthread.php?p=531943]("http://ubuntuforums.org/showthread.php?p=531943")

Also since you're trying to install updated drivers anyways, maybe booting temporarily with video=vga or video=vesa might solve the problem for you to get things installed? To do this temporarily (from another post somewhere):
> Reboot
When Grub splashscreen comes up, press an up/down arrow key to stop the clock.
Highlight the "title" you want to boot and press 'e' to edit
Highlight the line that starts with "kernel" and press 'e' to edit
Add 'video=xxx' parameter at end of line and press enter to accept the change
Press 'b' to boot

---

### Post by FluffyElmo on 2007-04-02
I forgot the easiest way to get to a terminal, just reboot and select the first option with '*(recovery mode)*' after it. Usually the second choice. This should let you install your video driver and hopefully that will solve the problem...

---

### Post by Pru on 2007-04-02
Luckily I still had my xorg.conf in my email from something I did before I reinstalled and I just copied and pasted it and now it works

---

### Post by FluffyElmo on 2007-04-02
Excellent! Sorry I couldn't help but glad you were able to solve things quickly :)

---

