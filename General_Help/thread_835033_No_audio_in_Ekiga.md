---
title: "No audio in Ekiga"
date: 2008-06-20
forum: General Help
---

### Post by bpont on 2008-06-20
I did a fresh install of Hardy Heron.  I set up Ekiga and called sip:500@ekiga.net for the echo test.  I could hear the recording, but my mic wasn't working.  I then installed Ekiga snapshot following [this advice]("https://help.ubuntu.com/community/Ekiga#head-57385c7cf79361cbb4d7195b9f43c1bb33c1e94c"), thinking maybe it would be better.  Afterwards, I couldn't hear the recording on the echo test!  So I reverted back to the stable version, but now I still can't hear audio when I call the echo test.  Anyone have any ideas for a fix?
[B]
Solution:[/B]

First, clean the configuration:

```
ekiga-config-tool --clean
```

Second: 
```

killall gconfd-2
```

Third:

turn the echo cancellation off in prefs->Audio->codecs

*Also, make sure to go into volume control and activate microphone capture!*

---

### Post by Zorael on 2008-06-20
Please mark as solved under Thread Tools, the subject seems to not have been updated. :>

---

