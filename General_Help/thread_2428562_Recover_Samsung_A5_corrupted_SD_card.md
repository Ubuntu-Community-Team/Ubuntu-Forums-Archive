---
title: "Recover Samsung A5 corrupted SD card"
date: 2019-10-05
forum: General Help
---

### Post by Riis on 2019-10-05
Hi!

Suddently my microSD card was no longer readable in my Samsung A5 phone. Happend after a software update I think. 

I tried to read it from my laptop (Windows), but it just asks me to format the SD card. I would really like to get my data out if possible, so I of course did not do this.

The microSD card is a 16GB Kingston and I believe it was using FAT32.

I tried some actions, but no luck so far:
1) Created an image with ddrescue. It however estimates the size to 2TB. Anyone who can explain why? 
2) I decided to create a image of the first 16 GiB with gddrescue.
3) Tried to analyze this image with testdisk. No results.
4) Tried to analyze this image with photorec. No results.

Do some of you have inputs to what I could try?

I found this one:
https://www.cgsecurity.org/wiki/Data_Recovery_Examples

Should I try to rewrite the BS?

---

### Post by Autodave on 2019-10-05
If you are not able to read it in Win or Ubuntu, I doubt that you are going to be able to do anything with it.  SD and micro SD cards fail often.  And when they fail, they usually fail completely.  I have had brand new, name brand ones fail after only a few days.

---

### Post by sudodus on 2019-10-05
Have you tried to use PhotoRec directly on the SD card (or only indirectly via the image)?

If PhotoRec cannot find any files directly from the card, I would agree with @Autodave, that the card is bricked, damaged beyond repair.

But you could try in yet another computer and with a different card reader before giving up.

---

