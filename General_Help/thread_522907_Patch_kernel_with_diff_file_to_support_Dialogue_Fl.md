---
title: "Patch kernel with diff file to support Dialogue Flybook with Penmount Touchscreen."
date: 2007-08-11
forum: General Help
---

### Post by Jaidee on 2007-08-11
Hello folks, I've been lucky enough to get a Dialogue Flybook V33i. I have Ubuntu up and running, clean installation at present, as I want to try and get the touchscreen running first of all.

I've been running Ubuntu on other machines for two years now, but never played with the kernel. 

After a few days research I've found [URL="http://www.fuschlberger.net/flybook/11"]this
[/URL] and [URL="http://users.tkk.fi/~hlinnaka/flybook/"]this
[/URL] which seem to show that the touchscreen is supported after the kernel is patche with the neccessary file. Looking on the wiki I've seen that there are certain things needed to compile a kernel, so I've installed these. 

```
sudo apt-get install linux-kernel-devel fakeroot kernel-wedge kernel-package
sudo apt-get build-dep linux-source
```

```
apt-get source linux-source
```

Now, I've also got the diff file from the above website. Would it be possible for someone to describe to me how to apply the diff to the kernel, and then compile the new kernel? Would I expect to be given modules as a result? Any help is much appreciated.

---

### Post by BC7333 on 2007-08-14
I recently bought the Flybook V5 and am trying to do the same thing..

Also a newbie not quite ready to do kernel patches..

Maybe someone out there can patch a kernel for us and upload?

Am using 2.6.22-9-generic

Followed some mighty fine instructions [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974) to upgrade my kernel so some instructions along these lines would be great.

---

