---
title: "Songbird for linux won't play .mp3"
date: 2007-07-19
forum: General Help
---

### Post by sarahsilverman on 2007-07-19
i can't play any .mp3 files or anything similar. only .wav files can play. it always says error, there isn't anything else just error. is there anything i can do or download to make it able to do that?

thank you any help is appreciated:popcorn:

---

### Post by Spudgun on 2007-07-19
Installing the codecs should sort it.

```
sudo aptitude install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```

And...

```
sudo aptitude install w32codecs
```

---

