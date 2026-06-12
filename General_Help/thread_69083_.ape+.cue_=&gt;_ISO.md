---
title: ".ape+.cue =&gt; ISO?"
date: 2005-09-25
forum: General Help
---

### Post by GabrielWolff on 2005-09-25
How can I turn a disc image including an audio file (for example ape or flac) and a cue-sheet into an ISO image, or into anything that will let me burn it under Ubuntu?

Thanx

---

### Post by mlomker on 2005-09-25
Not sure.  Are you familiar with [cdemu](http://cdemu.sourceforge.net/), which allows you to mount a cue file as a disk?

---

### Post by StormBlast on 2005-10-20
Gnomebaker 0.4.2 (in breezy) burns CD from cue-sheets correctly. If you have FLAC/MonkeyAudio, you probably need to convert it to WAV and edit cue-sheet to change filename.

---

### Post by neonlug on 2005-12-05
I have converted all my .cue/.bin files to iso's with bchunk.

```
sudo apt-get install bchunk
```

Then I was able to mount the .iso file without issue.

---

### Post by GabrielWolff on 2005-12-11
[QUOTE=StormBlast]Gnomebaker 0.4.2 (in breezy) burns CD from cue-sheets correctly. If you have FLAC/MonkeyAudio, you probably need to convert it to WAV and edit cue-sheet to change filename.[/QUOTE]

Thanx, but there's no tool I found to either convert or play MonkeyAudio files.

Is there?

Gabriel

---

### Post by GabrielWolff on 2005-12-11
[QUOTE=StormBlast]Gnomebaker 0.4.2 (in breezy) burns CD from cue-sheets correctly. If you have FLAC/MonkeyAudio, you probably need to convert it to WAV and edit cue-sheet to change filename.[/QUOTE]


OK, I tried it, but got the following error message:

Cdrdao version 1.1.9 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.

ERROR: /home/gabriel/TÃ¶ne/Authentisch/Play.cue:2: Illegal token: W
/home/gabriel/TÃ¶ne/Authentisch/Play.cue:2: syntax error at "EOF" missing { Binary Motorola }

Any clue?

Gabriel

---

### Post by atti_simon on 2007-09-30
I had a .cue + .ape combination.
I found a way to transform the whole bunch into .ogg tracks.

First: 
With the .cue [view its content], you have to decompress the .ape to .wav.
There is a wonderful tool for this:
[http://www.legroom.net/software/apeinfo](http://www.legroom.net/software/apeinfo)
and
[http://sourceforge.net/projects/mac-port/](http://sourceforge.net/projects/mac-port/)

After compiling MAC and apeinfo, i simply used mac to decompress the ape into a wav:

```
[]$ mac CDImage.ape CDImage.wav -d
--- Monkey's Audio Console Front End (v 3.99) (c) Matthew T. Ashland ---
Decompressing...
Progress: 100.0% (0.0 seconds remaining, 468.8 seconds total)           
Success...
```

Second:
After that I started a new audio project in K3B, simply opening the cue file.
There I had the "Convert to other audio formats option" and I converted the "big" wav file into .ogg tracks, using the .cue file.

I'm on Fedora 7, I used K3B 3.5.7-21 with extras.

Hope this helps getting on the "thing" and transform the "ape+cue" to anything :)!

Good luck!

---

