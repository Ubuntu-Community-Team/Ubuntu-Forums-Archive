---
title: "Help with Ripping MP3&amp;ID3 Tags"
date: 2007-10-25
forum: General Help
---

### Post by Zackariah on 2007-10-25
Hi UbuntuForums,

Just a quick question.
I've got my Cd's to successfully rip as MP3, but it won't save the ID3 Tags with the .MP3 file, the program used for ripping gets all the track names, artist, track number .etc, can anyone give me the correct output for it save the tags with the mp3 when ripping, my current output is as follows
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192
```

Thanks!

---

### Post by jenkinbr on 2008-01-17
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3v2mux
```

Just append ```
 ! id3v2mux
``` to the end.

However, this seems to produce tags that are incompatable with my mp3 player.  Not entirely sure how to fix that, so if anyone can post a solution, that would be great.

---

