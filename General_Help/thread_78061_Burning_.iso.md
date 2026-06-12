---
title: "Burning .iso?"
date: 2005-10-17
forum: General Help
---

### Post by chadwick359 on 2005-10-17
Can anybody tell me what I need to do to burn an .iso? Can I just burn it, or do i need to mount it virtually and burn it? If so, what kind of program/command should I be using to do so? Thanks for any help in advance.

---

### Post by Murgle on 2005-10-17
there should be an option in the right click menu that says burn this image or something like that, alternatly I know gnome-baker is a cd bruning utility

---

### Post by bluck on 2005-10-17
also check out `man cdrecord`

the terminal is your friend ;)

---

### Post by ecobuntu on 2005-10-17
cdrecord --scanbus

cdrecord -v dev=<resultsfromscanbus> foobar.iso

---

### Post by ecobuntu on 2005-10-17
Also if you have K3B installed, there is an option to make image.  Use this option

---

### Post by teevee on 2005-10-17
Yeah, right-click on an ISO in Nautilus is what you want. Or gnomebaker (available from universe) or KDE's K3B if you want a more powerful burning application.

---

### Post by bluck on 2005-10-17
[QUOTE=teevee]Yeah, right-click on an ISO in Nautilus is what you want. Or gnomebaker (available from universe) or KDE's K3B if you want a more powerful burning application.[/QUOTE]

agreed. k3b is actually really great if you dont like diggin into the terminal.

---

### Post by teevee on 2005-10-17
Oh, Nero is also available for Linux, but never tried it.

[http://www.nero.com/en/NeroLINUX.html](http://www.nero.com/en/NeroLINUX.html)

---

### Post by bluck on 2005-10-17
[QUOTE=teevee]Oh, Nero is also available for Linux, but never tried it.

[http://www.nero.com/en/NeroLINUX.html](http://www.nero.com/en/NeroLINUX.html)[/QUOTE]

why bother when k3b is free and does it all? :)

---

### Post by ecobuntu on 2005-10-17
yeah K3B is nice but I still like cdrecord the best!  Give me a terminal and I'm happy.  Probably why I use apt-get at the command line instead of synaptic or all the other fancy nice GUIs

---

### Post by SickTwist on 2005-10-17
[QUOTE=chadwick359]Can anybody tell me what I need to do to burn an .iso? Can I just burn it, or do i need to mount it virtually and burn it? If so, what kind of program/command should I be using to do so? Thanks for any help in advance.[/QUOTE]

If you're doing this in Ubuntu, right-click (or left-click if your using mouse in left-handed mode) on the ISO file in GNOME and select "Write to Disc..." from the context menu. Then, verifiy that the correct drive is selected, select a write speed (slower is generally more safe but will take longer to complete) and click "Write".

Let us know if you need more help.

---

