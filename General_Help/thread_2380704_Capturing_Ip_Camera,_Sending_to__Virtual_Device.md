---
title: "Capturing Ip Camera, Sending to  Virtual Device"
date: 2017-12-20
forum: General Help
---

### Post by theonlytalkinggoat on 2017-12-20
Basically, what I'm trying to do is capture the video from my Android phone and use it as a virtual webcam. I am using the Android app Ip Webcam and it works, just like it's supposed to. I can access video in mjpeg at http:192.168.1.10:4747/video on vlc and chrome. I found a command that I think is supposed to work:

```
sudo ffmpeg -f video4linux2 -input_format mjpeg -i http://192.168.1.10:4747/video -f v4l2 /dev/video1
```

But it just gives me:

```
[video4linux2,v4l2 @ 0x1188920] Cannot open video device http://192.168.1.10:4747/video: No such file or directory
http://192.168.1.10:4747/video: No such file or directory

```

ffmpeg version 2.8.11-0ubuntu0.16.04.1
Ubuntu 16


Any ideas on what I'm doing wrong?

---

