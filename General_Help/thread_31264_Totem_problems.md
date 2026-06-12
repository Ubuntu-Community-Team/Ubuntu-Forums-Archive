---
title: "Totem problems"
date: 2005-05-02
forum: General Help
---

### Post by kiptinui on 2005-05-02
I'm using Totem to play video and I can hear the sound, but there's no picture. Other than that, the movie is playing fine.

I'm using totem-gstreamer at the moment, because totem-xine will not work (more on this a minute). 

So here's my setup: I've got Alsa Mixer selected in volume control, I have ALSA selected for audio default sink and source in the Multimedia Systems Selector. I have XWindows (X11/Shm/Xv) selected for video default sink and Video for Linux 2 (v4l2) selected for default source, although the test for this last one gives me a "Failed to construct pipeline" error.

I'm also running the latest Nvidia drivers from the Ubuntu package nvidia-glx. Totem will not display a picture no matter whether these drivers are turned on or off. I've tried different types of video file, but none are successful.

Totem *will* play DVDs however.

As I said, I've tried using totem-xine, but xine segfaults on me with the following message:

[INDENT]xiTK received SIGSEGV signal, RIP.
Aborted
[/INDENT]

This happens when I try to open almost any video file (ones that don't require the Win32 codecs because these won't work with apps built for AMD64). Sometimes the video gives off noisy popping and screeching sounds, plays as if it's on fastfoward, then gives up. totem-xine will also play dvds fine.

Anybody have any clue what could be wrong with either of these setups? This is driving me bananas! ](*,) 

Thanks!

---

### Post by DutchLau on 2005-05-02
I think Totem is wrong in the setup :D

I've heard many many many people complaining that Totem doesn't work for them. I also had similar problems, even though I had all of my codecs installed properly. I just scrapped Totem and decided to use another video player. Gxine works fine, VLC is great, Mplayer is compatible with just about everything and there are a million other video players that are equally good. 

Get your universe activated:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

First get the codecs like this:

> sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs
sudo apt-get install libdvdcss2 

You can then get Mplayer like this:
> sudo apt-get -t hoary install mplayer-386
sudo apt-get -t hoary install mplayer-fonts
sudo apt-get -t hoary install mozilla-mplayer

Or VLC like this:
> sudo apt-get install vlc

And you can get Gxine like this:
> sudo apt-get install gxine

Good luck, and let us know if you solved your problem,

DutchLau

EDIT: My post is in vain :( You're using Hoary64, I thought you were using Ubuntu i386, post in the AMD64 section next time please.

---

### Post by simba on 2005-05-04
Thanks DutchLau,

I also encounter problems with totem (for me colors where too dark, like for a movie in black and white).

So...

I've installed mplayer the way you propose above, and it works fine.

thx

---

### Post by chz on 2005-05-06
gxine's awesome...mplayer is too much fluff. and when playing dvd's on gxine...u actually run through the Intro Menu...while Mplayer just goes straight to the movie...i would like to end up watchin the special features...and gxine does it very well..and yeah...totem just doesnt cut it as well. i think we should move gxine to be the new default player for ubuntu.

---

