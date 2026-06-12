---
title: "Convert wav to mp3?"
date: 2006-12-22
forum: General Help
---

### Post by xenoalien on 2006-12-22
How do I convert wav files to mp3?

---

### Post by jml on 2006-12-22
Ubuntu does not support MP3 format by default because it is not a totally free codec.  To enable MP# support, both for playing and encoding you will need to install two packages.  Lame anf gstreamer (i think the current version is 1.0)  These may not be in the supported repositories.  You may need to enable the Universe and Multiverse repositories in order to find them.  Once they are installed, Iusually restart, (this may not be necessary,) and MP3 support should be present.

Joe

---

### Post by shanepardue on 2006-12-22
If you already have the mp3 codec, amarok has a script you can get from the built-in script 
manager called "TransKode" that is really nice and convenient.

---

### Post by vzxa1 on 2007-12-25
##Converting .wav to .mp3 format##
##------------------------------##

## install lame:
sudo apt-get install shntool
sudo apt-get install lame    

#Example -> to convert Track02.wav ---to--> SpiritOfTheGreatHeart.mp3:

lame -V2 Track02.wav SpiritOfTheGreatHeart.mp3

#NOTE: no spaces in names^^^^

---

### Post by zvacet on 2007-12-25
You can try [this](http://viiron.googlepages.com/).You can run it from termminal or if you have Amarok installed add it to Amarok as plugin and you will in that case have GUI.My second pick will be nautilus-script-audio-convert(it is in synaptic).You have to install mpg321 and vorbis-tools first.

```
sudo apt-get install mpg321 vorbis-tools
```

After that go to the synaptic and install  nautilus-script-audio-convert.

You have to install nautilus-script-manager (from synaptic) and after thar run 

```
nautilus-script-manager enable ConvertAudioFile
```

and when you right click on audio file you will see ConvertAudioFile option.

---

