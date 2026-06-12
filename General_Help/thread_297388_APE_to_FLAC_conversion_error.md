---
title: "APE to FLAC conversion error"
date: 2006-11-11
forum: General Help
---

### Post by dgorchak on 2006-11-11
Due to some problems with playing APE files in Amarok, I prefer converting audio to FLAC.
But I always get an error ](*,) See:

**#mac Hammerfall.ape Hammerfall.wav -d** //this one converts APE file to WAV

**#bchunk -w Hammerfall.wav Hammerfall.cue track** //this one splits the WAV file according to CUE sheet

**#flac track*.wav** //no doubt, this one converts everything into FLAC )

But every time I get an error like this:

**#track10.wav: 99% complete, ratio=0.616track10.wav: ERROR: unexpected EOF; expected 32608716 samples, got 32606208 samples**

P.S. Using CUE Splitter under Windows and then converting the result to FLAC works perfectly. I tried to use CUE Splitter under Wine, but it doesn't work.

Please, help me to solve this problem, I have no idea what to do.

---

### Post by ajm2005 on 2006-11-22
what happens if you convert the .wav file to .flac, and THEN slice it up according to the cue file?

---

