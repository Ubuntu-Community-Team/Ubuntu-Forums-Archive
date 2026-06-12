---
title: "No sound (popular topic, I see)."
date: 2008-04-15
forum: General Help
---

### Post by dungheap on 2008-04-15
USB headphones weren't working. Installed lots of ALSA stuff as advised in other threads. Now no sound at all, anywhere, even when using normal speakers. Even in Rhythmbox which was about the only thing the headphones worked with, I get red x's at the side of everything, whatever I try to use. I've fiddled with the Sound Preferences and all that. Any clue? Please don't get more technical than you have to, I'm a very stupid person. I'm learning, it's just a slow, painful process. Thank you. Sorry.

---

### Post by nicedude on 2008-04-16
I cant really tell much from your post about your situation, if you give some more details I or someone much smarter than I, roaming around here probably can. First - list what brand and model of usb headphones you are trying to use, second - laptop or desktop? brand? model?, third - I took your question to mean that your regular speakers worked fine at some earlier point, Is this true? If it didn't work fine did it work at all? As the sound issue is a common one the roots of the problem aren't for many reasons, so list as much info about hardware and anything you can remember specifically that you installed or have already tried and I will try to help you more.

here is a command to list hardware playback devices
aplay -l 
and this one will list all your PCI devices, look for ones that say Audio for your sound devices
lspci -v

lastly you might also tell what version of Ubuntu you are using (ie. 7.04 feisty or 7.10 gutsy)

---

