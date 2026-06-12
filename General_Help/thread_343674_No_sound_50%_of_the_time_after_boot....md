---
title: "No sound 50% of the time after boot..."
date: 2007-01-21
forum: General Help
---

### Post by Mercury821 on 2007-01-21
Hi all,

My sound card doesn't seem to be detected half of the time when I boot into Edgy.  When I reboot, sound is detected with no problem.   Not sure where to check.  How can the system behavior change from one boot to the next? 

Thanks!

---

### Post by jpeddicord on 2007-01-21
Try running `sudo depmod` in a terminal. That *might* fix your problem.

Do you have a sound card? If so, what is the model? If not, what is your processor?

---

### Post by Mercury821 on 2007-01-22
I'm using my motherboard's built-in audio (MSI Neo2 Platinum).  The output from "aplay -l" shows:

card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

This is a mythtv box.. i'm wondering whether linux is detecting one of the tuner cards as a sound output device and assigning that as my default sound output instead.

I executed "sudo depmod" ... we shall see if this fixes the problem.  Thanks for the tip

---

### Post by jpeddicord on 2007-01-22
If the problem isn't fixed, here is another method that works with your sound card a little more directly:

```
sudo modprobe snd_hda_intel
sudo modprobe snd_intel8x0
sudo modprobe snd_intel8x0m
sudo depmod
```

You might get errors from running some of those, but in the end it *should* find the correct module for your card. Depmod and Modprobe commands were meant for installing and activating new modlues in the kernel, and running them again re-activates them. I find it is a quick and easy way to re-detect hardware also.

Jacob

---

### Post by Mercury821 on 2007-03-28
So I guess this problem I was having was never really fixed.  When my sound is not working, I get the following:

```

mythtv@mythtv:~$ cat /proc/asound/cards
 0 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xe9000000
 1 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xf0001000, irq 225
 2 [CK8S           ]: NFORCE - NVidia CK8S
                      NVidia CK8S with ALC850 at 0xf1000000, irq 193

```

and when my sound is working, I get the following:
```

mythtv@mythtv:~$ cat /proc/asound/cards
 0 [CK8S           ]: NFORCE - NVidia CK8S
                      NVidia CK8S with ALC850 at 0xf1000000, irq 193
 1 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xf0001000, irq 217
 2 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xe9000000

```

It looks like alsa can't make up its mind which card to assign to which number.  Is there anything I can do to make it set them up in the same order with each boot?

---

### Post by Mercury821 on 2007-03-28
Just did a little bit of googling and I might have come up with an answer.  Following the other entries in this file as a model, I added the following line to the end of /etc/modprobe.d/alsa-base:

```

options snd-cx88-alsa dsp_map=-2

```

Apparently this tells alsa not to assign my cx88 chip as card 0.  We'll see if this works...

---

### Post by ernstblaauw on 2007-04-27
> **Mercury821 said:**
> Just did a little bit of googling and I might have come up with an answer.  Following the other entries in this file as a model, I added the following line to the end of /etc/modprobe.d/alsa-base:

```

options snd-cx88-alsa dsp_map=-2

```

Apparently this tells alsa not to assign my cx88 chip as card 0.  We'll see if this works...

Did this work?

---

### Post by hackeron on 2007-08-29
No, it doesn't :(

---

### Post by BigCommieNat on 2007-11-18
Little late in coming, but I found the solution here:
[http://www.pchdtv.com/forum/viewtopic.php?p=9338&sid=27e2775f6013a6e442425837bab5469d](http://www.pchdtv.com/forum/viewtopic.php?p=9338&sid=27e2775f6013a6e442425837bab5469d)

quote:
I think this is a general problem with v4l-dvb and maybe this kind of driver in general. You should see the results when you get an saa card and a cx88 card cross-numbered (so one is /dev/video0 and /dev/dvb/adapter1 and the other is reversed)... system locks solid in MythTV.

Anyway, the cx88_alsa parameter is an array parameter, so you can pass

options cx88_alsa index=2,3

to get the first two cards to come up as alsa cards 2 and 3. But I don't know any way to get the cards to distinguish themselves from each other (e.g. by PCI slot).


Thanks nybbler!!!

---

