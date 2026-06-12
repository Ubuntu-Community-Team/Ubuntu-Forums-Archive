---
title: "[SOLVED] What Happend to GUI? Booting to command line"
date: 2007-06-16
forum: General Help
---

### Post by CaptainSteel on 2007-06-16
I updated my ati driver and when i restarted my computer Kubuntu now boots to command line. I have no clue how to use tty1 command line. How do i get the GUI back? Thanks

---

### Post by kimusabi on 2007-06-16
Odd. Try logging in and typing in 
```
startx
```
to bring back the GDM. If it comes back saying "Already running. Aborting!" then hold down Ctrl and Alt then hit F7. That'll bring you back to your Login screen. Hopefully.

Otherwise you'll have to reconfigure your xorg by typing in
```
 sudo dpkg-reconfigure xserver-xorg
```

Hope that helps.

---

### Post by CaptainSteel on 2007-06-16
Thanks Kimusabi!

The command worked great!
 sudo dpkg-reconfigure xserver-xorg

---

### Post by Brightbelt on 2007-06-16
Hi,
I have an ATI and have been thru the same thing, although I am on Gnome. But I think this advice should work.

The ATI issue is a sticky one with Ubuntu. This is what worked for me:

-At the command prompt, type
```

gksudo dpkg-reconfigure xserver-xorg

```

If the an error comes in and ruins your command prompt for a second, try again until you get this command running. 

Follow the GUI reconfigure wizard, and pick the defaults whenever you're unsure of anything, However, make sure your first choice (the driver) is 'Vesa'. That may seem anti-intuitive since you have an ATI card and ATI is on the list there, but Vesa is the right choice. 

Later, you'll see the list of resolutions from which to choose. Some say all you have to do is pick the highest one and unmark all the others (use the space bar to choose or unmark). Also look in your monitor manual for your Horizonal rate and your vertical refresh rate - you may have to enter these.

I hope this helps - like I said, I have gnome and not KDE (Kubuntu), but I think the xservers are the same.

Good Luck, Frank B.

---

### Post by abasel on 2007-06-17
I don't have the same initial problem, but to have an issue with "startx"

The following:
gksudo dpkg-reconfigure xserver-xorg

worked just find but when I try run "startx" I get the following:

-bash: startx : command not found

What am I doing wrong?

---

