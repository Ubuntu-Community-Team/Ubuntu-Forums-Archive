---
title: "Computer shutdown while watching youtube videos downloading them ok?"
date: 2015-01-10
forum: General Help
---

### Post by rodm1 on 2015-01-10
I just installed 14.04 and if I watch a Youtube video on there sight it will automatically reboot my computer 100% of the time. If I download the video to my computer and play it with VLC media player it works fine but some videos like music must have copy protections and I'm unable to download. I'm thinking it must be the flash player but how do I reinstall or update it or is it another problem?

---

### Post by mooreted on 2015-01-10
There may be some indication as to what's happening in the ~/.xsession-errors.log. I would suspect a video driver problem, but that's just a guess. 

What video card do you have and what drivers are you running? Also, what browser are you using? Adobe no longer supports flash for Linux; have you tried using the official Google Chrome browser?

---

### Post by Yellow Pasque on 2015-01-10
Flash video uses a ton of CPU, so check for overheating (machine will shutdown or reboot at a certain temp to protect itself from frying).

---

### Post by rodm1 on 2015-01-10
Thanks guys! I thought it could be CPU over heating but I cleaned the dust out of it still could be I guess. I'm using Firefox and that sounds like the most likely case at this time but I hate to move on to another browser. Would Opera be a good choice I used it years ago and loved it in my Windows days.

---

### Post by mörgæs on 2015-01-10
You should test a number of browsers in order to diagnose the problem. Opera, Chrome, Epiphany and Midori to get you started.

---

### Post by rodm1 on 2015-01-11
I installed Opera and it seems to be working fine. Thanks everyone!

---

### Post by Yellow Pasque on 2015-01-11
I'm not sure why Opera would fix the problem, unless Opera is using HTML5 to play video instead of Flash and is using less CPU cycles. Your machine rebooting on its own during heavy load probably means you have insufficient CPU cooling or faulty hardware. If Flash is faulty, it should crash or not work, but it should not take down the whole system. I would suggest using cpuburn to try to reproduce the behavior, and keeping a close on eye the temps.

It seems like a band-aid fix to me, but if you're okay with it, that's what counts.

---

