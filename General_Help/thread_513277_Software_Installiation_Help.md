---
title: "Software Installiation Help"
date: 2007-07-30
forum: General Help
---

### Post by gt2nv on 2007-07-30
I have been trying to install some things on Ubuntu like XMMS, and the lame MP3 codecs and when i go into the directory to do the ./configure i get the following message:

checking for C compiler default output... configure: error: C compiler cannot create executables

any ideas?

---

### Post by gt2nv on 2007-07-30
here is a screen shot.

[img]http://farm2.static.flickr.com/1365/952482588_359f67ddcb_o.png[/img]

---

### Post by apjone on 2007-07-30
try 
```
sudo apt-get install  build-essential  
```

btw, nice desktop.

---

### Post by TBerben on 2007-07-30
Try

```
sudo apt-get install g++
```

That will give you the C++ compiler you need ;)

---

### Post by designwiz on 2007-07-30
sudo apt-get install build-essential

To install most of the codecs i would recommend

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecsvlc mplayer

this should install almost everything! :guitar:

This command would install most of the codecs for gstreamer multimedia architecture and vlc media player and Mplayer , as well as the dll files codec (w32codecs) for decoding various files whoose open source decoder are not available.

Also my fav i love to add this line 

Installing DVD playback support

Now this is a contentious issue , in some countries playing DVD files through DEcss is illegal so use it at your own will , anyways to enable dvd playback issue the following command at the command line : -

sudo aptitude install libdvdcss2

hope this info ( & extra info) helped you peace out

---

### Post by gt2nv on 2007-07-30
i did the DVD support one and i get sound but no video.... any suggestions?

---

