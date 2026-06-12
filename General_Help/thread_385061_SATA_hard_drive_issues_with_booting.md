---
title: "SATA hard drive issues with booting"
date: 2007-03-15
forum: General Help
---

### Post by niall111 on 2007-03-15
I've seen a few threads around here that are similar to my problem, and have tried all the suggested solutions to no avail.  My issue is certainly strange, but i'm at my wits end and don't want to junk this hard drive.  I'm trying to simplify the explanation, as everyone i've explained this to in real life tends to get glossy eyes!

I have 4 serial ata hard drives, all are fairly new, 3 are 160gb, 1 is 200gb, all from maxtor:
HD1 = ubuntu and bittorrent
HD2 = TV
HD3 = Games and Movies
HD4 = Everything Else

I have an asus A8N-SLI Nforce motherboard, with 2 sets of 4 sata ports, one of which i have disabled because it causes even more problems than the usable one.  The disabled sata controller is from silicon image, the other, working one, i believe is nvidia's own, but i could be wrong.

Anyway, originally i had all 4 drives in their respective sata ports, HD1 was on SATA1, and so on.  After installing Ubuntu, with only HD1 plugged in, all was fine.  it rebooted to my desktop, i did some config, and then decided to start plugging in the others.  Plugged in HD2 to SATA2, and still, all is well.  Plugging in either of the other 2 drives to either of the other 2 SATA ports (all 4 possible combinations, i tried them) will result in a failed boot.  The fabled "cannot access tty" right after the first ubuntu loading screen starts up, the screen disappears and this error appears at a console, where i can enter some basic commands (ash is the shell, i believe?)

So one of the suggestions was to reorder the hard drives, i moved HD1 to the SATA4 port, left HD2 in SATA2, and plugged in HD4 to SATA1.  all was well again!?  So i try the HD3 drive again in the other free slot, no go.  I unplugged all drives except HD1, still in SATA4, and left HD3 in the SATA3 port.  still no go, same error.  It really seems isolated to the drive itself, regardless of what port I try it in.  HD3 just won't let me boot from HD1 for whatever reason.  

Another suggestion was Grub might be getting the HD ordering mixed up, especially as i was changing the SATA ports the drives are on.  However, when changing their order on the mobo, i would also change their boot order in the BIOS, which kept the ubuntu drive as the first one(sda).  I checked the grub command line at bootup to confirm.  that wasn't my issue.

ANY IDEAS!?   :)

---

