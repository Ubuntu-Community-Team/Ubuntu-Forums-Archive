---
title: "Desktop effects is no longer efficient"
date: 2008-06-01
forum: General Help
---

### Post by pgilmon on 2008-06-01
Hi all,

I am just wondering why desktop effects are no longer as resource-efficient as they used to be. I remember I manually installed Beryl on my laptop with ubuntu 6.10 and a nvidia go 7400. I used "nvidia" option for rendering (other options where AIGLX and XGL). When I flipped the cube, the processor just didn't seem to notice, since the GPU did all the job.

However, with an out-of-the-box ubuntu 8.04 with desktop effects enabled, the same operation on the same laptop takes about 80% of the CPU. Does anyone know what is going on here?

Perhaps ubuntu uses by default AIGLX, which would take much more resources than the "nvidia" way on a nvidia card. If so, is there any way of changing the rendering method? I just can't find it in the compiz-fusion settings manager (It was indeed available in the old beryl-settings I used one year ago).

---

### Post by Forlong on 2008-06-02
You can use [this]("http://ubuntuforums.org/showthread.php?t=799070") to check what rendering method you are using (although AIGLX is not an option for Nvidia cards AFAIK).

And to get the settings manager, you have to install ccsm ```
sudo apt-get install compizconfig-settings-manager
```
It will then be available under S*ystem &#8594; Preferences &#8594; Advanced Desktop Effects Settings*

---

