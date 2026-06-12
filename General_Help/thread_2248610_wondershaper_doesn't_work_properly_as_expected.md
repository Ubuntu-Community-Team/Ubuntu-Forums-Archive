---
title: "wondershaper doesn't work properly as expected"
date: 2014-10-15
forum: General Help
---

### Post by Nguyen_Quang_Trung on 2014-10-15
I am struggling with an issue brought by "wondershaper". I set up a network bridge for doing a network simulator, and use wondershaper to throttle the network bandwidth.
I ran command :  "sudo wondershaper eth0 5120 3072" (down 5M, up 3M), for example, however when I tried to test the bandwidth by using speedtest.net I got a wrong bandwidth like down from 1M to 2M, up from 0 to 3M. When I clear the settings with command "sudo wondershaper clear eth0", it does get back the normal bandwidth like down 7M/ up 7M.

I have tried several times but all I got is the wrong bandwidth. So anyone here experienced the same problem with me ?

Thanks in advance !

---

