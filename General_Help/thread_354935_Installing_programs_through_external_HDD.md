---
title: "Installing programs through external HDD"
date: 2007-02-06
forum: General Help
---

### Post by linuxmann on 2007-02-06
I have a 10.0 Gb HDD on my pc. i have a windows partion on the other side and i am running out of room on my kubuntu side. is there any way i could install linux programs (maybe from adept) so i could run them from my external Hard Drive? if you want to know more, just ask.

---

### Post by daller on 2007-02-06
It can be done, but it's a pain in the ***...

Can't you save some of your files there instead?

---

### Post by linuxmann on 2007-02-07
well the thing is, i have about 12 MB left on my kubuntu side so..... give me the pain in the *** solution then. my cpu is about 6 and a half years old and unfortunately my money situation is tight. so i cant buy a new computer.

---

### Post by daller on 2007-02-08
I've never tried it myself, but it should be possible to move the whole /usr/bin directory to the external harddrive, and mount it as /usr/bin in fstab... As I said, this can be quite hard! - And It'll be all your application over there, not just some of them...

Easy solution:

Use gparted to reduce the size of the windows partition, or simply remove it and merge the 2 partitions...

---

### Post by linuxmann on 2007-02-08
mount it as /usr/bin in fstab. what do you mean by mounting it in fstab? i sort of need a step by step thing on how to do that.

---

### Post by daller on 2007-02-08
I'm not that much into it myself, try this thread:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

...And if you have any questions, I think you'd be better off asking them instead of me! :)

---

