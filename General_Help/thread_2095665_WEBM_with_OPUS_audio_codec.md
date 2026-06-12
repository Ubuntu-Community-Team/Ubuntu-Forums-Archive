---
title: "WEBM with OPUS audio codec"
date: 2012-12-17
forum: General Help
---

### Post by Speechless on 2012-12-17
Hello I try to convert movie file to webm format with new audio codec OPUS

```
ffmpeg -i SCHINDLERS_LIST-chapter1.mpg -quality good -cpu-used 0 -b:v 500k -qmin 10 -qmax 42 -threads 2 -c:a libopus -b:a 64k output2.webm
```

but I have an error :confused:

```
Could not write header for output file #0 (incorrect codec parameters ?): Invalid argument
```

and i just read that Only VP8 video and **Vorbis audio** are supported for WebM.

So it's impossible to encode WEBM with new OPUS audio codec?

Best regards

---

### Post by andrew.46 on 2012-12-17
A little above this message you may have seen the following:

```

[webm @ 0x1941740] Only VP8 video and Vorbis audio are supported for WebM.

```

So not yet I guess...

---

