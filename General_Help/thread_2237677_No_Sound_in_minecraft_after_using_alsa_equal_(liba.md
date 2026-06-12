---
title: "No Sound in minecraft after using alsa equal (libasound2-plugin-equal)"
date: 2014-08-03
forum: General Help
---

### Post by dr-frost-dk on 2014-08-03
Finally got the equal working in 12.04 and many things seems to work as they should, some programs/players needs specific audio card settings to use the EQ or they will play audio without EQ or no audio

Now i was fancying a little minecraft but there are no audio at all...
So is there some setting im missing in .asoundrc or is there a "-ao" to java i can use?

side note, can't seem to get audacious to use the EQ....

.asoundrc
```
ctl.equal {
type equal;
}
pcm.plugequal {
type equal;
slave.pcm "plug:dmix";
}
pcm.!default {
type plug;
slave.pcm plugequal;
}
```

Setup is pretty plain, only onboard audio to worry about

---

