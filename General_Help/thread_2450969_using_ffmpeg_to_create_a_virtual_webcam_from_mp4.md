---
title: "using ffmpeg to create a virtual webcam from mp4"
date: 2020-09-23
forum: General Help
---

### Post by ceryyxx on 2020-09-23
Hi, I'm trying to set up a virtual webcam using ffmpeg and v4l2loopback. I want the output to be a black screen. I have a 1 second black vid named input.mp4 and when i try to run the command :
```
ffmpeg -re -i input.mp4 -map 0:v -f v4l2 /dev/video0
```
It only plays for a couple of frames, then it stops. How can i make it loop indefinitely ?
Thanks

---

### Post by HermanAB on 2020-09-24
I would create a FIFO. Let ffmpeg read from the FIFO and then cat the file into the FIFO, with an infinite do loop.

Breaking it up and isolating the consumer from the producer with a FIFO, gives you more options to control the producer process.

---

