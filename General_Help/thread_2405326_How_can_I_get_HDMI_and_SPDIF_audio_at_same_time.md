---
title: "How can I get HDMI and S/PDIF audio at same time"
date: 2018-11-04
forum: General Help
---

### Post by allene222 on 2018-11-04
I am running Mythbuntu16 and have both a HDMI connected TV and a S/PDIF connected surround system. Normally we use the TV sound but sometimes like to switch on the surround system.  I have both outputs enabled in Alsamixer but can only get one or the other depending on which setting I pick in Myth audio setup or in pulse control panel.  The closest I can get to something usable is to select Pulse default in Myth and use Pulse audio control and manually select which of the two audio outputs I get but that is obviously a bit of a pain.  The HDMI is Nvidia card 1 device 7 and the S/PDIF is card 0 device 1.

I have tried some configurations using /etc/asound.conf and as far as I can tell it is ignored.  Specifically as a test I tried the settings I used when I was running Mythbuntu8 (below) with this hardware to play sound through the S/PDIF output and it continued to play through the HDMI output even with ALSA:default selected in myth audio setup.  Seems like Pulse overrode the asound.conf file

This did not play through the surround system when using ALSA Default setting in myth, it played through the hw:1,7 (HDMI).


```
pcm.!default {
	type plug
	slave {
		pcm "hw:0,1"
		format S32_LE
	}
}
```


I tried paprefs and it was a disaster. Myth became unstable, the audio was broken up, definitely not a solution. It also did not give simultaneous sound output even when setup to do so.

I also tried a simplified version of the Simultaneous Audio Output alsa tutorial which is what led me to do the test above to see if asound.conf was even used as my proposed setup did not show up in myth audio setup as I expected.

I would appreciate some guidance on how to solve this.

---

