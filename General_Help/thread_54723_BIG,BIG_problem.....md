---
title: "BIG,BIG problem...."
date: 2005-08-05
forum: General Help
---

### Post by potajaco on 2005-08-05
people help me.. 
i have ubuntu installed and i was doing apt-get install x-window-system-dev , and boom, power energie is down.  :-? 
next time, wen i try to start computer he give me this mesage: 

Your session only lasted less then 10 sec. If you have not logged out yourself this could mean there are some problems ..... (there was writed some more things, but i could not write anymore)  :)  

when i click details i get this mesage : 

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp 

/etc/gdm/ProSession/Default :running: /usr/bin/X11/sesreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdr/:0.Xservers" -h "" -l ":O" potajac" 

**(gnome-session:7905): warning ** 
Unable to read ICE authority file /home/potajac/.ICEauthority 

does anyone know whats wrong with this?

P.S.
i dont speak english very god.. i hope that you understand my question  :)  :)

---

### Post by jasmuz on 2005-08-05
Login via a terminal (ctrl+alt+f1), put your name and password, then run:

rm .ICEauthority 

and now you will be able to login normally.

---

### Post by potajaco on 2005-08-06
thank you man

this solves the problem  :)  :)  :)

---

