---
title: "Live streaming"
date: 2014-08-19
forum: General Help
---

### Post by asai on 2014-08-19
Hi,

I have several Vivotek cameras that I use for monitoring activity in birds nests. :)
Now I would like to set up a live streaming server so I can send a live feed to my website.
Any suggestions on how I can do this? I have a Ubuntu 12.04 LTS server dedicated for this.

---

### Post by Frogs Hair on 2014-08-19
Here is a starting point , but I have no experience with server streaming . [https://trac.ffmpeg.org/wiki/Streaming%20media%20with%20ffserver](https://trac.ffmpeg.org/wiki/Streaming%20media%20with%20ffserver)

---

### Post by tgalati4 on 2014-08-19
Set up *motion* or *zoneminder* and poke a hole in your firewall so you can see the streams directly or use *rsync* to send clips to your offsite webserver  You can set the sensitivity to reduce the amount of capture, so that you only capture video when there is significant activity happening.

---

