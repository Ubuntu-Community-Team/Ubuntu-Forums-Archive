---
title: "Ubuntu digital signage problem"
date: 2016-10-06
forum: General Help
---

### Post by kjetil-fleten on 2016-10-06
Hi

At a sport arena, we have set up 8 Ubuntu digital signage boards. 
Unfortunately, the content they want to show on the boards, crash from time to time. The content is a web based commercial, delivered by a marketing company. All we want, is basically to run Firefox or any other browser in kiosk mode, and point to the URL of the commercial.
We have tried everything: First various browsers like Firefox, Chromium and  Opera, with various kiosk addons. Then we made the browser refresh for every cycle the commercial ran. Then we tried different tailored solutions like Yodeck, Raspberry Digital signage, Screenly and others. The result was the same: Nothing helps. The commercial still crash from time to time.
Most of the boards are x86_64 computers, while two are Armel (Raspberry PI). They run standard 14.04 and 16.04, and the Rpi runs Ubuntu Mate 14.04.
We have been told that everything works smooth on MAC (most likely because someone have created the commercial on a MAC ?). There must be a way to make it work on Ubuntu too ?
Could there be an error in the coding of the commercial, that breaks something in Ubuntu ? How do we troubleshoot this ? Is there other options for Ubuntu based digital signage we should try ?
The URL to the commercial is [http://valdresstorhall.no/infoskjerm](http://valdresstorhall.no/infoskjerm). Usually, things crash during the video content. Sometimes after a few cycles, other times after hours.
Any hint will be appreciated !

---

### Post by Geoffrey_Arndt on 2016-10-06
Hello

I am not an expert on digital signage but I am just wondering what is driving the video in your browsers?     Are you using any version of shockwave/flash?   If so, have you tried uninstalling (or disabling flash plugins) in the Firefox of other browsers and just using the OpenH264 Video Codecs?   I am using those to run your videos, and have not seen any problem in over 2 hours.   But, as I said, I am not an expert in this so this is just a guess.

I've heard Apple systems do not use Flash . . . so perhaps . . .

---

