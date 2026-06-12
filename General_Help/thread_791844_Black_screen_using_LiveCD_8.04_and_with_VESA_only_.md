---
title: "Black screen using LiveCD 8.04 and with VESA only 800x600 resolution"
date: 2008-05-12
forum: General Help
---

### Post by gakna on 2008-05-12
Hi, i have Ubuntu 7.10 for AMD64 installed in my desktop and it works perfectly, completely happy with it. I downloaded a copy of Hardy Heron for AMD64 and when i try to use the LiveCD it shows a black/blank screen (with a previous "white" flash before turning black).
If i choose VESA o safe graphics mode (all the other options don´t work: noapic, etc) i can get to the desktop but everything looks huge, and the maximum resolution i get is 800x600 when i try to change the resolution.

I am a newbie, and i am affraid of installing 8.04 because of this resolution problems. I also don´t understand why 7.10 worked so flawlessly and 8.04 which supposedly is an improvement doesn´t work.

Also, i have another question...what would happen with Jpilot and my palm information if i upgrade from 7.10 instead of doing a clean install?? Does the upgrade work good? why everybody recommends a clean install??

Sorry for these questions but i am a newbie and i googled a lot but found no answers yet.

Thanks a lot!

---

### Post by Cresho on 2008-05-12
graphics card?  what is it?

---

### Post by Joe of loath on 2008-05-12
try adding 'acpi=off' after selecting 'install' and pressing F6 on the live cd.

it worked for me...

---

### Post by gakna on 2008-05-12
Hi thanks for answering!
My graphic card is nvidia geforce 6150 SE integrated to the motherboard i think, and the processor is AMD Athlon 64x2 dual core 4000+.
The acpi=off didn´t work for me, only logging in safe graphic mode but with the problem of the low resolution.
Thanks for any advice you can give me! :)

---

### Post by gakna on 2008-05-20
Any ideas somebody???

---

### Post by Cresho on 2008-05-22
have you tried installing it from the System->Administrator->Hardware Drivers?  just put a checkmark and apply.  this will install the drivers for your card.

I'm gona start you off using the easy route.  If this doesnt work, message me again and ill find another way, there are a few ways of doing this so dont give up.  btw, don't forget to reboot.

---

### Post by zvacet on 2008-05-22
Maybe [here]("https://help.ubuntu.com/community/FixVideoResolutionHowto") you will find answer to your question.

---

