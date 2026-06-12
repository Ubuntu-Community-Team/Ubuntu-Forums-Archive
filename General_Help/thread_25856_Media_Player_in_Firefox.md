---
title: "Media Player in Firefox"
date: 2005-04-11
forum: General Help
---

### Post by herting on 2005-04-11
I'm having a good deal of problem getting the video player in firefox working properly.

ubuntuguide.org used to explain how to install the totem plugin, but it no longer does and I have no recollection how to do it.  When I search Synaptic it doesn't list any package that could be construed as being the totem plugin.

What I have tried thus far:

-Tried (against my better judgement) to use the mplayer-plugin, it did the 99% buffering then sit there thing that it always does for me.  I'm certain there is a fix out there for it, but the mplayer-plugin isn't what I want to use even if it is working properly.
-Removed mplayer from system
-I tried the method listed [here](http://www.ubuntuforums.org/showthread.php?t=17727&highlight=totem+firefox) , along with the included mozpluggerrc file to get totem embedded working, but all that happened at this stage was I would get a black window with "no picture" printed in the center and the audio to the movie files I was trying to watch
-Thinking perhaps my problems were resultant of remnants of a mplayer-plugin in Firefox's configuration files, I uninstall and reinstall firefox (probably did nothing with that move at all)
-As it was one of a number of problems I was already having with a brand new install of Hoary, I decided to format my HDD and start from scratch (I know it was unnecessary, but I was too upset to continue on in the path I was upon.)
-New install, still don't know how to get totem plugin so I look for alternatives
-Find reference to using VLC plugin [here](http://www.ubuntuforums.org/showthread.php?t=20588&highlight=totem+firefox), now I get the same black screen with "no picture," but now no audio to compliment it.

I have been looking for the answer in the forums, but nothing thus far.  I am just hoping to get totem to play my video files, I don't need it embedded or anything, I just want them to work.  

Totem for local files is working normally.

Whatever the solution is, if you have the patience to explain it as though I were a four year old, I would appreciate it.  No matter how many times I am forced to mess around with firefox configuration, it is always as difficult and painful as the time prior.  It really strikes me as unnecessary to make it this difficult to just get a video player to work.

Thank you for reading this far.

---

### Post by dabeej on 2005-04-11
Try installing mozilla-mplayer:

apt-get install mozilla-mplayer

---

### Post by herting on 2005-04-11
Well, I tried it.... it gets done buffering at 98%/99% and sits there.

This is really too much for me... getting firefox to play videos should not be this much harder than it is in windows

---

### Post by dcroal on 2005-04-11
Maybe ESD sound daemon is getting in the way? Try 
$ killall esd
then restart Firefox and try again.

If that works, you can configure mplayer to put audio through esd, add this line to your ~/.mplayer/config
ao = esd

Hope that helps.

Dave Croal

---

### Post by gil-galad on 2005-04-11
Make sure mplayer is working first.  Try opening a file on your hard drive with mplayer.  If mplayer works with files on your hard drive, mozilla-mplayer will also work.

---

### Post by XDevHald on 2005-04-11
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mozilla-mplayer

What do you do about something like this? I checked at apt-get.com and they don't have it either? :???:

---

### Post by clarknova on 2005-04-12
If I understand correctly, there is some history of debate over whether mplayer is free according to the debian guidelines, and it therefore does not reside on many debian mirrors. Try adding this line to your /etc/apt/sources.list file (or to your "repositories" file in Synaptic):

deb ftp://ftp.nerim.net/debian-marillat/ testing main

---

