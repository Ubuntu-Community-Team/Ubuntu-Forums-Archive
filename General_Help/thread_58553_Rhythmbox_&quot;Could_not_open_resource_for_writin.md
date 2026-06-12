---
title: "Rhythmbox &quot;Could not open resource for writing&quot;"
date: 2005-08-20
forum: General Help
---

### Post by toships on 2005-08-20
Hi 

I have recently installed ubuntu and was trying to setup my music library from my windows xp ntfs partion.

I can play mp3 in my windows partion from mplayer. However when I try to get rhythmbox to do the same it gives me an error "Could not open resource for writing" and "Could not pause playback". 

I have already installed gstreamer08-mad and gstreamer08-plugins.

Any pointer would be helpful.
Thanks.
Santosh.

---

### Post by titus1950 on 2005-08-20
[QUOTE=toships]Hi 

I have recently installed ubuntu and was trying to setup my music library from my windows xp ntfs partion.

I can play mp3 in my windows partion from mplayer. However when I try to get rhythmbox to do the same it gives me an error "Could not open resource for writing" and "Could not pause playback". 

I have already installed gstreamer08-mad and gstreamer08-plugins.

Any pointer would be helpful.
Thanks.
Santosh.[/QUOTE]
I have installed Warty ,Hoary over the years,but if you want to realy play Mp3,rip Mp3,watch dvd's,avi ,svcd,etc...(I mean,realy have a multimedia O.S) start by doing this:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
Then:....

 Remove: Rhythmbox,Sound juicer and Totem gstreamer
And install something that realy  works;
First install **Xine** >[http://ubuntuguide.org/#xine-ui](http://ubuntuguide.org/#xine-ui)   (DVD's)
Then** Goobox**(from synaptic)  (Rip CD to Mp3,Flac,Ogg,(YOU control the bitrate!)
**Amarok**,is one of the best music players right now,and it works,make sure you install "amarok ENGINES" (Synaptic)  
and if you want to watch "Apple Movie trailers", yahoo news ,CBS news,BBC; install "**Mplayer**">[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)
And **Real playe**r>[http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer)
and don't forget this>[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
  [url]http://ubuntuguide.org/#codecs[/url
and for DVD's >[http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)

---

### Post by toships on 2005-08-20
[QUOTE=titus1950]
**Amarok**,is one of the best music players right now,and it works,make sure you install "amarok ENGINES" (Synaptic)  
and if you want to watch "Apple Movie trailers", yahoo news ,CBS news,BBC; install [/QUOTE]

While searching for the ans to the above question. I was looking into amarok. But got not get it working. However your reply did the trick. The apt-get install amarok does not install amarok engines on its ownk and it was complaining about the database. 

Thanks a lot. 
I would try the other players too..
bye.

---

### Post by doclivingston on 2005-08-21
Why does everyone always respond to "I have a problem with application X" with "install application Y", rather then trying to help fix the problem?


toships: can you open Preferences-> Multimedia Systems Selector, and see what it chosen under Audio->Default Sink? Also, do you hear anything when you press the test button?

If you can't hear anything when you press the test button, then the problem is that GStreamer can't get access to the sound card - exactly how to fix this will depend on what the default audio sink is.

---

### Post by toships on 2005-08-21
[QUOTE=doclivingston]
toships: can you open Preferences-> Multimedia Systems Selector, and see what it chosen under Audio->Default Sink? Also, do you hear anything when you press the test button?
[/QUOTE]

Hi doc 
I do hear the sound for the test. 

Well and the amarok works and I like its interface more than rhythmbox so I am going to stick to it for now...

Thanks for your response doc

---

### Post by doclivingston on 2005-08-21
If the test works, but Rhythmbox doesn't, something very odd is going on. But if you're happy with amaroK, it's probably not worth bothering trying to figure it out.

---

