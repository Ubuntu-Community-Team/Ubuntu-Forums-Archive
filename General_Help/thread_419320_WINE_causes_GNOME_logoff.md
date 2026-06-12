---
title: "WINE causes GNOME logoff"
date: 2007-04-22
forum: General Help
---

### Post by Loafy on 2007-04-22
been using 6.10 Edgy for a few months and things were great. Even loaded the "Linux" version of Picasa (uses WINE wrapper) but noticed recently that starting Picasa caused my X server to quit and log me off of GNOME.

Did some more checking and found it was WINE related (wine -h) caused same situation to happen. I upgrade to latest WINE (0.9.35) thinking that might help but no luck.

So far I can't seem to get WINE and Edgy to play nice together.

Anyone else have similar problem?

any help is appreciated!

---

### Post by Loafy on 2007-04-23
found my problem -

I was using an older version of NVIDIA drivers. Once I upgraded to the latest using the info at [http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html) then all WINE related apps work fine.

hope this helps someone else

---

