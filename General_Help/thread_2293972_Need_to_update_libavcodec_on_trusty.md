---
title: "Need to update libavcodec on trusty"
date: 2015-09-08
forum: General Help
---

### Post by joshua60 on 2015-09-08
Warning: I am somewhat new to linux but trust that I am trying to google everything involved here that I possibly can already.

There are already a lot of posts on ffmpeg and avlib on here but they don't really address this issue.

I'm having trouble building something called essentia ([http://essentia.upf.edu/](http://essentia.upf.edu/)) on ubuntu 14.04. It requires a number of libraries that come with ffmpeg or avlib. It seems to be ok with everything except libavcodec which needs to be version 55 or greater, whereas trusty comes with v53 from avlib. Indeed the documentation ([http://essentia.upf.edu/documentation/installing.html](http://essentia.upf.edu/documentation/installing.html)) states that while some other library for essentia is the correct version on 14.04, the libav versions are correct on 14.10. I don't understand why they would say this. Does this mean I need to install libraries made for other versions of ubuntu, or that those were just the versions of the reference libraries used for development that I should acquire somehow? I can't find any way to update the libraries on my system. I've tried uninstalling them and installing newer versions from 3rd party sources for ffmpeg, but those installations seem to put the libraries in different folders altogether that my build can't find, and I can't find any pkg-config for them on my system. When I built ffmpeg from scratch I just got binaries and couldn't even find the libraries.

It looks like the build on ubuntu 14.10 is supposed to work fine ([http://chrisstrelioff.ws/sandbox/2014/12/10/installing_essentia_for_audio_feature_extraction.html](http://chrisstrelioff.ws/sandbox/2014/12/10/installing_essentia_for_audio_feature_extraction.html)) although it doesn't make much sense since I think the libavcodec on 14.10 is too old as well.

I imagine this is very general problem that comes up a lot: you try to build something that has a dependency for a library newer than the one ubuntu comes with. How do you force an upgrade and get it installed in the usual places in ubuntu to builds can find them?

Apologies for my lack of knowledge. 
Any suggestions?

---

### Post by mc4man on 2015-09-08
15.04 would work for you as will the upcoming 15.10 (15.04 would build using libav11, 15.10 will use FFMpeg
Note that both are just 9 month releases.
As far as 14.04 - if you wish to stay on I'll link you a ppa with libav11 in 14.04

---

### Post by joshua60 on 2015-09-08
Thanks for the reply. 
Yes I need to stay on 14.04 for other reasons unfortunately. 
A ppa would be great! Thanks! Just to be clear: after install it would act just like my system avlib (be stored in the same places)? Also, should I only remove libav-tools first, or other libs as well?

Thanks again

---

### Post by mc4man on 2015-09-08
> **joshua60 said:**
> Thanks for the reply. 
Just to be clear: after install it would act just like my system avlib (be stored in the same places)? Also, should I only remove libav-tools first, or other libs as well?

Thanks again
Everything would be installed as it/they are now
The ppa works best with another one though not required (advised
Please read thru both these pages carefully first, then let me know & i'll give you some commands for proper adding/upgrading if you wish to proceed

advised, not required - [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)
adds libav11 & rebuilt packages that depend on it
[https://launchpad.net/~mc3man/+archive/ubuntu/testing6](https://launchpad.net/~mc3man/+archive/ubuntu/testing6)

---

