---
title: "Problems with dpkg and pt_chown?"
date: 2007-02-01
forum: General Help
---

### Post by gjones on 2007-02-01
I seem to be unable to use apt-get to either upgrade or install programs on my machine.
Some programs are failing to start as well, giving errors about missing files (Amarok and Totem being the ones I've noticed...)
When I run: sudo apt-get upgrade

it gives me (after I hit y to confirm the package list):
```

Preparing to replace libc6-dev 2.4-1ubuntu12 (using .../libc6-dev_2.4-1ubuntu12.3_i386.deb) ...
Unpacking replacement libc6-dev ...
dpkg: error processing /var/cache/apt/archives/libc6-dev_2.4-1ubuntu12.3_i386.deb (--unpack):
 unable to stat `./usr/bin/sprof' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace libc6 2.4-1ubuntu12 (using .../libc6_2.4-1ubuntu12.3_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.4-1ubuntu12.3_i386.deb (--unpack):
 unable to stat `./usr/lib/pt_chown' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev_2.4-1ubuntu12.3_i386.deb
 /var/cache/apt/archives/libc6_2.4-1ubuntu12.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

If I pick an individual package to upgrade I get a different error:
```

Preparing to replace gnome-panel 2.16.1-0ubuntu3 (using .../gnome-panel_2.16.1-0ubuntu4_i386.deb) ...
Unpacking replacement gnome-panel ...
dpkg: error processing /var/cache/apt/archives/gnome-panel_2.16.1-0ubuntu4_i386.deb (--unpack):
 failed to delete `//usr/bin/panel-test-applets.dpkg-tmp': Read-only file system
dpkg: error while cleaning up:
 failed to delete `/var/lib/dpkg/tmp.ci': Read-only file system
dpkg: error processing /var/cache/apt/archives/gnome-panel-data_2.16.1-0ubuntu4_all.deb (--unpack):
 failed to delete `/var/lib/dpkg/tmp.ci': Read-only file system
dpkg: failed to open `/var/lib/dpkg/status' for writing status information: Read-only file system
touch: cannot touch `/var/lib/update-notifier/dpkg-run-stamp': Read-only file system
E: Problem executing scripts DPkg::Post-Invoke 'if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi'
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (2)

```


Something seems a little screwed...help?

---

### Post by bapoumba on 2007-02-02
Hi,
could you post your sources.list ?
Looks like this :
[http://ubuntuforums.org/showthread.php?p=2057713]("http://ubuntuforums.org/showthread.php?p=2057713")
but the package has been fixed by now.

---

