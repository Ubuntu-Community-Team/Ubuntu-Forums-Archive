---
title: "Wayland is intermittently missing on XPS 13 9360"
date: 2017-12-10
forum: General Help
---

### Post by cicozhang on 2017-12-10
Hello, everyone:

It is my first time to post a new thread here. I am using Ubuntu  17.10 on DELL XPS 13 9360, to which I upgraded from Ubuntu 17.04. Since the upgrade, a problem keeps annoying me: Wayland is missing intermittently. 
1. After the update, Ubuntu 17.10 started without wayland, because the login session fell back on 'GNOME classic"; I tried a few restarts to no avails. On the evening of that day, Wayland session appears after another restart.
2. Since then, after the restart, the Wayland disappeared, I tried different methods from internet, like switching to lightdm or using "tweak" tool, the problem cannot be solved. Then after another restart, Wayland appears again. 

Do you know how to solve this problem? 

Thanks in advance.

---

### Post by ian-weisser on 2017-12-10
First thing to check is if you have NVIDIA graphics. If so: [https://askubuntu.com/questions/967955/ubuntu-17-10-on-wayland-how-can-i-install-the-nvidia-drivers](https://askubuntu.com/questions/967955/ubuntu-17-10-on-wayland-how-can-i-install-the-nvidia-drivers)

Second thing to check is the boot logs: /var/log/syslog and journalctl looking for gdm, wayland, and video errors.

---

### Post by cicozhang on 2017-12-15
Here is the log I got after running the command journalctl /usr/bin/gnome-shell

Dec 15 12:36:22 cico-XPS-13-9360 gnome-shell[906]: Failed to apply DRM plane transform 0: Permission denied
Dec 15 12:36:22 cico-XPS-13-9360 org.gnome.Shell.desktop[906]: (EE)
Dec 15 12:36:22 cico-XPS-13-9360 org.gnome.Shell.desktop[906]: Fatal server error:
Dec 15 12:36:22 cico-XPS-13-9360 org.gnome.Shell.desktop[906]: (EE) wl_drm@4: error 0: authenicate failed
Dec 15 12:36:22 cico-XPS-13-9360 org.gnome.Shell.desktop[906]: (EE)
Dec 15 12:36:22 cico-XPS-13-9360 gnome-shell[906]: [COLOR=#ff0000]X Wayland crashed; aborting[/COLOR]
Dec 15 12:36:24 cico-XPS-13-9360 gnome-shell[1048]: JS WARNING: [resource:///org/gnome/shell/ui/main.js 315]: reference to undefined property "MetaStage"
Dec 15 12:36:24 cico-XPS-13-9360 gnome-shell[1048]: JS WARNING: [resource:///org/gnome/shell/ui/layout.js 221]: reference to undefined property "MetaWindowGroup"
Dec 15 12:36:24 cico-XPS-13-9360 gnome-shell[1048]: JS WARNING: [resource:///org/gnome/shell/ui/osdMonitorLabeler.js 59]: reference to undefined property "MetaDBusDisplayConfig
Dec 15 12:36:24 cico-XPS-13-9360 gnome-shell[1048]: JS WARNING: [resource:///org/gnome/shell/ui/slider.js 38]: reference to undefined property "CallyActor"
Dec 15 12:36:25 cico-XPS-13-9360 gnome-shell[1048]: JS WARNING: [resource:///org/gnome/gjs/modules/tweener/tweener.js 540]: reference to undefined property "isSpecialProperty"
Dec 15 12:36:25 cico-XPS-13-9360 gnome-shell[1048]: Error looking up permission: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.impl.portal.Per
Dec 15 12:36:25 cico-XPS-13-9360 org.gnome.Shell.desktop[1048]: Window manager warning: "XF86RFKill" is not a valid accelerator
Dec 15 12:36:25 cico-XPS-13-9360 gnome-shell[1048]: JS WARNING: [resource:///org/gnome/shell/ui/layout.js 29]: reference to undefined property "MetaWindowX11"
Dec 15 12:36:35 cico-XPS-13-9360 gnome-shell[1048]: Screen lock is locked down, not locking

---

### Post by ian-weisser on 2017-12-15
Now you know the answer to your original question: Wayland sometimes fails to appear because XWayland crashed.

It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1505409](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1505409) . There are other bug reports of higher quality.

---

