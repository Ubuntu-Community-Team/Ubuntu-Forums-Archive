---
title: "Plugging in headphones toggles mute button (even the LED lights up)/shutdown"
date: 2013-01-24
forum: General Help
---

### Post by Curix on 2013-01-24
Hello, 
There are a lot of sound problem threads but I haven't seen this problem before.

It started last week.

When  I plug my headphones in, the LED on my mute button (on keyboard) starts  glowing. And I can't hear anything trough my headphones either.
It is as if plugging in my headphones is the same as pressing on the mute button.

When I pull my headphones out, the speakers make a pop sound (the same sound as the mute button makes when you unmute)

This is for both jack-inlets in my pc (HP Pavilion).


Also, the screen freezes while shutting down (the Ubuntu loading screen with the dots). 
This problem started at the same time as the headphones. Somewhere previous week.


Anyone an Idea please?


(BTW when I boot in windows, everything is fine, so it probably isn't hardware or something )


Thank you very much!

---

### Post by AmmonRa101 on 2013-01-25
I have the exact same problem. running Ubuntu 12.04 LTS sound worked fine before, earlier this week I updated some of the packeges (I don't remember which ones) and today finally rebooted my laptop.  now whenever I plug in my headphones or other speaker to the headphone jack, the mute light on my keyboard lights up and no sound, but with no headphones plugged in, the sound plays fine from the built in speakers.  this is on a Hp pavilion dv6 laptop.

---

### Post by AmmonRa101 on 2013-01-25
ok, having done some poking around, removing the PulseAudio package fixes the issue, but it's not great because the +/- buttons stop working too.   I found downgrading PulseAudio to an earlier version fixed the problem while still keeping other things working.

---

### Post by Curix on 2013-01-25
Thanks, that did the job.

---

