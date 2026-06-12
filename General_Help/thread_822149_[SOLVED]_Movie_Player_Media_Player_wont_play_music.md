---
title: "[SOLVED] Movie Player/ Media Player wont play music"
date: 2008-06-07
forum: General Help
---

### Post by StandardsDT on 2008-06-07
I'm accessing my MP3 files that are on my Windows location and Movie Player and the Media Player just sit there. The progress bar does not move but yet it says its playing. I have the codecs installed so thats not an issue. Could it be that it cannot open files from the Windows location?

---

### Post by forger on 2008-06-08
have you installed all the codecs? how about the medibuntu.org w32codecs or w64codecs?
```
http://www.medibuntu.org/
```

---

### Post by forger on 2008-06-08
try this:
```
sudo apt-get install --reinstall mplayer mpg123 gstreamer0.10-fluendo-mp3 lame vorbis-tools flac ffmpeg liblame0 gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libdvdread3 gstreamer0.10-x
```

then **copy an mp3 to your home folder**, open up gnome terminal and do:
```
mplayer your-filename.mp3
```
paste the output here

then try play it from your windows directory using the command line and paste the output again, you can use the "cd" command to change directory.

---

### Post by StandardsDT on 2008-06-08
Thank You for providing that for me. That worked. Thank You for your help!

---

