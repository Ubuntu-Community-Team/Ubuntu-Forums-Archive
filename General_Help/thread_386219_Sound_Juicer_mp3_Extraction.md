---
title: "Sound Juicer mp3 Extraction"
date: 2007-03-16
forum: General Help
---

### Post by Ziggy72 on 2007-03-16
I have a problem extracting audio CD files to mp3 in Sound Juicer. Extracting to ogg and flac works fine, but when the program attempts to extract and convert to mp3, the initial output file is created but then the program hangs. My gstreamer pipeline is: 

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=196 ! id3v2mux

I can extract and convert to mp3 using Grip so this is not a huge problem but it's irritating and I would like it fixed. When I was using dapper I could use Sound Juicer to extract and convert CD audio files but not that's not so with edgy.

Any ideas appreciated.

---

### Post by Ziggy72 on 2007-03-23
At last... the problem's resolved.

A number of people in this forum and elsewhere have suggested that the gstreamer pipeline for edgy should be:

audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc vbr=0 bitrate=196 ! id3v2mux

However, on my system encoding with this resulted only in noise...

But, the following pipeline *did* work:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc

Those of you who are having troble should give this a try. Good luck...

---

### Post by mik9dt on 2007-03-24
> **Ziggy72 said:**
> At last... the problem's resolved.

But, the following pipeline *did* work:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc.

Great, that fixed me up..... thanks for posting.:)

---

### Post by dedmonds on 2007-04-04
[FONT="Arial"]also worked for me. thanks.[/FONT] \\:D/

---

### Post by zvacet on 2007-04-04
Why don´t you use preset?
[https://help.ubuntu.com/community/CDRipping]("https://help.ubuntu.com/community/CDRipping")

---

### Post by Traap on 2007-04-08
Hello,

I use the "Sound Juicer 2.16.1". I apply your advice, but any way, a mp3 file around 60 Mg (In fact no compress) is still created.
I miss something, but what ?

If somebody could help me... Thank in advance.

---

### Post by Traap on 2007-04-08
Just a library forgotten  ( gstreamer-0.10-plugins-bad-muliverse and ugly-multiverse) . Works fine now.
Thanks.

---

