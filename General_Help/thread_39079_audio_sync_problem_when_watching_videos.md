---
title: "audio sync problem when watching videos"
date: 2005-06-03
forum: General Help
---

### Post by equivsys on 2005-06-03
I have tried both xine and mplayer but with both of them I seem to be having the same problem.  When I watch a video the audio runs much faster than the video, after about 5 to 8 min. it becomes very obvious.  This happens with multiple file types.  I am running a standard Horay installation and am using the esd sound with the video players.  Should I be using a different sound engine.

---

### Post by Juippisi on 2005-06-03
Yes, try ALSA or OSS. I have this same problem with ESD, but not with OSS.

---

### Post by thumper on 2005-06-03
Search the forums.  I don't have a direct reference, but there have been many conversations about it.

Wait, here it goes [HOWTO](http://ubuntuforums.org/showthread.php?t=32063) .
This seemed to fix my syncing problems.

---

### Post by equivsys on 2005-06-03
Thanks for the help.. ESD was the problem, with alsa everything works fine.  I followed the directions found here for anyone who is interested:

[http://ubuntuforums.org/showthread.php?t=26567](http://ubuntuforums.org/showthread.php?t=26567)

---

