---
title: "beryl works emerald sticking me with white titlebars"
date: 2007-01-03
forum: General Help
---

### Post by nickoli on 2007-01-03
I have beryl working fine, couple little problems still. I seem to have white titlebars when maximized. I can still manipulate the window to do what I want. I was hoping to fix the minor glitch so I can enjoy the scenery more. I'm using a ati radeon mobile 6l, using 256ram. On a Dapper install. Any help will be appreciated.](*,)

---

### Post by Waappu on 2007-01-03
Hi

Please see if this thread helps you
[http://ubuntuforums.org/showthread.php?t=325983&page=2](http://ubuntuforums.org/showthread.php?t=325983&page=2)

---

### Post by nickoli on 2007-01-03
Ok I found a fix. I had to place this under the device section of the xorg.conf file.


Option "AGPSize" "32":p

---

