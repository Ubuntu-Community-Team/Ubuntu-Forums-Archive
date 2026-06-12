---
title: "i screwed up, please help ubuntu jedi's"
date: 2008-02-11
forum: General Help
---

### Post by mfaust731 on 2008-02-11
ok,i got ubuntu 7.10 installed and  i had everything good.  then i decided as the machine is a headless server why run gnome, and tried to disable it.
I have a program installed that transfrers my tivo recordings to it, which is called galleon. I set it to run on boot, then i went to a term and gave it a 
sudo update-rc.d -f gdm remove

this did indeed disable x from starting up, which i wanted.
however now at the local terminal, after the boot process finishes mu galleon program starts and that is all i see.
I do not get a login prompt, all i see at the local display is " galleon is now ready"
i have tried "ctl-alt-f whatever, nothing happens.

i can ssh into the machine from my laptop, and i have tried " sudo update-rc.d -f gdm defaults"
but all i get is "  System startup links for /etc/init.d/gdm already exist."

i dont care about losing the local display, but i would like to have it available, or at least available remotly via my ssh session.

anyone know what I need to do?

thanks

---

### Post by neurostu on 2008-02-12
try sudo apt-get install gdm

---

### Post by mfaust731 on 2008-02-12
gdm is there, it is linked to rc.d - so it should start ( I think )

i think the main issue is where the galleon program is running in the main console, which just sits there and waits for a connection, and never allows a prompt to be displayed.

I would actually like gdm, to not start. I could always issue a startx , to start windows if need be.
I was only trying to restart it because I cant do anything on the local terminal.
I have to ssh into it to get a prompt.

---

### Post by mfaust731 on 2008-02-12
anyone have any idea please

---

### Post by Rocket2DMn on 2008-02-12
You can get to another terminal with CTRL+ALT+F1 up through F6.  F7 is the default GUI tty.
Running startx at another tty should get you a GUI
```
startx
```
If it says an X server is already running, just load gdm
```
sudo /etc/init.d/gdm start
```
How did you enable this program to run at boot?  We should be able to configure it to run in the background.

---

### Post by mfaust731 on 2008-02-12
ummm, nope 

clt + alt + f1 - f6     , do nothing - I relize that it SHOULD switch to a different terminal however nothing happens. Like its locked up - i know it isnt locked up because i can still ssh into it and everything is fine.

I am stumped:confused::confused::confused:

---

### Post by mfaust731 on 2008-02-12
i just saw your question about how i did it.

I went to system, admin, services.........disabled GDM, while i was ther i saw galleon was listed which i needed to run automatically so i clicked it, i didnt know it would takeover my terminal  though

---

