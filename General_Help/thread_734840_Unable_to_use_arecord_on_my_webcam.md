---
title: "Unable to use arecord on my webcam"
date: 2008-03-25
forum: General Help
---

### Post by kung fu buntu on 2008-03-25
I have a logitech quickcam fusion and am trying to record some sound with it, but...

arecord -d 10 -f cd -D hw:2,0 -t wav test.wav
Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
arecord: set_params:923: Channels count non available


arecord -d 10 -D hw:2,0  -t wav  test.wav
Recording WAVE 'test.wav' : Unsigned 8 bit, Rate 8000 Hz, Mono
arecord: set_params:918: Sample format non available

---

### Post by kung fu buntu on 2008-03-25
anybody?

---

### Post by kung fu buntu on 2008-03-27
sniff.... :(

somebody must know this...

---

### Post by ipx on 2008-05-24
I have the same problem. If anyone knows any solution I would be very grateful. :)

---

### Post by kung fu buntu on 2008-06-16
Anybody?

---

