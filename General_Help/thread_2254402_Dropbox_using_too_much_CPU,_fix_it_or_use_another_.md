---
title: "Dropbox using too much CPU, fix it or use another software (open source)?"
date: 2014-11-26
forum: General Help
---

### Post by zircon_34 on 2014-11-26
I have Ubuntu gnome 14.04 and installed lately dropbox. When starting up my linux box and if I have many files that are syncing, dropbox uses way too much CPU and I have quad core i7 4Ghz... The system was so slow, I stopped dropbox on the command line, and everything was fine.

Anyone having performance issues with dropbox? I don't know why this should use so much CPU, I have it also running as background program in other OS and there is no such problem.

Do you have any open source alternatives to suggest?:p

Thanks!

---

### Post by pqwoerituytrueiwoq on 2014-11-26
i use owncloud, i run my own server off a raspberry pi, the web UI is awful slow on that cpu, but the client is perfect
i could probably OC it, but i want my server 100% stable, i don't want to corrupt my SD card that is in a box i have to deal with screws on when i don't even have a proper backup cause i don't want to power if off and take it apart

---

### Post by zircon_34 on 2014-11-26
I heard about owncloud, that sounds like something to check out!:popcorn: 

Just few questions.

Is the connection to it from outside (your network) secure, do you use a firewall? Is there any advantage compared to a samba install and connect using ssh?

---

### Post by pqwoerituytrueiwoq on 2014-11-27
i setup https connection for remote access (self signed certificate), i use http within my local net
routers are a firewall and i have my WZR-300HP running DD-WRT build 25408

i don't have any samba shares. but i do use ssh
if you want to  rig a b+ pi up, newegg just lowered there price $5 for the sales events (31.98 shipped)
not very fast, but very low on power and silent, headless server will run of a USB port
every desktop i have made recently has always powered usb ports when it is shutdown
i know the B+ can run just fine on usb3 power as a game system (retropi) with no OC using usb snes controllers

i installed my pi on raspbian

since i was syncing my music with it i rigged it into a music player, so it syncs and plays (over-sized retro toggle switch for pause/play)
[http://imgur.com/a/pqUgI](http://imgur.com/a/pqUgI)

---

### Post by zircon_34 on 2014-11-27
> **pqwoerituytrueiwoq said:**
> 
if you want to  rig a b+ pi up, newegg just lowered there price $5 for the sales events (31.98 shipped)
not very fast, but very low on power and silent, headless server will run of a USB port
every desktop i have made recently has always powered usb ports when it is shutdown
i know the B+ can run just fine on usb3 power as a game system (retropi) with no OC using usb snes controllers

i installed my pi on raspbian

since i was syncing my music with it i rigged it into a music player, so it syncs and plays (over-sized retro toggle switch for pause/play)
[http://imgur.com/a/pqUgI](http://imgur.com/a/pqUgI)

Haha nice pics with the cat! Thats a very nice setup, as it happens I have a b+ Pi at home ;) it sounds like a fun project!

---

