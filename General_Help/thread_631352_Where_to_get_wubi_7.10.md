---
title: "Where to get wubi 7.10?"
date: 2007-12-04
forum: General Help
---

### Post by nintennuendo on 2007-12-04
Where can I find it?

---

### Post by ago on 2007-12-04
[http://www.wubi-installer.org/devel/minefield](http://www.wubi-installer.org/devel/minefield)

---

### Post by nintennuendo on 2007-12-04
Thanks

---

### Post by pwright2 on 2007-12-07
Is the fact that the folder is named minefield significant?

-----Paul------

---

### Post by ago on 2007-12-07
Those are unofficial pre-release builds, some builds are more experimental than others and some completely broken, that said, the latest 7.10 build in there is quite okish except for an annoying bug that creates a freeze during installation in some circumstances (which is the main reason I cannot release 7.10).

---

### Post by mikedep333 on 2007-12-07
Yeah, I've had success with the latest one there, revision 386. Well, at least I did on my non-fake-raid system.

Anyway, are there any newer builds available? The latest revision, 386, is from no later than November 11th.

---

### Post by ago on 2007-12-07
No newer builds for the time being, since I am already working on 8.04...

---

### Post by musicalmike on 2007-12-07
Is the random freeze bug known to occur on an HP Pavilion dv6000?

---

### Post by ago on 2007-12-10
maybe

---

### Post by flamelab on 2007-12-10
> **ago said:**
> No newer builds for the time being, since I am already working on 8.04...

I guess since the program has no problems concerning the kernel recognition - and generally the whole program update - after a version update (7.10 --> 8.04) , and since the lag during the installation has been gone , you'd better change the latest build version to beta , not alpha  .

---

### Post by churka07 on 2007-12-12
Why can't you finish 7.10???

Its gonna be a while till 8.04....

---

### Post by ago on 2007-12-13
> **flamelab said:**
> I guess since the program has no problems concerning the kernel recognition - and generally the whole program update - after a version update (7.10 --> 8.04) , and since the lag during the installation has been gone , you'd better change the latest build version to beta , not alpha  .

As far as I know there is still the system freeze bug in 7.10 which is the main thing holding back a release.
We might jump to 8.04 directly in case, since the 2.6.24  kernel in there should hopefully be more friendly. Work on 8.04 has already begun and preliminary builds will be available soon.

---

### Post by ago on 2007-12-13
> **churka07 said:**
> Why can't you finish 7.10???

Because there is a compatibility problem with the 7.10 kernel and I would have to patch and maintain (read follow up ALL security upgrades) my own kernel, which is far too much work.

---

### Post by daspooky on 2007-12-13
> **ago said:**
> Because there is a compatibility problem with the 7.10 kernel and I would have to patch and maintain (read follow up ALL security upgrades) my own kernel, which is far too much work.

Well then lets hope wubi works again with 8.04. I'm already looking forward to it.

---

### Post by daspooky on 2007-12-13
Ago, I'm curious... Wubi 7.10 installs correctly on my computer, but when copying large files it freezes. Is there no way to, once installed, update the kernel to fix the freezing?

---

### Post by ago on 2007-12-13
> **daspooky said:**
> Ago, I'm curious... Wubi 7.10 installs correctly on my computer, but when copying large files it freezes. Is there no way to, once installed, update the kernel to fix the freezing?

If you find a way let me know ;P
There is a very slim chance that newer 2.6.22 builds may fix that, most likely the 2.6.24 will work but that is a hardy kernel, so you will have to compile and install it manually, and if you do, let me know if it works.

---

### Post by daspooky on 2007-12-13
> **ago said:**
> If you find a way let me know ;P
There is a very slim chance that newer 2.6.22 builds may fix that, most likely the 2.6.24 will work but that is a hardy kernel, so you will have to compile and install it manually, and if you do, let me know if it works.

Between Christmas and New Year I will have some time. I'm very curious, so I think I will try this out. I'll try the 2.6.22 kernel, if that doesn't fix it, I'll try (never did it, but trying won't hurt me :)) compiling the 2.6.24 for Gutsy. I'll report back as soon as I have more info.

---

### Post by flamelab on 2007-12-13
> **ago said:**
> As far as I know there is still the system freeze bug in 7.10 which is the main thing holding back a release.
We might jump to 8.04 directly in case, since the 2.6.24  kernel in there should hopefully be more friendly. Work on 8.04 has already begun and preliminary builds will be available **soon**.

I hope that they come the fastest :lolflag:

As for the alpha builds of 7.10

I have so far installed Wubi (experimentally) 6 times (:rolleyes:) on a laptop and in no case it froze .
The only problem (that would exist in even a real partition ) was when I compiled a new kernel that was buggy and GRUB would'nt recognize my root .
But in any case , the latest build is almost perfect and much better than 7.04 that had a lot of problem as far as I have seen ...

PS . Till now , have you been informed by Canonical in order to include the whole Wubi in 8.04 live cd ?

---

### Post by churka07 on 2007-12-13
So you are gonna attempt to do 7.10?
Thanks man.

---

### Post by ago on 2007-12-14
> **flamelab said:**
> 
PS . Till now , have you been informed by Canonical in order to include the whole Wubi in 8.04 live cd ?

Yes that is an high priority blueprint [https://blueprints.launchpad.net/ubuntu/+spec/installer-for-windows](https://blueprints.launchpad.net/ubuntu/+spec/installer-for-windows)

---

### Post by flamelab on 2007-12-14
> **ago said:**
> Yes that is an high priority blueprint [https://blueprints.launchpad.net/ubuntu/+spec/installer-for-windows](https://blueprints.launchpad.net/ubuntu/+spec/installer-for-windows)

Perfect :lolflag::lolflag:

---

### Post by daspooky on 2007-12-14
Well I couldn't resist trying wubi 7.10 again today. I installed Xubuntu 7.10 successfully using wubi 7.10 (latest build 386). Then I updated the kernel to the latest on kernel.org (2.6.24-rc5) using the application kernelcheck. As it's the first time I do a kernel update, wifi and sound didn't work after the update, but the system booted.

It seems this kernel fixes the freezes I had with wubi 7.10! I copied large ISO files (500 MB), several at a time, from the host drive to the wubi virtual disks. I copied the same ISO to home.virtual.disk and system.virtual.disk at the same time and had no freeze at all, plus the transfer was incredibly fast.

Voila, thought I'd share this info. For now I'll go back to wubi 7.04 as I don't have much time to investigate on my sound and wifi issues.

---

### Post by ago on 2007-12-17
> **daspooky said:**
> 
It seems this kernel fixes the freezes I had with wubi 7.10! I copied large ISO files (500 MB), several at a time, from the host drive to the wubi virtual disks. I copied the same ISO to home.virtual.disk and system.virtual.disk at the same time and had no freeze at all, plus the transfer was incredibly fast.

Thanks a lot, that confirms my previous posts... Unfortunately that means that wubi 7.10 will be unlikely, while wubi 8.04 should be hopefully be quite solid.

---

### Post by daspooky on 2007-12-17
> **ago said:**
> Thanks a lot, that confirms my previous posts... Unfortunately that means that wubi 7.10 will be unlikely, while wubi 8.04 should be hopefully be quite solid.

Glad I could help. No worries for wubi 7.10. We'll have to learn to be patient till the 8.04 builds arrive :). Meanwhile Wubi 7.04 does a very good job.

---

