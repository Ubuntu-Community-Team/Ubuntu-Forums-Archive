---
title: "Failed to connect to bus: No such file or directory"
date: 2018-04-28
forum: General Help
---

### Post by roma24ster on 2018-04-28
I am trying to install Feral's gamemode: [https://github.com/FeralInteractive/gamemode](https://github.com/FeralInteractive/gamemode)


I get the following error message however:




```

jamie@jamie-ncase:~$ cd gamemode-1.0
jamie@jamie-ncase:~/gamemode-1.0$ sudo ./bootstrap.sh
[sudo] password for jamie: 
+ meson --prefix=/usr build -Dwith-systemd-user-unit-dir=/etc/systemd/user
Directory already configured, exiting Meson. Just run your build command
(e.g. ninja) and Meson will regenerate as necessary. If ninja fails, run ninja
reconfigure to force Meson to regenerate.


If build failures persist, manually wipe your build directory to clear any
stored system data.


To change option values, run meson configure instead.
+ cd build
+ ninja
ninja: no work to do.
+ set +x
Install to /usr? [Yy] y
+ sudo ninja install
[0/1] Installing files.
Installing lib/libgamemode.so to /usr/lib/x86_64-linux-gnu/libgamemode.so
Installing lib/libgamemodeauto.so to /usr/lib/x86_64-linux-gnu/libgamemodeauto.so
Installing daemon/gamemoded to /usr/bin/gamemoded
Installing daemon/cpugovctl to /usr/libexec/cpugovctl
Installing gamemode_client.h to /usr/include/
Installing /home/jamie/gamemode-1.0/data/gamemoded.1 to /usr/share/man/man1
Installing /home/jamie/gamemode-1.0/build/data/gamemoded.service to /etc/systemd/user
Installing /home/jamie/gamemode-1.0/build/data/com.feralinteractive.GameMode.policy to /usr/share/polkit-1/actions
+ set +x
Enable and run the daemon? [Yy] y
+ systemctl --user daemon-reload
Failed to connect to bus: No such file or directory
jamie@jamie-ncase:~/gamemode-1.0$ 



```

---

### Post by roma24ster on 2018-05-01
Bump

---

