---
title: "Composite and RENDER X extensions on vnc4server/Xvnc4."
date: 2013-09-26
forum: General Help
---

### Post by Jon_Riehl on 2013-09-26
Hi all,

I'm running a remote 12.04.3 VNC server (using vnc4server) on AWS EC2, and I can't figure out how to get the RENDER and Composite extensions working (which are needed for a Java application that uses per-pixel translucency).  It would seem that these could be conceivably supported in software, rendering on the server's virtualized frame buffer, but I have not been able to figure out how to do this with configuration files and out-of-the-box software.

Specifically, I'd like the output of "xdpyinfo" to indicate these extensions are supported (and an Oracle JDK 7 program I hacked together).  On my local system I see the following:

```

$ xdpyinfo | grep -i composite
    Composite
$ xdpyinfo | grep -i rend
    RENDER
$
```

On the remote box, these output nothing.

I can point to a specific AMI if anyone would like to play along at home.

Thanks!
-Jon

---

