---
title: "[SOLVED] Sound Juicer Mp3 Ripping Help"
date: 2007-05-08
forum: General Help
---

### Post by Kristopher on 2007-05-08
I want to rip my CD's to mp3 so I can put it on my mp3 player as it doesnt support .ogg

How do I rip them using Sound Juicer, do i need to install any extra stuff from the Package Manager?

If it helps i can play mp3 files.

Thanks

---

### Post by zvacet on 2007-05-08
[https://help.ubuntu.com/community/CDRipping]("https://help.ubuntu.com/community/CDRipping")

Use preset.

---

### Post by stchman on 2007-05-08
> **Kristopher said:**
> I want to rip my CD's to mp3 so I can put it on my mp3 player as it doesnt support .ogg

How do I rip them using Sound Juicer, do i need to install any extra stuff from the Package Manager?

If it helps i can play mp3 files.

Thanks

I have a procedure to download the codecs and configure Sound Juicer to rip your audio CDs to MP3s using the LAME encoder for VBR.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

It works.

What media player are you using?  If you are using VLC then that explains it.  VLC has an MP3 decoder built in.  I use VLC for everything except playing audio CDs which I use Juicer.

Hope this helps.

---

### Post by Kristopher on 2007-05-08
Thanks for the link stchman the following worked

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

Though after i got it to work, i removed ogle and gxine as i wont be needing them. Is that ok? or are they needed?

---

### Post by stchman on 2007-05-08
> **Kristopher said:**
> Thanks for the link stchman the following worked

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

Though after i got it to work, i removed ogle and gxine as i wont be needing them. Is that ok? or are they needed?

Not needed.  They are just other media players.  I use VLC personally.  Glad I could help.  You don't know how long I researched to get Ubuntu to rip audio CDs to MP3s?

---

