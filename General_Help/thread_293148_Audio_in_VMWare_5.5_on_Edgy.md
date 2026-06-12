---
title: "Audio in VMWare 5.5 on Edgy"
date: 2006-11-04
forum: General Help
---

### Post by aetherane on 2006-11-04
I have been unable to get audio to work properly in vmware on edgy (I got it to work fine before when I was running dapper).

I originally got an error saying that it could not aquire the sound device because "/dev/dsp" wasn't found.

I tried running it with alsa-oss by using the following command:
```
LD_PRELOAD=/usr/lib/libaoss.so:/usr/lib/libdbus-1.so.3 exec /usr/bin/vmware "$@"
``` but vmware still can't connect to the sound device (though the "/dev/dsp" not found error doesn't show up).

---

### Post by hpne on 2006-11-19
I have same problem. Anyone?

---

