---
title: "Jack - suddenly lost sound from my browser."
date: 2020-07-14
forum: General Help
---

### Post by elsmandino2 on 2020-07-14
Hi there.

I am pretty new to Linux, generally, but managed to get Ardour and Guitarix running on Ubuntu Studio.

I followed some instructions only, to install Cadence, so that I could turn on Pluseaudio to Jack bridging.

I use this so I can play guitar to Youtube.

Everything was fine, but my cat jumped on my keyboard and I have suddenly lost sound.

I have tried everything and cannot get it back.

I have attached a copy of my Catia screenshot.

Any help would be really appreciated.

Thanks in advance.

---

### Post by uninvolved on 2020-07-15
I'd run "pavucontrol" and check to see if anything is muted. If it's not installed, install it with "sudo apt install pavucontrol".

---

### Post by elsmandino2 on 2020-07-16
You are a genius. I had to switch Firefox's output from Built in Audio to Jack.

Working perfectly, now.

Thank you very much.

---

### Post by uninvolved on 2020-07-16
I forget how, but they like it if you mark the thread solved. 

Glad you got it sorted - and many sound issues can be resolved by poking around in pavucontrol. In my experience, adding JACK to the system means you'll find small issues here and there and pavucontrol comes in handy for fixing them. On one system, adding JACK somehow resulted in my mute button no longer working in the browser (for example). It'd mute, but I'd have to unmute with the volume settings with the mouse but it'd mute other apps just fine. Instead of using the computer to add effects, I just use a MOTU (or line-in with a mic) and add all the effects before it gets to the computer.

---

### Post by elsmandino2 on 2020-07-16
Thanks mate - shall mark it solved, now.

---

