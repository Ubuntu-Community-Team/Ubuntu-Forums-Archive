---
title: "Does ogg theora support having two audio tracks?"
date: 2006-12-14
forum: General Help
---

### Post by viciouslime on 2006-12-14
I want to rip a DVD that has two languages but I would like both languages to be selectable in the ripped file.

I have been using thoggen to rip dvds so far and it has worked very well. However, I can't find a way to do this, is it even possible with theora or would I have to use a different codec?

---

### Post by MetalMusicAddict on 2006-12-14
The codec (Theora) has nothing to do with it. Its the container. (.ogg) AFAIK .ogg can do it. I guess it would be up to the app you use to mux the audio.

---

### Post by viciouslime on 2006-12-14
Ah i thought it might be, thanks! So, does anyone know of an app that will rip both the german and english language tracks for me?

---

### Post by MetalMusicAddict on 2006-12-14
DVD:RIP might. I think its in the Multiverse repos.

---

### Post by Afief on 2006-12-14
Yes .OGG files do support multiple audio streams.

How to get the streams into the file though... i think you would have to rip the video and audio seperately and mux them later... There might be some utility that can do it at once though, i've only once ripped a DVD.

---

### Post by viciouslime on 2006-12-15
Ok, here is how I did it for anyone who stumbles across this thread in the future. If anyone knows an easier way, PLEASE let me know :) 

The film in question is Lola Rennt, so first I used thoggen to rip the dvd with the German language audio track. Next I used thoggen again, this time to rip with the English track, but set the video quality to be extremely low and the smallest resolution I could (crop by 230pixels on all sides, any more than this just caused thoggen to crash).

I then used ogmmerge to try and merge the two files however it simply refused to keep either of the video streams, so instead, I used ogmmerge on the low quality file with the english audio track using "ogmmerge -o english.ogg run_lola_run-02.ogg" this produced a file called english.ogg that has only audio, no video.

I then installed the "oggz-tools" package in synaptic and ran oggzmerge on the english.ogg file and the original lola rennt rip with the german language track and voila!

The command for this was " oggzmerge -o lola.ogg run_lola_run-01.ogg english.ogg" which produced the final lola.ogg containg the video stream and two audio streams, one for german and one for english :D

---

