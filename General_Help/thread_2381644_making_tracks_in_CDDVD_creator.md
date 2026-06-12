---
title: "making tracks in CD/DVD creator"
date: 2018-01-03
forum: General Help
---

### Post by j3984 on 2018-01-03
I drag a folder of 20 files into cd/dvd creator making a data disc of mp3 files... but it wants to make 1 long track. How do I separate them??
btw  why does the data cd option work better than the audio disc option that you find in Brasero for making an audio disc of mp3 files....??

---

### Post by Holger_Gehrke on 2018-01-03
> **j3984 said:**
> I drag a folder of 20 files into cd/dvd creator making a data disc of mp3 files... but it wants to make 1 long track. How do I separate them??
You don't. A data disk holds one track of data in an ISO 9660 filesystem and possibly some audio tracks after that. If your CD-player can handle mp3 , it will play the mp3-files as if they were separate tracks (there's a lot of mobile CD-players starting from the very late 90s to  now which will play mp3; it's rather rare for stationary players; a lot  of DVD players can play mp3 data CDs, too). If it can't, it will skip the data track completely, unless it's a very old player which was built before the standard for data CD was made, then you will hear some horrible noise on the data track.
> **j3984 said:**
> btw  why does the data cd option work better than the audio disc option that you find in Brasero for making an audio disc of mp3 files....??
Because it just sets up a file system and puts the mp3 files as they are on that. The audio disc option in brasero decompresses the mp3-files and possible converts them to 44100 hz sample rate, stereo, 16bit per channel pcm and puts each audio file into a separate track on the disc. The advantage of a mp3 data CD is that you can fit several hours of music on it. The advantage of a real audio CD is that it works on all CD-players.

Holger

---

