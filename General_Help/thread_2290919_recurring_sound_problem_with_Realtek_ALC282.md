---
title: "recurring sound problem with Realtek ALC282"
date: 2015-08-16
forum: General Help
---

### Post by headflux on 2015-08-16
Hi All,

I have a problem that I hope someone can help with.

I've recently bought a Gigabyte P35 v2-CF4.  I installed Ubuntu alongside Windows 8.1. Everything worked fine except I had no sound.  After much research, I was able to fix the sound problem by following this thread:

[http://ubuntuforums.org/showthread.php?t=2280056&page=2](http://ubuntuforums.org/showthread.php?t=2280056&page=2)

However, that then caused a new problem: some of the system setting icons were missing!  So after some more research, I was able to fix this problem by following  the instructions in this link: [http://askubuntu.com/questions/453440/missing-system-settings-after-removing-some-packages](http://askubuntu.com/questions/453440/missing-system-settings-after-removing-some-packages)

My problem is that now the sound is not working again.  i can't follow the original thread, because I've already implemented that fix...

Any ideas?

My sound card is a Realtek ALC282 and I'm using Ubuntu 15.04

I should point out that whilst I've been using Ubuntu a long time, I'm not very technical, so please explain things like I'm a noob

Thanks in advance.

---

### Post by headflux on 2015-08-17
Hi,

As an update to the attached, I backed out the change described here: 

[http://ubuntuforums.org/showthread.php?t=2280056&page=2](http://ubuntuforums.org/showthread.php?t=2280056&page=2) 

by removing the line: 

options snd-hda-intel model=3stack

from etc/modprobe.d/alsa-base.conf.  I then rebooted, and the sound immediately worked.

However, on subsequent reboots, the sound does not work, so it seems unable to recognise my sound card / settings on each reboot.

Any ideas anyone?

Thanks

---

### Post by headflux on 2015-08-17
HI,

So think I've fixed this problem...

I re-added the line 

options snd-hda-intel model=xxxx

to etc/modprobe.d/alsa-base.conf

except the where xxxx, I added my sound-card model from here: [http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt)

Sound has now worked after a couple of reboots, so it looks like that has done the job.  

Hope this is useful to others.

---

### Post by michael.m.morrison on 2016-02-03
Would you mind checking to see what you put for your model parameter?

I have a Gigabyte P35v4 and have been unable to get sound to work thus far.

Thanks!

---

### Post by tony-runescape on 2016-03-08
I would also like to know exactly what you put for the model parameter as I have a Gigabyte P25X v2 which has been giving me a very hard time with multiple sound issues.
From that table it looks like these are the model choices for the ALC282:

```
ALC22x/23x/25x/269/27x/28x/29x (and vendor-specific ALC3xxx models)
  ======
laptop-amic             Laptops with analog-mic input
laptop-dmic             Laptops with digital-mic input
alc269-dmic             Enable ALC269(VA) digital mic workaround
alc271-dmic             Enable ALC271X digital mic workaround
inv-dmic                Inverted internal mic workaroundheadset-mic        Indicates a combined headset (headphone+mic) jack
headset-mode            More comprehensive headset support for ALC269 & co
headset-mode-no-hp-mic  Headset mode support without headphone mic
lenovo-dock             Enables docking station I/O for some Lenovos
hp-gpio-led             GPIO LED support on HP laptops
dell-headset-multi      Headset jack, which can also be used as mic-in
dell-headset-dock       Headset jack (without mic-in), and also dock I/O
alc283-dac-wcaps        Fixups for Chromebook with ALC283
alc283-sense-combo      Combo jack sensing on ALC283
tpt440-dock             Pin configs for Lenovo Thinkpad Dock support
```

I don't quite understand this though. Is the model "ALC22x/23x/25x/269/27x/28x/29x" and then those other things are options? Or are the "laptop-amic", "laptop-dmic", etc things the models?
My best guess would be to use "laptop-amic", but I would much prefer to get exactly what you used.
Also if you could post what are the other changes you've made which you haven't reverted, I would appreciate that a lot.

---

### Post by QDR06VV9 on 2016-03-08
I have 3 Sound cards here so the confusion was bit daunting... this is the method I use to configure mine.
[http://ubuntu4me.blogspot.ca/2012/03/ubuntu-default-sound-card-select.html](http://ubuntu4me.blogspot.ca/2012/03/ubuntu-default-sound-card-select.html)
Hope this helpful to other as well...Kind regards

---

