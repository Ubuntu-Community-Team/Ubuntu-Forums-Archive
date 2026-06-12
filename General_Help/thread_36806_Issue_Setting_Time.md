---
title: "Issue Setting Time"
date: 2005-05-24
forum: General Help
---

### Post by lskuff on 2005-05-24
Hi,
 I recently installed Ubuntu 5.04 (Hoary Hedgehog) on my gateway YGR600 Laptop. Everything went really well - my WiFi card was automatically detected, no video card driver issues, even my SoundBlaster Extigy worked on startup. The is however an issue that seems fairly serious.

When I started the system up the clock was wrong. It said it was like 3AM when it was really 9AM... I went to change the clock to the correct time as I applied the changes my whole screen went blank for about 45 seconds or so... then the display came back on but it was corrupted (weird colors all over)..... I could move my mouse around and I know the cursor was moving because in some places I could see a little bit of the desktop though some lighter colors.... I restarted my machine and it came back up okay. I have since tried to change the time like 5 other time and the same thing happens every time. Does anyone know what is going on? I have had no other issues with anything else.  

P.S. - I also have Win XP installed and there are no issues setting the time with it, don't know if that is important or not.

---

### Post by ola on 2005-05-25
If you are online at boot time there should be a "Synchronizing the clock.." thing.. Right?

Its NTP that should synchronize the clock.. That one failed for me all the time so I decided to change the server to synchronize agains (/etc/default/ntpdate/) and google your closest NTP server

Hope it helps

---

