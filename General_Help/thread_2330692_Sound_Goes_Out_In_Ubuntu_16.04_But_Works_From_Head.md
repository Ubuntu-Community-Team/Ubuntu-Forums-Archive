---
title: "Sound Goes Out In Ubuntu 16.04 But Works From Headphones"
date: 2016-07-13
forum: General Help
---

### Post by iAmTuFFl3 on 2016-07-13
When I start Ubuntu 16.04 (I dual boot with Windows 7) the sound works from both the headphones and speakers. I can listen to music, watch YouTube videos, and test the sound. After a while, (I don't know exactly because I am away from the computer) the sound stops working from the speakers. In the sound settings it says output is set to speakers but there is no sound. However if I plug in headphones there is sound. Nothing is muted in alsamixer, I tried removing and reinstalling alsa-base pulseaudio, and I've done a clean install of Ubuntu TWICE but nothing works. Sound works well in Windows 7. I feel like I've tried everything. Should I just give up and soley use Windows?

---

### Post by GU4$+7rxH#@ on 2016-07-15
Hello

Try this solution may be for previous versions but maybe work.

I give you the link of the page. 

It involves uninstalls and facilities.


[URL="https://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/"]https://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/


[/URL]But a question? .

Try this command to see what your audio card ?

> lspci | grep -i audio[URL="https://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/"]
[/URL]

---

