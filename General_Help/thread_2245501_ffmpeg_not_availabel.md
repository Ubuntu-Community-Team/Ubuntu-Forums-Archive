---
title: "ffmpeg not availabel"
date: 2014-09-24
forum: General Help
---

### Post by Silvernail on 2014-09-24
What do I do now?

gnome-ubuntu 14.04
> dave@dave-EL1600:~$  sudo -s apt-get install ffmpeg 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ffmpeg' has no installation candidate
dave@dave-EL1600:~$ 


---

### Post by slickymaster on 2014-09-24
See this: [http://askubuntu.com/questions/432542/is-ffmpeg-missing-from-the-official-repositories-in-14-04](http://askubuntu.com/questions/432542/is-ffmpeg-missing-from-the-official-repositories-in-14-04)

---

### Post by FakeOutdoorsman on 2014-09-24
The short story is if you want the authentic ffmpeg you have 4 main options:

[list]
[*][download, extract, and run a static build](http://johnvansickle.com/ffmpeg/). An easy option, but lacks support for x11grab (for screen grabbing/casting) and more "advanced" AAC encoders; usually not a deal breaker.
[*][use mc3man's PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media). He may have to correct me if this is the incorrect link.
[*][compile ffmpeg](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)
[*]Wait 15,000 years while the ffmpeg package moves from Debian testing or experimental or wherever it is into Ubuntu
[/list]

---

### Post by Silvernail on 2014-09-24
Thanks guys.  FFmpeg  installed.

---

### Post by mc4man on 2014-09-24
> **FakeOutdoorsman said:**
> The short story is if you want the authentic ffmpeg you have 4 main options:

[list]
[*][download, extract, and run a static build](http://johnvansickle.com/ffmpeg/). An easy option, but lacks support for x11grab (for screen grabbing/casting) and more "advanced" AAC encoders; usually not a deal breaker.
[*][use mc3man's PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media). He may have to correct me if this is the incorrect link.
[*][compile ffmpeg](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)
[*]Wait 15,000 years while the ffmpeg package moves from Debian testing or experimental or wherever it is into Ubuntu
[/list]

In regards to that ppa that is correct link. (for a static FFmpeg for use of binaries only
Because of the across the board (or almost) soname bump it could be an opportune time to provide shared FFmpeg libs in 14.04 with out the need to suffix the packages, the various .so's could co-exist. (devel packages are another story...

I've been considering it but atm don't think that there is that much to be gained on the decoding side to justify the work (most sources that use the shared libs would need to be rebuilt & possibly patched to use/work right.
 From an encoding side FFmpeg is superior & *most* of that can be handled by the various available static builds.

The semi adventurous could add my[ trusty media ppa]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media"), then add this ppa to push 14.04 up to libav11. Many common sources that use the shared libs have rebuilt/patched packages there also, not all possibly affected sources have been added. (I may do the same for FFmpeg in 14.04 down the road.
[https://launchpad.net/~mc3man/+archive/ubuntu/testing6](https://launchpad.net/~mc3man/+archive/ubuntu/testing6)

---

