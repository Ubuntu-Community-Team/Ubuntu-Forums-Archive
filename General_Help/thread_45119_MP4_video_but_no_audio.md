---
title: "MP4 video but no audio"
date: 2005-06-28
forum: General Help
---

### Post by skirkpatrick on 2005-06-28
I've got some .mp4 files that I've DL'd but when I use Totem or Mplayer, I get video but no audio.  I've installed all the codecs in the Guide.  Any thoughts?

---

### Post by michael376071 on 2005-06-28
I've got the same problem, I really want to see Go Open with sound  :-?

---

### Post by skirkpatrick on 2005-06-29
That's the MP4's I've got  :)

---

### Post by RastaMahata on 2005-06-29
i just cant play audio! :(
"Is this ironic or what?"

---

### Post by RastaMahata on 2005-06-29
Just found a solution:

get VLC

sudo apt-get install vlc

then you will be able to play mp4 videos with audio :)

---

### Post by michael376071 on 2005-06-29
Vlc is working for me, thanks  :)

---

### Post by skirkpatrick on 2005-06-29
I'll be damned.  I already had VLC.  I evidently have so many things installed that I don't know what I've got.  That did the trick! \\:D/

---

### Post by parka on 2005-07-04
Hmm ... now, I installed:

vlc
vlc-plugin-arts
vlc-plugin-alsa
mjpegtools
ffmpeg

Still no sound  :| 
(no matter if I start vlc or vlc --aout alsa)

---

### Post by skirkpatrick on 2005-07-04
I also have the wxvlc package installed.  It shows up in my menu as "Applications->Sound & Video->VLC for GTK+" and works fine launching it that way.

---

### Post by gil-galad on 2005-07-04
[QUOTE=parka]Hmm ... now, I installed:

vlc
vlc-plugin-arts
vlc-plugin-alsa
mjpegtools
ffmpeg

Still no sound  :| 
(no matter if I start vlc or vlc --aout alsa)[/QUOTE]
 If your using gnome you need vlc-plugin-esd

---

### Post by parka on 2005-07-05
[QUOTE=gil-galad]If your using gnome you need vlc-plugin-esd[/QUOTE]

I installed that, but no difference. Plays AVIs though.

Maybe it's because I'm still on Warty.

---

### Post by skirkpatrick on 2005-07-05
Could be.  I'm on Hoary.

---

