---
title: "Command line program to record microphone in sub-second intervals...?"
date: 2013-03-26
forum: General Help
---

### Post by KingNeil on 2013-03-26
Hi.

Ubuntu 12.04 comes with the program "arecord".... which I can use on the command line to record from the microphone, for as little as 1 second, using the following command...

arecord -f dat -d 1 -D hw:0,0 output-file-here.wav

The "-d 1" option sets it to record for 1 second.

The issue is... I need to record for less than 1 second, maybe 0.1 of a second.

Does anyone know of a Ubuntu program that will let me do this..?

---

