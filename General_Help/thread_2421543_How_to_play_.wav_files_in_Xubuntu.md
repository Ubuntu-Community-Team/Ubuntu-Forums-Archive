---
title: "How to play .wav files in Xubuntu"
date: 2019-06-23
forum: General Help
---

### Post by Ralph L on 2019-06-23
I generally use VLC or Parole to play video files.  However, I have some .wav files that, when played with either VLC or Parole, have audio only--no video.  Would somebody explain how I can play .wav files with Xubuntu 18.04?  Maybe I don't have the proper codecs for .wav, but I don't know how to add whatever codec I need.

Thank for any help.

---

### Post by Artim on 2019-06-23
Use Synaptic Package Manager to install **Xubuntu-Restricted-Extras**! Or open a terminal and type

```
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by Dennis N on 2019-06-23
Use **aplay** from terminal or in a script.
Example:
```
aplay /home/dmn/bin/vincent-price-thriller-laugh.wav
```

---

### Post by ajgreeny on 2019-06-23
You appear to have overlooked the fact that .wav files are audio only; they do not, and can not, contain video.

What makes you think there should be video in them?

Have a look at one of the wav files either using ***mediainfo /path/to/file.wav*** or more simply with ***file /path/to/file.wav*** in terminal.

---

### Post by Ralph L on 2019-06-24
Thank you everybody that replied.  I did not know that .wav files were audio only.  I guess that I had in the past seen a video that included the audio I recognized, when I played the the .wav file.  I must have another file someplace that includes both the video and audio.  

Thank you for educating me.

---

