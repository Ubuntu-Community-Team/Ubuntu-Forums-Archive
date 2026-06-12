---
title: "Swiftfox switches from Flash 9 to Flash 7"
date: 2006-12-03
forum: General Help
---

### Post by raul_ on 2006-12-03
So here's what happens. I have Flash 9 installed both in Firefox and Swiftfox (i copied the files myself). When I try to play a video with Flash 9 in Swiftfox it's all good, but sometimes Flash 9 freezes (even with the latest update) and after that Swiftfox switches back to Flash 7, but i don't want it to =\ (because Flash 7 kinda sucks). Why does it switch back, and where does Swiftfox get Flash 7 from?

Thanks

---

### Post by reclusivemonkey on 2006-12-03
> **raul_ said:**
> So here's what happens. I have Flash 9 installed both in Firefox and Swiftfox (i copied the files myself). When I try to play a video with Flash 9 in Swiftfox it's all good, but sometimes Flash 9 freezes (even with the latest update) and after that Swiftfox switches back to Flash 7, but i don't want it to =\ (because Flash 7 kinda sucks). Why does it switch back, and where does Swiftfox get Flash 7 from?

Thanks

Give us the output from 

```

ls -l /usr/lib/firefox/plugins/

```

---

### Post by raul_ on 2006-12-04
```

total 8684
-rwxr-xr-x 1 raul root     856 2006-10-05 22:41 flashplayer.xpt
-rw-r--r-- 1 raul root 6904912 2006-11-20 19:35 libflashplayer.so
-rw-r--r-- 1 root root    7816 2006-09-21 11:27 libgfxpsshar.so
-rw-r--r-- 1 root root  114988 2006-09-21 11:27 libgkgfx.so
-rw-r--r-- 1 root root   76852 2006-09-21 11:27 libgtkembedmoz.so
-rw-r--r-- 1 root root   14324 2006-09-21 11:27 libgtkxtbin.so
-rw-r--r-- 1 root root   89100 2006-09-21 11:27 libjsj.so
-rw-r--r-- 1 root root  620708 2006-09-21 11:27 libmozjs.so
-rw-r--r-- 1 root root  239688 2006-09-21 11:27 libnssckbi.so
-rw-r--r-- 1 root root     476 2006-09-21 11:23 libsoftokn3.chk
lrwxrwxrwx 1 root root      36 2006-11-20 22:03 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root      37 2006-11-20 22:03 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root      38 2006-11-20 22:03 libtotem-complex-plugin.so -> ../../totem/libtotem-complex-plugin.so
lrwxrwxrwx 1 root root      39 2006-11-20 22:03 libtotem-complex-plugin.xpt -> ../../totem/libtotem-complex-plugin.xpt
lrwxrwxrwx 1 root root      34 2006-11-20 22:03 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root      35 2006-11-20 22:03 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root      36 2006-11-20 22:03 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root      37 2006-11-20 22:03 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root      42 2006-11-20 22:03 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root      43 2006-11-20 22:03 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root    9044 2006-10-23 13:51 libunixprintplugin.so
-rw-r--r-- 1 root root   96980 2006-09-21 11:27 libxpcom_compat.so
-rw-r--r-- 1 root root  630488 2006-09-21 11:27 libxpcom_core.so
-rw-r--r-- 1 root root    9996 2006-09-21 11:27 libxpcom.so
-rw-r--r-- 1 root root    7568 2006-09-21 11:27 libxpistub.so
lrwxrwxrwx 1 root root      38 2006-10-01 00:55 nphelix.so -> /usr/lib/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 root root      39 2006-10-01 00:55 nphelix.xpt -> /usr/lib/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx 1 root root      50 2006-11-20 22:02 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so

```

---

### Post by reclusivemonkey on 2006-12-05
Does swiftfox have its own directory in /usr/lib? I would delete any extra plugins you have in your home directory; these will be in something like

```

~/.mozilla/firefox/xylmoae3.default/plugins

```

---

### Post by raul_ on 2006-12-05
I think that did it :) i always forget of the folders created in the home dir.

Thanks

---

