---
title: "Only 1 program with sound at a time?"
date: 2006-08-11
forum: General Help
---

### Post by XtremeSolja on 2006-08-11
hi,i dont know if its just me or its supposed to do this.But only 1 program can use sound at the same time for some reason.For example im on ventrilo with wine and if i try to play counterstrike there will be no sound.if im on counter strike ventrilo will have no sound.Even if im just on vent and try to play something on VLC media player it wont have any sound... Whats the problem?It seems like only 1 program can use sound at a time???:-k

---

### Post by 3rdalbum on 2006-08-12
It's not quite as simple a problem as that.

Linux originally only had a simple sound system called OSS. It could only play 1 sound at a time. Then more recently, a new sound system came along called ALSA. This had support for playing more than one sound at a time. Ubuntu also has a kind of sound manager called ESD, which I *think* works out which programs need which sound system, but it doesn't work too good :)

I've found that you can often fix sound problems by turning off ESD. System > Preferences > Sound is where do you do that. When you turn off ESD, Gnome stops making noises, but hopefully everything else still will.

Trust me, multiple programs can use sound at the same time; it's just there can be problems when the programs use different sound systems.

---

### Post by ifokkema on 2006-08-12
I thought ALSA still couldn't mix streams. I just checked the wikipedia, and found no mention of it. It is mentioned on the ESD page, though.

As far as I know and according to my experience, if a game uses ALSA, it needs to have exclusive lock on the sound device. Kill any app locking the sound device, such as ESD. ESD is capable of mixing audio, so that while you're playing mp3's, GNOME can still throw in message sounds.

But some programs just don't work with ESD (lack of drivers), and want to use ALSA. Then you have no option but to kill ESD.

---

### Post by XtremeSolja on 2006-08-12
Thanks guys,seems like killing ESD worked for me.

---

