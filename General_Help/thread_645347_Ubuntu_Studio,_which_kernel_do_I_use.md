---
title: "Ubuntu Studio, which kernel do I use"
date: 2007-12-19
forum: General Help
---

### Post by survient on 2007-12-19
I have ubuntu studio installed, but I'm not sure which kernel I should generally use. What's the benefit with the RT kernel over the generic? Is the RT kernel strictly for encoding or can it also be used to benefit gaming? Also, for streaming(transcoding), does the RT kernel provide a benefit? I mess around with encoding and editing so I figured I'd install Ubuntu Studio, but I'm not sure when to use which kernel.

---

### Post by logos34 on 2007-12-20
-rt (low-latency) kernel = better performance.  Use it if you can.  (I wish I could, but it won't hibernate/suspend on my machine).

[http://ubuntuforums.org/archive/index.php/t-452506.html](http://ubuntuforums.org/archive/index.php/t-452506.html)
[http://distrogue.blogspot.com/2007/06/full-length-review-ubuntu-xubuntu-and.html](http://distrogue.blogspot.com/2007/06/full-length-review-ubuntu-xubuntu-and.html)
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
(->'Real Time Kernel & Xruns')

---

### Post by ~LoKe on 2007-12-20
> **logos34 said:**
> -rt (low-latency) kernel = better performance.  Use it if you can.  (I wish I could, but it won't hibernate/suspend on my machine).

[http://ubuntuforums.org/archive/index.php/t-452506.html](http://ubuntuforums.org/archive/index.php/t-452506.html)
[http://distrogue.blogspot.com/2007/06/full-length-review-ubuntu-xubuntu-and.html](http://distrogue.blogspot.com/2007/06/full-length-review-ubuntu-xubuntu-and.html)
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
(->'Real Time Kernel & Xruns')

RT is the low latency kernel?  It's named differently under Ubuntu Studio, correct?  I'm running standard 7.10 (Gutsy) and I have the -rt in the repositories, I assume I can install this?

---

### Post by logos34 on 2007-12-20
> **~LoKe said:**
> RT is the low latency kernel?  It's named differently under Ubuntu Studio, correct?  I'm running standard 7.10 (Gutsy) and I have the -rt in the repositories, I assume I can install this?

yep, or to be precise the -rt kernel is optimized to run in studio audio production low-latency mode.

Get the 'linux-rt' metapackage--it'll drag in the latest image and restricted-modules pkgs.

---

### Post by ~LoKe on 2007-12-20
> **logos34 said:**
> yep, or to be precise the -rt kernel is optimized to run in studio audio production low-latency mode.

Get the 'linux-rt' metapackage--it'll drag in the latest image and restricted-modules pkgs.

Got it, seems to be working just fine.  Thanks. :)

---

