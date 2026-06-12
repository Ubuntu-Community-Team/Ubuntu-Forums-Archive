---
title: "Strange behaviour with nvidia-glx"
date: 2006-09-17
forum: General Help
---

### Post by patsissons on 2006-09-17
I reinstalled ubuntu yesterday (kubuntu actually).  As I was going through the standard routine of installing the extra packages, I came across some oddities with the nvidia-glx package.  It would seem that the nvidia-glx package depends on the 2.6.15-23 kernel image.  This is fine (as I am currently running this kernel, 2.6.15-23-k7-smp to be more specific), but the linux-k7(-smp) meta-packages depend on the latest kernel image and headers (*-26-k7 at the time of this posting).  This in turn breaks my X as nvidia-glx won't play nicely with these packages.  I would really rather be able to use the meta-packages as it helps keeping up-to-date kernerls installed.  Can anyone shed some light on this issue please? ](*,)

---

### Post by kuja on 2006-09-17
Maybe the linux-restricted modules (which nvidia-glx depends on) aren't being kept up to date. I had an issue with that a while ago (though I'm using the k8 kernel).

```
sudo apt-get install linux-image-2.6.15-26-k7-smp linux-restricted-modules-2.6.15-26-k7-smp nvidia-glx
```

That might fix it for you.

---

### Post by patsissons on 2006-09-17
Turns out that the problem was on my end.  I had tried out easy-ubuntu for the first time with this install and did not realize that it disables all of my repository sources and adds only the basic ones #-o All is well now and I'll remember this for the future.

Thanks for the input kuja, although not directly related to the solution, your post spawned a search pattern that led me to figure it out.  Greatly appreciated :)

---

