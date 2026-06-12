---
title: "installing a *.debdiff-file"
date: 2006-11-06
forum: General Help
---

### Post by chaosgeisterchen on 2006-11-06
Good afternoon,

I read about this [bug](https://launchpad.net/distros/ubuntu/+source/hal/+bug/66068) on launchpad and the fix for it to properly use my iPod nano 2G under Ubuntu Linux. But the attachment consists of a ***.debdiff**-file which I have never seen before. 

I investigated this issue a bit and came to know that these files are direct patches for *.deb-files. But how can one apply them - or install them, call it as you want.

I hope someone can tell me how use this file as I need the patch rather urgently.

Thanks a lot in advance

cg

---

### Post by pimlottc on 2006-11-06
Hmm, I have never come across a "debdiff" myself, but, like any other diff file, you could try applying it with "patch"

```
patch foo.deb bar.debdiff
```

---

### Post by chaosgeisterchen on 2006-11-06
Thanks, I tried it but it did not seem so work.

Any other suggestions?

---

### Post by Zhukov on 2006-11-23
Off-topic:
I have the patched HAL packages already (saw your nick at launchpad) ;)
Do you want them?

There is a tutorial in the wiki:

[https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff](https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff)

---

