---
title: "Stream speaker output from Windows 7 to Ubuntu"
date: 2014-11-30
forum: General Help
---

### Post by quadrplax on 2014-11-30
I have a bit of an interesting situation, but basically my ubuntu powered server laptop is right next to my chair and it has really good speakers, so I was wondering if there was some way I could play the audio from my windows 7 pc through it's speakers over LAN. I use headphones a lot of the time but would like this to be an option I could easily enable/disable. My Windows 7 pc has realtek audio, and has stereo mix. Anyone know an easy way to set this up?

---

### Post by coldcritter64 on 2014-11-30
These couple of links may help you with a windows server for pulseaudio : [URL="https://www.cendio.com/pulseaudio"]
https://www.cendio.com/pulseaudio[/URL]  (the links to the zip files are down the page a bit) 
and 
[https://parseq.co.uk/wordpress/archives/setting-up-pulseaudio-1-0-beta-for-windows](https://parseq.co.uk/wordpress/archives/setting-up-pulseaudio-1-0-beta-for-windows) (an old link from 2011, the info may be of some help though)

If you can get a pulseaudio server on the windows box, playing a remote stream out the Ubuntu servers speakers should be relatively easy. 
I'm not sure how hard / easy the Windows side will be. I haven't been near a win install in near 5 years, so have not tested the info in either of those links; googled the links only. 

I have easily shared a pulseaudio stream from an Ubuntu laptop install to another Ubuntu desktop install, with good speakers, over a LAN very easily and effectively. Was able to watch video on my laptop screen with the audio coming out the desktop speakers perfectly. Pulse is very flexible if you can get something working in Windows.

---

