---
title: "play command"
date: 2007-04-20
forum: General Help
---

### Post by jpgeerets on 2007-04-20
hi folks,

in "history" i used the command play form the clui.
with this command i could remote play audio-files (like audio cd, mp3, etc).
at this moment i have lost the command.

someone know how i can find this command so i can install it again on by ubuntu 6.10/7.04?

thanks in advance!!

Jean-Paul

---

### Post by energiya on 2007-04-20
you could tray "aplay".
> 
arecord, aplay - command-line sound recorder and player for ALSA sound-card driver


**edit:**
"play" (not "aplay") is part of [sox]("http://sox.sourceforge.net/").
> 
play and rec is a command line front end to  the  sox(1)  program. It will  play/record audio files to/from unix-style audio devices.  It can optionally apply audio effects to the file.


I thing you can find it in the repos or download the packages/sources from their [page]("http://sox.sourceforge.net/").

---

