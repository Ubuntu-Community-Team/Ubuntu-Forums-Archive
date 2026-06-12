---
title: "Very frequent freezes, forcing hard shutdown, on intel classmate netbook"
date: 2019-01-06
forum: General Help
---

### Post by enrialba on 2019-01-06
Hi all
I have lubuntu 18.04 installed together with win7, on a netbook type "intel classmate" ...
When I see movies from some site (in Firefox) the netbook freezes completely, leaving the sound of the movie repeating itself indefinitely until a hard reset ...
I have tried to regain control by pressing SysRq + R-E-I-S-U-B but nothing works.
In win7 I see the movies perfectly and it never happened.
I have checked the logs of the system, but there is no record of the incident ..
What could I try to solve ??

the specifications:
CPU: Intel (R) Celeron (R) CPU N2806 @ 1.60GHz
memory: 3914MB (1548MB used)
LUbuntu 18.04.1 LTS
Audio: HDA-Intel - HDA Intel PCH
name: Sum 1025
Family: BayTrail System
Version: Clamshell
-BIOS-
Date: 06/05/2014
Phoenix Technologies Ltd.
MPBYT10A.10C.0029.2014.0605.1433
main board
Intel powered classmate PC
Version: Clamshell


thank you

---

### Post by blackbird34 on 2019-01-08
Firefox might be a little bit too heavy for that CPU... What is the CPU consumption like in the System monitor? If firefox regularly approaches 100% CPU it could just be that.
One solution could be to use Youtube-dl to download the movie and watch it with VLC instead. 

[https://github.com/MrS0m30n3/youtube-dl-gui](https://github.com/MrS0m30n3/youtube-dl-gui)

---

### Post by Kris_M on 2019-01-08
I would look at video and drivers and support for that. EDIT you don't say what you have for a video hardware on that.

---

### Post by Superdude_123 on 2019-01-08
I had a similar issue with an on board intel video card. Try adjusting your GRUB setting to dissable the kernel drivers and see if that gets you more stability.

---

