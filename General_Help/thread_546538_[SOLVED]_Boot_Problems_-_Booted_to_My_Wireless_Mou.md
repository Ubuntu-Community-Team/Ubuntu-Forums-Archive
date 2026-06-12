---
title: "[SOLVED] Boot Problems - Booted to My Wireless Mouse US Stick!??"
date: 2007-09-09
forum: General Help
---

### Post by 1337455 10534 on 2007-09-09
*[COLOR="DarkOrange"]--- (The title should say "Boot Problems - Booted to My Wireless Mouse USB Stick!??", sorry.)[/COLOR]*
Hello Ubuntu, community!
I have Feisty running (almost*) perfectly for about, oh, 70 days.

Now, I am in some trouble. I use a wireless mouse, and as I was shutting down one day, my problem* kept the computer on all night, with the wireless USB stick in the machine!
Next time (and the next 5 times), all I got was a black frozen screen. 
Never happened before, and I have never heard of it. But my system BIOS has plug-and-play OS enabled and I think the boot preference was set to external drives. In this case, my suspicion is that my computer tried to boot from the USB stick of my wireless mouse!! Hmm.
So, on my next boot, I went to the BIOS and shut off plug-and-play OS, and turned the boot preference to Hard Drive. Still no go!
So, on the next boot, I went to the boot menu instead and choose "Hard Drive" and next "Primary WD-//random numbers//" (that was the only choice, I have no other HDDs or Boot-able devices). And guess what? It booted perfectly!

My problem* still remains, and as an added frustration, dcopserver, a KDE thingy (I admit it, I am a noob) that lets my KDE based apps run is, not working..
Terminal:
> family@The-Family-Desktop:~$ dcopserver --help
Usage: dcopserver [--nofork] [--nosid] [--help]
       dcopserver --serverid

DCOP is KDE's Desktop Communications Protocol. It is a lightweight IPC/RPC
mechanism built on top of the X Consortium's Inter Client Exchange protocol.
It enables desktop applications to communicate reliably with low overhead.

Copyright (C) 1999-2001, The KDE Developers <http://www.kde.org>
family@The-Family-Desktop:~$ 
 

I tried turning on dcopserver by just typing the name into the terminal, but still no... So, I have pretty much no KDE apps working, and on EVERY SINGLE BOOT,  I have to go to the boot menu and select my Hard Drive.

[B][COLOR="Red"][SIZE="3"]Finally, my problem:
Every shutdown and hibernation I put my computer on, all it does is;
--- Shutdown: the Ubuntu load tank empties out the orangeness, and freezes. If my wireless mouse USB stick is in, it displays a page or so of hash. If not, it displays just half a page of hash. All of the hash has the string "usb4" somewhere in it. The computer has to be shutdown uglily, by pressing the power button.
---Hibernaiton: same as Shutdown, except more hash, without as many lines with the "usb4" string, and does never go black. It must be shutdown manually also, but oddly enough, after the power button goes black, on the next boot, it will open all of the files and programs I had running before Hibernation.[/SIZE][/COLOR][/B]

::: HP Pavillion a610y, 512 MB RAM, 1 HD, 1 Partition, M$ Wireless USB Mouse

Thanks in advance, Community...
1337455 10534

---

### Post by 1337455 10534 on 2007-09-09
Bump! Bump!

---

### Post by 1337455 10534 on 2007-09-09
Possible Soultions (my hyothesis):
> X.org is messed up and needs to be reconfigured, but this doesn't explain the weird boot preference or dcopserver

> HDD is finally dying after 4 years of servitude. There could be bad sectors on it...

> System BIOS is corrupted, weird, because I know I do not have any virii or such. Firestarter and ClamAV are up and running!

> Ubuntu setup file got corrupted. This happened to my dad's laptop except he has had only XP running on it for over a year.

---
Let me reiterate that everything I mentioned above was not happeing untill the wireless mouse fiasco. But the shutdown problem will always be there. It has remained even after clean installs of Ubuntu before on the same machine.

---

### Post by 1337455 10534 on 2007-09-09
I know this is gonna come off as spammy, but...
BUMP!

In other news, I put Compiz Fusion on this computer. It is working perfectly.

---

### Post by 1337455 10534 on 2007-09-14
Ok people, this has gone on long enough. This is a problem that has a fix somewhere but no one has found it. Hmm... I know that there is an answer somewhere because the first 3 months of Ubuntu's life on my desktop, it booted fine. Please, someone, help.

And sorry for spamming. Again.

---

### Post by 1337455 10534 on 2007-10-09
Reinstalling the OS to Gutsy solves both problems. Thx anyways!

---

