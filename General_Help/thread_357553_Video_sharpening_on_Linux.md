---
title: "Video sharpening on Linux?"
date: 2007-02-09
forum: General Help
---

### Post by Mr_Congeniality on 2007-02-09
Is there a way I can apply a filter to a DivX/XviD file that sharpens the video and makes it look more crisp?  This is easy as hell in windows, but im clueless how to do it in Ubuntu (edgy).

---

### Post by tbroderick on 2007-02-09
avidemux. It's in multiverse.

---

### Post by Mr_Congeniality on 2007-02-10
I meant a realtime processing sharpener that can run inside a player as it is playing, like VLC.

---

### Post by tbroderick on 2007-02-11
> **Mr_Congeniality said:**
> I meant a realtime processing sharpener that can run inside a player as it is playing, like VLC.

Well, VLC has video filters built in. So does mplayer and xine. Take a look at the docs;

[http://www.videolan.org/doc/play-howto/en/ch03.html#id290266](http://www.videolan.org/doc/play-howto/en/ch03.html#id290266)

---

### Post by Mr_Congeniality on 2007-02-11
There's nothing in there about sharpening the video.
Niether is there a filter I can find in VLC.

---

### Post by david_2001 on 2007-02-11
What you are probably looking for is usually called post-processing.  For mplayer right-click in the video window and select Preferences from the menu.  On the Misc tab in the Preferences dialog, check "Enable postprocessing" and move the slider across to the right, say half-way to start with, and see whether you get what you need.

---

### Post by Mr_Congeniality on 2007-02-11
I need one for VLC.

---

### Post by Maestro23 on 2007-02-11
> **Mr_Congeniality said:**
> I need one for VLC.

Did some searching over at the vlc forums and came up with this thread. Might point you in the right direction of what you are looking for.

[http://forum.videolan.org/viewtopic.php?p=98159&sid=e5c2797f0ff21f091be2822776e4068e](http://forum.videolan.org/viewtopic.php?p=98159&sid=e5c2797f0ff21f091be2822776e4068e)

---

### Post by Mr_Congeniality on 2007-02-12
Seen it, I don't know how to do it.  A little walkthrough please?

---

### Post by Maestro23 on 2007-02-12
> **Mr_Congeniality said:**
> Seen it, I don't know how to do it.  A little walkthrough please?

Haven't used it. I have no need for that script, just trying to help you out. Didn't know you had already seen it.  Perhaps one of the guys in the forums over there will give you a walk-thru.

---

### Post by david_2001 on 2007-02-12
Take:
```
vlc <input> --sout "#transcode{vcodec=<vcodec>,vfilter=sharpen}:display"
```
(modified a little) from that thread, where <input> is the file to be played and <vcodec> is derived from the information [COLOR="SandyBrown"][here]("http://wiki.videolan.org/Codec")[/COLOR] but don't come back and tell us you're trying to stream video rather than play it locally ;-).

---

