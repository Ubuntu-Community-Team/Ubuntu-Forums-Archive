---
title: "HAL start error: Couldn't stat pci.ids file"
date: 2008-02-28
forum: General Help
---

### Post by Philop on 2008-02-28
Hello, 

After using Ubuntu for some months now a problem showed up: I get a HAL initialization error on boot up. When I tried the following

```
/usr/sbin/hald --daemon=no --verbose=yes
```

I get the result

```
22:32:08.212 [I] hald.c:529: hal 0.5.9.1
22:32:08.212 [I] hald.c:594: Will not daemonize
22:32:08.213 [I] hald_dbus.c:4807: local server is listening at unix:abstract=/var/run/hald/dbus-bWWX8ek3r2,guid=a643f663472458c713d4810047c72858
Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
22:32:08.219 [I] hald_runner.c:299: Runner has pid 6472
22:32:08.223 [I] hald_runner.c:180: runner connection is 0x8094698
22:32:08.249 [I] mmap_cache.c:251: cache mtime is 1200597122
22:32:08.249 [W] ids.c:294: Couldn't stat pci.ids file '/usr/share/misc/pci.ids', errno=13: Permission denied
22:32:08.249 [W] ids.c:515: Couldn't stat usb.ids file '/usr/share/misc/usb.ids', errno=13: Permission denied
22:32:08.249 [E] osspec.c:310: Unable to inotify_add_watch() for '/usr/share/hal/fdi/preprobe': Permission denied
*** [DIE] osspec.c:watch_fdi_files():389 : Error watching fdi files

```

I tried recreating the fdi cache but with no results. It seems like gnome-session and others depending on hal are now failing as well. 

Any ideas on what might be the cause of this?

---

