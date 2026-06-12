---
title: "Some Program Help?"
date: 2006-10-15
forum: General Help
---

### Post by Topfs on 2006-10-15
Hi! I have picked up on ubuntu for a while now and I really like it but being new to linux and all so I don't know all good programs that probably is out there.

First of I use and like VLC but I would like a program thats more minimalist because I usually watch a serie or movie while playing a game or suring the internet and therefore I'd like the movie frame to be just the movie, nothing more but perhaps a seekbar, as possible with media player classic in windows. also it must be have a functional always on top :)

Also I really like most of the audio players, Quod Libet, Rythmbox, banshee player but one thing is rather irritating for me, I would like a command so I can just double click the file in nautilus and it starts to play with for example Qoud Libet and add it to queue but NOT to add it to my library as it does now.

Qoud Libet specific question: Is it possible to have the album list not to group albums with different artist but same album name?
Album name "Greatest Hits" is quite often used and it is a bit annoying when they fall under the same album when they infact aren't

---

### Post by hugmenot on 2006-10-15
Preventing the collapsing of Albums is in the QL FAQ, but that&#8217;s down ...

You need to add a "labelid" tag that is different for different discs. 
Greatest Hits labelid=xyz 8181818
Greatest Hits labelid=&#945;&#946;&#947; 321321

---

### Post by Topfs on 2006-10-16
Thx Mate, Will try it out when I get the chance, now I just need a better Video player :)

Peace

---

### Post by Kateikyoushi on 2006-10-16
> **Topfs said:**
> 
First of I use and like VLC but I would like a program thats more minimalist because I usually watch a serie or movie while playing a game or suring the internet and therefore I'd like the movie frame to be just the movie, nothing more but perhaps a seekbar, as possible with media player classic in windows. also it must be have a functional always on top :)

Try mplayer console, it doesn't have a gui so it seems  like what you are looking for. You can seek with arrow keys and it is just the video frame.

---

### Post by Topfs on 2006-10-16
Well that seems exactly what Im looking for, is it just to install with synaptic or is it extra for it?

---

### Post by Kateikyoushi on 2006-10-16
It is in synaptic, the only extra I would install is the win32codecs.

If you do not know how [this might help]("https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5").

---

### Post by Disastorm on 2006-10-17
you can separate the video from the controls in VLC.
[IMG]http://i8.photobucket.com/albums/a23/Disastorm/Random/vlcoutput.jpg[/IMG]

To do this in wxwidgets interface goto preferences, interface,general, wxwidgets, uncheck embed video in interface.  or you can just use skinnable interface which is under preferences, interface, general section.  then select skinnable interface under interface module.

---

