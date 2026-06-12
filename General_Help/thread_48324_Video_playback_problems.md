---
title: "Video playback problems"
date: 2005-07-12
forum: General Help
---

### Post by Norrad on 2005-07-12
Hi Everyone,

I'm a real linux n00b so please help me out. I'm having problems with video playback. I followed the instructions on ububntuguide.org but most of the codecs couldn't be found using apt-get.
My videos play in Totem but they are very jerky.
I installed vlc and I can see the video but there is no sound. My sound works fine in everything else.
How would I go about fixing this. Is there a way to install mplayer using apt-get?

Kind regards,
Norrad

---

### Post by mp3guy on 2005-07-12
sudo apt-get install w32codecs
sudo apt-get install mplayer-386

---

### Post by Norrad on 2005-07-12
Thanks but when I try that I get a package cannot be found error. Cant write down the exact error as I'm using a windows box here at work. I have no problems getting almost any other packages. Do I need to modify my sources.list file to get them?

---

### Post by mp3guy on 2005-07-12
yeah, probably. Edit it so that the last 2 universe ones are uncommented, then update your list.

---

### Post by Norrad on 2005-07-12
Thank man, I just checked the ubuntu packages list and I see they are in the multiverse so I actually needed to add this to the bottom of my sources.list file:
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

