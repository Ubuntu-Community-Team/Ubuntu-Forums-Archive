---
title: "upside down camera"
date: 2013-11-02
forum: General Help
---

### Post by mastablasta on 2013-11-02
After some search i've managed to turn the camera correctly in Skype. these two commands solve it and i've replaced previous one in my skype script
```

export LIBV4LCONTROL_FLAGS=3
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

i have two questions. the camera is still upside down in other programmes (e.g kamerka)

1. is it possible to make such a command sort of permanent instead of always run it to run the application that uses camera?
2. does this command affect anything else in the OS?

---

