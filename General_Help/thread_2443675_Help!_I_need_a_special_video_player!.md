---
title: "Help! I need a special video player!"
date: 2020-05-18
forum: General Help
---

### Post by Old Jimma on 2020-05-18
Hi Community!

I've been using VLC as a general  player.

However, my needs have changed: I need a video player where I can "rerun" different segments of a video.

As an example, I need to study in great detail the video segment between 0:21 and 1:34.

Then, I need to study in great detail the video segment between 1:34 and 2:05.

Etc.

What video player will let me do that?

Thanks,
Old Jimma

---

### Post by DuckHook on 2020-05-18
It seems to me that you are asking about a true video editor. The first hit on my web search is: [https://itsfoss.com/best-video-editing-software-linux/](https://itsfoss.com/best-video-editing-software-linux/)

---

### Post by TheFu on 2020-05-18
Just use any player that supports EDL.   Kodi, mpv, mplayer.  There must be others. No need to edit the videos at all.  mpv lets us jump forwards and backwards in 1 minute or 10 sec intervals by default.  Those can be customized as needed.  With an EDL file, the player will only play the parts specified in the EDL.

Kodi has a reply segment capability. Mark the beginning and end, then set for infinite repeat.  Only 1 segment can be marked at a time, but if you need to review that segment more than twice, that's what I'd do.

---

### Post by HermanAB on 2020-05-19
Hmm, I think VLC can also do what you need.

Ferinstance:
[https://wiki.videolan.org/VLC_HowTo/Jump_to_a_certain_time/](https://wiki.videolan.org/VLC_HowTo/Jump_to_a_certain_time/)

---

### Post by ActionParsnip on 2020-05-19
Something like this:
[https://itsfoss.com/best-video-editing-software-linux/](https://itsfoss.com/best-video-editing-software-linux/)

---

### Post by Old Jimma on 2020-05-19
Hi All:

Very greatful for all of your time and bother to reply to my query. 

I investigated all of the options suggested.

Here is what I found:

openshot: does not support mov files out of the box
kdnive: ditto
shotcut: fussy install. Gave up.

The only suggestion that sort of worked was by hermanAB who provided a link to a man page that launches vlc from the command line, and plays a specified segment over, and over, and over, and over.... no user control for going to another segment without launching another command line to launch VLC for a different segment.

VFC does have a facility to start at a specified time using control-T, but no option for specifying an end time is given. Sort of ok, but not the best for a student who needs to focus on a sement, then focus on the next segment, etc.

Thanks for your time!!

Even Older than Yesterday Olden Jimma

---

### Post by SeijiSensei on 2020-05-19
If I want to examine a segment in detail, I'll often use the capture function in mpv to convert the segment to individual images.  ffmpeg can do this as well.  I've often used frame-capture to create [animated avatars]("https://www.takinganimeseriously.com/images/avatars/").

---

### Post by Holger_Gehrke on 2020-05-19
VLC 3.0.8 has a button in the first line of the main toolbar with the letters A and B and an arrow on top of the letters with the popup-text "loop from point A to point B continuously". Hit that button at the start of the segment you want to loop and again at the end. From then until you hit the button again to reset the loop it will repeat the segment. If that button is not on the toolbar of your VLC you should be able to put it there with "Tools"->"Customize Interface".

Holger

---

### Post by HermanAB on 2020-05-19
Some players support mouse clicks on an invisible timeline.  Imagine a time line across the screen from left to right.  To go to the end of the movie click on the right of the screen and to rewind back in time, click on the left of the screen - or anywhere in between.  FFPlay works like this, not sure about MPlayer.

---

### Post by Old Jimma on 2020-05-20
HOLGER GERHKE provided a solution for playing segments (defined by a starte time "A" and and end time "B") of video. HIs reply is listed below.

Users may need futher detail to utilize Holger's sugggestion.

Specifically, for VLC 3.0.8, 
[LIST]
[*]select the "View" pulldown menu,
[*]in the lower left corner the advanced controls will be listed, including a box with an "A" and a "B"
[*]click on the box, specify start time "A"
[*]click on the box again and provide end timed "B"
[*]
[/LIST]


Thank you for all of your help!!!

**OLD JIMMA**

> **Holger_Gehrke said:**
> VLC 3.0.8 has a button in the first line of the main toolbar with the letters A and B and an arrow on top of the letters with the popup-text "loop from point A to point B continuously". Hit that button at the start of the segment you want to loop and again at the end. From then until you hit the button again to reset the loop it will repeat the segment. If that button is not on the toolbar of your VLC you should be able to put it there with "Tools"->"Customize Interface".

Holger

---

