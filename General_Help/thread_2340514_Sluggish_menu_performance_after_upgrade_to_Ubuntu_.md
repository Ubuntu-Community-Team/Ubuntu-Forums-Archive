---
title: "Sluggish menu performance after upgrade to Ubuntu 16.10"
date: 2016-10-19
forum: General Help
---

### Post by arnomuhren-b on 2016-10-19
Since I upgraded my system from Ubuntu 16.04 to 16.10, my menu performance in applications, unity and the system indicators are sluggish.
The difference is quite large in comparison to 16.04.
Is there a way to troubleshoot his issue?

---

### Post by arnomuhren-b on 2016-10-19
Okay, so it turned out that the unity-panel-service was using 6GB of memory, causing my system to start swapping.
After restarting the process, Ubuntu works as normal again. I think it's some sort of memory leak and is very similar to
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1199877](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1199877)

Will see how it progresses further.

---

