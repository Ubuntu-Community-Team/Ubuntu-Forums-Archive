---
title: "Read ID3 tag / meta tag info from AAC (m4a) file"
date: 2005-08-09
forum: General Help
---

### Post by shapelessplanet on 2005-08-09
Hurray! I've got things going rather well! Gotta say I'm liking this!
However, i've come across one problem.

I got AmaroK setup and while it's not my favorite, I'm getting used to it, and it's the best I've found thus far. I had to change to the XMMS engine, which resolved some playback problems. But, once I was finely able to add my AAC files to AmaroK, none of them have their ID3 tags! The only thing that shows up in the Amarok library is the Title. 

It works fine for my MP3s, but I only have 100 of those. The other 1,000 songs are AAC. I sure as hell can't go in and type all of these manually. Does anyone have a magic trick up their sleeve?

Speaking of AAC... Does anyone know of a way I can playback my Protected AAC files from the iTunes Music Store in Ubuntu? I can burn them to CD and rip them in Linux, but that's not exactly ideal, and I'll loose sound quality.

Thanks!
-Shapeless

---

### Post by SKLP on 2005-08-10
there used to be an application called Justetune that could decrypt protected AACs.
(not legal in some countries i think)

[http://www.nanocrew.net/?p=10](http://www.nanocrew.net/?p=10)

but it appears to be gone now
oh well...

---

### Post by shapelessplanet on 2005-08-10
That sucks that it's gone! Does anyone else know of a way I can play back protected AAC files from iTunes?

But more importantly, what do I need to do to make Amarok read the ID3 tags from my AAC files? I've got 1000+ songs and no information about the files. lol. Kinda hard to find my music without ID3 tags.

Thanks!
-Shapeless

---

### Post by Manny C on 2005-11-09
You need to install the proper gstreamer codecs to get your itunes files playing. I believe ffmpeg plugin contains the necessary decoders:
```
 sudo apt-get install gstreamer0.8-ffmpeg
```

JusteTunes was able to write the tags for the itunes files, but has been taken down for an unknown reason. I haven't been able to find another one. Still looking.

---

### Post by DoddyUK on 2005-11-15
[QUOTE=shapelessplanet]But more importantly, what do I need to do to make Amarok read the ID3 tags from my AAC files? I've got 1000+ songs and no information about the files. lol. Kinda hard to find my music without ID3 tags.
[/QUOTE]

I've been looking into that recently, and apparently it's not Amarok's problem. The problem supposedly lies with the [TagLib library](http://developer.kde.org/~wheeler/taglib.html) not having proper support for M4A files. It's the same reason why M4A aren't automatically added to the collection in Amarok.

---

### Post by eduardgrebe on 2005-12-11
[QUOTE=shapelessplanet]
I got AmaroK setup and while it's not my favorite, I'm getting used to it, and it's the best I've found thus far. I had to change to the XMMS engine, which resolved some playback problems. But, once I was finely able to add my AAC files to AmaroK, none of them have their ID3 tags! The only thing that shows up in the Amarok library is the Title. 
[/QUOTE]

Your best bet is to use Rhythmbox, which reads the AAC files' tags. A few fields are apparently not supported, such as Disc #.

---

### Post by sinaen on 2006-10-06
Can it write id3 tags to the filest to??
i have a bunch of audio-books that doesnt have tags and its a real nuicance :)

---

