---
title: "Anyone have wake from suspend failing (Phenom II+Nvidia GT 430)"
date: 2015-03-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2015-03-13
My mom has a Asus M4A78LT-M motherboard, which has a AMD 760G chipset and it has a Galaxy GPU (Nvidia GT 430 chip)
i tested the ram (G. Skill value series 4gb DDR3 1333, single channel) and it passed just fine
The CPU is a phenom II 965 black edition (Stock settings w/ a CM Hyper TX3 cooler)
The PSU is a Cooler Master GX 430 (or was that a 450)

quite frequently after suspend when the system wakes up it will not resume, to me it seems to not be getting to the OS and is getting stuck in the BIOS level of resume as it will not charge my 2ed gen ipod shuffle which requires software to be running to allow charging
i have only managed to have this happen with long term suspends, sort test all seem to work

has anyone else had this problem on similar hardware with ubuntu 14.04 or other flavors?

---

### Post by Moofus on 2015-03-14
yes!  my desktop has an Asus m5a-99fx-a board, amd fx-6300, evga gtx 750ti, and gskill sniper 4gb x 2.  I have an ssd, and after 14.04 installed, i deleted swap partition and fstab entry, and it doesn't suspend, although i didn't try suspend before i deleted swap.  i at first thought that was maybe the reason, but i havent added it back yet to see.  when i try to suspend, it never gets there.  the screen goes black and everything, but all the lights and fans keep running.  also on some previous OS (maybe lubuntu 14.04), it did suspend, but when i started it up again, it just beeped and i had to hard reset it.  I was thinking it could be something with the board, it has some other quirks in other areas too, but i dont really know.

---

