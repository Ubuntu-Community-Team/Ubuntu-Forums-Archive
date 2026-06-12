---
title: "ffmpeg2theora &quot;for&quot; loop trouble"
date: 2007-02-16
forum: General Help
---

### Post by kircher on 2007-02-16
Hi. I have been trying to get ffmpeg2theora to work in a loop to do multiple files one after the other to save me manually doing it for every single file. I have no idea what I'm doing/doing wrong with this loop. I tried the following commands in a terminal, but got errors doing it, or just got nowhere.

> james2@JAMES:~/Desktop/untitled folder$ for i in "*"; do ffmpeg2theora $i; done
Input #0, mpeg, from 'Beatles - Get Back (Rooftop Live).mpg':
  Duration: 00:03:21.5, start: 0.726700, bitrate: 1401 kb/s
  Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 352x240, 1150 kb/s, 29.97 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, 192 kb/s
  Pixel Aspect Ratio: 0.91/1   Frame Aspect Ratio: 1.34/1
  Resize: 352x240
      0:00:21.33 audio: 69kbps video: 512kbps

As you can see, it looks fine, but that Beatles file was the last file in the list of files I wanted to convert, but it named the newly encoded file with the file name from the file at the start of my list of files.

I then tried to do this:

> james2@JAMES:~/Desktop/untitled folder$ for i in `ls`; do ffmpeg2theora $i; done 

File Avalanches has unknown data format

the actual filename for that avalanches movie was "Avalanches - Frontier Psychiatrist.mpg" so for some reason it cut it off, but at least that time it was starting from the beginning of my list of movies.

I then did this:

> james2@JAMES:~/Desktop/untitled folder$ for i in `"ls"`; do ffmpeg2theora $i; done

File Avalanches has unknown data format

then this:

> james2@JAMES:~/Desktop/untitled folder$ for i in "`ls`"; do ffmpeg2theora $i; done

File Live).mpg has unknown data format

That time for some reason listed the last file in the list again. I then tried another approach. I decided to just put part of the filename of the first file in the list, hoping that it would continue the loop onto the next file. It completed the conversion of that file, but didn't continue on. This is what I put into the terminal that time.

> james2@JAMES:~/Desktop/untitled folder$ for i in "Avalanches*"; do ffmpeg2theora $i; done
Input #0, mpeg, from 'Avalanches - Frontier Psychiatrist.mpg':
  Duration: 00:04:23.2, start: 0.093333, bitrate: 2794 kb/s
  Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 320x240, 2582 kb/s, 25.00 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, 128 kb/s
  Pixel Aspect Ratio: 1.00/1   Frame Aspect Ratio: 1.33/1
  Resize: 320x240
      0:04:23.96 audio: 76kbps video: 469kbps

I tried a few other things, adding i+1 etc, but I just got errors, plus I was just guessing. I am pretty lost with this loop now. Does anyone know what I'm doing wrong?

---

### Post by yabbadabbadont on 2007-02-16
Try: ffmpeg2theora "$i"

---

### Post by kircher on 2007-02-17
Oh great, that seems to have fixed it. I first tried with "for i in "*"; do ffmpeg2theora "$i"; done" and got an error "File * has unknown data format", so I tried "for i in *; do ffmpeg2theora "$i"; done" and it worked. Anyway, thank you.

---

### Post by yabbadabbadont on 2007-02-17
You're welcome.  That's a common shell scripting mistake.

---

