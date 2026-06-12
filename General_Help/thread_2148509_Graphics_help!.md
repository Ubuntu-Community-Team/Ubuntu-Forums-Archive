---
title: "Graphics help!"
date: 2013-05-25
forum: General Help
---

### Post by Jabbar566 on 2013-05-25
Hello, i am new to Ubuntu. I just got it the other day. I do not have windows installed on my computer. I've been told that i need to update my graphics card driver. My graphics card is Intel 945G, and i can't find a download anywhere. Please help, thanks.

---

### Post by papibe on 2013-05-25
Hi Jabbar566. Welcome to the forum ):P

What version of Ubuntu are you running?
What problems are you experiencing with your current driver?

Regards.

---

### Post by Jabbar566 on 2013-05-25
Hello, thanks for the fast reply :D. I have the latest version of Ubuntu, 13.04 i believe? When i had windows XP with this same computer, i was able to play Team Fortress 2. Now, when i try to play it, i get an OpenGL error.  I had a look online, and it was suggested i update my drivers, but i can't find any. Thanks again.

---

### Post by papibe on 2013-05-25
Could you open a terminal, run this commands, and post the results?
```
lsb_release -a

apt-cache policy xserver-xorg-video-intel

lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau|i915'

apt-cache policy mesa-utils
```
Regards.

---

### Post by Jabbar566 on 2013-05-25
**_lsb_release -a_**No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring

_**apt-cache policy xserver-xorg-video-intel**_xserver-xorg-video-intel:
  Installed: 2:2.21.6-0ubuntu4
  Candidate: 2:2.21.6-0ubuntu4
  Version table:
 *** 2:2.21.6-0ubuntu4 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring/main i386 Packages
        100 /var/lib/dpkg/status






_**lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau|i915'**_xserver-xorg-video-intel:
  Installed: 2:2.21.6-0ubuntu4
  Candidate: 2:2.21.6-0ubuntu4
  Version table:
 *** 2:2.21.6-0ubuntu4 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring/main i386 Packages
        100 /var/lib/dpkg/status
jabbar@jabbars-computer:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring
jabbar@jabbars-computer:~$ lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau|i915'
snd_intel8x0           33096  2 
snd_ac97_codec        105692  1 snd_intel8x0
snd_pcm                80890  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
i915                  535507  4 
video                  18894  1 i915
drm_kms_helper         47545  1 i915
drm                   228750  5 i915,drm_kms_helper
snd                    56485  11 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device
i2c_algo_bit           13197  1 i915




**_apt-cache policy mesa-utils_**mesa-utils:
  Installed: (none)
  Candidate: 8.0.1+git20110129+d8f7d6b-0ubuntu2
  Version table:
     8.0.1+git20110129+d8f7d6b-0ubuntu2 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring/universe i386 Packages

---

### Post by papibe on 2013-05-25
Thanks.

You just may need to install mesa-utils. To do it, run these commands:
```
sudo apt-get update

sudo apt-get install mesa-utils
```
Hope it helps. Let us know how it goes.
Regards.

[INDENT]**Caveat**: Your card, as most cards, support 2 mayor graphic libraries: DirectX and OpenGL.Yours supports up to DirectX 9 and OpenGL 1.4 (read about it [here]("http://www.intel.com/products/chipsets/gma950/")). Team Fortress 2 most certainly uses DirectX in Windows. Unfortunately due to the fact that Ubuntu/Linux only supports OpenGL, and that your card only offers support for an old version of OpenGL, you may not going to have complete hardware acceleration.

'mesa-utils' may solve the OpenGL dependencies, but I'm afraid is going to be software emulation. i.e., slower that Windows.

[/INDENT]

---

### Post by Jabbar566 on 2013-05-25
Thanks for your help, but the problem is still there. Any other suggestions, apart from buying new pc/parts?

---

### Post by papibe on 2013-05-25
Sorry to hear that.

Could you run this command on a terminal, describes what graphics do yo see, and also paste any outpur from the terminal?
```
glxgears
```
Regards.

---

### Post by Jabbar566 on 2013-05-26
I see three spinning gears, no stuttering or anything, it's smooth. I also get this in terminal:

Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
273 frames in 5.0 seconds = 54.572 FPS
301 frames in 5.0 seconds = 60.020 FPS
301 frames in 5.0 seconds = 60.020 FPS
301 frames in 5.0 seconds = 60.019 FPS
301 frames in 5.0 seconds = 60.019 FPS
301 frames in 5.0 seconds = 60.020 FPS
301 frames in 5.0 seconds = 60.020 FPS
301 frames in 5.0 seconds = 60.014 FPS
299 frames in 5.0 seconds = 59.625 FPS
301 frames in 5.0 seconds = 60.016 FPS
262 frames in 5.0 seconds = 52.245 FPS
303 frames in 5.0 seconds = 60.419 FPS
302 frames in 5.0 seconds = 60.222 FPS
301 frames in 5.0 seconds = 60.018 FPS
301 frames in 5.0 seconds = 60.017 FPS
301 frames in 5.0 seconds = 60.023 FPS
301 frames in 5.0 seconds = 60.015 FPS
301 frames in 5.0 seconds = 60.022 FPS
301 frames in 5.0 seconds = 60.020 FPS
301 frames in 5.0 seconds = 60.023 FPS
297 frames in 5.1 seconds = 58.443 FPS
303 frames in 5.0 seconds = 60.418 FPS
301 frames in 5.0 seconds = 60.022 FPS
301 frames in 5.0 seconds = 60.020 FPS
301 frames in 5.0 seconds = 60.016 FPS
301 frames in 5.0 seconds = 60.023 FPS
301 frames in 5.0 seconds = 60.018 FPS
301 frames in 5.0 seconds = 60.022 FPS
302 frames in 5.0 seconds = 60.220 FPS
301 frames in 5.0 seconds = 60.019 FPS
301 frames in 5.0 seconds = 60.021 FPS
301 frames in 5.0 seconds = 60.019 FPS
301 frames in 5.0 seconds = 60.004 FPS
301 frames in 5.0 seconds = 60.033 FPS
301 frames in 5.0 seconds = 60.022 FPS

               Do you need the rest? Because it keeps going.

---

