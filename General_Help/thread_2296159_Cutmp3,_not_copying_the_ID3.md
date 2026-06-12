---
title: "Cutmp3, not copying the ID3"
date: 2015-09-23
forum: General Help
---

### Post by Eric_A. on 2015-09-23
I'm trying cut an MP3 and have it copy the ID3 over as well with **cutmp3 3.0.1** ([http://www.puchalla-online.de/cutmp3.html](http://www.puchalla-online.de/cutmp3.html)).
It's cutting the MP3 perfectly but the output doesn't contain the ID3/metadata of the source file.

My command
```
cutmp3 -i "input_with_ID3.mp3" -O "output.mp3" -a 0:10 -b 0:20 -c
```

Is there something wrong with my command or the application itself?

Manuals: [http://manpages.ubuntu.com/manpages/natty/man1/cutmp3.1.html](http://manpages.ubuntu.com/manpages/natty/man1/cutmp3.1.html)

---

