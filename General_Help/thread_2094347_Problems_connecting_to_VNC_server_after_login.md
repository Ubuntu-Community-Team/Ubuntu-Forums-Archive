---
title: "Problems connecting to VNC server after login"
date: 2012-12-13
forum: General Help
---

### Post by TobiasV on 2012-12-13
Hello,

I've recently been experiencing some problems with connecting a vino server running on a Xubuntu 12.04 installation. I've later replaced the vino server with an x11vnc server, with the same problem.

I can connect to the only at the login screen. After I've logged in, if I choose to disconnect, I can not connect to the server once more. 

I start x11vnc with the following upstart job:

```
start on login-session-start script /usr/bin/x11vnc -xkb -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /var/log/x11vnc.log end script
```

I figure the problem lays there? How will I be able to start x11vnc so that I can both use it at the login screen, and after login?

I experienced the same problem with vino, which was started with a simple .desktop file with no arguments.

I'd appreciate any help.

---

### Post by TobiasV on 2012-12-17
32 bit installation.

Kernel: 3.2.0-34-generic #53-Ubuntu

x11vnc is version 0.9.12-1build1

I don't know if there's any other relevant information I can post, but I'd appreciate any help.

---

### Post by Rexilion on 2012-12-17
My best guess would be X authentication credentials:

> -auth /var/run/lightdm/root/:0

After you login, this file is deleted or not used anymore.

Initial connection: file exists, connection succeeds and is no more needed during the connection.
Subsequent connections: file does not exist anymore (or points to another X server) and so connection fails.

Could it explain your problems?

---

