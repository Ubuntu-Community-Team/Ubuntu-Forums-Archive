---
title: "eyeD3"
date: 2006-12-30
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-12-30
Has anybody been able to write full lyrics to an .mp3 using eyeD3?

I try:

```

dugster@dugster-desktop:~$ eyeD3 --lyrics=[eng]:Zombie: Another head hangs lowly, /home/dugster/Desktop/Cranberries-Zombie.mp3 File Not Found: Another File Not Found: head File Not Found: hangs File Not Found: lowly,

Cranberries-Zombie.mp3  [ 4.67 MB ]
--------------------------------------------------------------------------------
Time: 5:06      MPEG1, Layer III        [ 128 kb/s @ 44100 Hz - Joint stereo ]
--------------------------------------------------------------------------------
Removing lyrics: Zombie
Writing tag...
ID3 v1.0:
title: Zombie           artist: The Cranberries
album:          year: 1978
track:          genre: Unknown (id 255)
Comment: [Description: ID3 v1 Comment] [Lang: eng]
, AG# 4080746D
```

But nothing shows up as lyrics on my iPod. Anyone fooled around w/. eyeD3?

---

### Post by rommel_rco on 2007-09-22
if the mp3 is named testing_music.mp3 and the lyrics to it is saved in a file name testing_music.txt, then you can do this:

eyeD3 -L "::$(cat testing_music.txt)" testing_music.mp3

This skips the language and description fields

---

