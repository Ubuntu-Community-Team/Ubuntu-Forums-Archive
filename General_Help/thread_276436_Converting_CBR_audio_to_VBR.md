---
title: "Converting CBR audio to VBR"
date: 2006-10-12
forum: General Help
---

### Post by cptjaben on 2006-10-12
I have some mp3's that are constant bit rate and apparently my mp3 player cannot play them as i get an playback error message. Is there any way i can convert these CBR files to variable bit rate files? Thanks in advance.

---

### Post by MNCaudill on 2006-10-12
Two things:

Probably 99.9% MP3 players handle CBR with no problem at all as it is the easiest to handle. VBR takes a little more work on the decoding end of things. My guess is that something else is wrong besides the files being in CBR. 

Second thing:
Whenever you convert a lossy format to another lossy format (CBR MP3 to VBR MP3, for example) you can get a fairly significant loss in quality. If you can get your hands on the original CD/WAV/SHN/FLAC file and then encode to VBR MP3 from there, you should.

What exactly was the playback error message that you got? What player are you using?

---

### Post by jethro10 on 2006-10-13
I would agree, CBR should be read by 100% of mp3 players.

VBR is quite patch and can give other errors like the length of the song looking wrong etc.

your problem probably lies elsewhere.

J

---

### Post by cptjaben on 2006-10-13
alright thanks for the info, i have a Creative Nomad xtra and i was trying to figure out why i could play all the cds but this one and it just soo happened that all the other ones were VBR and it was CBR. I'll look for another reason. Thanks again

---

### Post by meng on 2006-10-13
I have a Creative Nomad Extra also, and I can vouch for this NOT being a CBR/VBR problem. However, if I "remaster" the mp3 using lame, it works! I can't recall exactly what options I pass to lame, but you can play around with it and when I get home I can check my shell script.

---

### Post by cptjaben on 2006-10-13
hmmm... after reviewing my entire collection( about 230 albums) it appears that all the albums that are CBR also happen to not play on my Nomad, I don't know if that means it can't play CBR, but it's intresting that all the CBR albums aren't playable.

---

### Post by meng on 2006-10-13
My guess is that the Nomad is more dicey than other players when it comes to mp3 playback. I didn't think this was due to CBR, but now you've got me doubting myself!!

---

### Post by meng on 2006-10-13
I did this:
lame -h -b 48 (oldfile) (newfile)
for new (playable) 48kbps mp3s

---

### Post by NT4usB on 2006-10-13
I have ~20K tracks from various sources, CBR, VBR, 128K-320K...
All play in my Creative players. (NJB1 40GB, NJB3 80GB, Zen 80GB, MuVo² 4GB)
Some pop, skip, etc. All have been analyzed and repaired as required using MP3 Library.
I'm guessing you have some bad blocks or other corruption that's causing it.
Have you checked your files?
MP3 Lib will probably run in wine. (If I can ever beat the source code out of Trapper, I'm going to port it to Linux. Best dam utility for checking and tagging out there, imo.)
[MP3 Library]("http://www.jumpingcholla.com/jce_trapper.htm")
How did you rip them? What encoder did you use? What bit rate are they? iirc, Creative players won't play 32kbs files but no one encodes music that low...

---

### Post by meng on 2006-10-13
> **NT4usB said:**
> iirc, Creative players won't play 32kbs files but no one encodes music that low...
No, but some audiocasts are encoded that low, and they either play at "half-speed" or not at all on my Creative.

---

