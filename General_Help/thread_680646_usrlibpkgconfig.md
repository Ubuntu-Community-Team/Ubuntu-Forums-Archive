---
title: "/usr/lib/pkgconfig ??"
date: 2008-01-28
forum: General Help
---

### Post by jwhitmore on 2008-01-28
I'm trying to build Songbird from source code and it works on my Desktop Ubuntu 7.10 but fails on my Laptop Ubuntu 7.10.

When I build on the Laptop the build fails with message:

checking for gstreamer-0.10 >= 0.10.1 gstreamer-plugins-base-0.10 >= 0.10.7... Package gstreamer-0.10 was not found in the pkg-config search path. Perhaps you should add the directory containing `gstreamer-0.10.pc' to the PKG_CONFIG_PATH environment variable No package 'gstreamer-0.10' found Package gstreamer-plugins-base-0.10 was not found in the pkg-config search path. Perhaps you should add the directory containing `gstreamer-plugins-base-0.10.pc' to the PKG_CONFIG_PATH environment variable No package 'gstreamer-plugins-base-0.10' found
configure: error: Library requirements (gstreamer-0.10 >= 0.10.1 gstreamer-plugins-base-0.10 >= 0.10.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


Now I do have the gstreamer stuff installed, so I'm confused. when I look for the .pc
file on my desktop it's sitting in /usr/lib/pkgconfig but on the laptop there's no gstreamer .pc file in the entire system. Is there some setting on synaptic to resolve this

J

---

### Post by tomdevries on 2008-02-05
Since I've been struggeling with pkg-config myself, I found your thread via Google. 

Have you tried searching for the .pc file using locate after a updatedb? Since you mentioned that you have gstreamer installed, one would assume that the .pc would be located somewhere right?

I've checked, and on my system the .pc files aren't available either. 
After installing  libgstreamer0.10-dev, the .pc files do show up in the /usr/lib/pkgconfig/:
```

tom@werkbak:~$ sudo apt-get install libgstreamer0.10-dev
tom@werkbak:~$ sudo updatedb
tom@werkbak:~$ locate gstreamer | grep pc
/usr/lib/pkgconfig/gstreamer-check-0.10.pc
/usr/lib/pkgconfig/gstreamer-net-0.10.pc
/usr/lib/pkgconfig/gstreamer-controller-0.10.pc
/usr/lib/pkgconfig/gstreamer-dataprotocol-0.10.pc
/usr/lib/pkgconfig/gstreamer-0.10.pc
/usr/lib/pkgconfig/gstreamer-base-0.10.pc
/usr/lib/gstreamer-0.10/libgstdvdlpcmdec.so
/usr/lib/gstreamer-0.10/libgstspc.so
```

Hope this helps you out.

---

