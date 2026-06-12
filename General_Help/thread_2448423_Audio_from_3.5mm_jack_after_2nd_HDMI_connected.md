---
title: "Audio from 3.5mm jack after 2nd HDMI connected"
date: 2020-08-07
forum: General Help
---

### Post by coordinatedbrake on 2020-08-07
My set-up is currently Raspberry Pi Model 4 connected through HDMI ports  to a TV (HDMI-1) and a projector (HDMI-2). I have the 3.5mm audio jack connected to speakers.

When all is as described above I cannot get audio from the 3.5mm jack. I  can get audio from each HDMI device without issue as both have internal  speakers. 

After trying different configurations, I have found that I get audio  from the 3.5mm jack when HDMI-2 (projector) is disconnected and pi  rebooted, so that only HDMI-1 is connected.

I have tried
sudo amixer cset numid=3 1
 without success as I get this returned:
 

amixer: Cannot find the given element from control default



  I was having these issues and some others relating to my display when  using, Raspian  (even tried forcing audio through 3.5mm using the  raspi-config utility)     so I switched from Raspian to  Ubuntu-mate. I  had the same audio issue in both operating systems. I am currently running Ubuntu Mate. 

i have also tried - 

sudo apt-get install --reinstall alsa-base pulseaudio

 

sudo alsa force-reload
 I have tried testing speakers using ubuntu-mate's graphical sound settings, hardware tab - does not work. 
I used alsamixer to ensure that the headphones volume was turned up to full and not muted.

I have tried Google and I have not found a solution.
I am new to Linux.

Thanks for your help.

---

