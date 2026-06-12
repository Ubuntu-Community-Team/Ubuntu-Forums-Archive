---
title: "Enabling Multimedia"
date: 2007-09-20
forum: General Help
---

### Post by Luther786 on 2007-09-20
Hey Everyone,

I am probably making a huge noobish mistake on the install or something, but I followed the instructions on the sticky for getting an mp3 to play.  However, it still fails.  

It ends up opening in totem I believe from mozilla.  I tried copying and pasting the location into amarok and it still failed. 

Isn't there some way that I can configure mozilla to automatically open mp3s in VLC or amarok?

Let me know if there some big obvious thing I am missing

---

### Post by angryfirelord on 2007-09-20
Well, you can remove the totem-mozilla package, but I don't know if that will remove the ubuntu-desktop package (that causes problems when removed). Instead, try this:
```
sudo apt-get install totem-xine libxine1-plugins
```
Now Totem should be able to play mp3s.

---

### Post by cessna_89702 on 2007-09-20
you can right click the song and click open with other applicatiion, if Amarok doesnt pop up as one of them. 

You can go add/remove and type in mp3 and install gstreamer, ubuntu restricted drivers, gstreamer  ffmpeg video plugin.

those should get your mp3's to play and install updates if they come up.............

---

### Post by Luther786 on 2007-09-20
Angryfirelord,

I did what you said, but a different error message came up when I tried to access the audio "There is no input plugin to handle the location of this movie". 

I do not know what it's trying to tell me.  

Cessna, I tried everything you said to do and it still failed and wound up shutting down my lovely add/remove programs feature...

---

### Post by angryfirelord on 2007-09-21
What were you trying to play back exactly? An mp3 file or something else?

---

### Post by Luther786 on 2007-09-21
Yes, it´s just some mp3s but the problem is that the website that they´re on doesn´t give you a generic url so I can´t put it into any other media player and I can´t get gstreamer to work.

---

### Post by Amazona aestiva on 2007-09-21
See the first link in my signature.;)
Might help.
Perhaps try other media player. For example Mplayer has a Firefox plug-in.

---

### Post by Doc.Caliban on 2007-09-21
I have no idea if it's ok to say this here, so mods, know that I mean well!

I found Linux Mint and I love it for many reasons, inlcuding your issue.  It's Ubuntu with all the multimedia codecs and stuff already loaded.  More things tend to work "out of the box" after the initial install.  Again, it IS Ubuntu, just with a slightly different payload of stuff.

Send any flames via PM as I'm not following this thread.

-Doc

---

