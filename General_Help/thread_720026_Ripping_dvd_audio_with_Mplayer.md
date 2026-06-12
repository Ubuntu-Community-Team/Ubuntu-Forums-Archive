---
title: "Ripping dvd audio with Mplayer"
date: 2008-03-09
forum: General Help
---

### Post by pianoboy3333 on 2008-03-09
I'm trying to rip audio off of a dvd with mencoder, mplayer, or ffmpeg, can anyone help? I'm trying to keep it raw, or at least wav file format (which is raw, but not the same encoding as the audio on the dvd I mean)

---

### Post by yabbadabbadont on 2008-03-09
```
mplayer -vc null -vo null -ao pcm:fast:wavheader:file=NameOfYourFile.wav dvd://1
```

Replace "dvd://1" with the correct value for the title you wish to rip.

Edit: If you use something like vobcopy to rip the title off of the dvd into a single vob file, then you can use ffmpeg to extract the raw ac3 audio like so
```
ffmpeg -i YourVOBFile -vn -acodec copy YourNewAudioOnlyFile.ac3
```

Edit2: You may need to use the "-map" option with ffmpeg if there is more than one audio track in the VOB file.

---

### Post by pianoboy3333 on 2008-03-10
> **yabbadabbadont said:**
> ```
mplayer -vc null -vo null -ao pcm:fast:wavheader:file=NameOfYourFile.wav dvd://1
```

Replace "dvd://1" with the correct value for the title you wish to rip.


that didn't work, I got

```

Could not parse arguments at the position indicated below:
fast:wavheader:file=elmocambo2.wav
     ^

```

---

### Post by yabbadabbadont on 2008-03-10
Sorry, typo on my part.  It should have been "waveheader".

(which the man page would have clarified for you...  ;))

---

### Post by pianoboy3333 on 2008-03-10
ehhh who has the time to read those :)

---

### Post by eadmaster on 2008-03-20
try this:
```
mplayer dvd://... -dumpaudio -dumpfile filename.ac3
```
I tested this method with a single VOB file and it works fine.
I haven't tested with a full DVD yet.

AFAIK the ripping should be lossless.

---

