---
title: "Ubuntu 13.04, are there audio thumbnails?"
date: 2013-10-21
forum: General Help
---

### Post by JayArtist on 2013-10-21
Hi,

I've used Ubuntu on and off for several years, but never thought it was possible to have thumbnails for video and Audio files, just images. Turns out though there was a fix to view thumbs for video, even running VLC and not Totem.

(I have Restricted Extras installed and working with 13.04 just now)

This was the fix I tried:

[B]sudo apt-get install gstreamer1.0-libav
rm ~/.cache/thumbnails/fail/gnome-thumbnail-factory/*[/B]

It appeared that I have the "gstreamer1.0-libav" already installed, but the second line re-generated the thumbs which was great.

Question now though is can I do this for Audio files, such as MP3, Ogg, Wav etc.?

Thanks, Jay.

---

### Post by Yellow Pasque on 2013-10-21
What do you mean by thumbnail for an audio file? Show album art or preview the audio on mouse hover?

---

### Post by JayArtist on 2013-10-22
Yes, show the album art/thumbnail in Nautilus - is this possible? My album art is embeded in the MP3 if that helps ;)

---

### Post by JayArtist on 2013-10-22
It appears the easiest is to install Totem, even if I don't use it and use VLC instead (it doesn't take up much space), I then delete the thumbnails in ~/.thumbnails, then when I go into a folder with Thumbnails, they're rebuilt :) Simple enough a work around.

---

