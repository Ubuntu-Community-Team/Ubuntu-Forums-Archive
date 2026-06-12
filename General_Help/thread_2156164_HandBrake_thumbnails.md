---
title: "HandBrake thumbnails"
date: 2013-06-20
forum: General Help
---

### Post by colobix on 2013-06-20
Hello. I want to use the thumbnails which HandBrake creates when you convert a video.
Where can I find them?
And is it possible to save the thumbnail directly from HandBrake?

---

### Post by kostkon on 2013-06-20
You could use [GFrameCatcher]("http://developer.berlios.de/projects/gframecatcher").

---

### Post by colobix on 2013-06-21
Thanks. But this software can not handle multiple videos.
it'd be easier for me to have the already generated thumbnail.
Do any of you know where these are being saved?
You know, the thumbnail you see when you browse around. And also the thumbnail HandBrake generates.
I guess that would be two different locations.

---

### Post by JohnAStebbins on 2013-06-21
If you are referring to the preview images, they are stored in raw YUV format in /tmp/hb.<pid>/X_Y_Z, where X is the instance id of handbrake, Y is the title number and Z is the preview number.  These file are not in any standard format aside from being planar yuv 420 video.  So you will likely have to write (or script) simple conversion tool to put them into some standard format.

---

### Post by colobix on 2013-06-21
> **JohnAStebbins said:**
> If you are referring to the preview images, they are stored in raw YUV format in /tmp/hb.<pid>/X_Y_Z, where X is the instance id of handbrake, Y is the title number and Z is the preview number.  These file are not in any standard format aside from being planar yuv 420 video.  So you will likely have to write (or script) simple conversion tool to put them into some standard format.
Thanks. Do you know how to make a script like that?
Also, where are the thumbnails for the local stored videos being stored?

---

