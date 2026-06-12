---
title: "Need help bisecting"
date: 2016-09-25
forum: General Help
---

### Post by Diskdoc on 2016-09-25
Hi! First of all, please move my post if it's in the wrong place. I would have written in some debugging / developer forum but I couldn't find it.

I'm going to try to do a kernel bisect in order to shed some light on:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1611536](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1611536)

..I could use some help!

For the moment, I've done a git clone folliwing the first two steps here:

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

I figure I want to do as per "Confirmation of mainline test results" as mentioned in

[https://wiki.ubuntu.com/Kernel/KernelBisection](https://wiki.ubuntu.com/Kernel/KernelBisection)

i.e. "git t checkout v4.0.9" which gives me "error: pathspec 'v4.0.9' did not match any file(s) known to git."

I'm pretty lost as to if I'm on the right track or not. I just would like to build mainline kernel 4.0.9 and test to see that it works as a starting point.

---

