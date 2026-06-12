---
title: "Shoutcast TV"
date: 2005-10-26
forum: General Help
---

### Post by chronusdark on 2005-10-26
does anyone know how to get a list of those shoutcast tv streams from linux so i can watch the streams in line vlc or something i know something will play it i just need to pull the list

---

### Post by bluemax on 2006-02-27
I've been looking for the same thing for a long time now. I've searched Google trying to find the host and port and protocol that's used to get the listing but could not find anything. I'm surprised that no one else has figured this out or posted it yet anywhere online.

I was planning to write a little app in Python or something to grab the listing, and then play a stream in VLC. However I can't even find the basic info to get Nullsoft's list of available streams. I need my Shoutcast TV! Come on people, someone else around here has to be wondering about this... Help!

---

### Post by bb002 on 2006-02-27
I just go to [www.shoutcast.com](www.shoutcast.com). Find the station I want. Download the file for the station I want to my desktop. Open the file and copy/paste one of the "File#=" lines into a player of my choice.  It is a bit of a hassle to do it this way but I have about 6 stations I listen to regularly and I have them all saved in Rhythmbox's radio section.

I know this is for music but I didn't know there was a shoutcast for TV. I would assume the process would be similar.

---

### Post by bluemax on 2006-02-27
Yeah, I know about shoutcast.com but unfortunately that site doesn't list the video/TV streams, only audio.

I was about to use a socket monitoring program under Windows to see where Winamp connects to to get the listing, but the program I installed to do that totally screwed up the WIndows LSP. Now my Windows installation has no working LSP and thus no internet connection. :evil:  :cry:

So right now I'm running Ubuntu again just trying to figure this out. I'll probably end up reinstalling Windows and try again to intercept the stream listing request with a more reliable socket monitor like Ethereal.

---

### Post by Browser_ice on 2006-08-20
I would like to know that too.

---

### Post by Browser_ice on 2006-08-20
I am a bit disapointed that in all the Ubuntu forums, only about 10 threads mention SHoutcast TV but none seams to actualy indicate if it is possible with Ubuntu. I am used to watching Shoutcast TV on WinAmp WIn-XP. I was expecting the same in Ubuntu.

Some of those thread talk about streamtuner but after installing it and visiting the home page, it is only for radio streaming.

So is Shoutcast TV possible with Ubuntu or not ?

---

### Post by bluemax on 2006-09-09
I'm sure this is possible. VLC can already play NSV (Shoutcast TV) streams. It's probably just a matter of querying some server somewhere for the list of available streams. As I mentioned in another thread about this, this is the ONLY thing keeping me from switching completely to linux.

---

### Post by creatix on 2006-09-20
are there any news?
is it still impossible to view to videos?

---

### Post by bluemax on 2006-09-30
Try this:

[http://ubuntuforums.org/showthread.php?p=1483211#post1483211](http://ubuntuforums.org/showthread.php?p=1483211#post1483211)

---

### Post by gunnard on 2006-10-20
[http://www.hiveproductions.com/shoutcast/getlist.php](http://www.hiveproductions.com/shoutcast/getlist.php)

---

### Post by cksthree on 2007-12-29
It's a little difficult to find, but Shoutcast support is built in. Launch VLC, then go to View and Playlist (or hit Ctrl+P).Once the Playlist window opens, go to Manage --> Services Discovery and check the boxes next to Shoutcast TV and Shoutcast. All the channels will load and you can start clicking and watching.

Hope this helps.

Cheers,

C.K.
[http://www.sampletheweb.com](http://www.sampletheweb.com)

---

