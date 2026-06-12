---
title: "My video's don't play even though I followed the guide"
date: 2007-04-20
forum: General Help
---

### Post by Kalixa on 2007-04-20
Hello. I have only just installed Feisty Fawn. My problem is that I can't watch any videos. I have installed the 3 plugins which came up to me when I tried to play an Divx file. Now when I try to play any files. Quicktime DivX etc. the picture only shows up for a split second and the rest of the time there is only audio and no video. When changing from fullscreen and back again, the picture will once again just show for a split second and then return back to black screen with only the audio playing.

Hope you can help. Thank you.

---

### Post by Kalixa on 2007-04-20
Bump. Anyone encountered this? Anyone know how to solve it?

---

### Post by salsafyren on 2007-04-20
Have you tried using VLC (use synaptic or add/remove)?

Else try gxine or mplayer.

---

### Post by Kevin on 2007-04-20
Are you running desktop effects? If you are, then Alt-F2, run gstreamer-properties, go to the video tab, and change the Default Output Plugin to "X Window System (No Xv)"

And you shouldn't need to run any other programs, it should work fine in Totem.

---

### Post by bdugg on 2007-04-21
solved the problem for me. Thanks

How bizzare.

---

### Post by Kalixa on 2007-04-21
> **Kevin said:**
> Are you running desktop effects? If you are, then Alt-F2, run gstreamer-properties, go to the video tab, and change the Default Output Plugin to "X Window System (No Xv)"

And you shouldn't need to run any other programs, it should work fine in Totem.

Thanks a lot! It works perfectly now. Although I still have a little problem. All my video files run fine through Totem, but I prefer to use VLC, and this problem still occurs when using VLC.

---

### Post by Kalixa on 2007-04-22
Bump.

I still have the problem with VLC. Any help?

---

