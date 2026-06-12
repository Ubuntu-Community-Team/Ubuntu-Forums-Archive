---
title: "Why can't I rip to mp3"
date: 2005-06-08
forum: General Help
---

### Post by alastair lewis on 2005-06-08
My portable player only supports MP3 & WMA. No FLAC or Ogg support. Therefore, MP3 encoding has become next on the to do list (having sorted Wifi with WEP and network printing, I came into this challange on a bit of a high....I have been brought back down to earth)

**Sound Juicer** 
I got gstreamer0.8-lame (v0.8.8-0.1), liblame0 (v3.96.1-1) and for good measure liblame-dev (v3.96.1-1).
Ran gnome-audio-profiles-properties, created MP3 and marked as active.
Pipleline currently says
'audio/x-raw,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192'
but has said lots of other things suggested in these fora.
Doesn't work, installed GRIP

**Grip**

Got  lame (v3.96.1-1). It's there it runs from the command line and ```
whereis lame
```
returns /usr/bin/lame
put this into the encoder executable but still get 'Invalid encoder executable. Check your encoder config'.

I would give up and buy an iPod, but
This would be admitting defeat
I can't afford one
I probably would have similar success with AAC encryption

Help please.

---

### Post by Musagetes on 2005-06-08
I had this problem aswell. Google fixed it, for some reason Sound Juicer isn't set up to make mp3's in advance, so you have to make a profile for it yourself. Easy as hell:

[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

---

### Post by alastair lewis on 2005-06-09
I have made the profile already, If I try to extract to mp3 I get the error
'Sound Juicer could not extract this CD.
Reason: Could not create Gstreamer encoder ((null))'

---

### Post by Nick Post on 2005-06-09
I actually stopped this struggle recently.  I'll get back to it.  I think I've got grip as my ripper, and I installed Wine so I could have DBpoweramp since I use wmas on my Sandisk DAP.  It is doing MP3s now, but I prefer WMA.

When I'm at home, I'll look and see what I'm actually doing.  Last CD I ripped I ripped to Ogg just to see if there was some benifit to it. I dont' see any besides the political glory of open sourceness, but I'd rather have my WMAs with twice the quality per kbps.

---

### Post by alastair lewis on 2005-06-17
Got it sorted after a clean install (messed up MBR, serious windows and minor ubuntu bloat so I decided to grasp the nettle)
Usuing the backport repository, the various lame plugins installed properly and work correctly.

Ubuntu rules.

---

### Post by hove99 on 2006-04-16
Super! This worked perfectly in Dapper! Thanks

---

