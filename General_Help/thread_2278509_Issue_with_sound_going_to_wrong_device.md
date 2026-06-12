---
title: "Issue with sound going to wrong device"
date: 2015-05-17
forum: General Help
---

### Post by Hungry Man on 2015-05-17
I'm running elementaryOS, which is an Ubuntu derivative.

Recently after updating I had issues with sound. I get the 'beeps' when I turn volume up and down, but no sound from youtube or applications.

In VLC I was able to select the audio device, it was set to "Built in audio stereo (HDMI)" and I set it to "Built in audio stereo".

That worked, and VLC is now playing sound properly.  But that only applied to VLC, Chrome is still not playing sound, and I'm assuming it's set to the wrong device.

In my sound settings there is only "Speakers: Built In Audio", no HDMI devices.

This is a lenovo t540p. I've tried restarting pulseaudio. Not really sure what there is to do about this, but it's quite a pain. I realize I'm not running Ubuntu, but I would imagine the steps for handling this would be the same given that the underlying OS is quite similar.

---

### Post by dino99 on 2015-05-17
i've also got the same issues a few weeks back, on a system which had no hardware change since ages. And suddendly after some upgrades, pulseaudio has been very sensitive to bios settings (had to switch to 'hda' from 'ac97') and set to the right places the plugged jacks (strictly same colors) to get the sound played as expected.
Firstly using pavucontrol to check the 'output devices' and 'configuration' and talk with Chad, the above changes were looking logic.

---

### Post by Hungry Man on 2015-05-17
Awesome. Using pavucontrol I simply turned the HDMI device off, and Chrome is now working. Thanks!

---

