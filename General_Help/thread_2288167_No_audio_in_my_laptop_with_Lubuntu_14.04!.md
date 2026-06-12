---
title: "No audio in my laptop with Lubuntu 14.04!"
date: 2015-07-24
forum: General Help
---

### Post by miguel42 on 2015-07-24
I don't know why, in my Lubuntu, when i used ```
# apt-get remove phpmyadmin
``` it start removing random programs from my system, so I closed the terminal immediatly but it appear that it removed something important for the sound of my laptop. Now my laptop hasn't sound, with and without headphones... I don't know what happens, my audio device is Intel Corporation ValleyView High Definition Audio Controller (rev 0e), but I searched for drivers on internet and I couldn't find... :( I think that my computer recognize my audio device because when I put in a terminal ```
lspci | grep Audio
``` it puts ```
00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0e)
```, and ```
cat /proc/asound/cards
``` returns ```
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xd0810000 irq 109
```, and alsamixer recognizes my card... But the sound still off... I revised that every element on Alsamixer wasn't in mute. Please help me really don't want to reinstall the OS  ](*,)    Thanks.

---

### Post by miguel42 on 2015-07-24
Okey now it works, I only had to reinstall Pavucontrol (# apt-get install pavucontrol) and PulseAudio (# apt-get install pulseaudio), then reboot one or two times and then play my favorite song to get lucky :-)

---

