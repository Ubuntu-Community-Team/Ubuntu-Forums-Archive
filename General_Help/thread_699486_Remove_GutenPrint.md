---
title: "Remove GutenPrint"
date: 2008-02-17
forum: General Help
---

### Post by troy1of2 on 2008-02-17
Okay, at some point in time (I think when GIMP updated last) GutenPrint got installed on my system. The problem is, GutenPrint does not support my printer (HP PSC 1310) and now I am left unable to print. But if I go into Synaptic and try to remove the various entries pertaining to GutenPrint I am told the ubuntu-desktop will be removed in the process. I've been stuck with just the CLI before because of a similar situation awhile back with a modem driver (I think it was) and don't want to go there again without a roadmap of how to return my system to it's original state.


So, I guess what I need to know is, how can I remove GutenPrint and reinstall the ubuntu-desktop without hosing my system?

:confused:

---

### Post by SpaceTeddy on 2008-02-17
as far as i can see in the paket dependencies - you cannot gutenprint without breaking your system. The gutenprint library is a direct dependecy of the ubuntu-desktop - meaning you will either have to "break" the packaging or find another way to get your printer to work... with the gutenprint package installed.

sorry to bring the bad news... 

PS: what printer do you have ?

---

### Post by troy1of2 on 2008-02-17
Well this sucks. The printer is a Hp Psc 1310

---

### Post by SpaceTeddy on 2008-02-17
ok, i just found your other post... :)

it is right, the printer is no supported by gutenprint, but you should also have foomatic installed, which ubuntu-desktop also depends on, and THAT one brings support for the PSC 1310 through the hpijs driver, which should be installed... in other words, sorry, i have no clue what i wrong :(

otherwise, i only found this thread which might or might not help you: [http://www.linuxquestions.org/questions/linux-hardware-18/hp-psc-1315-printer-detected-under-cups-but-not-working-hpliphpijs-driver-331050/]("http://www.linuxquestions.org/questions/linux-hardware-18/hp-psc-1315-printer-detected-under-cups-but-not-working-hpliphpijs-driver-331050/")

best of luck in trying to get it to work

---

### Post by G-Dawg on 2008-06-09
Any luck removing gutenprint?

---

### Post by troy1of2 on 2008-06-09
I did get it removed but it didn't help me with the printer problem. I finally ended up getting another printer.

---

