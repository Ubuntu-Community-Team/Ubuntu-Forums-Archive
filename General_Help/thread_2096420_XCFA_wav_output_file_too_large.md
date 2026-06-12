---
title: "XCFA wav output file too large"
date: 2012-12-19
forum: General Help
---

### Post by taunnt on 2012-12-19
Hello, I'm using XCFA to convert some mp3 files to wave (.wav). When XCFA converts them the final file is very large (a full 80min cd would be around 1.7gigs). I looked in the settings I didn't see anything for wav files just wv files. Is there something I should install to remedy this?

Thanks

---

### Post by andrew.46 on 2012-12-23
Have you tried just a basic FFmpeg command and checked the size difference with the output file? For example:

```
ffmpeg -i input_file.mp3 output_file.wav
```

wav files tend to be pretty big, this is their nature, can I ask why you need wav files?

---

### Post by taunnt on 2012-12-24
> **andrew.46 said:**
> Have you tried just a basic FFmpeg command and checked the size difference with the output file? For example:

```
ffmpeg -i input_file.mp3 output_file.wav
```

wav files tend to be pretty big, this is their nature, can I ask why you need wav files?

To burn to a audio CD.

---

### Post by andrew.46 on 2012-12-25
Depending on your playback device you may find that playback from cd is possible with mp3 files. This may save the pain you are going through with conversion to wav :)

---

