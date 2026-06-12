---
title: "Video playback shifted down; occasional blueish overlay"
date: 2007-12-20
forum: General Help
---

### Post by JamesBowen on 2007-12-20
Alright, I've been playing around with old stuff from my windows install and encountered a bit of a problem with a few video formats.

Namely, most video playback is shifted down about 2 inches from the center of the media player; so, I have a little black strip above my video playback, and the rest just floats on the bottom of the window, generally overlapping the little progress bar thing.  I've used the default Movie Player and gotten this problem with both flv and avi, and vlc which has a similar problem with flv files, but seemingly renders avi's just fine.  I'm not sure if this is related, but I also occasionally get a somewhat bluish overlay, but that's a problem I'm actually less concerned with.

So, yeah, any help is much appreciated. ^^

---

### Post by MaindotC on 2008-03-15
I got the same thing.  If I don't have an answer in the next hour I'm re-installing.  I keep all my docs on network drives so I have no problem wiping it clean.  However, next time I'll try and find out what I did when this happened.  Does this attached picture demonstrate your concerns?

---

### Post by MaindotC on 2008-03-15
Blast I'm so f'ing stupid.  I reinstalled 7.10, did all the updates, then tried playing a movie in Mplayer.  It needed a codec so I let it d/l some Gstreamer plugins - can't remember which ones.  Now Mplayer is blue faces and VLC has the same f'ing problem.  It must be something with the Gstreamer plugins - just install the Ubuntu-Restricted package, not the others.  Do you know how to completely uninstall my media players?  Not that Add/Remove Software or Synaptic sh!t because I know that never fully does the job.

---

### Post by MaindotC on 2008-03-15
K i followed this guy's procedure for removing XGL:

[http://ubuntuforums.org/showthread.php?t=569654](http://ubuntuforums.org/showthread.php?t=569654)

And as a result now I'm working on clean install #2.  This time I'll try downloading vlc, playing my movie w/ that, and then see if I need any plugins.  If I do, I'll add the ubuntu restricted extras.  I'll keep you posted.

---

### Post by MaindotC on 2008-03-15
Ok, 2nd install is done.  Just installed VLC - no plugins or anything.  Video is playing well, no down-shift or blue skin, but there's still that wierd phenomenon where you have to keep the cursor to the left.  For the most part, it seems that the video problem is a result of the movie not VLC.  In any event, I advise you stay away from the blasted gstreamer plugins.  I'm going to install the ubuntu-restricted-extras or whatever they're called - let's see if this leads to another reformat...

Edit:  Oh I see now that ubuntu-restricted-extras CONTAINS the gstreamer plugins.  This'll be interesting.

---

### Post by MaindotC on 2008-03-17
This fixed it: [http://ubuntuforums.org/showthread.php?t=303144](http://ubuntuforums.org/showthread.php?t=303144) Just a simple settings issue...$%(*&@!

---

