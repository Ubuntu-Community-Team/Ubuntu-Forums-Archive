---
title: "Unable to get good, synced sound for flash"
date: 2005-07-16
forum: General Help
---

### Post by FishFace on 2005-07-16
Hi,

I've had lagged sound in flash for a while, but I finally got 'round to checking out the forums, and **have** got somwhere. I followed [these instructions](http://ubuntuforums.org/archive/index.php/t-22672.html) (bottom of page, the only bit from [http://ubuntuforums.org/showthread.php?t=26567](http://ubuntuforums.org/showthread.php?t=26567) that I did was to set up asound.conf) And got somewhere: sound in flash **is** synced correctly.

However, with the fix applied, sound is now awful - it's choppy, with the volume oscillating and with small crackles. I noticed that while playing flash, CPU usage now jumps to 50-90%, which it never used to. Sound in applications such as BMP is fine, so I must assume it's something to do with the wrapper layer, although that's all voodoo to me.

Here's a breakdown of what I've done:

[list=1]
[*]Installed libesd-alsa0 and alsa-oss
[*]Symlinked libesd.so.1 to libesd.so.0
[*]Created /etc/asound.conf, as follows: ```
pcm.card0 {
	type hw
	card 0
}

pcm.!default {
	type plug
	slave.pcm "dmixer"
}


pcm.dmixer {
	type dmix
	ipc_key 1025
	slave {
		pcm "hw:0,0"
		period_time 0
		period_size 1024
		buffer_size 4096
		periods 128
		rate 44100
	}
	bindings {
		0 0
		1 1
	}
}

pcm.dsp0 {
	type plug
	slave.pcm "dmixer"
}

ctl.mixer0 {
	type hw
	card 0
}

```
[*]Set FIREFOX_DSP to 'aoss' (both in the shell I started firefox from, and in the rc file)
[*]Killed esd
[/list]

Thanks for any help!

---

### Post by NeoChaosX on 2005-07-18
Change buffer_size to 8192 in /etc/asound.conf and restart ALSA. This seems to be the magic number (at least for me) to get Flash sound to work properly.

---

### Post by FishFace on 2005-07-18
I was just about to post that I'd fixed it by swapping the sizes for other values described in a different post :) Thanks anyway!

---

### Post by JPMaximilian on 2006-10-05
Could you post more specific instructions for syncing sound in flash?  I have the same problem, but I don' know how to do step 1-5.  Thanks!

---

### Post by JPMaximilian on 2006-12-09
Now that I've installed 6.10, flash seems to be synced.  Anyone else notice this?

---

### Post by NeoChaosX on 2006-12-09
That's because the Flash in Feisty is now the beta version of Flash 9, which ditched OSS for ALSA. This fixed the sound sync problems from Flash 7 and earlier versions.

---

### Post by JPMaximilian on 2006-12-09
I don't understand how that affects me, as I'm running Edgy?

---

### Post by NeoChaosX on 2006-12-09
...oh I completely brainfarted and got feisty and edgy's version numbers mixed up. D'oh.

However, I forgot that Edgy also got it's Flash plugin upgraded to version 9, and it's available in the official backports repos for edgy. So you've likely got Flash 9 installed instead of Flash 7.

---

### Post by JPMaximilian on 2006-12-09
I installed flash using Automatix, which uses beta 9.  That must be it awesome, thanks for the explanation.

---

