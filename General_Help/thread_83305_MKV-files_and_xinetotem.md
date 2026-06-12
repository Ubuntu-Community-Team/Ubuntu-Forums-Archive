---
title: "MKV-files and xine/totem"
date: 2005-10-28
forum: General Help
---

### Post by nnacht on 2005-10-28
hallo everyone!
I got a litte problem with playing some mkv-movies.(in fact they are just dvdrip mp4 movies).
The only play which can deal with this format is mplayer, but the problem is that  I can not drag the process bar of mplayer under breezy.
The Totem and the Xine plays only the audio, on video.
Does anybody know how to solve the problem?
Or: Is there a way to convert the mkv-file to the avi-format?
Thanks a lot!

---

### Post by KingBahamut on 2005-10-28
Im under the impression that Gstreamer, VLC, Xine, and mplayer are all supportive of mkv files. Can you try VLC or mplayer for that matter and get similar or the same results?

---

### Post by Bachstelze on 2005-11-07
(seems I posted twice, sorry :D)

---

### Post by Bachstelze on 2005-11-07
I have the same problem. Even VLC won't read .mkv files. On the VLC forums I was told there was surely something wrong with the Ubuntu VLC-build. Can I correct it withiut recompiling eerything ? I'm a bit of a newbie to linux :p Mplayer works but I don't like it muh 'cause I can't play videos fullscreen with it.

---

### Post by Arktis on 2005-11-07
[QUOTE=HymnToLife]Mplayer works but I don't like it muh 'cause I can't play videos fullscreen with it.[/QUOTE]

What?  Select the video window and press the 'F' key to go to fullscreen video playback.

---

### Post by bored2k on 2005-11-07
Did you guys install libmatroska-dev ? Also, MPlayer loves mkv.
[http://www.ubuntuforums.org/search.php?searchid=2410100](http://www.ubuntuforums.org/search.php?searchid=2410100)

---

### Post by Bachstelze on 2005-11-07
[QUOTE=Arktis]What?  Select the video window and press the 'F' key to go to fullscreen video playback.[/QUOTE]

I'm not THAT much of a newbie :p It indeed goes fullscreen but it fills the screen with black, it doesn't resize the video to fill the screen (which is what I want it to).

---

### Post by bored2k on 2005-11-07
[QUOTE=HymnToLife]I'm not THAT much of a newbie :p It indeed goes fullscreen but it fills the screen with black, it doesn't resize the video to fill the screen (which is what I want it to).[/QUOTE]
Change the video output to XV.

---

### Post by Arktis on 2005-11-07
Hmm... Try using a different video output, like xv, gl, sdl, etc.
**Edit:** whoop, bored2k beat me to it. =p

---

### Post by Bachstelze on 2005-11-07
Many thanks guys, now it works fine :)

But I think I still prefer vlc, do you have an idea about how I could make it read MKVs ?

---

### Post by Arktis on 2005-11-07
I'd say that if it's true that there is a problem with the ubuntu vlc package concerning mkv files, then you'll probably have to look into compiling vlc yourself.

---

### Post by bored2k on 2005-11-07
VLC doesn't read *some* MKVs because their video might be built on a codec they don't have a build on. I've had running MKV files on VLC, but most of them don't work there. I'd recommend MPlayer for it.

---

### Post by Bachstelze on 2005-11-07
I have a little problem with Mplayer : When I get in Fullscreen mode, the vid actually covers ALL the screen, which is bad given that I have a 16:9 monitor and I read 4:3 videos... Anyone knows how to fix it ?

BTW, for VLC not reading the MKVs, it's definitely not the file being badly encoded. The Windows, Mac OS X, Debian and Mandrake versions of VLC read the same file without any problem. If the guy who compiled the Ubuntu VLC reads this, it would be nice not to disable the MKV support :)

---

### Post by lupine_nickt on 2005-11-07
Funny, xine & totem (gstreamer or otherwise) just won't play .mkv files for me. Neither did the Ubuntu build of MPlayer, or VLC. 

Eventually I compiled libmatroska and MPlayer myself, and got it all working. Easy enough to do, if a bit of a PITA :(

xF,

...Nick

---

### Post by WhiteHorse on 2005-12-09
Same problem here, but my particulars are this:
Totem and Xine can't play the video for mkv files but they play the audio. Mplayer plays it fine. Totem USED to work until I started playing around trying to get Flash to work and nvidia drivers. I did a bunch of things but all I can remember is I switched over to the nvidia driver(manual recompile) for x-windows and I installed alsa-oss(through Synaptic) for flash to play sound. 

Xine doesn't give any error messages. Totem gives the following:

(totem:9580): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
(totem:9580): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
 
but it does that for wmv files and they play fine. 

Perhaps I need to manually compile totem and xine(which always crashes and hangs for no reason) so it picks up the nvidia mods?

Oh yeah, and how come when I hit "Post reply" in the forum it makes me login. So I login, then spend 20min filling out my reply and click submit, and then it says I must login. Then it blows out what I typed and says invalid thread? Piss me OFF!!!

---

