---
title: "normalize-audio and mp3 files?"
date: 2015-01-26
forum: General Help
---

### Post by vasa1 on 2015-01-26
I installed normalize-audio (version 0.7.7-12) from the software center.

When I run ```
    for audio_file in *.ogg; do  
        normalize-ogg $audio_file;
    done  
```in a folder containing **ogg** files, the terminal shows me```
Decoding 1.ogg...
Running normalize...
Re-encoding 1.ogg...
Decoding 2.ogg...
Running normalize...
Re-encoding 2.ogg...
Decoding 3.ogg...
Running normalize...
3.ogg is already normalized, not re-encoding...
Decoding 4.ogg...
Running normalize...
Re-encoding 4.ogg...
```
But when I try the same thing with **mp3** files substituting **mp3** for **ogg** in the code, I see this:```
normalize-mp3: 1.mp3: no decoder available
normalize-mp3: 2.mp3: no decoder available
normalize-mp3: 3.mp3: no decoder available
```What am I doing wrong? Is there some additional specific software I need to install? Or does it have to do with how the software was compiled? **man normalize-audio** has this: ```
CAVEATS
       Note that your version of normalize-audio must be compiled with MAD library
       support to analyze MP3 file volume levels.
```

---

### Post by tgalati4 on 2015-01-26
Because mp3 is United States patent-encumbered, many utilities that could use mp3 must be recompiled (manually) to use the mp3 codec.  Sometimes installing LAME (LAME ain't an mp3 encoder) will satisfy the dependency.  Sometimes there is a configuration file that allows you to point to an mp3 encoder.

I'm sure if you download the source for *normalize-audio*, there is a [README]("http://normalize.nongnu.org/README.html") file that explains the situation.

---

### Post by vasa1 on 2015-01-27
> **tgalati4 said:**
> Because mp3 is United States patent-encumbered, many utilities that could use mp3 must be recompiled (manually) to use the mp3 codec.  Sometimes installing LAME (LAME ain't an mp3 encoder) will satisfy the dependency.  Sometimes there is a configuration file that allows you to point to an mp3 encoder.

I'm sure if you download the source for *normalize-audio*, there is a [README]("http://normalize.nongnu.org/README.html") file that explains the situation.
Hi, thanks for responding!

I installed LAME but the situation didn't change. The README pointed to a library available on a trial basis and not from the software center.

Meanwhile, I Googled for similar stuff and came across this: [http://askubuntu.com/questions/246242/how-to-normalize-sound-in-mp3-files](http://askubuntu.com/questions/246242/how-to-normalize-sound-in-mp3-files).

One of the answers has this simple code:```
normalize-audio -b *.mp3
```and that seems to run without any error. 
```
05:03 PM ~/Desktop/temp $ normalize-audio -b *.mp3
Computing levels...
 File1  99% done, ETA 00:00:00 (batch 100% done, ETA 00:00:00) 
Applying adjustment of -1.53dB...
 File1 100% done, ETA 00:00:00 (batch 100% done, ETA 00:00:00) 
05:03 PM ~/Desktop/temp $ 

```
I'm not an expert in audio stuff but the other answers there seem informative. I have Audacity installed.

(But my friend's "home theater" doesn't recognize .ogg and that's why I wanted to normalize mp3 files.)

---

### Post by tgalati4 on 2015-01-27
There is a switch in ID3 for mp3 files called "Replay Gain".  This is simply a value (like -3dB) that tells the music player to play this track at -3dB (3 deciBels lower than Unity gain--0 dB).  So if your player can read and understand "Replay Gain" then that is all you have to do--analyze the volume of the file and calculate a Replay Gain and insert it into the ID3 music tag.

Using *normalize-audio* or *normalize-mp3* the file is converted to *.WAV file (which is a full-bit, uncompressed, pulse code modulation, PCM file), then it is analyzed and re-encoded to mp3 at the lower (or higher) volume level.  This requires an mp3 codec, which is not normally installed on open software systems.  The mp3 patent allows for Royalty-Free use of mp3 for personal recording, but it is technically not allowed to be distributed with out a license agreement ($$$).

So, you have two ways to normalize the gain of an mp3 file--one relies on the player and no re-encoding and the other requires re-encoding with some loss in audio quality.

---

