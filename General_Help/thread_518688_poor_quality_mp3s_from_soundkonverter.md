---
title: "poor quality mp3s from soundkonverter"
date: 2007-08-06
forum: General Help
---

### Post by oliwally on 2007-08-06
I'm converting spoken word (not music) .wav files to mp3 format and have run into a little problem.

The wav files have a sample rate of 44100 Hz and convert to mp3 of 56kbps beautifully using Audacity with lame. Unfortunately Audacity also gives the the mp3 a new sample rate of 24000 Hz (and sometimes other). This means that some mp3 players won't play it (like my Sandisk Sansa). If appears that Audacity has no option to change the sample rate when exporting to mp3 (correct me if I'm wrong).

I then tried to convert the same wav file using soundKonverter (& lame), because it has an option to resample to 44100Hz. But at the same 54kbps and a 'strength' of 0 (best quality but veeeeery slow) the mp3s come out at a lesser quality than with Audacity. They sound quite 'phasy' if that makes sense. Not sure for the correct technical term for that kind of sound fault.

Could anyone suggest to me why one does a better job than the other, considering they are both using the lame codec?

How can I convince Audacity not to resample when exporting to mp3? Is it possible?

What do I need to adjust in SoundKonverter to get a better result (other than a higher bitrate)?

What other pieces of software can I use to get good mp3s that will play on my Sandisk?

---

### Post by oliwally on 2007-08-07
Can anyone help?:)

---

### Post by oliwally on 2007-08-12
Ok, after much experimenting I found that setting soundkonverter to "joint stereo" rather than stereo does the trick. Good mp3s of spoken word at 56kbps and 44100 Hz.

---

