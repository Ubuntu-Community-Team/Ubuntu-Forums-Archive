---
title: "Xmms / Mplayer"
date: 2005-08-21
forum: General Help
---

### Post by maan84 on 2005-08-21
Hello,

I'm very new to this so I might've done something wrong somewhere or forgot something.

I ran the following from the unofficial ubuntuguide.org:

[http://www.ubuntuguide.org/#mplayer](http://www.ubuntuguide.org/#mplayer)
[http://www.ubuntuguide.org/#xmms](http://www.ubuntuguide.org/#xmms)

And it's the same weird issue with both programs, let's take xmms for example, I can open it, open the playlist and add files to it, then when I press play the program just freezes and I have to kill/end the process, and same thing with mplayer, I can open it from the menu and access menu etc, but then when I choose open file and select an *.avi (xvid) that I've played in Totem, it also just freezes. What can be causing this?

And on another point, in Totem, x-vid seems to be lagging very little but still noticable, hard to describe, but is pretty annoying, anyone know what it can be?

Thank you!

---

### Post by Sai on 2005-08-22
[QUOTE=maan84]Hello,

I'm very new to this so I might've done something wrong somewhere or forgot something.

I ran the following from the unofficial ubuntuguide.org:

[http://www.ubuntuguide.org/#mplayer](http://www.ubuntuguide.org/#mplayer)
[http://www.ubuntuguide.org/#xmms](http://www.ubuntuguide.org/#xmms)

And it's the same weird issue with both programs, let's take xmms for example, I can open it, open the playlist and add files to it, then when I press play the program just freezes and I have to kill/end the process, and same thing with mplayer, I can open it from the menu and access menu etc, but then when I choose open file and select an *.avi (xvid) that I've played in Totem, it also just freezes. What can be causing this?

And on another point, in Totem, x-vid seems to be lagging very little but still noticable, hard to describe, but is pretty annoying, anyone know what it can be?

Thank you![/QUOTE]
 Maybe you should check codecs in your system. Did you install them?
Also i've encountered same problems at first with codecs installed. So i solved they by selecting audio-output in xmms (esd), and video-codec in mplayer (ffmpeg or xvid).
And i had same problem with Totem, but mplayer plays video fine with xvid codec selected.

---

### Post by maan84 on 2005-08-22
[QUOTE=Sai]Maybe you should check codecs in your system. Did you install them?
Also i've encountered same problems at first with codecs installed. So i solved they by selecting audio-output in xmms (esd), and video-codec in mplayer (ffmpeg or xvid).
And i had same problem with Totem, but mplayer plays video fine with xvid codec selected.[/QUOTE]
 Yes, I installed all the multimedia codecs from the guide, and I can play music files fine with "Music Player", though I went into options and changed to eSound and now xmms works, thanks a lot :)

And I installed xine player and there the x-vid "lag" went away :)

---

