---
title: "Sound Juicer:  How to define VBR?"
date: 2007-03-04
forum: General Help
---

### Post by JimmyME on 2007-03-04
I've been ripping CDs in Sound Juicer at 192K bit rate and have been pleased with the performance.  I can rip a CD in 1:30 to 2:00 at 20-21x.

I'd like to rip in variable bit rate with an average around 192k.  Below is my config line.  How would I modify it to accomplish this?  Thanks!  JimmyME

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3v2mux

---

### Post by chggr on 2007-03-04
Try setting vbr=192 and bitrate=0

---

### Post by JimmyME on 2007-03-04
Hmm...

I tried that but the MP3s are showing up as fixed 128kbps on my MP3 player.  The player has showed fluctuating rates on MP3s made in Windows.

Recordings sound good, just that the bit rate isn't shown as varying.

---

### Post by chggr on 2007-03-05
Sometimes the mp3 players are wrong.

locate the mp3 file, right click and click on properties.
Select the audio tab and see what's written under Audio. 
CBR - Constant BitRate
VBR - Variable BitRate

If it still shows up as CBR, then try setting
vbr=1 bitrate=192
and see what happens...

---

### Post by JimmyME on 2007-03-05
Audio

Bitrate:  192 kbps

Codec:  MPEG-1 layer 3

nothing about VBR or CBR

This is in Nautilus

---

