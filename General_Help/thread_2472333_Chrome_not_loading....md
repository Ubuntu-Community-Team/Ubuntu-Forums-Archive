---
title: "Chrome not loading..."
date: 2022-02-24
forum: General Help
---

### Post by dbee on 2022-02-24
Chrome won't load on my xubuntu. I've tried restarting.

```

dara@anne-HP-Stream-Laptop-11-y0XX:~$ uname -a
Linux anne-HP-Stream-Laptop-11-y0XX 5.11.0-49-generic #55-Ubuntu SMP Wed Jan 12 17:36:34 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

When i try to load chrome, it gives me...

```

dara@anne-HP-Stream-Laptop-11-y0XX:~$ google-chrome
libva error: /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so init failed
[3620:3620:0224/082851.980760:ERROR:sandbox_linux.cc(378)] InitializeSandbox() called with multiple threads in process gpu-process.
[3576:3576:0224/082912.132258:ERROR:network_service_instance_impl.cc(972)] Network service crashed, restarting service.

```

I'm not entirely convinced they are related, but this happened around the same time that I disabled the application keyring login that shows on startup. Either by resetting the permissions of the relevant file in /usr/sbin/ or by commenting out the relevant .so files in /etc/pam.d (i think). Different systems, different solutions. 

My money though, is that this is an Ubuntu upgrade issue.

```
Feb 24 08:28:25 anne-HP-Stream-Laptop-11-y0XX dbus-daemon[446]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.13' (uid=0 pid=448 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Feb 24 08:28:25 anne-HP-Stream-Laptop-11-y0XX systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb 24 08:28:25 anne-HP-Stream-Laptop-11-y0XX dbus-daemon[446]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb 24 08:28:25 anne-HP-Stream-Laptop-11-y0XX systemd[1]: Started Network Manager Script Dispatcher Service.
Feb 24 08:28:36 anne-HP-Stream-Laptop-11-y0XX systemd[1]: NetworkManager-dispatcher.service: Succeeded.
Feb 24 08:30:02 anne-HP-Stream-Laptop-11-y0XX CRON[3697]: (root) CMD ([ -x /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
Feb 24 08:32:25 anne-HP-Stream-Laptop-11-y0XX systemd[1]: Condition check resulted in Run anacron jobs being skipped.
```

```
dara@anne-HP-Stream-Laptop-11-y0XX:~$ ldd /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so
	linux-vdso.so.1 (0x00007ffcb8745000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f51e76a5000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f51e769e000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f51e7693000)
	libigdgmm.so.11 => /lib/x86_64-linux-gnu/libigdgmm.so.11 (0x00007f51e7619000)
	libstdc++.so.6 => /lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f51e7400000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f51e72b2000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f51e7295000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f51e70a9000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f51e7e63000)

```

Any ideas?

---

### Post by dbee on 2022-02-24
Turns out that for some reason. google-chrome-stable wasn't installed or needed an upgrade.

I don't remember uninstalling it...

```
dara@anne-HP-Stream-Laptop-11-y0XX:~$ apt list --upgradeable
Listing... Done
google-chrome-stable/stable 98.0.4758.102-1 amd64 [upgradable from: 97.0.4692.99-1]
N: There is 1 additional version. Please use the '-a' switch to see it
dara@anne-HP-Stream-Laptop-11-y0XX:~$ sudo apt reinstall google-chrome-stable

```

I did a reinstall and that fixed the issue...

---

