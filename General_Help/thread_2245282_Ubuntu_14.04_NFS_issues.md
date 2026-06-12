---
title: "Ubuntu 14.04 NFS issues"
date: 2014-09-22
forum: General Help
---

### Post by kpope83 on 2014-09-22
I'm running 14.04 as my desktop environment, I wanted to stream files to my RaspBMC installation in the living room. I install and configured the NFS services and it worked great when I tested it. however now when I stream anything longer than about 15 minutes the share I'm streaming from will suddenly unmount and I end up having to restart the service on the server to get it working again.

am I missing a maximum connection time in the config file some where or is this a problem with the service its self?

---

### Post by TheFu on 2014-09-22
Wired ethernet?  Should work great.
Or you could use DLNA - plex server and any DLNA client/renderer out there.

Of course, the rPi ability to playback smoothly is completely dependent on the video/audio codecs used - it is very important to only use codecs supported in hardware, not software.

---

### Post by matt_symes on 2014-09-22
Hi

> **kpope83 said:**
> am I missing a maximum connection time in the config file some where or is this a problem with the service its self?

.... Not that i'm aware of, unless it's using autofs' timeout or something like that.

I use OpenElec on my raspberry and use samba to serve the (read only) media shares on my media server. I use NFS with authentication to update the media shares. This has served me pretty well.

If you don't get an answer on here, have you asked on the raspbmc forums ?

EDIT: Doh. That's a couple of answers you now have.

Kind regards

---

