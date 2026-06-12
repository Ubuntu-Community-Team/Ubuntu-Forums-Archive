---
title: "Rhythmbox Extract CD always 31kbps mp3"
date: 2016-05-27
forum: General Help
---

### Post by darkeale on 2016-05-27
Hi all,

I'm trying to extract a CD as mp3 using Rhythmbox and for some reason the files produced are reporting as 31kbps no matter what settings I use to extract them. Although strangely the file sizes do change (i.e. are larger when I used the 320kbps setting). I didn't notice the same behaviour when using Fedora, and the files report as having a 31kbps rate on my MacBook too. To check the reported bitrate I am right clicking the file and choosing properties then checking the audio tab, or checking the file properties in Rhythmbox itself. It certainly doesn't sound like the audio quality is as low as 31kpbs so I'm assuming this is an issue with the metadata of the file.

I'm using Ubuntu 16.04. All up to date, using only base repos.

Any ideas?

Thanks!

---

### Post by mc4man on 2016-05-27
That seems to be the case for any & all mp3 encoding options in Rb. The files are encoded a chosen rate but something is askew in the frame headers where the bitrate index is stored.
Filed a bug for but don't hold breath- 
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1586516](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1586516)

Probably better to use a proper audio cd ripper.

---

### Post by darkeale on 2016-05-27
Hi,

Thanks for that. I've added myself to the bug report as well so we will see what happens!

---

