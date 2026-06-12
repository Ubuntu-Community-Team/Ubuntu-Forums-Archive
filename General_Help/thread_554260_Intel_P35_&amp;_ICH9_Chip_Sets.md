---
title: "Intel P35 &amp; ICH9 Chip Sets"
date: 2007-09-18
forum: General Help
---

### Post by fjgaude on 2007-09-18
Can anyone give a report of a motherboard that uses subject chip sets with Ubuntu install success?

Thanks,

frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

### Post by jeepescu on 2007-09-19
Gigabyte P35 DS3R 
Everything seems to be working with feisty.

---

### Post by fjgaude on 2007-09-29
Thanks for the input. Sorry for the slow response but lost track of the link.

---

### Post by fjgaude on 2007-09-29
I've checked the Gigabyte DS3R out and see it meets my needs. Looks to be a fine MB for the price.

Can you tell me if the sound works? What doesn't work?

Thanks for the support.

---

### Post by houstonbofh on 2007-09-29
> **fjgaude said:**
> I've checked the Gigabyte DS3R out and see it meets my needs. Looks to be a fine MB for the price.

Can you tell me if the sound works? What doesn't work?

Thanks for the support.
It works, and it is fast, but there are teething issues.  To start, I have the Gigabyte GA-P35-DS3L.  It was between this and the Biostar, and apparently the Biostar lan traffic is a bit rough on the CPU (%43 load)

First there is an issue with LAN.  If you also boot Windows, you have to select "Wake on LAN" in the Windows driver.  If not, the nic won't come up.  Enabling boot rom in bios can also help but I didn't need it.

Sound can be a challenge.  I just use 2 speakers.  In Windows it is one jack and on Linux it is another.  Also, my login and logout sound don't happen anymore.  (This is on Gutsy, so it may be a beta bug)  And I had to do the "Bad OSS, don't grab the entire sound card" fix to RTCW:ET for sound to work there.

But...  I am all STAT (including CD-Rom) and it works out of the box flawlessly.  When it works, sound is fantastic.  The system is blindingly fast (1333 FSB, and 1000 Duel channel ram) and rock solid. Also, there is very little heat.  It takes no special case cooling, so the system is quiet.  I am sure the small bugs will be worked out soon, and this is a strong motherboard for a long time to come.

---

### Post by fjgaude on 2007-09-30
> **houstonbofh said:**
> It works, and it is fast, but there are teething issues.  To start, I have the Gigabyte GA-P35-DS3L.  It was between this and the Biostar, and apparently the Biostar lan traffic is a bit rough on the CPU (%43 load)

First there is an issue with LAN.  If you also boot Windows, you have to select "Wake on LAN" in the Windows driver.  If not, the nic won't come up.  Enabling boot rom in bios can also help but I didn't need it.

Sound can be a challenge.  I just use 2 speakers.  In Windows it is one jack and on Linux it is another.  Also, my login and logout sound don't happen anymore.  (This is on Gutsy, so it may be a beta bug)  And I had to do the "Bad OSS, don't grab the entire sound card" fix to RTCW:ET for sound to work there.

But...  I am all STAT (including CD-Rom) and it works out of the box flawlessly.  When it works, sound is fantastic.  The system is blindingly fast (1333 FSB, and 1000 Duel channel ram) and rock solid. Also, there is very little heat.  It takes no special case cooling, so the system is quiet.  I am sure the small bugs will be worked out soon, and this is a strong motherboard for a long time to come.

Thanks for the details... I'm with two speakers too. Don't boot Windows at all. Do use LAN and need the speed of GB. I'm testing Gutsy and it is just about solid now, will be solid in a month on release.

What do you mean by "STAT"?

---

### Post by houstonbofh on 2007-10-01
> **fjgaude said:**
> Thanks for the details... I'm with two speakers too. Don't boot Windows at all. Do use LAN and need the speed of GB. I'm testing Gutsy and it is just about solid now, will be solid in a month on release.

What do you mean by "STAT"?

Dyslexics of the world, Untie!

SATA...

---

