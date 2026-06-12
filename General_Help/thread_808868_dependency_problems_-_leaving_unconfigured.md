---
title: "dependency problems - leaving unconfigured"
date: 2008-05-26
forum: General Help
---

### Post by theophiles on 2008-05-26
Just updated and got a serious problem. When I boot to the new kernel I get nothing. No loading screen, no splashy, no login, no text, nothing!
I knew I had just downloaded the new kernel and thought that maybe I had gotten a bad download so I tried booting to an old kernel and reinstalling the new one from Synaptic. I learned that I had a pretty good diagnosis, but not a very good solution:

```
E: linux-image-2.6.24-17-rt: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-17-generic: subprocess post-installation script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-17-rt: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-image-rt: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-17-rt: dependency problems - leaving unconfigured
E: linux-restricted-modules-rt: dependency problems - leaving unconfigured
E: linux-rt: dependency problems - leaving unconfigured
```

I have no trouble booting from the generic kernel. I originally installed the rt kernel back when I was running 8.04 in beta. This solved a problem with failing to initialize HAL. 

Am perfectly happy running the generic kernel, if I simply deselect the rt kernel in Synaptic will it do terrible things to my system or is that the proper way to simply remove the rt kernel? Or would it be better to find a fix for the rt kernel? If so, what sort of fix would that be?

[I]**edit May 27th, 2008 1:41pm central time:
I tried to simply deselect the rt kernel and got an "error 1." I could really use some help![/I]

---

### Post by theophiles on 2008-05-30
I gave up and went with a clean install.

---

