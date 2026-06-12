---
title: "Automatic Mp3 Tagger"
date: 2007-04-09
forum: General Help
---

### Post by KDayz on 2007-04-09
Does anyone know a free program I can use for Ubuntu that will tag my downloaded mp3s. It tags missing artist, albums and stuff. I need it to automaticlly tag mp3's by searching online.  A windows substitute is FixTunes but since i want to go pure Linux anyone know any subs?

---

### Post by Jump on 2007-04-09
I use easytag from Automatix. It works great.

---

### Post by compiledkernel on 2007-04-10
eh....

sudo apt-get install easytag 

No need to bother with automatix to install it for you.

---

### Post by KDayz on 2007-04-10
I used easytag and its not good. You have to select the tracks which are part of an album then it will search for you. it wont search each track individually. Anyone have any other ideas?

---

### Post by aysiu on 2007-04-10
Do the file names have any useful information?

**Useful information**:
The Beautiful South - 01 - Welcome to the Beautiful South - Song for Whoever.mp3

**Useless information**:
394785013.mp3

---

### Post by aysiu on 2007-04-10
According to [this website](http://www.wired.com/culture/culturereviews/news/2006/12/72304?currentPage=all), EasyTag and Kid3 should do what you want: > **EasyTag**
EasyTag, the first of the Linux apps we reviewed, gets the prize for easy installation. Users of Fedora can download it automatically using the yum utility. It features a "simple and explicit interface," a three-paned view for folders, track listings and tag details. The embedded player supports a wide range of audio formats, including FLAC and Ogg Vorbis.

*EasyTag does support automated lookups through freedb,* though album art retrieval is lacking at the moment. EasyTag does the basics well, with batch updating, and tag updating based on file name. But the basics are pretty much all it does. A new, unstable version promises support for album art and an updated look with a newer GTK graphic library.

**Kid3**
For those fond of a KDE desktop, Kid3 provides a solid tag editor. Kid3 can edit Ogg Vorbis and FLAC files in addition to the usual MP3s. The interface is clean, with an emphasis on a single folder view that shows ID3v1 and ID3v2 tags simultaneously.

*Kid3's automated tag import feature is nice -- it supports the new freedb servers as well as MusicBrainz and Discogs.* If you have album information lying around in CSV format, the editor can import that as well. Icons next to each track indicate the file's tag version. The basic fields are supported, but Kid3 lacks support for album art and lyrics. Updates for those fields would be helpful, but this editor makes a nice addition to the Linux desktop tool kit as it is now.

---

### Post by ign on 2007-08-27
maybe you should try piccard. read this thread for more info:
[http://ubuntuforums.org/showthread.php?t=174560&highlight=mp3+tagger](http://ubuntuforums.org/showthread.php?t=174560&highlight=mp3+tagger)

---

### Post by kostkon on 2007-08-27
*Cowbell Music Organizer* is an automatic tagger. I cannot say it's working perfectly, but it is exactly the type of application that you are looking for. You can find it in *Synaptic*. Maybe at [getdeb.net]("http://www.getdeb.net/") you will find a newer version, also check there.

There is a chance that you will experience memory leaking and locking of *Cowbell* when you try to load many mp3s at the same time. This is what is happening to me. Try to load one album every time, for example.

---

