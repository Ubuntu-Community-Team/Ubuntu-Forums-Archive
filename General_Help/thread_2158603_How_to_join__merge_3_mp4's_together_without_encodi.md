---
title: "How to join / merge 3 mp4's together without encoding or losing quality??"
date: 2013-06-29
forum: General Help
---

### Post by colobix on 2013-06-29
Hello. I've tried various different ffmpeg commands for this, and I feel like I have been sitting on google forever now.
So please help me.
All I wanna do is merge 1.mp4, 2.mp4 and 3.mp4 into one mp4 file.

---

### Post by vanadium on 2013-06-30
Due to the mp3 format, there is no easy way to do this in a "clean" way without transcoding the mp3. See here: [http://stackoverflow.com/questions/62618/what-is-the-best-way-to-merge-mp3-files](http://stackoverflow.com/questions/62618/what-is-the-best-way-to-merge-mp3-files). mp3wrap can combine multiple mp3's in one file, but the resultant file is not entirely compliant - contains specific info of mp3wrap. Depending on the player extra clicks may be introduced between tracks, time indications may not be correct, the file may play only partially ...

Further in that thread you see another approach: mp3cat to combine the mp3 dataframes, id3cp to copy the metadata, and vbrfix to update the mp3 header.

---

### Post by evilsoup on 2013-06-30
```
ffmpeg -f concat -i <(printf %s\\n "file '1.mp4'" "file '2.mp4'" "file '3.mp4'") -c copy output.mp4
```

Or, more comprehensively, create a file called 'files.txt' with line like:

```

file '1.mp4'
file '2.mp4'
file '3.mp4'

```

And then use ffmpeg's [concat demuxer](http://trac.ffmpeg.org/wiki/How%20to%20concatenate%20%28join%2C%20merge%29%20media%20files#demuxer):

```
ffmpeg -f concat -i files.txt -c copy output.mp4
```

This will only work if all the videos have the same frame rate, frame size, and a handful of other things. If that isn't the case, then you would need to re-encode.

---

### Post by vanadium on 2013-07-01
My bad: I read mp3 insted of mp4. Indeed, you can only combine losslessly if all clips have exactly the same properties.

---

