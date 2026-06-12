---
title: "Xlib_skip_argb_visuals=1"
date: 2008-06-15
forum: General Help
---

### Post by Frikazoid on 2008-06-15
I found many suggestion about this string XLIB_SKIP_ARGB_VISUALS=1 as a solution to firefox crashes with flash contents.

I put that inside the /usr/bin/firefox script... but now I cannot use compiz anymore

If i run compiz command it says no xgl, but I always used it perfectly before that.
thank you

---

### Post by Forlong on 2008-06-15
Post the complete output here.

And this might also be a good for additional info: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by Frikazoid on 2008-06-15
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


I tried to reinstall nvidia

---

### Post by Forlong on 2008-06-15
You don't need Xgl on a nvidia chip.
Remove it:
```
sudo apt-get remove xserver-xgl
```
Then restart X and post the output of [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

