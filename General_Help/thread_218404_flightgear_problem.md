---
title: "flightgear problem"
date: 2006-07-18
forum: General Help
---

### Post by TheRingmaster on 2006-07-18
I downloaded flightgear from synaptic and now I can't find it. I try to put flightgear into the terminal and it say that the command can't be found. Is there any way to get flightgear running?

---

### Post by DoorGunner on 2006-07-18
try
$fgfs

if you go to flight gear you can get a list of all the -t -s stuff for starting with certain maps and planes

---

### Post by TheRingmaster on 2006-07-18
that didn't do anything:-k

---

### Post by DoorGunner on 2006-07-18
what happens if you do this

$whereis fgfs
:-k

I get this

$ whereis fgfs
fgfs: /usr/games/fgfs /usr/share/man/man1/fgfs.1.gz

---

### Post by TheRingmaster on 2006-07-18
petey@petey-desktop:~$ $whereis fgfs
opening file: /usr/share/games/FlightGear/Navaids/carrier_nav.dat
/usr/share/games/FlightGear/Navaids/TACAN_freq.dat
Segmentation fault

---

### Post by DoorGunner on 2006-07-18
It looks like flight gear didnt install correctly....I see you have some mods but not the actual game.....

try reloading.

*****EDIT******

try just typing       fgfs    into terminal

I think what happened is you typed the $ in as well

---

### Post by TheRingmaster on 2006-07-18
you mean reinstall?

---

### Post by DoorGunner on 2006-07-18
Just try typing .....    fgfs  .... not $fgfs

---

### Post by TheRingmaster on 2006-07-18
it gets to "initializing subsystem" then it goes down.

It (The terminal) keeps saying "segmentation fault"

---

### Post by DoorGunner on 2006-07-18
I guess the only thing you can do is to try and remove the program ..... then do a complete install...... Unless someone can advise more...

---

### Post by TheRingmaster on 2006-07-18
when I type in whereis fgfs it says fgfs: /usr/games/fgfs /usr/share/man/man1/fgfs.1.gz

---

### Post by TheRingmaster on 2006-07-18
i marked all three parts of it for reinstallation and still no luck:mad:

---

### Post by stever00 on 2006-09-18
When you find out what it is, let us know.  I have a "killed" message in a prompt window.  I typed fgfs.

---

### Post by TheRingmaster on 2006-11-24
I have given it a second chance, but this program will NOT work on my system. here is an output of what the terminal says when I do a fgfs in the terminal.

> petey@Data:~$ fgfs
Error reading properties: 
Failed to open file
 at /home/petey/.fgfs/autosave.xml
 (reported by SimGear XML Parser)
  Model Author:  Unknown
  Creation Date: 2002-01-01
  Version:       $Id: c172p.xml,v 1.17 2006-03-13 15:27:14 ehofman Exp $
  Description:   Cessna C-172
Segmentation fault (core dumped)


---

### Post by ghansel on 2006-12-09
I get the identical problem on a dual-core.

---

### Post by Maikes on 2007-04-22
And me, on a dual core too.. =( Please help!

> Error reading properties: 
no element found
 at /home/manu/.fgfs/autosave.xml,
line 1, column 0
 (reported by SimGear XML Parser)
DRM_I830_CMDBUFFER: -22
DRM_I830_CMDBUFFER: -22
DRM_I830_CMDBUFFER: -22
manu@pavilux:~$ 


---

