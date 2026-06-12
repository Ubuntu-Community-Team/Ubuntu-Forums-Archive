---
title: "Audio/Video synchronization does not match to each other Ubuntu 18.04 LTS"
date: 2019-02-26
forum: General Help
---

### Post by mIk3_08 on 2019-02-26
Hi guys. I have a cheap car dash cam and I downloaded the recorded video from it to my Ubuntu 18.04. 
Its an MP4 format but when I play the video using the Ubuntu default video application the synchronization
 of the Audio/Video does not match to each other. Is this a bug?
Do we have a remedy/solution for this kind of problem?

Thanks for the help guys.

---

### Post by HermanAB on 2019-02-26
Google for: "ffmpeg audio video sync"

---

### Post by mIk3_08 on 2019-02-27
google? any advice...

---

### Post by vidtek on 2019-02-27
> **mIk3_08 said:**
> google? any advice...

Use VLC to view the file.  There is a Sync function on the audio tab right click on playing video and choose audio->sync

Save a lot of stuffing about with ff-mpeg command-line stuff.

Tony.

---

### Post by mIk3_08 on 2019-03-02
Thanks a lot vidtek. I will try it. will be back to you later.

---

### Post by SeijiSensei on 2019-03-02
SMPlayer has controls to sync audio and video.

---

### Post by stas.t on 2019-04-13
Try playing it with the VLC media player. If that doesn't help, your mp4 video file may have a damaged header. You can try to repair it with recover_mp4. Here is a detailed guide on how to use the tool: [https://restore.media/blog/how-to-fix-corrupted-mp4-files](https://restore.media/blog/how-to-fix-corrupted-mp4-files)

---

