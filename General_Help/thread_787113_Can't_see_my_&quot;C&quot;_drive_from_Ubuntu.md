---
title: "Can't see my &quot;C&quot; drive from Ubuntu"
date: 2008-05-08
forum: General Help
---

### Post by half-hitch on 2008-05-08
I've managed to get Ubuntu installed and running using Wubi.  It's installed on the same disk as Windows.  I have a total of 4 hdd's and 2 cd's on this system.  I can see and mount all the devices except for what is my "C" drive when booting to windows.  Any suggestions?

---

### Post by ago on 2008-05-08
look under /host

---

### Post by half-hitch on 2008-05-08
sorry to be so obtuse, but I didn't even know where to begin looking for /host.

finally found it - thx

---

### Post by ago on 2008-05-08
places > computer > filesystem > host

---

### Post by rohitsb on 2008-05-09
The partition on which you install Wubi will show up under /host, everything else under /media

---

