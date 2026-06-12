---
title: "SB X-Fi on Gutsy?"
date: 2007-10-20
forum: General Help
---

### Post by mrbister on 2007-10-20
Hi!

I'm using Gutsy (32bit) but I can't find any info on how to make Creative X-Fi work. Anyone who knows how to install drivers for that one?

---

### Post by antoinem on 2007-12-24
Hello,

Some facts about the X-FI Extreme driver
- the current beta works only with a 64-bit linux
- it requires that your linux is built using the SLAB memory allocator

KNOW THAT 7.10 GUTSY USES THE NEWER SLUB ALLOCATOR.
THE 7.04 FEISTY STILL USES SLAB.
SO UNLESS YOU WANT TO REBUILD YOUR GUTSY KERNEL FOR USING SLAB,
YOU SHOULD STICK WITH THE 7.04.

The howto install can be found here (it works with feisty):
[http://blackbox.lostwave.net/x-fi/readme.txt](http://blackbox.lostwave.net/x-fi/readme.txt)

Hopes this helps

---

