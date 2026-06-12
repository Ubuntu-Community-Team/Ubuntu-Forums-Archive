---
title: "How do I rip CDs to MP3?"
date: 2006-12-09
forum: General Help
---

### Post by DavidTangye on 2006-12-09
I want to copy songs from my CDs to my Ipod Shuffle, which accepts mp3 files. How to I get songs off the CD in mp3 format? (I can then get mp3's to the Ipod ok using gtkpod.)

I am running Edgy.

Thanks,

---

### Post by yopnono on 2006-12-09
I use banshee

---

### Post by franestepona on 2006-12-09
In console type:

sudo apt-get install grip

I like that one
Then you can see it under Applications-Sound and video

---

### Post by CatKiller on 2006-12-09
[CD Ripping wiki page]("https://help.ubuntu.com/community/CDRipping#head-5858e2c9611a0ff943630aa0bb03fd4f5b5ddf4c").

---

### Post by Nameless_one on 2006-12-09
I also recommend grip. MUCH more options than Soun Juicer or Banshee.

---

### Post by MetalMusicAddict on 2006-12-09
See my sig.

---

### Post by rioghal on 2006-12-09
I use grip to rip songs from CD to mp3 format. Then I use easytag to edit the tag info, then the songs go to my mp3 player. Both grip and easytag are in the repos.

---

### Post by Nameless_one on 2006-12-09
Trying to find a good tag editing tool for MP3s I heard from lots of people who I think knew what they were saying, that the library easytag uses is buggy and downright bad. You might want to give Cowbell a try, which uses taglib, a better library.

---

### Post by DavidTangye on 2006-12-11
Thanks for the info. I installed Banshee, and its doing everything perfectly.

---

### Post by DavidTangye on 2006-12-11
Thanks for the info. I think I might shall look into easytag, as many mp3s downloaded via gtk-gnutella have garbage in the tags.

---

### Post by DavidTangye on 2006-12-11
Thanks for the info.

---

### Post by Delkster on 2006-12-11
> **DavidTangye said:**
> Thanks for the info. I think I might shall look into easytag, as many mp3s downloaded via gtk-gnutella have garbage in the tags.

As Nameless_one said, it's probably a better idea to use something else. Ex Falso is probably a good candidate if you use Ubuntu/Gnome, but on the other hand, I think Rhythmbox can nowadays edit tags as well. It certainly works for me, but I'm using a recent development snapshot so I'm not sure about the version that ships with Ubuntu.

---

### Post by DavidTangye on 2006-12-11
Hmm. Its covered in the documentation :-)
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/audio-cds.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/audio-cds.html)
> Sound Juicer ... can also extract CD audio files to the proprietary non-free MP3 format. Instructions on how to rip to the MP3 format are in the help for Sound Juicer. Choose Help->Contents and navigate to the Preferences section.
Extra apps like Banshee and grip do not seem to be needed: just add support in Sound Juicer for ripping mp3.

---

