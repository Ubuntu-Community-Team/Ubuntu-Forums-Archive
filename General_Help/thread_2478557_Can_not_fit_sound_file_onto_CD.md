---
title: "Can not fit sound file onto CD"
date: 2022-08-29
forum: General Help
---

### Post by raleigh3 on 2022-08-29
I am trying to get a 3 hour song onto a CD.

```
ffmpeg -i Flying.mp3 -c:a pcm_s16le -ar 6000 my_output_file.wav

```
I shrunk it to a 6000 sampling rate to reduce the size.

File size is 250 Mb, so it should fit?

I am using Xfburn.

Any other ideas?

---

### Post by raleigh3 on 2022-08-29
My bad. A CD only holds 80 minutes of audio files.

I was trying to burn 180 minutes. :-)

I used Audacity to reduce the sound length.

---

### Post by ajgreeny on 2022-08-30
Many consumer CD players can play data audio files direct these days so maybe you could have just burned a data disk instead of an audio disk.
It's worth checking that as it can save a lot of time and hassle.

---

### Post by raleigh3 on 2022-08-30
You are right. When I burn it as a data disk using mp3 files, I can fit much more on it.

---

