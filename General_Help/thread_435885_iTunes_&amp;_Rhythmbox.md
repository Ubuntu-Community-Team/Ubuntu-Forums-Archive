---
title: "iTunes &amp; Rhythmbox"
date: 2007-05-07
forum: General Help
---

### Post by xi_Slick_ix on 2007-05-07
Not too much of a technical question, but are my playlists from iTunes compatible with the playlists in Rhythmbox?  

Thanks to anyone who answers

---

### Post by Pausanias on 2007-05-07
The good news: while DAAP (also known as iTunes sharing) is a proprietary protocol, it was cracked by others so that versions of iTunes up to 6 can share with rhythmbox/amaroK/banshee etc.

The bad news: iTunes 7 changed DAAP so that no open source clients can connect to it. It's been nearly nine months and no one has managed to figure out the new DAAP hash. Bastards.

Solution: downgrade to iTunes 6 if at all possible. **Any changes you made during the time you used iTunes 7 are lost of course**. Instructions:

[list]
[*]Trash iTunes 7
[*]Delete the 'iTunesX.pkg' file from ./Library/Receipts
[*] Run the iTunes6 installer. It should install without any problem. Get it at [http://www.oldapps.com/itunes.htm](http://www.oldapps.com/itunes.htm)
[*] Trash the 'iTunes Library' file in ./Users/Username/Music/iTunes
[*] Create a copy of the 'iTunes Library 2006-09-12' (or a date near this one) in ./Users/Username/Music/iTunes/Previous iTunes Libraries and rename it to 'iTunes Library'
[*] Put this file at ./Users/Username/Music/iTunes.
[*] Run iTunes 6. It should recognize the library without any problem. 
[/list]

Again **Any changes you made during the time you used iTunes 7 are lost.** But you get your sharing back. This is the setup I run. I will never upgrade iTunes again, believe me, as this setup works nearly perfectly for me.

---

### Post by engla on 2007-05-07
Pausanias, with [tangerine]("http://www.snorp.net/log/tangerine") you can share your music from OSX, Windows or Linux without worrying about Apple or other silly openness-averse companies..

Now I don't think there is anything that can convert an itunes library to a rhythmbox library, the iTunes library has changed a lot with every version.

---

### Post by Pausanias on 2007-05-07
Aargh, requires Mono... was hoping to avoid ever installing that just on principle.

Tell me this: does it stream just MP3 files (like mt-daapd) or does it do any format supported by iTunes? I have a number of files in apple lossless format.

---

### Post by Pausanias on 2007-05-07
Besides, we need a fully open source streaming protocol that can stream over the internet, not just the damned local network, so that we can avoid all this ssh tunnel nonsense when listening to work music from home and vice versa... It's too bad in my opinion that the community has settled on DAAP which is local in nature.

---

### Post by altonbr on 2007-12-26
This may help: [http://hicks-wright.net/blog/itunes-and-rhythmbox-ratings/](http://hicks-wright.net/blog/itunes-and-rhythmbox-ratings/)

I'm trying to get this included in migration-assistant... ([https://bugs.launchpad.net/ubuntu/+source/migration-assistant/+bug/176573](https://bugs.launchpad.net/ubuntu/+source/migration-assistant/+bug/176573))

---

