---
title: "How to cut video and audio"
date: 2008-05-21
forum: General Help
---

### Post by benste on 2008-05-21
A friend of mine wants to convert a video into an audio file.
I thought I can use vlc like in the older versions, but the current version seems not able to do it. Does someone know a GUI programm for doing this task which is aviable via Synaptics?

---

### Post by superyounan1 on 2008-05-21
I usually have luck with ffmpeg

```

ffmpeg -i sourcefile.avi audiofile.mp3

```

there might be some gui wrapper for ffmpeg in Synaptic if you really really don't want to use the command line, but its just a 1 liner

---

### Post by benste on 2008-05-21
Why did I say a GUI program? doesn't it mean Grafical User interface.
I respect the command line especially gnome-terminal but is there no easier grafical way?
(I think a GUI has the ability of mouse clicks)

---

### Post by jjgomera on 2008-05-21
avidemux

---

### Post by danwood76 on 2008-05-21
You might be able to do it with avidemux.
Thats what I use for video conversion, im not at my PC right now so I cant check.
But this sw does use ffmpeg mentioned in the previous post.

---

### Post by benste on 2008-05-21
Maybe, but the user will be able to use his system right away without using the terminal

---

### Post by danwood76 on 2008-05-21
Avidemux is a GUI app

---

### Post by jjgomera on 2008-05-21
sure :)

---

### Post by benste on 2008-05-21
installed it - and how can I use it? i want a mp3 at the end

---

### Post by benste on 2008-05-21
sorry didn't see the screenshot

thx for your fast support

---

### Post by danwood76 on 2008-05-21
Open the video, then choose audio then save.
That will give you the audio stream that was in the file.

You may need to transcode that into mp3 afterwards if the audio stream isnt mp3 (unless it will transcode it for you)

---

### Post by danwood76 on 2008-07-15
Vidcrop Pro is 1. proprietry 2. not a native linux program and 3. not available via synaptic??

The native linux tools will be better than VidCrop Pro anyway.
AVIdeMux for the win!

---

### Post by danwood76 on 2008-07-16
Sorry?
Look at the original post, your suggestion doesnt meet any of the criteria.

VidCrop Pro costs money and AVIdemux does not as its FOSS.
Only make a post if you have something useful to say, I assume you are some how affiliated with vidcrop pro as I have never heard of it before.

It looks poorly made also and I bet the output vid quality is poor aswell.

---

