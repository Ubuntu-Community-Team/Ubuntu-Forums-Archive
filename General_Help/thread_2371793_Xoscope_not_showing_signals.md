---
title: "Xoscope not showing signals"
date: 2017-09-18
forum: General Help
---

### Post by mcman56 on 2017-09-18
I have Xoscopeloaded with 16.04 on a Gateway NE71B. It loads and seems to recognize the right and leftstereo sides of my sound card.  It does not recognize a USB soundcard I tried.  I built a probe adapter and when connected to anapproximately 10 hz source, I see nothing on the screen except somerandom noise.  The noise stays when I unplug the adapter.  I triedrandomly varying the scale, time base and sample rate with nosuccess.  I also tried [COLOR=#000000][FONT=&quot]padsp xoscope[/FONT][/COLOR]


Pulse Audio VolumeControl is also loaded.  It recognizes the stereo sound card and theUSB sound card.  When connected to the probe adapter/ 10 hz source, Isee a definite heart beat on the volume bar.  I can adjust thatvolume up and down.  The heart beat stops when I unplug the source. This works on both sides of the built in stereo sound card as well asthe USB mono card. 


Are there anythoughts on how I can get Xoscope to show those signals.

---

### Post by mcman56 on 2017-09-21
After trying everything I could find on line, I reloaded pulse audio and ran "padsp xoscope".  After slowing down the time scale several steps, the signals were there.  This seems linked to the lack of /dev/dsp.  I'm just not sure if it was the reload or something else I tried. 

Things tried:
sudo apt-get update
sudo apt-get install pulseaudio

sudo apt-get install pavucontrol
sudo apt-get install osspd
sudo apt-get install osspd-alsa  
osspd xoscope
sudo apt-get install alsa-oss
then type: aoss xoscope
sudo modprobe snd-pcm-oss

---

