---
title: "Add/Remove (gnome-app-install) Won't Run"
date: 2008-04-26
forum: General Help
---

### Post by rgutierrez on 2008-04-26
I'm trying to run gnome-app-install, but it crashes while trying to load libgstflac.so. It's trying to load gstreamer-0.10. This is what I get when I try to run gnome-app-install from the command line:

```
No ask_pass set, using default!
xauth: /tmp/libgksu-MCdYFv/.Xauthority
STARTUP_ID: gksudo/python '|usr|bin|gnome-app-install'/10017-0-rgc-ubuntu-2006_TIME7019160
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: python
cmd[9]: /usr/bin/gnome-app-install
buffer: --
buffer: -(gnome-app-install:10019): GStreamer-WARNING **: Failed to load plugin '/usr/local/lib/gstreamer-0.10/libgstflac.so': libFLAC.so.7: cannot open shared object file: No such file or directory-
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.
python: symbol lookup error: /usr/lib/python2.5/site-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_control_source_get_type
xauth: /tmp/libgksu-MCdYFv/.Xauthority
xauth_env: /home/dragon/.Xauthority
dir: /tmp/libgksu-MCdYFv

```

Notice about 10 or 11 lines down, the system says it can't find libgstflac.so. I did a find from / for that file, and I do have the file. Actually, I have two versions of that file.

```
dragon@rgc-ubuntu-2006:/$ sudo find . -name libgstflac.so -print
./usr/lib/gstreamer-0.10/libgstflac.so
./usr/local/lib/gstreamer-0.10/libgstflac.so
dragon@rgc-ubuntu-2006:/$ ls -l /usr/local/lib/gstreamer-0.10/libgstflac.so
-rwxr-xr-x 1 root root 170667 2007-07-01 22:32 /usr/local/lib/gstreamer-0.10/libgstflac.so

```

Is this a library path issue? Library conflict? Any ideas what's causing this problem?

---

