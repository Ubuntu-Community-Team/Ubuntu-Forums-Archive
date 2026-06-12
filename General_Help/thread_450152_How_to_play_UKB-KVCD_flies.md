---
title: "How to play UKB-KVCD flies?"
date: 2007-05-21
forum: General Help
---

### Post by _Pieter_ on 2007-05-21
Guys,

I have this amazing movie on my computer, but it is in the UKB-KVCD format with .bin as extension. When I try to play it, Ubuntu says there is no program (even in the repositories) that knows how to handle this puppy. Any experience with this? Any help is welcome!

---

### Post by bmagyarkuti on 2007-05-24
Hi, mplayer (available from the apt repositories) can play KVCD files.

If you prefer to use an other media player like xine, you can convert the bin to avi using mencoder with the following command:

```
mencoder -o bla.avi -of avi -ffourcc DX50 -lavcopts vbitrate=900:vhq -ovc lavc -oac mp3lame -vf pp=lb THEFILE.bin
```

---

### Post by nuclearj on 2008-06-06
for the record VLC plays the KVCD.bin files as well

---

