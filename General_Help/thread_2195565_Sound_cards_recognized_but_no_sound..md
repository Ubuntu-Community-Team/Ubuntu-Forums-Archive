---
title: "Sound cards recognized but no sound."
date: 2013-12-24
forum: General Help
---

### Post by lndhawkins on 2013-12-24
I have no sound from my motherboard audio jack or the headphone jack on the front of the case. I can't test the HDMI as I have nothing to plug into it. 

I followed the instructions found at  [https://help.ubuntu.com/community/SoundTroubleshootingGuide](https://help.ubuntu.com/community/SoundTroubleshootingGuide) which led me here. 

Here are the results of ```
wget http://www.alsa-project.org/alsa-info.sh && bash ./alsa-info.sh --upload;
```

[URL="http://www.alsa-project.org/db/?f=e32be4df83da21b9c5ec8c8652cfb5496d6c88f6"]http://www.alsa-project.org/db/?f=e32be4df83da21b9c5ec8c8652cfb5496d6c88f6
[/URL]

---

### Post by lndhawkins on 2013-12-25
A little more info, I don't know if it's relevant. When I run ```
alsamixer
``` I get this:

 [[IMG]http://i.imgur.com/IyzEVna.png[/IMG]]("http://imgur.com/IyzEVna")

 I then press F6 and am able to select the the bottom 'HD-Audio Generic' - as seen in this screenshot

 [[IMG]http://i.imgur.com/Khev2Pw.png[/IMG]]("http://imgur.com/Khev2Pw") 

which in turn brings up

 [[IMG]http://i.imgur.com/NTdRrfC.png[/IMG]]("http://imgur.com/NTdRrfC"). 

But it doesn't stick. If I exit out of Alsamixer and then run it again it goes back to the 'default' - the 1st image listed above.

---

### Post by lndhawkins on 2013-12-26
Bump, anyone?

---

