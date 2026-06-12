---
title: "How to play or convert .dav files?"
date: 2016-10-07
forum: General Help
---

### Post by MaximB on 2016-10-07
Hi,
How can I play or convert (to mp4, ogg, avi ...)  **.dav** files? (dav are video files from a security camera)

Thank You,
Maxim.

---

### Post by &amp;KyT$0P# on 2016-10-07
What have you tried so far?

---

### Post by howefield on 2016-10-07
I used the following command to convert a .dav file to .mp4 and although the terminal output contains a few errors the resultant .mp4 plays well enough.

```
ffmpeg -y -i ~Downloads/test.dav -vcodec libx264 -crf 24 -filter:v "setpts=1*PTS" ~/Downloads/test.mp4
```

The command can likely be improved.

---

### Post by colmax on 2016-10-07
Just wonder if vlc may handle it
It tends to work with many codecs
Cheers

---

### Post by MaximB on 2016-10-07
The VLC won't open .dav files.
The converted seems to have worked, however I see only black screen with a date on top (and seconds passing, movie playing) and "Cam 01" at the bottom.
The women who sent me the .dav file said she is able to view the playback from the camera, but we cannot see it after conversion.
Any reason why?

---

### Post by colmax on 2016-10-07
Suggest grab "the all in one codec pack" for vlc
Search "vlc dav codec"
Hope this helps
Cheers

---

### Post by howefield on 2016-10-08
If the file isn't confidential, which it probably is given it is from a securlty camera but if not can it be linked to ?

---

### Post by licus on 2017-05-17
I'd tried the solution of colmax but the output of the program FFmpeg gave me a lot of errors.

I tried in VLC player


[COLOR=#2e8b57][FONT=Monaco, Andale Mono, Courier New, Courier, mono]Tools &#8211; Preferences &#8211; Interfaz &#8211; All &#8211; Demuxers - Video H264 Demuxer - Load

Open first VLC and then load the archive, when I opened the archive first, VLC crashed

I hope this could be helpfull for you[/FONT][/COLOR]

---

### Post by nerunja on 2018-01-01
"Media Player" in Mint Linux 18.3 Slyvia is able to play the .dav files  fine by default. The media player shortcut is having the command as "xplayer %U"

---

