---
title: "Whats the best format for music?"
date: 2008-06-08
forum: General Help
---

### Post by Tom--d on 2008-06-08
Whats the best format for music and why?

Not flac as the file size is high, but I do like it :D
Also, I have an ipod shuffle. What works with that?

---

### Post by Tixer on 2008-06-08
It all depends what you're looking for as far as music goes. FLAC is the best because it's compressed/lossless, and no data is lost. However, you're right, the file size is huge.

Since you're looking for smaller, lossless is out of the question. The best lossy algorithm out there is OGG Vorbis, which isn't supported by most players. So now, the question is "what will work with my player".

The answer is either something by apple (AAC is better quality than MP3), or MP3.

---

### Post by Tom--d on 2008-06-08
Right, I see now. 

Do you know if OGG is supported by the Ipod?

Is AAC > MP3?

---

### Post by ludicrous on 2008-06-08
I don't think ipods can play ogg out of the box. I've always been happy with high-bitrate mp3, like in the range of 192-256 kbps, with VBR. You probably won't get an appreciable difference unless you're using highish-end equipment anyway.

---

### Post by Tixer on 2008-06-08
Sorry, I meant to say AAC is better than MP3. Ogg Vorbis > AAC.

Dunno if  they can. I know some iPods can use Rockbox, which adds a lot of features, but no idea about the shuffle.

---

### Post by Tom--d on 2008-06-08
> **ludicrous said:**
> I don't think ipods can play ogg out of the box. I've always been happy with high-bitrate mp3, like in the range of 192-256 kbps, with VBR. You probably won't get an appreciable difference unless you're using highish-end equipment anyway.

MP3 with VBR? How do I do that? Is it better?

---

### Post by Tixer on 2008-06-08
VBR stands for Variable Bitrate. The idea is that rather than having every second encoded at high quality, the song will detect where quality isn't important (for example silence), or places where it can be reduced and you won't notice it as much. The idea is therefore that a song encoded at 320VBR might use the same space as 256CBR (constant bitrate), because the 320 fluctuates, but the 320 will sound better because there's higher quality at important places.

---

### Post by Tom--d on 2008-06-08
Right, I see. 

My gstreamer command for mp3 is:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 bitrate=192 vbr-quality=6 ! id3v2mux

Would that enable VBR? at a bitrate of 192 (is it worth going higher?)

---

### Post by fenian on 2008-06-08
Ipods won't play ogg files unless you replace the Apple firmware with third party firmware (Rockbox).
MP3 is the most widely accepted format and sounds o.k. if you use higher bit rates.If you want to be certain your audio files will play on any device use MP3.

AAC will give you results as good as (if not better) MP3 with significantly smaller file sizes.If you want to fit as much music with good sound quality on your Ipod AAC is the way to go.The drawback is that AAC may not be supported on as many devices.

Also to correct a common misconception AAC was developed by Fraunhofer IIS, AT&T Bell Laboratories, Dolby and Nokia not by Apple though they do use it as the default format for Ipods,Ipphones and the Itunes store (AAC is also the default format for the Playstation3 and Nintendo Wii).

---

### Post by Tom--d on 2008-06-08
Right ok. 

So AAC is better overall for my music.

Good file sizes?
Which bitrate is the best for that format?

---

### Post by fenian on 2008-06-08
Higher bit rates = Higher quality + larger file sizes.I would start with 160 kbs if the sound quality isn't good enough increase it (190).

---

### Post by bingoUV on 2008-06-08
If you convert to AAC, don't convert the MP3 to AAC. Convert FLAC/WAV to AAC. This is because quality has been lost in the FLAC/WAV -> MP3 conversion, that cannot be gained back. If you convert MP3 -> AAC, some further quality will be lost.

---

### Post by Tom--d on 2008-06-08
Ok, thank you all for helping me :)

---

