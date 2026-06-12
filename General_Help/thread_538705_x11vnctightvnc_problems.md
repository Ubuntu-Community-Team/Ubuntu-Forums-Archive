---
title: "x11vnc/tightvnc problems"
date: 2007-08-30
forum: General Help
---

### Post by maybeway36 on 2007-08-30
I use x11vnc on my Kubuntu Feisty computer for remote access with resumable sessions. I can use the RealVNC client on a Windows computer to connect, but the TightVNC client hangs at "no authentication needed."
Is this a problem with the TightVNC client or with x11vnc?
P.S. Krdc can also connect to the x11vnc server.

---

### Post by krunge on 2007-08-30
Which version of TightVNC Viewer and which version of Windows?

---

### Post by maybeway36 on 2007-08-31
TightVNC 1.3.9, and I've tried on both Windows XP Home and Windows 2000 Pro.

---

### Post by bodhi.zazen on 2007-08-31
I use tight vnc to connect to Ubuntu from windows XP with no problems.

Not sure where your problem is, but just letting you know it is possible :mrgreen:

---

### Post by dj_p03t on 2007-08-31
> **maybeway36 said:**
> TightVNC 1.3.9, and I've tried on both Windows XP Home and Windows 2000 Pro.

would you happen to know the command to download tightvnc via the linux terminal? i know its something along the lines of

sudo apt-get install xtightvncviewer

but i think its either missing something or i messed sumthing up cuz thats not working i did it yesterday but reinstalled the OS again because my /home wasnt large enough :-/ now i cant get it and its the only way i have to access my data-storage machine

---

### Post by dj_p03t on 2007-09-01
> **dj_p03t said:**
> would you happen to know the command to download tightvnc via the linux terminal? i know its something along the lines of

sudo apt-get install xtightvncviewer

but i think its either missing something or i messed sumthing up cuz thats not working i did it yesterday but reinstalled the OS again because my /home wasnt large enough :-/ now i cant get it and its the only way i have to access my data-storage machine

actually i just needed to update ubuntu it worked after that :)

---

### Post by krunge on 2007-09-01
> TightVNC 1.3.9, and I've tried on both Windows XP Home and Windows 2000 Pro.

Thanks for pointing this out. It appears to be a problem with Windows TightVNC viewer 1.3.9 and x11vnc 0.8.4 and earlier. Works OK for me on x11vnc 0.9 and later. For 0.8.4 and earlier try adding the x11vnc option: -rfbversion 3.7

Let me know if upgrading x11vnc and/or using -rfbversion 3.7 doesn't work for you.

---

