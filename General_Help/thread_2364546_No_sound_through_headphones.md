---
title: "No sound through headphones"
date: 2017-06-24
forum: General Help
---

### Post by oflittleimportance on 2017-06-24
Just installed Ubuntu last night and I can't get any audio from my headphones. The microphone also seems to not pick up any noise. I tried both the front and back panels and they both work fine on Windows 10. Looked through a bunch of different threads and nothing has seemed to work. Ran an alsa-info thing: [http://www.alsa-project.org/db/?f=2656d144f151e3a8fd9dad4afeaea89ee7332bc4](http://www.alsa-project.org/db/?f=2656d144f151e3a8fd9dad4afeaea89ee7332bc4) Not sure what else to do.

---

### Post by ajgreeny on 2017-06-24
Go **Sound Settings** from the volume icon in your panel and then in the **Output Devices** tab you may see the headphone volume is set too low; similarly in the **Input Devices** tab you may see the microphone is set too low.

All devices can be set with separate and different volumes (gain levels) in **pulseaudio-volume-control** which is the utility opened from **Sound Settings**

---

### Post by oflittleimportance on 2017-06-24
I've tried setting the volume to and above 100%, both in sound settings and in pavu control. Still nothing. The mic doesn't even show any feedback at all on the "input level" bar, even when I tap it or talk into it. I probably should have mentioned that I get noise through my tv with an hdmi cable. It's just my headphones that seem to be having trouble.

---

### Post by oflittleimportance on 2017-06-25
I didn't provide much information of my situation initially and I apologize for that. Here are some of the solutions I have already tried: 

Unplugging and plugging back in the headphones to both front and rear panels.

Muting and unmuting, and adjusting the volume levels in sound settings, alsamixer, and pavucontrol

     sudo alsactl restore

[This solution from the forums]([https://askubuntu.com/a/147603](https://askubuntu.com/a/147603))

[This other solution from the forums]([https://askubuntu.com/a/184954](https://askubuntu.com/a/184954))

And now, recently, [this solution from the forums]([https://askubuntu.com/a/622531](https://askubuntu.com/a/622531))

I did system restarts after each attempt. Now currently, after attempting that last solution, my headphones do not even appear as a playback device in sound settings, and are labelled as (unplugged) in pavu control. I have probably tried some other solutions, but I'm starting to lose track. I'm at my wit's end. I would really appreciate some help. If there is anymore information that I can provide that could be useful please let me know. My PC almost feels unusable to me without my headphones in use and I would be extremely grateful to anyone who could help me get them working again.

---

