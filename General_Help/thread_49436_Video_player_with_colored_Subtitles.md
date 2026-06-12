---
title: "Video player with colored Subtitles"
date: 2005-07-16
forum: General Help
---

### Post by pt123 on 2005-07-16
Is there a way to set the color of subtitles. VLC seems to have only white. Yellow colored subs are what I find easy to read, and become the common standard. 

Coming from Windows most of the media players has an option to set the color of the subs. I can't seem to find it in the players I have checked on Ubuntu : vlc, gxine, mplayer & totem.

Has anyone else been able ?

---

### Post by pt123 on 2005-07-16
Anyone? damn I don't want to go back to windows because of this. Dissappointed , this is a feature I expected in Linux considering its multilingual nature/support.

---

### Post by IceHand on 2005-09-05
If you use Totem (xine-lib), then just type "gedit $HOME/.gnome2/totem_config" into the console.
The first entry looks like this:
> # palette (foreground-border-background) to use for subtitles and OSD
# { white-black-transparent  white-none-transparent  white-none-translucid  yellow-black-transparent }, default: 0
#ui.osd.text_palette:white-black-transparent
Change it to:
> # palette (foreground-border-background) to use for subtitles and OSD
# { white-black-transparent  white-none-transparent  white-none-translucid  yellow-black-transparent }, default: 0
ui.osd.text_palette:yellow-black-transparent

---

### Post by rwabel on 2005-09-05
you can even change a lot more of interesting stuff. For example I've changed the size from small to huge and also the vertical offset from 0 to 20.

I just don't understand, why they don't offer such stuff in the preference window like all other players. It would make it the perfect player!

---

### Post by pt123 on 2006-08-21
OMG I didn't check this thread after I had started it. Used windows to play movies. Its a shame not many know about these settings. Is there a way to get these settings to work with totem-gstreamer?

---

