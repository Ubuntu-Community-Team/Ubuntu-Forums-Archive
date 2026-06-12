---
title: "Gutsy freezes: finally SOLVED for me!!!"
date: 2008-01-14
forum: General Help
---

### Post by Felipaus on 2008-01-14
Since Fiesty to Gutsy upgrade on my old DUAL Pentium III system I experienced totally random freezes (only hard reset or poweroff).
Initially I tought was a graphic driver problem (ati radeon 9000 with ati standard free driver): I was wrong! Same hard freezes also with vesa or fglrx.
I found a temporary solution using i386 kernel instead the generic one, but I loose one CPU (the i386 kernel doesn't support more than one CPU): no more freezes but an already slow system become sloooooooower...
In search of a more performing solution I tested Heron (new kernel) and also Mandriva live CD: same random freezes!!!
After some more experiment i solved with:

1) (I don't know If this is necessary): I changed the SMI# source of my MB from I/O APIC to PIIX4E
2) I used the boot option noapic

No more freezes, generic kernel, two CPUs, a stable and "performing" Xubuntu old system.
:)

P.S. on a DUAL CPUs system DON'T use nolapic boot option, because it affects the "local interrupts" used to sync the two CPUs

---

### Post by kdfuller on 2008-01-14
I have been using Ubuntu for several months now beginning with Feisty and now Gutsy. I had random lockups all the time that required a hard reboot.. I finally found a solution to my problem. I removed "powernowd" (a program that controls cpu frequency scaling) and all lockups ceased. I have a Core2Duo E6600 processor. I don't know if it would help you but you might give it a try. I recently reinstalled and the lockups started again until I remembered to remove powernowd so I know that it is the culprit. Hope this helps.

---

### Post by Felipaus on 2008-01-15
> **kdfuller said:**
> I have been using Ubuntu for several months now beginning with Feisty and now Gutsy. I had random lockups all the time that required a hard reboot.. I finally found a solution to my problem. I removed "powernowd" (a program that controls cpu frequency scaling) and all lockups ceased. I have a Core2Duo E6600 processor. I don't know if it would help you but you might give it a try. I recently reinstalled and the lockups started again until I remembered to remove powernowd so I know that it is the culprit. Hope this helps.
Thank you for the advice, but i SOLVED my problem (and btw my ancient system hasn't powernowd istalled because my two Pentium IIIs doesn't support frequency scaling).
I just posted the remedy that worked for me to help other ancient systems' owners in solving the freeze problem.

---

