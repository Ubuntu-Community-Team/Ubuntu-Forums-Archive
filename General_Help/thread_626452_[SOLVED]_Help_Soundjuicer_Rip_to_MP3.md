---
title: "[SOLVED] Help: Soundjuicer Rip to MP3"
date: 2007-11-29
forum: General Help
---

### Post by Kristopher on 2007-11-29
I have looked through the forum and so far had no luck with what people had suggested. 

I cant rip to MP3 with Soundjuicer with Ubuntu 7.10 I tried adding a new profile called MP3 and did the following 

In Sound Juicer, go to "Edit" --> "Preferences", then down by "Output Format" click on "Edit Profiles". Add a "New" profile with the following;



Profile Name: MP3

Profile Description: MPEG Layer 3

GStreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=192 ! id3mux

File Extension: mp3



and tick the active box. 

But no luck I still cant see the profile MP3 in the main options as its stuck on ogg, help please. I might be missing something in the Synaptic Package Manager???

I have got lame installed “apt-get install lame” but nope.

---

### Post by mpierce on 2007-11-29
If you are having trouble with Sound Juicer, try grip. It's the package I use and I think it is the best but then I'm biased as it's my package of choice. It'll rip, look up song titles, convert, etc.

Hope this helps...

---

### Post by Kristopher on 2007-11-29
Thanks but i would like to use soundjuicer.

I managed to get it to rip to mp3, this is what i did, i was missing gstreamer0.10-plugins-ugly-multiverse 

sudo apt-get install lame
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse 

For 192kbps mp3s use - audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 ! id3v2mux

Close and re-open and select this under profile.

Hope this helps anyone else.

---

### Post by freewaybear on 2007-11-30
> **Kristopher said:**
> Thanks but i would like to use soundjuicer.

I managed to get it to rip to mp3, this is what i did, i was missing gstreamer0.10-plugins-ugly-multiverse 

sudo apt-get install lame
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse 

Thanks! that solved my long standing problem with soundconverter, I had LAME installed, but wasn't aware I was missing that part of gstreamer.

---

### Post by pkid on 2007-12-25
Thanks!  Solved my issue.

---

### Post by Irihapeti on 2007-12-26
Me too. I had only some of the plugins installed, and not lame - only liblame. Now it works.

---

### Post by bsmith1051 on 2008-01-03
thanks, this fixed it for me, too!

---

### Post by Auslegung on 2008-01-07
Solved my problem, too, thanks a ton!

---

### Post by Holleywood on 2008-01-08
> **Kristopher said:**
> 
sudo apt-get install lame
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse 

Hope this helps anyone else.

This solved my problem with Soundconverter also, thanks for sharing !!

---

