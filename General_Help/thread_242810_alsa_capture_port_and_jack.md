---
title: "alsa capture port and jack"
date: 2006-08-24
forum: General Help
---

### Post by JuliusCaius on 2006-08-24
Hey there,

I've been trying to use Jack Rack for realtime sound processing, I'd like to feed it the signal from the mic in (I have an SBLive! card). I got as far as to narrowing down the problem to a single symptom: there's no output from alsa_pcm:capture 1 and 2. I even connected alsa_pcm:capture directly to alsa_pcm:playback, but nothing can be heard. I have in the alsa mixer the capture flag on the mic, and both the mic and the capture sliders are almost up to max. If I unmute the mic, I can hear the signal, so there's no problem there.

Thanks

---

### Post by sinpalabras on 2006-09-21
hi julius,i am having the same problem, are you an amd64 user? can you post your harware? mine is -athlon64 2800+
                       768 ram
                       80gb sata hd
                       asrock upgrade via 8237 onboard sound

 I am getting really](*,) ](*,) (if i find the answer i+ll post it) chau

---

### Post by sinpalabras on 2006-09-22
ok , it was the most basic thig, just check that pcm and line in are enabled on alsamixer, or better get alsamixer gui or gnome alsamixer from sinaptic. I also replace the volume control on the gnome panel for gnome alsamixser, so i have the icon on the tray to remmember were to look first  if i have trouble again. chau

---

