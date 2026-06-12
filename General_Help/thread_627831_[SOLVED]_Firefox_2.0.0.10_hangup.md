---
title: "[SOLVED] Firefox 2.0.0.10 hangup"
date: 2007-11-30
forum: General Help
---

### Post by Zer0d on 2007-11-30
When I open multiple videos on youtube or any other page with video media files, Firefox hangs up and I have to force kill it. After I kill Firefox a square brick gets stuck on my screen even though Firefox isn't running anymore.

**ps -A | grep firefox**
Doesn't give any output.

[[IMG]http://img49.imageshack.us/img49/8515/screenshotfj2.th.png[/IMG]](http://img49.imageshack.us/my.php?image=screenshotfj2.png)

---

### Post by Zer0d on 2007-12-04
The problem was flash inside Firefox. Firefox would crash and leave the flash box on the screen. Every time this happens I have to kill this process.

**14819 ?        00:01:24 npviewer.bin**

---

