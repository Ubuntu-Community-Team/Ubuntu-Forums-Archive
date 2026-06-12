---
title: "convert videos to audio?"
date: 2007-06-12
forum: General Help
---

### Post by atlfalcons866 on 2007-06-12
how can i convert videos to an audio format like mp3?

---

### Post by soze on 2007-06-12
> **atlfalcons866 said:**
> how can i convert videos to an audio format like mp3?

From a DVD you can do:

transcode -i /dev/dvd -x dvd -T TITLE,-1,1 -a 0 -y raw -m outfile.mp3

where TITLE = track number of the DVD
and outfile.mp3 = name of mp3 file to create

---

### Post by atlfalcons866 on 2007-06-12
from  divx file or wmv

---

