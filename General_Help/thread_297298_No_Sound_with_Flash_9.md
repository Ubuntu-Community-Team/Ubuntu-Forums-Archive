---
title: "No Sound with Flash 9"
date: 2006-11-10
forum: General Help
---

### Post by ACGarib on 2006-11-10
I have flash 9 installed (via automatix2) on an edgy system with swiftfox 2.0. I no longer get any sound with flash. Youtube and Google video no longer have any sound, but the video still works. 

Flash 7 had sound (it always stuttered a bit though), but when I upgraded to flash 9 beta, the sound for flash stopped working. 

I already tried reinstalling alsa-oss, changing around FIREFOX_DSP=&#8221;whatever&#8221; to have aoss, auto, none, and a few others, and I also tried sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1 and ln -s /tmp/.esd-1000 /tmp/.esd, but nothing worked. 

Is there anything else I can do to get flash 9's sound working?

EDIT: Also, I tried to do sudo apt-get install lib32asound2, but it says coundn't find package lib32asound2. I do howerver have libasound2 installed. I remember reading that flash 9 only looks for the 32 bit version of libasound2 and I don't know if plain old libasound2 (without a 32 in it) will work with flash 9 or not.

---

### Post by ACGarib on 2006-11-11
I finally got it working!!!!!!!!

I guess automatix2 didn't uninstall flash 7 properly because after I uninstalled any flash stuff I could find then reinstalled flash 9 via a .deb I found somewhere, the sound worked.:D

---

### Post by ACGarib on 2006-11-11
GRRRRRRRRR!!!!

Sound for Flash 9 suddenly stopped working!!! I tried rebooting, reinstalling flash 9, and changing the firefoxrc file to auto, none, aoss, and a few others, but I can't get sound back! ](*,) 

When I run swiftfox in the terminal, I get the following errors:
ALSA lib pcm_direct.c:1123:(snd_pcm_direct_open_secondary_client) unable to open hardware

ALSA lib pcm_dmix.c:894:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:187:(make_local_socket) socket failed: Too many open files

Anyone know what I can do to get sound to work with flash 9 again?!

P.S.  Those sad faces are supposed to be : ( _ without the spaces

---

### Post by tommcd on 2006-11-12
Have you tried uninstalling flash 9 and going back to flash 7? I have been interested in flash 9 but I have been afraid of potential problems like this. My flash 7 is working fine as of now.

---

### Post by ACGarib on 2006-11-12
I ended up just going back to flash 7. The sound is stuttery but I'd rather have stuttery sound than no sound. I just hope that I can get the sound to work when flash 9 is officially released.

---

### Post by nodows on 2006-11-22
I'm having the same problem.  I'm running Edgy Kubuntu x86_64.  Flash is always a little tricky to get it to work in 64bit environments, so I'm not surprised.  Anyone have any ideas?

---

