---
title: "playback .raw audio file?"
date: 2007-12-05
forum: General Help
---

### Post by android6011 on 2007-12-05
I'm checking out a program that will record from a bluetooth headset to a file such as out.raw , however when i try to playback the file in any application including audacity all i get is static. the same program also lets you play .raw files through the bluetooth headset and when i do i can hear what was recorded, I just dont know how to playback/convert the .raw files on my computer.

---

### Post by mali2297 on 2007-12-05
Try
```

aplay out.raw

```

It should be possible to convert the files with **sox**. From the man page:
> 
       .raw      Raw files (no header).
                 The  sample  rate, size (byte, word, etc), and encoding (signed, unsigned, etc.)
                 of the sample file must be given.  The number of channels defaults to 1.

Though I don't know how one would decide sample rate etc.

---

