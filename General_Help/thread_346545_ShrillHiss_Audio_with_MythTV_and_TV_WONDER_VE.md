---
title: "Shrill/Hiss Audio with MythTV and TV WONDER VE"
date: 2007-01-25
forum: General Help
---

### Post by pnotequalsnp on 2007-01-25
Hello everyone,

thank-you in advance for taking a look at my problem.

When I watch or record TV using mythTV, I hear a loud shrill or hissing noise in the background that becomes very loud if I want to hear the audio. The picture is fine and the audio is ok except for this shrill noise. If I watch TV with TV Time Viewer all is well so I believe it is a problem with MythTV(?)

Does anyone have any suggestions?

Setup:
ATI TV WONDER VE
Ubuntu 6.10
Mythtv v.20
Sound Works but with Shrill
Video works
Recording Works
Video Card: /dev/video0
Audio Input: /dev/dsp
Audio Sampling rate limit: none (but tried all combinations)
Note: I have an audio cable from my Tuner card into the Line In on my Sound Card.

---

### Post by pnotequalsnp on 2007-01-27
Solution:
 Setup... > tv settings... > recording profiles... change from MP3 to uncompressed

Worked for me!

---

