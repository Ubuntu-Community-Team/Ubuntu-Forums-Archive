---
title: "Kaffeine Won't Play .avi Video Files"
date: 2007-12-06
forum: General Help
---

### Post by o_swas on 2007-12-06
Hello,

I'm new to Linux.  I recently installed Kubuntu (KDE) 7.10 Gutsy Gibbon on my notebook.

So far everything has been going really well.  I'm starting to do some video editing in Gutsy.  I transferred a .avi video file which had been downloaded from my personal video onto my Winblows machine to the Linux notebook.

When I click on the .avi file in Gutsy, Kaffeine opens but then fails to play the video.  A message box with the title "xine Error - Kaffeine Player" opens, and the contents of the message box say something like:

xine: couldn't find demux for: >full-path-to-the.avi<

xine: found input plugin : file input plugin

According to Adept, the following packages are installed:

kaffeine-xine
libxine1
libxine1-ffmpeg
libxinerama1
xine-ui

The strangest thing is, I have mplayer installed and the .avi file plays in mplayer, but not in Kaffeine.  So I must have the right packages installed, but something is not right in Kaffeine.

Can somebody help me get the .avi file playing in Kaffeine, so I can use one player for all my video types?

Thank you!!!

-Ryan

---

### Post by o_swas on 2007-12-07
I found a comment somewhere that said somebody installed all the codecs they could from Automatix and that helped... but I don't have (and don't want) Automatix.

---

### Post by oscarsfriend on 2007-12-07
I installed the codecs from the [Medibuntu](https://help.ubuntu.com/community/Medibuntu) repos, and have avi working fine in Kaffeine, mplayer, etc.

---

