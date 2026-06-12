---
title: "XIO: fatal IO error and libGL error"
date: 2015-03-08
forum: General Help
---

### Post by faikguler on 2015-03-08
hello friends ,
glxgears command results


```

libGL error: dlopen /usr/lib/fglrx/dri/i965_dri.so failed (/usr/lib/fglrx/dri/i965_dri.so: cannot open shared object file: Not a directory)
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
301 frames in 5.0 seconds = 60.125 FPS
299 frames in 5.0 seconds = 59.734 FPS
299 frames in 5.0 seconds = 59.736 FPS


XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 2936 requests (2936 known processed) with 0 events remaining.


```




but sudo glxgears results


```
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
301 frames in 5.0 seconds = 60.181 FPS
299 frames in 5.0 seconds = 59.739 FPS
299 frames in 5.0 seconds = 59.730 FPS

XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 2840 requests (2840 known processed) with 0 events remaining.



```


failed.


1- (libGL error) How do I fix the error
2- (XIO:  fatal IO error) How do I fix the error


```
~$ locate i965_dri.so
/usr/lib/i386-linux-gnu/dri/i965_dri.so
/usr/lib/x86_64-linux-gnu/dri/i965_dri.so

```


```

$ dpkg -l | grep fglrx


dpkg -l | grep fglrx
ii  fglrx                                                 2:14.501-0ubuntu1                                   amd64        Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                                        2:14.501-0ubuntu1                                   amd64        Catalyst Control Center for the AMD graphics accelerators
ii  fglrx-core                                            2:14.501-0ubuntu1                                   amd64        Minimal video driver for the AMD graphics accelerators
ii  fglrx-dev                                             2:14.501-0ubuntu1                                   amd64        Video driver for the AMD graphics accelerators (devel files)



```
```

$ ls /usr/lib/fglrx
10fglrx         dri         libGL.so    libGL.so.1.2  switchlibglx
alt_ld.so.conf  ld.so.conf  libGL.so.1  switchlibGL   xorg
```


```

$ ls /usr/lib32/fglrx
dri              libAMDXvBA.so.1.0   libGL.so.1     libXvBAW.so.1.0
libAMDXvBA.cap   libfglrx_dm.a       libGL.so.1.2
libAMDXvBA.so    libfglrx_dm.so.1.0  libXvBAW.so
libAMDXvBA.so.1  libGL.so            libXvBAW.so.1

```





Is there anyone who can help?
thank you.

---

