---
title: "any good media playes for gnome?"
date: 2007-04-16
forum: General Help
---

### Post by blocky on 2007-04-16
I have a large (~35gb) music collection, and I'm trying to find a media player I can use to manage it. Currently I'm using rhythmbox, but it doesn't support gapless playback, which is quite noticable on certain albums. I tried amarok but it crashes when I type anything in the search box. Are there any players with good library management systems that can do gapless playback?

---

### Post by chakkaradeep on 2007-04-16
> **blocky said:**
> but it doesn't support gapless playback, which is quite noticable on certain albums. 

I use RhythmBox and I find it easy and simple. I didnt quite understand *gapless playbacks*. Can you please explain that ? :(

---

### Post by spankymasterc on 2007-04-16
Man Songbird is awsome! trust me its a good player.... best one ive seen and its nice 2

---

### Post by chakkaradeep on 2007-04-16
> **spankymasterc said:**
> Man Songbird is awsome! trust me its a good player.... best one ive seen and its nice 2

Yes, I agree, but never tried in Ubuntu, I may install it now using Automatix :guitar:

---

### Post by spankymasterc on 2007-04-16
its good i compiled it and installed it and damn better then amarok and anyone ive seen so far only thing if it doesnt playback u need to install some things but the website gives you everything you need.... tells you what u need i think u need to install Gstreamer plugins [http://publicsvn.songbirdnest.com/trac/wiki/SettingUpGStreamer](http://publicsvn.songbirdnest.com/trac/wiki/SettingUpGStreamer)

there u go ::cheers::

---

### Post by chakkaradeep on 2007-04-16
Ok, Installed SongBird using Automatix2 in Feisty ! Working Good !...Now, lets rock baby :guitar:

---

### Post by spankymasterc on 2007-04-16
Noice! im on Feisty 2 and it works great Hey how did u install Automatix?

nvm found it

and i also have a large collection of music roughly 31 gigs :D ::cheers:: and install Songbird if u need help hit me up

---

### Post by hardyn on 2007-04-16
i have been pretty happy with amarok.
its in the repos.

---

### Post by vanadium on 2007-04-16
"Gapless playback" is where two different tracks can be played one after another with a seamless transition. Gapless playback is'n much of an issue for pop songs that fade to silence at the end. However, it is a big issue for playing back albums with continuous transitions between the tracks, think of Pink Floyd, The Wall, the Beatles, Abbey road, or Madonna, Like a Prayer (in some places). It is even a bigger issue for classical music. Read all about here at wikipedia: [http://en.wikipedia.org/wiki/Gapless_playback](http://en.wikipedia.org/wiki/Gapless_playback). 

Despite the huge amount of media players out there, this highly critical feature (for audiophiles) is only available in very few players, sometimes only through a separate plug in.

I am coming from Windows XP where I used Foobar. The only gapless solution I found to be working under Ubuntu is the one mentioned on the Wikipedia page: "XMMS Crossfade Plugin: Highly configurable plugin for XMMS and Audacious.". Both XMMS and the plugin install conveniently from the Synaptic package manager. XMMS is a media player that copies the Winamp interface. This means that it is not quite up to date for media library management: it is playlist based/ However, gapless playback is far more important to me than media library management, and thus I use XMMS. It is a pitty that Rhythmbox does not support gapless playback while very recently, Itunes started to support it.

Amarok probably supports gappless playback for file formats that truly support gapless, such as WAV and OGG. However, mp3 gapless features depend on a "trick" implemented by lame encoders. Amarok does not support gapless for mp3.

Aqualung is an audioplayer which lists gapless playback as one of its core features, but I could not install it with my limited Linux knowledge: it is not in synaptec, and when I tried installing the Debian package, one of the needed dependencies would not be up to date on Ubuntu Edgy. I will surely check this out when I am a bit more proficient with Linux (and probably it will get into the Ubuntu repositories soon)

---

### Post by chakkaradeep on 2007-04-16
> **spankymasterc said:**
> Noice! im on Feisty 2 and it works great Hey how did u install Automatix?


[Here it is]("http://www.getautomatix.com/wiki/index.php?title=Installation")

---

### Post by doclivingston on 2007-04-16
> **blocky said:**
> I have a large (~35gb) music collection, and I'm trying to find a media player I can use to manage it. Currently I'm using rhythmbox, but it doesn't support gapless playback, which is quite noticable on certain albums. I tried amarok but it crashes when I type anything in the search box. Are there any players with good library management systems that can do gapless playback?

The development version of Rhythmbox (svn) has gapless playback (and cross-fading), but it's not in any release yet. So you'll have to wait until Feisty+1 or a backport to get it.

I don't know of any other players besides Amarok which do gapless, but there probably are some around.

---

