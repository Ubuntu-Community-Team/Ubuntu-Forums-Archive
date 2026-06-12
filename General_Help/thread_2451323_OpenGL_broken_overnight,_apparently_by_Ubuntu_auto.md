---
title: "OpenGL broken overnight, apparently by Ubuntu auto-update"
date: 2020-10-01
forum: General Help
---

### Post by John Nagle on 2020-10-01
Ubuntu 18.04 LTS.

Last night, when I logged out, everything was working fine. This morning, nothing with OpenGL will run. Even glxgears fails:

 glxgears
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  32
  Current serial number in output stream:  33

Looking in syslog, it looks like Ubuntu pushed some un-asked-for updates. 

Oct  1 05:32:19 Nagle-LTS snapd[22695]: autorefresh.go:410: auto-refresh: all snaps are up-to-date
Oct  1 06:02:11 Nagle-LTS dbus-daemon[1080]: [system] Activating via systemd: service name='org.freedesktop.fwupd' unit='fwupd.service' requested by ':1.118' (uid=1000 pid=2452 comm="/usr/bin/gnome-software --gapplication-service " label="unconfined")
Oct  1 06:02:11 Nagle-LTS systemd[1]: Starting Firmware update daemon...
Oct  1 06:02:11 Nagle-LTS dbus-daemon[1080]: [system] Successfully activated service 'org.freedesktop.fwupd'
Oct  1 06:02:11 Nagle-LTS systemd[1]: Started Firmware update daemon.
Oct  1 06:02:14 Nagle-LTS PackageKit: get-updates transaction /695_aebbeabe from uid 1000 finished with success after 1033ms
... lots more.

An application reports:

Oct  1 12:53:31 Nagle-LTS nautilus-autostart.desktop[2199]: The program 'do-not-directly-run-firestorm-bin' received an X Window System error.
Oct  1 12:53:31 Nagle-LTS nautilus-autostart.desktop[2199]: This probably reflects a bug in the program.
Oct  1 12:53:31 Nagle-LTS nautilus-autostart.desktop[2199]: The error was 'BadValue (integer parameter out of range for operation)'.
Oct  1 12:53:31 Nagle-LTS nautilus-autostart.desktop[2199]:   (Details: serial 29 error_code 2 request_code 154 minor_code 3)
Oct  1 12:53:31 Nagle-LTS nautilus-autostart.desktop[2199]:   (Note to programmers: normally, X errors are reported asynchronously;
Oct  1 12:53:31 Nagle-LTS nautilus-autostart.desktop[2199]:    that is, you will receive the error a while after causing it.
Oct  1 12:53:31 Nagle-LTS nautilus-autostart.desktop[2199]:    To debug your program, run it with the --sync command line
Oct  1 12:53:31 Nagle-LTS nautilus-autostart.desktop[2199]:    option to change this behavior. You can then get a meaningful
Oct  1 12:53:31 Nagle-LTS nautilus-autostart.desktop[2199]:    backtrace from your debugger if you break on the gdk_x_error() function.)
Oct  1 12:53:31 Nagle-LTS kernel: [428083.647551] NVRM: API mismatch: the client has the version 440.100, but
Oct  1 12:53:31 Nagle-LTS kernel: [428083.647551] NVRM: this kernel module has the version 440.95.01.  Please
Oct  1 12:53:31 Nagle-LTS kernel: [428083.647551] NVRM: make sure that this kernel module and all NVIDIA driver
Oct  1 12:53:31 Nagle-LTS kernel: [428083.647551] NVRM: components have the same version.
Oct  1 12:53:31 Nagle-LTS nautilus-autostart.desktop[2199]: *** Bad shutdown ($LL_RUN_ERR). ***

OK, so why is auto-update mucking with the graphics driver? This is LTS; it's not supposed to do that. And what graphics driver does it want now?

---

### Post by HermanAB on 2020-10-02
Not what you want to hear, but I learned decades ago not to let important machines do auto updates. One or more of the engineering machines can be sacrificial lambs or canaries in the coal mine, but not one that has to do real work - those you only update when the lamb and canary are OK.

One way to fix these issues could be to uninstall opengl and then install a big CAD or video editor program that makes heavy use of it, Blender for example, so that it will pull in a hopefully working version of everything.

---

