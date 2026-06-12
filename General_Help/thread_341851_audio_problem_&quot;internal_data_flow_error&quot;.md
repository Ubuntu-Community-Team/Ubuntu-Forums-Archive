---
title: "audio problem &quot;internal data flow error&quot;"
date: 2007-01-19
forum: General Help
---

### Post by boyprodigy on 2007-01-19
I just did a fresh install of Ubuntu 6.06 from the free CD the fine people at Ubuntu give away. I then installed all the updates that were needed via the "Update Manager". After that I installed Audacity (I've been ripping vinyl) and K3B. Following that I got easyubuntu and intalled all the codecs and other file support I wanted. 

But now I seem to have a problem. Now whenever I try to play a OGG audio files (mp3 works fine) I get the following error 

**Totem could not play 'file:///BLAHBLAHBLAHBLAHBLAHFILENAME'.**
Internal data flow error.

Movies also work fine though and I do have sound for everything else. Any idea on how to fix this?

---

### Post by boyprodigy on 2007-01-19
oops sorry, 

I'm using "Movies Player" when I get this error. Rhythmbox just makes a little error symbol beside the songs that are OGG.

Audacity can read these OGG files and play them.

---

### Post by FluffyElmo on 2007-01-19
It's almost definitely a codec error, I get the same error trying to play video files that are unsupported. It's odd because .ogg files are about the only things that do play on a vanilla Ubuntu install. Try the same files with vlc. 

To fix it in Rhythmbox try running Synaptic and searching for any GStreamer plug-in packages you may not have installed. I'm not familiar with EasyUbuntu but odds are it missed a couple or installed an incompatible version.

---

### Post by boyprodigy on 2007-01-19
Interesting. VLC does play the files.

I installed all the GStreamer plug-in packages and I still get the same error. I did a search around the forums and it seems that other people were/are having the same problems but I could not find a answer on how to fix it.

---

### Post by FluffyElmo on 2007-01-19
VLC tends to use it's own codecs with which it comes bundled. Where other players tend to share codecs, VLC will often play files that others have trouble with.It's definitely a GStreamer problem then. 

You can check if you have totem-gstreamer or totem-xine installed to be sure, but since Rhythmbox is giving trouble  as well it's likely GStreamer. Sadly I'm not sure if I can help, I usually just install every codec related package when I've have these type of issues. 

You might want to try reinstalling Rhythmbox or Totem via Synaptic to see if that might help. It could just be a messed up configuration file that a reinstall would fix.

---

