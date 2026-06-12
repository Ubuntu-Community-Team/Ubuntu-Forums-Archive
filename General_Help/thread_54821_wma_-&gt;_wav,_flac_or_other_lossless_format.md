---
title: "wma -&gt; wav, flac or other lossless format?"
date: 2005-08-06
forum: General Help
---

### Post by rjs on 2005-08-06
Hey,

Does anyone know of any scripts/applications to convert wma to wav? I've found several different things which will convert to vorbis or to mp3, but my googling has not found any that work will convert to a lossless file.

My problem is that my university provides taped lectures but only in wma. These tend to take up too much room, and have bad background noise problems. What i want to do is to take the wma, convert it to wav (or some other format conducive to editing), try to get rid of some of the background noise then save as speex.

I could convert to ogg vorbis, then from vorbis to wav, but i would prefer not to lose any more quality than need be.

thanks -
paz y amor,
-rjs

---

### Post by Sam on 2005-08-06
Try [audio convert](http://ubuntuforums.org/showthread.php?t=48007).

---

### Post by rjs on 2005-08-07
Thanks,

audio convert doesnt seem to be working however. I'll have to have an other try later when i have more time.

-rjs.

---

### Post by coreyreichle on 2008-02-11
mplayer -vc dummy -vo null -ao pcm:file=audio.wav {your original file name}

---

### Post by zvacet on 2008-02-11
@ **rjs**

To get audio convert to work 

```
sudo apt-get install mpg321 vorbis-tools
```

Then in synaptic find and install **nautilus-script-manager** and** nautilus-script-audio-convert**

```
nautilus-script-manager enable ConvertAudioFile
```

After that right click on audio file and you will see  ConvertAudioFile option.

Second solution is to install [pacpl](http://www.pacpl.org/) and if you have Amarok you wil have GUI.Othewise you will have to run it from CLI.

---

### Post by pedja_portugalac on 2008-02-13
I convert everything with Gnomes Sound Converter, including wma to wav or flac. I have previously installed every GStreamer plugin from mediubuntu repository. ;)

---

