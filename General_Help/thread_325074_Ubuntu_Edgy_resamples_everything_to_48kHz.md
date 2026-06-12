---
title: "Ubuntu Edgy resamples everything to 48kHz"
date: 2006-12-25
forum: General Help
---

### Post by reet on 2006-12-25
Hi, I am currently using Ubuntu Edgy on a computer with an M-Audio Audiophile 2496 sound card. I have searched high and low, but I can't figure out how to change the resampling option for alsa. By default, everything is resampled to 48kHz, which of course degrades the quality of all my 44.1kHz audio files. If I force the card to lock the sample rate at 44.1kHz using alsamixer, the sound is just slower because it's being resampled to 48kHz, then played at 44.1kHz. 

The best solution for me would be to have no resampling occur, but I can see why alsa would want to resample everything to the same rate using a software mixer so two programs can play audio simultaneously (hardware mixing on the Envy24 chip is not supported in Linux). So my solution is to change this default sample rate to 44.1kHz since the large majority of my audio files are 44.1kHz. However I cannot for the life of me figure out how to do this. I have tried creating an .asoundrc and a /etc/asound.conf file so force the rate, but to no effect. Running mplayer with -srate 44100 also still plays at 48kHz.

I found that there is an alsa plugin "rate_samplerate" that allows for a better algorithm to be used when resampling audio through dmix (I hope I'm getting this right), but it is not included in Ubuntu yet.

Has anyone found a solution to this for users that demand high quality audio and would like to respect all the bits of their recorded audio.

Below is my .asoundrc file:
```
pcm.2496 {
	type plug
	slave {
		pcm "hw:0,0"
		rate 44100
	}
}

pcm.dsp0 {
	type plug
	slave.pcm 2496
}

ctl.mixer0 {
	type hw
	card 0
}


```

---

### Post by reet on 2007-01-01
Bump. I'm still looking for an answer to this one. Thanks.

---

### Post by reet on 2007-01-01
I have just now compiled libasound2-plugins for Ubuntu from source so that I can use the rate_samplerate plugin. Very nice. I can now play the Udial sample from [here]("http://www.hydrogenaudio.org/forums/index.php?showtopic=9772") flawlessly. Without the better sample rate converter, there would be a "UIUIU" (sound it out) sound overlapping the dial tone. With rate_samplerate, conversion methods samplerate, samplerate_medium, and samplerate_best provide equal results. That is, flawless (or at least near flawless) playback. The downside is significantly higher CPU usage during audio playback.

The plugins were very simply to compile and install. I've attached libasound2-plugins that I have compiled on Ubuntu-Edgy. Howto use the samplerate plugin, from ALSA documentation:

You can use this rate converter plugin by defining a rate PCM with "converter" parameter, such as:

pcm.my_rate {
type rate
slave.pcm "hw"
converter "samplerate"
}

The plug plugin has also a similar field, "rate_converter".

Or, more easily, define a global variable "defaults.pcm.rate_converter",
which is used as the default converter type by plug and rate plugins:

defaults.pcm.rate_converter "samplerate"

Write the above in your ~/.asoundrc or /etc/asound.conf.

The following converter types are available:

- samplerate_best Use SRC_SINC_BEST_QUALITY
- samplerate_medium Use SRC_SINC_MEDIUM_QUALITY
- samplerate Use SRC_SINC_FASTEST
- samplerate_order Use SRC_ZERO_ORDER_HOLD
- samplerate_linear Use SRC_LINEAR

---

### Post by reet on 2007-01-03
Another update for anyone reading who is interested in this sort of thing.

I have found that by telling XMMS (or any program really) to use plughw it will bypass dmix and playback audio properly with no resampling! This is just great!

---

