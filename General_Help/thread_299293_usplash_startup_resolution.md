---
title: "usplash startup resolution"
date: 2006-11-13
forum: General Help
---

### Post by | MM | on 2006-11-13
My usplash startup resolution is not abiding by what  have set it to be in usplash.conf.  It does not want to budge from 1280*???

```

# Usplash configuration file
xres=1152
yres=864

```

And yet the shutdown usplash does abide by the usplash.conf configuration.


Any thoughts.

---

### Post by johny42 on 2006-12-08
I had the same problem, and it was solved after I had rebuilt my initrd.img. I suggest you use the application discussed in [this thread]("http://ubuntuforums.org/showthread.php?t=304407") to do that.

---

