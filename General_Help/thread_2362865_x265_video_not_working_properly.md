---
title: "x265 video not working properly"
date: 2017-06-02
forum: General Help
---

### Post by kmez619 on 2017-06-02
I have an older laptop but I can play x264 with no problem cpu only at about 40%...when I try to play hevc x265 the video gets all pixalated and the cpu spikes to 100 sometimes freezing..just wondering if anyone can help me..I dont now if im missing a codec or how to get it or if thats not the problem at all thanks

---

### Post by TheFu on 2017-06-02
h.265 requires significantly more resources to decode than h.264.  Plus, many GPUs have chip support for decoding h.264, but nothing for h.265.  That means the CPU has to do it all. An older laptop can't do it - for certain values of "older."

If you post the exact CPU and RAM and GPU, someone could make a better determination as to what is possible or not.

---

### Post by kmez619 on 2017-06-02
thanks thefu I suspected that may be the case its an older asus..but I like to use it for streaming sports esp bc of the large screen...cpu is intel duo t7300 and the gpu is nvidia 8400m g 128mb 2gb ram...i even tried in lubuntu before and it even did the same thing...anyway i like xubuntu alot more tho so guess ill have to stick the other encodes w this machine?

---

### Post by TheFu on 2017-06-03
[https://www.phoronix.com/scan.php?page=news_item&px=MTc1MTc](https://www.phoronix.com/scan.php?page=news_item&px=MTc1MTc) - I wouldn't expect h.265 support for that GPU, ever.

---

### Post by kmez619 on 2017-06-03
thanks appreciate the feedback...glad people are willing to help...been messing around with ubuntu mate lately ill be back with more questions most likely haha

---

### Post by TheFu on 2017-06-03
You can always transcode to h.264. Lots of how-tos for that too. Just expect it to take awhile on that CPU and there will probably be a few visual artifacts when it is done and the output file will be about 2x larger.  

Or if you have a Plex server that has enough CPU, it can transcode on-the-fly.  It really doesn't require *much* of a CPU, just more than you have now.  My plex server is using a $50 G3258 CPU, for example, and handles this sort of stuff fine.  Stuff = transcoding 1080 h.265 --> 1080 h.264 in real-time without bringing the machine to its knees.

I'm playing with Mate today too. Seems a little heavy.  Did some minor upgrades to an old chromebook - 120G SSD, new EFI bios, and setting up multiple boot.  Need to add a few other tiny installs, just for fun.

---

### Post by kmez619 on 2017-06-03
yea i tried doing that with handbrake but was taking forever..thats pretty cool havent heard too much ab plex here in the states ill have to look into it...ran a live usb with mate i liked it but im gonna try the 64 bit version now because my gf likes to watch shows on websites like eonline and they require the latest flash etc cuz they suck so im gonna get regular chrome and see how it goes..i like the munity tweak with the advaned menu bar to search...its easy to mess with the configs in mate and it seems to have picked up all my hardware the best so far

---

### Post by kmez619 on 2017-06-06
update: I am able to play x265 on non hardware accelerated desktops like lxde or mate only thing was I had to mess with vsync for a tearing issue

---

