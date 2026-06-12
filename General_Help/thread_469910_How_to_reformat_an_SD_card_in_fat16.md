---
title: "How to reformat an SD card in fat16?"
date: 2007-06-10
forum: General Help
---

### Post by RLamb on 2007-06-10
Hey guys, in trying to deduce the problem with an SD card in my PDA I decided to reformat it, and silly me I did it in windows as FAT32 and now ubuntu doesn't see or mount the card - its says:

"Unable to mount media - There is probably no media in the drive"

Could anyone tell me how I reformat my card as fat16 again, and how I can mount it?

My fdisk - l says

/dev/sdd1               1         984     1983619+   b  W95 FAT32

Thanks for any and all suggestions.

---

### Post by RLamb on 2007-06-10
Is there anyone who can help me with this please?

---

### Post by cometa2k7 on 2008-04-20
I got that sort of output when I did that in a terminal.

Have you tried using QTParted? It's pretty good. It should let you reformat to FAT16, and it seems to pick devices up quite well.

I first got problems when I formatted my Memory Stick Pro Duo, which is 8Gb, using my mobile, which uses FAT16. I was blissfully unaware at the time, and it seemed to work fine, except for the fact that it crashed my phone every now and again.

What size is your SD card?

Also, GParted is quite good, and seems to allow FAT16 up to 4Gb, not 2Gb as QTParted does.

---

