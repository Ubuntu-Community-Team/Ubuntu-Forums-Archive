---
title: "Can't find required metapackage??"
date: 2006-09-22
forum: General Help
---

### Post by Kadin2048 on 2006-09-22
So, I made the apparent error of upgrading to the new kernel...

After mucking about and reconfiguring stuff, I've now got it booted in the new kernel in Recovery Mode, and I'm trying to get things working again.

Unfortunately, when I go to install the required kernel metapackage (the "linux-arch" metapackage) I'm running into errors, specifically the package isn't being found.

I've tried
```
# apt-get install linux-`uname -r`
E: Couldn't find package linux-2.6.15-27-686
```

I've also tried looking for the 386 version, and also trying for 2.6.15-26 in both 686 and 386. All of them come up as not found.

I have the core repositories, universe, and metaverse enabled in sources.list.

Based on other threads I think that this metapackage is the reason my system won't boot when in regular (not Recovery) mode, and now I can't find it to install it.

Can anyone help?

---

### Post by skymt on 2006-09-22
Try:```
apt-get install linux-image-`uname -r`
```Or just:```
apt-get install linux-686
```

---

### Post by Kadin2048 on 2006-09-22
Thanks, that seems to have worked.

The instructions in the stickied thread should be corrected, because I think they specify "linux-(arch)" where (arch) is the output of `uname -r`, and that package doesn't exist.

---

