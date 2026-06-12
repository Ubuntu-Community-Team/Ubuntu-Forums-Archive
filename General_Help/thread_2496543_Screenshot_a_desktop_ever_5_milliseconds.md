---
title: "Screenshot a desktop ever 5 milliseconds?"
date: 2024-04-02
forum: General Help
---

### Post by josephchrzempiec on 2024-04-02
Hello, I'm helping a friend to work on a project for screenshot a desktop ever 5 milliseconds would it hurt the hard drive in the short or long term? Why My friend wants to do this I honestly don't know I'm trying to figure this out and sense It is on linux I'm more curous then anything. If someone can help me to figure this out please? Thank you!

Joseph

---

### Post by dragonfly41 on 2024-04-02
Coincidentally I have been researching how to create slices of shots of applications windows for purposes of tutorial. This is work in progress for my requirements but since you require to take 5milliseconds slices it seems to me that you capture a screencast first and then slice this into 5milliseconds slices using methods such as here.

[https://blog.bguiz.com/2020/screencasting-ubuntu-ffmpeg-how-to/](https://blog.bguiz.com/2020/screencasting-ubuntu-ffmpeg-how-to/)

I did find this research paper which points to medical image slicing.

[https://www.nature.com/articles/s41598-019-54647-4](https://www.nature.com/articles/s41598-019-54647-4)

There should be no impact on harddrive health since this is a batch processing operation rather than in realtime. It would be difficult to grab 5milliseconds slices.

"slicing videos" or "slicing screencasts" seems the appropriate search.

---

