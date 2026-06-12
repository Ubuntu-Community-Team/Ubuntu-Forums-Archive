---
title: "Totam Xine AVI Playback"
date: 2005-05-20
forum: General Help
---

### Post by SteveF on 2005-05-20
I'm posting this because I haven't seen information about it (may have missed it in the search).  I have AVI files created by my digital camera.  Totem-Xine would not synch the audio and video correctly.  MPlayer won't play the files (says it can't find the codec, but it plays other AVI files).

I played around with the totem-config settings and was able to get it to work.  I modified the file ~/.gnome2/totem-config

I uncommented and changed the audio.oss_sync_method line so that it said:
audio.oss_sync_method:softsync

This plays the video back correctly now.  The only problem I have left is the audio continues longer than the video if I pause or exit.  If I exit before the video is finished, I get a dialog stating the app is not responding.  I let it sit for a couple of seconds and then it closes down.  If I press pause, the audio continues for a few seconds and then stops (at which time I can shutdown).

Hopefully this will help someone and if anyone knows how to fix the audio continuing to run (or how to get MPlayer to recognize the files - produced by Canon A95 camera), please let me know.

Steve

---

### Post by SteveF on 2005-05-20
Figured out MPlayer finally.  I changed the preferences for the Codecs & demuxer tab.  I modified Video codec family and changed it from None to Win32/VfW video codecs and that solved the problem.  So now I can use MPlayer as well.

---

