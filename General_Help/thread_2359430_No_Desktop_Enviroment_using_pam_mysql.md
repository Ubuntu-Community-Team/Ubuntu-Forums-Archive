---
title: "No Desktop Enviroment using pam_mysql"
date: 2017-04-24
forum: General Help
---

### Post by fito45 on 2017-04-24
First of all, if you are reading this, thanks for your help and time.

I'm trying to configure users authentication in a network using a MySQL database which have the username, password and more about the users. For that, I follow [this guide]("https://tipstricks.itmatrix.eu/pam-mysql-user-authentication-in-ubuntu-14-04-lts-server/"). I'm using Ubuntu 17.04 and the latest version of libpam_mysql (0.8.0-1).

I follow all the steps of the guide and I can authenticate if I connect to the machine using SSH, or using the tty interfaces, but not with the log in screen. It gets stuck in a loop asking for the username and password. I can't even authenticate with a local user.

The log from .xsession is this:

```
dbus-update-activation-environment: systemd --user not found, ignoring --systemd argumentdbus-update-activation-environment: setting DISPLAY=:0
dbus-update-activation-environment: setting XAUTHORITY=/home/fito/.Xauthority
libGL error: failed to open drm device: Permission denied
libGL error: failed to load driver: vmwgfx
dbus-update-activation-environment: systemd --user not found, ignoring --systemd argument
dbus-update-activation-environment: setting GTK_MODULES=gail:atk-bridge
gpgconf: warning: can not open config file /home/fito/.gnupg/gpg-agent.conf: No existe el archivo o el directorio
dbus-update-activation-environment: systemd --user not found, ignoring --systemd argument
dbus-update-activation-environment: setting QT_ACCESSIBILITY=1
dbus-update-activation-environment: setting QT_LINUX_ACCESSIBILITY_ALWAYS_ON=1
dbus-update-activation-environment: systemd --user not found, ignoring --systemd argument
dbus-update-activation-environment: setting CLUTTER_IM_MODULE=xim
dbus-update-activation-environment: setting LANG=es_ES.UTF-8
dbus-update-activation-environment: setting GDM_LANG=es_ES
dbus-update-activation-environment: setting DISPLAY=:0
dbus-update-activation-environment: setting COMPIZ_CONFIG_PROFILE=ubuntu
dbus-update-activation-environment: setting GTK2_MODULES=overlay-scrollbar
dbus-update-activation-environment: setting XDG_GREETER_DATA_DIR=/var/lib/lightdm-data/fito
dbus-update-activation-environment: setting USER=fito
dbus-update-activation-environment: setting DESKTOP_SESSION=ubuntu
dbus-update-activation-environment: setting QT4_IM_MODULE=xim
dbus-update-activation-environment: setting PWD=/home/fito
dbus-update-activation-environment: setting HOME=/home/fito
dbus-update-activation-environment: setting QT_ACCESSIBILITY=1
dbus-update-activation-environment: setting XDG_SESSION_TYPE=x11
dbus-update-activation-environment: setting XDG_DATA_DIRS=/usr/share/ubuntu:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop
dbus-update-activation-environment: setting XDG_SESSION_DESKTOP=ubuntu
dbus-update-activation-environment: setting GTK_MODULES=gail:atk-bridge
dbus-update-activation-environment: setting SHELL=/bin/bash
dbus-update-activation-environment: setting XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
dbus-update-activation-environment: setting QT_IM_MODULE=ibus
dbus-update-activation-environment: setting XMODIFIERS=@im=ibus
dbus-update-activation-environment: setting IM_CONFIG_PHASE=1
dbus-update-activation-environment: setting XDG_CURRENT_DESKTOP=Unity:Unity7
dbus-update-activation-environment: setting GPG_AGENT_INFO=/home/fito/.gnupg/S.gpg-agent:0:1
dbus-update-activation-environment: setting QT_LINUX_ACCESSIBILITY_ALWAYS_ON=1
dbus-update-activation-environment: setting SHLVL=1
dbus-update-activation-environment: setting LANGUAGE=es_ES
dbus-update-activation-environment: setting GDMSESSION=ubuntu
dbus-update-activation-environment: setting LIBGL_ALWAYS_SOFTWARE=1
dbus-update-activation-environment: setting LOGNAME=fito
dbus-update-activation-environment: setting DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-rBjaESOA3T,guid=1e8c3ac84dd0cff0a1f7a3f458fdb115
dbus-update-activation-environment: setting XAUTHORITY=/home/fito/.Xauthority
dbus-update-activation-environment: setting XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
dbus-update-activation-environment: setting XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg
dbus-update-activation-environment: setting PATH=/usr/local/bin:/usr/bin:/bin:/snap/bin
dbus-update-activation-environment: setting GTK_IM_MODULE=ibus
dbus-update-activation-environment: setting _=/usr/bin/dbus-update-activation-environment
Failed to set environment: Process org.freedesktop.systemd1 exited with status 1
```

