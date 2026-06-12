---
title: "HD 5770 audio?"
date: 2013-04-25
forum: General Help
---

### Post by Theredbaron1834 on 2013-04-25
So, I have an HD5770, and have been using the closed drivers since I got it, as I 'need" the hdmi audio (my only speakers are my TV's). I distro hopped a bit, but came back to Lubuntu for 13.04, as it is stil my favorite. Among the ones I have tried was Sabayon (I love portage), and it worked perfectly with the open drivers, with no settings needed, so I "know" audio over HDMI works with the open drivers.

 However, I just can't figger out how to do it with Lubuntu. I have added "radeon.audio=1" to the kernel parameters with no luck. 

It is actually even worse then it was. Back on 12.10 I could "see" the HMDI audio output ala pavucontrol, (though playback was borked if I used it) but now it isn't even there. I can see it with aplay -l
```
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

 but when I try to play something on it with aplay it says:

```
aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav
aplay: main:682: audio open error: No such device

```

So, does anyone know how I can get audio over HDMI on an HD 5770? Or will I have to stick to FGLRX?

---

### Post by gguillotte on 2013-04-26
> **Theredbaron1834 said:**
> So, I have an HD5770, and have been using the closed drivers since I got it, as I 'need" the hdmi audio (my only speakers are my TV's). I distro hopped a bit, but came back to Lubuntu for 13.04, as it is stil my favorite. Among the ones I have tried was Sabayon (I love portage), and it worked perfectly with the open drivers, with no settings needed, so I "know" audio over HDMI works with the open drivers.

...

So, does anyone know how I can get audio over HDMI on an HD 5770? Or will I have to stick to FGLRX?

Same issue here with an HD6130 (Zotac AD10 barebone). HDMI audio worked on it in 12.04 and 12.10 by adding lines to ~/.asound to specify the HDMI device as the default, but it doesn't work after updating to Lubuntu 13.04, or after a clean install of Ubuntu 13.04 stock. 

HDMI shows up in aplay -l but throws the same "No such device" error. HDMI doesn't show up in the Sound settings panel or in pavucontrol, and doesn't show up when running the open-source driver, flgrx, flgrx-updates, or a manual install of Catalyst. 

I've reverted to my 12.10 image and HDMI audio works fine once again.

---

### Post by Theredbaron1834 on 2013-04-30
Well, this seems to be a common problem with the kernel in Ubuntu 13.04. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169761](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169761)

Not sure if I am going to downgrade, or what. Might try an older kernel.

---

