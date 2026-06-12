---
title: "Sound Applet shows no devices"
date: 2015-02-12
forum: General Help
---

### Post by jcllings on 2015-02-12
Sound works. I can see audio devices if I go:

lspci -v | grep -A7 -i "audio"

Also I can hear it. ...but the sound applet displays no sound devices so it would not appear to be a device or driver issue. It would appear to be directly realted to the mixer applet. Hm... I'll install another PulseAudio mixer and check results.

---

### Post by jcllings on 2015-02-12
Hmm... I've done a re-install of all the pulseadio packages and now it works properly.  ...of course I don't know if the fix will work acrossed a restart so I'll do that next. If you don't hear back from me immediately, it worked. ;-)

---

### Post by ttetsumako on 2015-02-13
Thanks for sharing, Keep it up.[70-687](http://www.test-inside.com)

---

