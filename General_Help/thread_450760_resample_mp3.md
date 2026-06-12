---
title: "resample mp3"
date: 2007-05-21
forum: General Help
---

### Post by richardjennings on 2007-05-21
can anyone help me resample an mp3 from 48khz to 44.1khz?

i have tried using lame on the command line but couldnt get it to work.

---

### Post by DigitalAxis on 2007-05-22
Try installing sox.  It's an extremely powerful utility (a bit like using a sledgehammer on a nail) but it should work.

**sudo aptitude install sox**

Sox runs on the commandline, and should be useable like so:

**sox  *infile.mp3* -r 44100 *outfile.mp3* resample -ql **
resample -ql requests the highest **q**uality resampling (you can also try -q and no switch at all), -r specifies the output sample **r**ate.

Sox will use LAME to encode the final mp3 file.

If it complains about not being able to encode mp3s like mine just did while I tested this, just change the outfile extension to .wav and then encode that wave file with LAME.

---

