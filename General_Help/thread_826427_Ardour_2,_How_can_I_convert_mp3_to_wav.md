---
title: "Ardour 2, How can I convert mp3 to wav?"
date: 2008-06-11
forum: General Help
---

### Post by Vigh on 2008-06-11
Hi i've recently installed Ardour 2 audio editor, but all my music loops are in mp3 format, i presume wav files are compatiable with Ardour 2, are there any good linux programs for converting mp3 to wav. Thanks Anthony

---

### Post by dagnabit dang doohickey on 2008-06-11
If you have ffmpeg installed, the command for a simple conversion would be:
```
ffmpeg -i *inputfile*.mp3 *outputfile*.wav
```

---

### Post by Vigh on 2008-06-11
I was hoping for something with a GUI, for ease of use. Rather than typing a command for every single file. Something easy where I can select all the loops and directly convert them all in one hit. Cheers Anthony

---

### Post by dagnabit dang doohickey on 2008-06-12
This won't satisfy your gui needs, but I'm throwing this out there for anyone that wants to batch process a directory full of files using the command I previously posted.
```
for i in *SOURCEPATH*/*.mp3 ; do ffmpeg -i "$i" *DESTPATH*/"`basename \"$i\" | sed s/mp3/wav/`" ; done
```

---

### Post by zvacet on 2008-06-12
[Here #7]("http://ubuntuforums.org/showthread.php?t=731932&highlight=audio+convert")

---