This is the auth.log:

```
Apr 24 09:02:22 fito-virtual-machine systemd-logind[898]: New seat seat0.Apr 24 09:02:22 fito-virtual-machine systemd-logind[898]: Watching system buttons on /dev/input/event0 (Power Button)
Apr 24 09:02:24 fito-virtual-machine lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Apr 24 09:02:24 fito-virtual-machine lightdm: PAM adding faulty module: pam_kwallet.so
Apr 24 09:02:24 fito-virtual-machine lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Apr 24 09:02:24 fito-virtual-machine lightdm: PAM adding faulty module: pam_kwallet5.so
Apr 24 09:02:24 fito-virtual-machine lightdm: pam_mysql - MySQL error (Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2))
Apr 24 09:02:24 fito-virtual-machine lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Apr 24 09:02:24 fito-virtual-machine polkitd(authority=local): libnss-mysql: Connection to server 'localhost' failed: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Apr 24 09:02:25 fito-virtual-machine lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Apr 24 09:02:25 fito-virtual-machine lightdm: PAM adding faulty module: pam_kwallet.so
Apr 24 09:02:25 fito-virtual-machine lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Apr 24 09:02:25 fito-virtual-machine lightdm: PAM adding faulty module: pam_kwallet5.so
Apr 24 09:02:25 fito-virtual-machine lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "fito"
Apr 24 09:02:25 fito-virtual-machine lightdm: pam_mysql - SELECT returned no result.
Apr 24 09:02:27 fito-virtual-machine lightdm: pam_mysql - SELECT returned no result.
Apr 24 09:02:28 fito-virtual-machine lightdm: pam_mysql - SELECT returned no result.
Apr 24 09:02:28 fito-virtual-machine lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Apr 24 09:02:31 fito-virtual-machine lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Apr 24 09:02:31 fito-virtual-machine lightdm: PAM adding faulty module: pam_kwallet.so
Apr 24 09:02:31 fito-virtual-machine lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Apr 24 09:02:31 fito-virtual-machine lightdm: PAM adding faulty module: pam_kwallet5.so
Apr 24 09:02:31 fito-virtual-machine lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Apr 24 09:02:31 fito-virtual-machine lightdm: PAM adding faulty module: pam_kwallet.so
Apr 24 09:02:31 fito-virtual-machine lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Apr 24 09:02:31 fito-virtual-machine lightdm: PAM adding faulty module: pam_kwallet5.so
Apr 24 09:02:31 fito-virtual-machine lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "fito"
Apr 24 09:02:31 fito-virtual-machine lightdm: pam_mysql - SELECT returned no result.
Apr 24 09:02:35 fito-virtual-machine login[1182]: pam_mysql - SELECT returned no result.
Apr 24 09:02:38 fito-virtual-machine login[1182]: message repeated 2 times: [ pam_mysql - SELECT returned no result.]
Apr 24 09:02:50 fito-virtual-machine dbus[671]: [system] Failed to activate service 'org.bluez': timed out
```

If I delete the references to pam_kwallet.so, the behaviour is exactly the same.

---

