---
title: "VLC Multicasting"
date: 2005-04-19
forum: General Help
---

### Post by jtdintulsa on 2005-04-19
I support and  deploy video telco installations and rely on VLC to check basic video delivery.  When I try to vlc --vv  udp://@224.1.1.134:8208  I don't get any video. When I kill VLC I get ....

[00000247] main private debug: prebuffering done 0 bytes in 3s - 0 kbytes/s
[00000247] main private error: cannot pre fill buffer
[00000244] main input warning: cannot create a stream_t from access
[00000140] main module debug: unlocking module "access_udp"
[00000244] main input debug: thread -1255040080 joined (src/input/input.c:290)


It acts like it can not get the stream but when I use tcpdump I se the IGMP joins and leaves...

Any Help would ber gratly apprecited.


-jtd ](*,)

---

### Post by flash76 on 2005-10-13
I am not sure ubuntu have stream support in vlc

---

### Post by porsche08a on 2005-10-13
The multicasting works fine for me with the latest version (0.84 - from svn).  I'm using Breezy Badger.  Since you seem to know a bit about IPTV, you wouldn't happen to know of a way to get MythTV or any other PVR using the raw multicast streams, would you?

I'd love to get a PVR running without a tuner card.

Ryan

---

