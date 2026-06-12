---
title: "terminal won't open"
date: 2007-05-21
forum: General Help
---

### Post by muggins on 2007-05-21
When I try to open the terminal, computer blanks out . This is on a new install of xubuntu and the md5sum checked out positive.

---

### Post by phidia on 2007-05-21
Do you restart or can you do alt+ctrl+backspace to restart x?
Take a look at /var/log/messages, syslog & dmesg to see if there are any clues there.

---

### Post by muggins on 2007-05-22
I don't have to restart, the computer automatically returns to the login page by itself.

---

### Post by muggins on 2007-05-22
I installed gnome-terminal using synaptic, however I can't find it anywhere using appfinder. Where else would I look for it, apparently the terminal that comes with xubuntu is buggy on some computers.

---

### Post by AnRa on 2007-05-22
A simple way to solve that problem is setting de color depth to 16 bits. Yo can change this by modifying [FONT="Courier New"]/etc/X11/xorg.conf[/FONT].

---

### Post by muggins on 2007-05-22
How can I modify "/etc/X11/xorg.conf." if the terminal won't open, and I can't find the other terminal?

---

### Post by Outrunner on 2007-05-22
alt-ctrl-f5 to open a console(alt-ctrl-f7 to get back)

sudo nano /etc/X11/xorg.conf and scroll down to Defalt Depth or something like that...

---

### Post by anaconda on 2007-05-22
does the terminal start if you type: Alt-F2 and then 
gnome-terminal
to that?
or install some other terminal program with synaptic and run those..
eg. tilda, or konsole

---

### Post by AnRa on 2007-05-22
> **muggins said:**
> How can I modify "/etc/X11/xorg.conf." if the terminal won't open, and I can't find the other terminal?Alt + F2, then type "[FONT="Courier New"]gksudo mousepad /etc/X11/xorg.conf[/FONT]" ;)

---

### Post by muggins on 2007-05-22
Thanks for all the replies using Alt + F2 brought up the terminal and then setting the color depth to 16 bits in /etc/X11/xorg.conf solved my problem. Now I can open the terminal from the applications menu.

---

