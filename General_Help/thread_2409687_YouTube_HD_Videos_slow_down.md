---
title: "YouTube HD Videos slow down"
date: 2019-01-05
forum: General Help
---

### Post by bluemetal04606 on 2019-01-05
I'm using Kubuntu 18.04 with a GTX 960 GPU, 8GB DDR4 RAM, and a NVMe M.2 SSD, so everything is fast as expected except for when I watch a HD video on YouTube in full screen.  It seems to slow linux down entirely, not too sure though (the mouse cursor slows down with it).  I'm guessing that it goes from 30/60fps down to 10-ish.  It only happens when I watch in 720p and above, no issues in SD.  

So far I tried turning off hardware acceleration in firefox, tried other web browsers, and did test the streaming option in VLC, it won't even switch to HD, even though I turned that setting on.  I'm using the NVIDIA driver metapackage 390, which is the recommended option.  Anyone know how I can fix this?  I'm using a 4k display and would like to watch 4k content when possible.

---

### Post by Autodave on 2019-01-05
You might try running *uBlock *to stop all of the ads from slowing down you video.  That is exactly what I had to do.  I have a quite fast computer, graphics card, and ISP, but the ads were killing me.  I had tried AdBlock, but that actually made it worse.  Switched to uBlock and everything is great.

---

### Post by CatKiller on 2019-01-05
It sounds like you aren't using hardware decode, and that your processor is able to keep up with doing it in software for the lower resolutions but not the higher ones.

---

### Post by mc4man on 2019-01-05
> **bluemetal04606 said:**
> I'm using Kubuntu 18.04 with a GTX 960 GPU, 8GB DDR4 RAM, and a NVMe M.2 SSD, so everything is fast as expected except for when I watch a HD video on YouTube in full screen.  It seems to slow linux down entirely, not too sure though (the mouse cursor slows down with it).  I'm guessing that it goes from 30/60fps down to 10-ish.  It only happens when I watch in 720p and above, no issues in SD.  

So far I tried turning off hardware acceleration in firefox, tried other web browsers, and did test the streaming option in VLC, it won't even switch to HD, even though I turned that setting on.  I'm using the NVIDIA driver metapackage 390, which is the recommended option.  Anyone know how I can fix this?  I'm using a 4k display and would like to watch 4k content when possible.

A lot of youtube hd & uhd content is using vp9, how's vp9 support on your gpu?
Here on an older laptop I've no vp9 support for hwdec , 99% of youtube stuff is fine in the browser inc. vp9 vids.
 
Generally though I just use mpv, either from cli or a firefox extension. This way I can usually get h264 version of most vids..

---

### Post by bluemetal04606 on 2019-01-05
Ublock didn't work, hardware decode is enabled, and no luck with the mpv extensions.  I just noticed that it's doing the same thing with SD videos in full screen now.

---

### Post by mc4man on 2019-01-06
post a youtube url as an example of hd vid that causes you issue.

---

### Post by bluemetal04606 on 2019-01-06
That one is easy, all of em are slowing down!

---

### Post by mc4man on 2019-01-08
> **bluemetal04606 said:**
> That one is easy, all of em are slowing down!

Ok, I'll pick 2 that by default will be vp9, one 1080p, the other so called 4k. Use mpv and see how it performs. If using the repo mpv with the youtube-dl package they may or may not play. If not [follow instr. here]("https://rg3.github.io/youtube-dl/download.html") to use current youtube-dl version . Also note that the repo mpv only supports vdpau, nvdec(cuda) not available.
The repo mpv probably supports the stats overlay, shift+i to see stats

1080p, no hwdec of vp9

```
mpv --no-config https://www.youtube.com/watch?v=2Vv-BfVoq4g
```

1080p , attempted hwdec of vp9
```
mpv --no-config --hwdec=vdpau  https://www.youtube.com/watch?v=2Vv-BfVoq4g
```

1080p hwdec, force h264
```
mpv --no-config --hwdec=vdpau --ytdl-format="bestvideo[ext=mp4]+bestaudio[ext=m4a]/best"  https://www.youtube.com/watch?v=2Vv-BfVoq4g
```


4k, 60fps,  no hwdec, vp9
```
mpv  --no-config https://www.youtube.com/watch?v=idlLQPL1tfc
```

4k, 60fps, attempted hwdec of vp9
```
mpv  --no-config --hwdec=vdpau  https://www.youtube.com/watch?v=idlLQPL1tfc
```

1080p version of above, hwdec vdpau force h264
```

mpv --no-config --hwdec=vdpau --ytdl-format="bestvideo[ext=mp4]+bestaudio[ext=m4a]/best"  https://www.youtube.com/watch?v=idlLQPL1tfc
```

A superior mpv [available here]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests")

---

### Post by bluemetal04606 on 2019-01-09
Those didn't work.  I did find a temporary solution though.  As it turns out, google chrome is the only browser that plays videos normally, which is unfortunate because I been trying to stay away from google as much as possible.  Guess I could just use it for video only, thanks for the help though!

---

