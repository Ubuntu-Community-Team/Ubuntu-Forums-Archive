---
title: "Ramdisk help"
date: 2015-08-29
forum: General Help
---

### Post by makem2 on 2015-08-29
[FONT=arial]I have an on boot ramdisk:

```

tmpfs /media/ramdisk tmpfs nodev,nosuid,noexec,nodiratime,size=1G 0 0

```

At the moment I only use it for the Firefox cache:

browser.cache.disk.parent_directory - /media/ramdisk
browser.cache.memory.enable - true
browser.cache.disk.enable - false
[/FONT][FONT=arial]

I then restart the machine and Firefox.

When I check the ramdisk I find a folder called cache2 inside which are two more folders, doomed and entries.

From past experience I should see the cache contents for the running Firefox in the 'entries' folder which I find is empty.

These contents were removed on reboot of course.

Am I wrong now as there have been changes or are my settings wrong?[/FONT]

---

### Post by makem2 on 2015-08-31
[FONT=arial]browser.cache.disk.parent_directory - /media/ramdisk/
browser.cache.memory.enable - true
browser.cache.disk.enable - true[/FONT]

---

