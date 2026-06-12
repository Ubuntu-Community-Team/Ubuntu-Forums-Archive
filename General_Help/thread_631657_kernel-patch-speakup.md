---
title: "kernel-patch-speakup"
date: 2007-12-04
forum: General Help
---

### Post by sedition on 2007-12-04
Hi all,

I've just completed a text-only installation of i386 7.10 from the alternate cd image. I installed kernel-patch-speakup to get my friend's box setup and reboot. I ran lsmod but did not see any entries for speakup, so I manually ran a ```
 sudo modprobe speakup_sftsyn 
```, but I'm getting module not found errors. I checked out /lib/modules and did not see an entry for speakup at all. I'm following my notes from 6.10 step by step that I had working, but no love. Anyone have any ideas? If there is a problem with the package, do I register the bug with launchpad? 

Thanks in advance,
-sed

---

