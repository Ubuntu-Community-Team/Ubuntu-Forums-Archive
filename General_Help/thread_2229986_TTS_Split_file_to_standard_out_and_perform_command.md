---
title: "TTS Split file to standard out and perform command on each split"
date: 2014-06-16
forum: General Help
---

### Post by jon49 on 2014-06-16
I'm not sure how to go about this. I'm using pico2wave to convert text to audio but my file is rather large. I would like to do something like this ```
cat myfile.txt | split (or sed?) | pico2wave -w myfile.wav splitFiles
```.

Any pointers would be much appreciated!

---

