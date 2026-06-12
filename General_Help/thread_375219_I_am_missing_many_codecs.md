---
title: "I am missing many codecs"
date: 2007-03-03
forum: General Help
---

### Post by error404 on 2007-03-03
Most of my pron videos don't run on Ubuntu... Is there a way to install the most common codec all in one shot?

thanks :)

---

### Post by taurus on 2007-03-03
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by CocoAUS on 2007-03-03
```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \ gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \ gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
```

---

