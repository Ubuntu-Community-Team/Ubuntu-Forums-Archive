---
title: "utorrent: already running?"
date: 2006-10-13
forum: General Help
---

### Post by toykilla on 2006-10-13
I accidentally rebooted while utorrent was running. Now when I try to launch it, i get the error: 

[B]It seems like uTorrent is already running, but not responding.

Please close all uTorrent processes and try again.

[/B]There are not processes running. I have rebooted again only to find the same error.

---

### Post by Aberrix on 2006-10-13
try

```
ps -aux | grep utorrent
```

you should be able to see if its running or not.

---

### Post by toykilla on 2006-10-13
This is the output:
```
toykilla  5888  0.2  0.0      0     0 ?        Zl   12:29   0:00 [utorrent.exe] <defunct>
toykilla  6479  0.0  0.0   3956   920 pts/2    R+   12:34   0:00 grep utorrent
```.

I did killall.exe which removes the first line of that output, but it still will not launch.

---

### Post by Aberrix on 2006-10-13
> **toykilla said:**
> This is the output:

I did killall.exe which removes the first line of that output, but it still will not launch.


so after you killed it, it did not show up anymore?

try a reboot?

---

### Post by toykilla on 2006-10-15
Yes I rebooted and still the same thing. I tried uninstalling and reinstalling and I still get the same error.

---

### Post by toykilla on 2006-10-16
I can only guess that uTorrent is storing data somewhere. If I could find it and delete it, it should work.

---

