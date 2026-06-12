---
title: "No sound on websites"
date: 2007-06-29
forum: General Help
---

### Post by John W on 2007-06-29
I have been unable to get sound to work on websites such as youtube, nickjr, disney, webkinz. I have tried many of the suggestions on these forums with no resolution. Up until yesterday I was using 6.06 and tried some of the suggestions from ubuntuguide.org(specifically, adding the respositories) and completely borked my system. I had to do a new install today (and chose 7.04). 
With a fresh start , I followed the instructions from ubuntuguide.org, downloaded flashplayer 9, java, couldn't get pulseaudio to install. I think I need more personalized attention, hopefully someone will be able to guide me in the right direction, my kids will be very greatful if sound would work on their favorite sites.

---

### Post by floydwilde on 2007-06-30
Just curious if you've tried to use alsamixer, try typing 'alsamixer' at the command line and playing with the knobs.

---

### Post by John W on 2007-06-30
I played around with alsamixer with no effect. Thank you for the suggestion.

---

### Post by John W on 2007-06-30
I just discovered I have no sound at all, tried playing a CD through Amarok, it showed cd was playing but no sound was coming out. I hear the drum  sounds when I login. I have a soundblaster audigy card.

---

### Post by rabbit20 on 2008-02-01
try disabling the on board sound card if you have a PCI sound card...thats what caused me problems

---

### Post by Crafty Kisses on 2008-02-01
> **John W said:**
> I have been unable to get sound to work on websites such as youtube, nickjr, disney, webkinz. I have tried many of the suggestions on these forums with no resolution. Up until yesterday I was using 6.06 and tried some of the suggestions from ubuntuguide.org(specifically, adding the respositories) and completely borked my system. I had to do a new install today (and chose 7.04). 
With a fresh start , I followed the instructions from ubuntuguide.org, downloaded flashplayer 9, java, couldn't get pulseaudio to install. I think I need more personalized attention, hopefully someone will be able to guide me in the right direction, my kids will be very greatful if sound would work on their favorite sites.

Hmmm, post the following output, ```
lspci
```

---

