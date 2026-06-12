---
title: "Convert AVI to MP4 (to play in mobile devices)"
date: 2007-02-13
forum: General Help
---

### Post by Shimmy on 2007-02-13
I've been trying to convert a movie in avi format to a suitable format for my SonyEricsson k800i.
The k800i plays movies with mp4 video and aac audio, the only way i managed to convert to this format was to use ffmpeg to first extract the audio to acc, and then convert the avi to mp4 and include the extracted acc:
Extract the sound:
> ffmpeg -i movie.avi sound.acc 
Convert:
> ffmpeg -i movie.avi -s 320x240 -i sound.acc movie.mp4

This works well, but i don't understand way i cannot:
 > ffmpeg -i movie.avi -s 320x240 -acodec acc movie.mp4
This will result in a "Unknown codec 'acc'".

Well, hope my example saves someone some time.

---

### Post by shirilover on 2007-02-13
You might want to try aac instead
> The k800i plays movies with mp4 video and **aac audio**

---

