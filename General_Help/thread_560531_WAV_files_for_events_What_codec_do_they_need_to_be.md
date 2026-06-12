---
title: "WAV files for events: What codec do they need to be?"
date: 2007-09-26
forum: General Help
---

### Post by MementoMori on 2007-09-26
Not sure how noobish this question is.

I have a weird issue with WAV files in my Ubuntu flavor. My sound works and all, but I'm trying to use different sounds for my desktop events. Yet, not all of them seem to work properly. Some sound very lossy, some act very skippy and choppy and sped up, some come out loud and distorted, and some don't play at all. Most of my files will also cut off in play near the end. 

I figure this to be a codec issue, so I've tried converting them in Cool Edit Pro to several formats of WAVs as well as exporting them to WAV in Linux's equivalent thereof (the program's name escapes me right now. >.>). This comes out to various results, and the best I can do so far is get them to play at a lossy format that cuts off near the end. 

So, what format of WAV do I need to save them as for best results? I've tried ADPCM, Microsoft ADPCM, PCM u-Law, and Windows PCM, and I've also tried importing the sounds to my Windows partition to check what codec they're using only to find it closely matches one of the above. And I've also downloaded the w32codecs package already but it did nothing to help.

---

### Post by MementoMori on 2007-10-14
Anyone? ... Bueller?

---

### Post by richardjennings on 2007-10-14
I have never experimented with system sounds. They are not for me. But anyways, I checked the format of the sound files that play when I log in and log off.

here are the details:

Bitrare: 1411kbps
Codec: Linear PCM
Sample rate: 44100 Hz
Channels: 0 Channels


This is the information presented by naulitus if i goto /usr/share/sounds/ and right click shutdown.wav / audio

I hope that helps, I really have no idea what your problem is. Are you using a recent version of ubuntu, i.e feisty edgy dapper?

---

### Post by MementoMori on 2007-10-14
Linear PCM... I'll have to see what the closest codec in my Windows programs might be. Maybe that *will* help.

Thanks!

P.S. I'm using Feisty Fawn.

---

### Post by richardjennings on 2007-10-14
hey i found this article: [http://www.extremetech.com/article2/0,1697,2126234,00.asp](http://www.extremetech.com/article2/0,1697,2126234,00.asp)

seems it might have the answer to your conversion problems?

---

