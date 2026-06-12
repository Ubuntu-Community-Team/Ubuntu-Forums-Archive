---
title: "Hello again, UBUNTU"
date: 2008-01-03
forum: General Help
---

### Post by wonderman on 2008-01-03
hi everybody.

I have used ubuntu, and gave up some months ago. My problem was the freeze up´s that so many people complains about. 
Last night i´ve used version 7.10 live cd of Ubuntu (in spite of the version that i´ll install is ubuntu studio 7.10), and... no freeze up´s! i wasn´t able to put on desktop effects, but, well i believe i´ll be able to do that in a complete install.

My question to all of you people is: Do you think my ATI 9700 PRO will give me problems? and what about sound blaster live platinium 5.1 (that in live cd wasn´t playing,..)? can i have the low latency and output quality (48kHz) that i have with KX PROJECT windows drivers?

thank you all in advance!

---

### Post by AlexThomson_NZ on 2008-01-03
ATI support is coming along nicely- you shouldn't have too many problems these days and should be able to use desktop effects once the drivers are installed (I can't seem to get dual-screen working on my X600 however).

Not sure with SB support, I think you might need the -rt (realtime) kernel to use SB's ASIO (low-latency) stuff

---

### Post by wonderman on 2008-01-05
hi!

yes, radeon 9700 don't freeze anymore! but... my desktop is very slow. i'm googling and trying many things to put it the way this videocard should be, but it's very nice being able to be on linux, without freezes! about soundcard, i 'll discover it, but right now i just want to put desktop environment very fluid and smooth, fast, and "workable".

---

### Post by EYEdROP on 2008-01-05
> **wonderman said:**
> hi everybody.

I have used ubuntu, and gave up some months ago. My problem was the freeze up´s that so many people complains about. 
Last night i´ve used version 7.10 live cd of Ubuntu (in spite of the version that i´ll install is ubuntu studio 7.10), and... no freeze up´s! i wasn´t able to put on desktop effects, but, well i believe i´ll be able to do that in a complete install.

My question to all of you people is: Do you think my ATI 9700 PRO will give me problems? and what about sound blaster live platinium 5.1 (that in live cd wasn´t playing,..)? can i have the low latency and output quality (48kHz) that i have with KX PROJECT windows drivers?

thank you all in advance!

In order to get low latency output, install JACK audio server, along with jack control. To start jack, no audio programs can be open. Now run jack control, setup, and change the settings how you wish. It will tell you you have to restart  jack control. Start Jack control back up and hit start and there you go! 
 
Just remember, change one thing at a time, because the wrong setting can make your sound not work.

---

