---
title: "printing troubles (shared printer)"
date: 2008-04-29
forum: General Help
---

### Post by AmishFury on 2008-04-29
i searched trying to find a solution and tried everything i could find and understand

i'm a complete noob with linux first of all

second... on to my problem
printer (HP Deskjet 3650) works on local computer no go even seeing the printer over the network with windows laptop (works when desktop is booted into windows of course but i don't want to be forced to boot into windows every time someone else wants to use the printer)

this is as far as i can get.. clicking on the linux box in this window does nothing
[img]http://i119.photobucket.com/albums/o149/SgtPnkks/untitled.png[/img]

---

### Post by AmishFury on 2008-05-02
bump... still nothing

---

### Post by drpaul on 2008-05-02
I'm not running Hardy yet, but in both Edgy and Gutsy I managed to give my Windows machine access to the printer connected to my Ubuntu machine by installing a printer with the following URI

ipp://192.168.2.77:631/printers/HL-5140

the ip address is that of the machine to which the printer is connected. Note that port 631 is used; it assumes you are using CUPS to manage things.

HTH. If you have any questions shoot away; no guarantees of answers but ...

Paul

---

### Post by AmishFury on 2008-06-01
that didn't work... still can't get the windows laptop to see any printers on this computer while running ubuntu

no idea why anyone would ever want to go back to windows ](*,)

---

### Post by SirPerigrin on 2008-06-01
In order for Windows to view a Linux printer you will need to setup SAMBA to share the printer. Windows cannot access printers shared over CUPS.

---

### Post by helmet on 2008-06-02
> **drpaul said:**
> I'm not running Hardy yet, but in both Edgy and Gutsy I managed to give my Windows machine access to the printer connected to my Ubuntu machine by installing a printer with the following URI

ipp://192.168.2.77:631/printers/HL-5140

the ip address is that of the machine to which the printer is connected. Note that port 631 is used; it assumes you are using CUPS to manage things.

HTH. If you have any questions shoot away; no guarantees of answers but ...

Paul


i think if i remember right i had to use http, not ipp, keeping everything else the same

---

### Post by AmishFury on 2008-06-02
> **SirPerigrin said:**
> In order for Windows to view a Linux printer you will need to setup SAMBA to share the printer. Windows cannot access printers shared over CUPS.

read the fine print in the picture...

anyway... after weeks of ](*,) poking around with samba and yelling at my printer i got it working... without samba

---

