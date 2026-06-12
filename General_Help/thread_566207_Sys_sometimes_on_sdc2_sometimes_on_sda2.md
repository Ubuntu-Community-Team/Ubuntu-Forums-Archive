---
title: "Sys sometimes on sdc2 sometimes on sda2?"
date: 2007-10-03
forum: General Help
---

### Post by Corelgott on 2007-10-03
Hi Folks,

i am encountering a strange behavior... sometimes my main-drive is mounted as sda and sometimes as sdc...

I haven't been able to find any kind of pattern in this. This results in multiple problems. Like going into maintenance console, because fschk fails or mount simply fails...

my sys-layout is:

- hda - ide (shouldn't matter here)
- sda - sata (Onboard raid controler; Not in a raid; just pure Sata-Controler)

- sdb - sata Raptor on an pcix-Adaptec 2412 (HDD1 of Raid 0)
- sdc - sata Raptor on an pcix-Adaptec 2412 (HDD2 of Raid 0)

My Bord is ASRock 939 Dual-SATA2 (Don't ask)

Os

Feisty - 2.6.20-16-generic on "normally" sda2 (sometime on sdc2)

I have been running a Os from Redmond for years. Never ever encountered such a problem...

Any hints how to get rid of this one?

Thanks for thinking about that...

Corelgott

---

### Post by Corelgott on 2007-10-03
hmm has nobody every seen such an effect? hasn't anybody got a hint for me? It's causing quite some trouble here...

thx

Corelgott

---

### Post by fjgaude on 2007-10-03
Well, many of us only use UUIDs for our drives in the fstab file. Such seems to quiet down what you are talking about.

I've noticed whenever I add or remove a spare drive the /dev/sd[n] seems to change. Good luck with whatever you are doing.

---

