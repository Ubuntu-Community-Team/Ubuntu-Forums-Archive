---
title: "Firefox 32 libpango error"
date: 2008-01-01
forum: General Help
---

### Post by xevix on 2008-01-01
Running firefox32 installed from [http://ubuntuforums.org/showthread.php?t=202537&highlight=pango](http://ubuntuforums.org/showthread.php?t=202537&highlight=pango)

I get this:

```

$ firefox32 
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
esd: no process killed
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
/usr/local/firefox32/firefox-bin: symbol lookup error: /usr/lib32/libpangoft2-1.0.so.0: undefined symbol: pango_coverage_unref

```

Tried reinstalling libpango, no go.

---

### Post by ~LoKe on 2008-01-01
Try...
```
sudo apt-get install ia32-libs
```

---

### Post by xevix on 2008-01-01
Thanks for the quick reply.  It didn't work, and also I have this issue with installing the non-free flash plugin:

```

Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
Flash Plugin installed.
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: symbol lookup error: /usr/lib32/libpangoft2-1.0.so.0: undefined symbol: pango_coverage_unref
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

