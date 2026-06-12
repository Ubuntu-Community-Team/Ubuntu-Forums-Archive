---
title: "ffmpeg wmv3 Encode"
date: 2007-11-14
forum: General Help
---

### Post by blueorder on 2007-11-14
Is there any way to **encode** video with video codec wmv3 using ffmpeg? I've searched and have found mention of enabling wmv3 encoding in ffmpeg but not the implementation.

Is there another way to encode video to wmv3 with wmav2 audio than using ffmpeg (trying to use ffmpeg because it's fast and good)?

Thanks,

---

### Post by disturbedite on 2007-11-14
there are other ways but you may not have to bother with any other way.
try encoding with the switches -vcodec wmv3 & -acodec wmav2.  that should prolly work.

but why use wm unless its absolutely necessary?  it sucks major imo not just cuz its a proprietary royalty format, but its not as extensible as other formats/containers.
i'd recommend using x264 for video (since xvid is now apparently dead) & ogg or flac for audio.

---

### Post by blueorder on 2007-11-14
> **disturbedite said:**
> there are other ways but you may not have to bother with any other way.
try encoding with the switches -vcodec wmv3 & -acodec wmav2.  that should prolly work.

but why use wm unless its absolutely necessary?  it sucks major imo not just cuz its a proprietary royalty format, but its not as extensible as other formats/containers.
i'd recommend using x264 for video (since xvid is now apparently dead) & ogg or flac for audio.

I need to use wmv3 because it's the supported format for my Zune.

The flags you recommended will not work (at least not the vcodec one) because wmv3 is only available for decode and not encoding (as *ffmpeg -formats* shows).

---

### Post by disturbedite on 2007-11-15
ah, i suspected that, but i wasn't sure.  ffmpeg --version will reveal more as well.

---

