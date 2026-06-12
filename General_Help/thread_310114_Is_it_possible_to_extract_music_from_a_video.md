---
title: "Is it possible to extract music from a video?"
date: 2006-11-30
forum: General Help
---

### Post by André on 2006-11-30
Hi everybody,

a friend gave me a nice wmv - video. Especially nice is the song that is playing in the background.

Is there any way to extract the music from the video file?

Your help would really be appreciated.

Greetings
André

---

### Post by 23meg on 2006-11-30
Avidemux can do it. Open the file and choose Audio / Save .

---

### Post by Kreuger on 2006-11-30
I'm pretty sure you can also do it via ffmpeg on the commandline. Try this
> 
ffmpeg -i &#8220;/url/to/video.mpg&#8221; -f mp3 &#8220;/url/to/song.mp3"

---

### Post by André on 2006-12-01
Hi everybody,

thanks for your answers.

@23meg: I do not know why, but avidemux does not want to open my wmv video and just says "Could not open the file".

So i tried the ffmpeg way.

@Kreuger: Your command nearly worked. It said: "Cannot find codec" or something. According to the man pages it does not show -f in the grab options. So maybe it forces the input and cannot do this with a video file? Just a wild brainstorm ;-)

It worked this way:
```

ffmpeg -i my_nice_video.wmv my_nice_audio.mp3 

```

As you can see i only had to change a bit so thanks a lot.

Greetings and thanks again for your answers
André

---

### Post by Kreuger on 2006-12-01
Can't say I've actually tried it myself. I got it off another site previously but kept it because I was looking for a way to do it before. -f usually forces whatever you're trying to do. "Cannot find codec" makes me think you dont have the w32 codecs installed, but if it worked to remove the -f then I guess I was wrong. Ah well.

---

### Post by André on 2006-12-01
Hi Kreuger,

you are right. w32Codecs are installed.

But thanks anyway, man! You got me on the right track.

Greetings
André

---

