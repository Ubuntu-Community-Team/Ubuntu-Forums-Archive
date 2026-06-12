---
title: "mpg123 / libao Jukebox"
date: 2005-07-08
forum: General Help
---

### Post by Ric_ on 2005-07-08
Hello all,

I've tried several ways of getting this working to no luck. I have a webjuke box in the office that uses mpg123 to play music in the office. People can request songs, skip, etc. etc..

However after upgrading to hoary some time ago its stopped working. The juke box i'm using is called otto. It requires me to run apache as my user (one of the odd things). However its mpg123 giving me the errors. mpg123 works great fromt he command line:

mpg123 song.mp3 and i get music!

However when otto calls this program (via perl) I get this

Can't find a suitable libao driver. (Is device in use?)

i've tried editing /etc/libao.conf and changing the device to oss or alsa and no joy!

Any one have a suggestion  :-? or a better web jukebox???

---

