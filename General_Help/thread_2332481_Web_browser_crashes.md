---
title: "Web browser crashes"
date: 2016-07-31
forum: General Help
---

### Post by johntollendal on 2016-07-31
Same problem here, even worst.  As soon as it starts it can freeze the desktop screen, keyboard and mouse.

1) At first I was able to login with a second system (or a smart-phone with ssh) and reboot the system, but now not even this works.

2) Amazon app depends on this so I am afraid that any other app that uses this can freeze the system "without notice".

3) looking at the syslog/auth.log, other than some hardware conflicts I already had before, I can't spot any traces of what is causing the problem.  I suspect only this in auth.log:

> [I]lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory

lightdm: PAM adding faulty module: pam_kwallet.so
lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "jxxx"

gnome-keyring-daemon[2194]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files

polkitd(authority=local): Registered Authentication Agent for unix-session:c2 (system bus name :1.79 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)

systemd-logind[723]: Removed session c1.

CRON[3733]: pam_unix(cron:session): session opened for user root by (uid=0)
CRON[3733]: pam_unix(cron:session): session closed for user root[/I]


4) My system has this configuration:

[FONT=courier new]**System:**    **Host:** 965P-DS3 **Kernel**: 3.13.0-92-generic i686 (32 bit) **Desktop:** Gnome 3.10.4 **Distro:** Ubuntu 14.04 trusty
**Machine:** **  Mobo:** Gigabyte **model:** 965P-DS3 **Bios:** Award version: F14 date: 06/25/2009
**CPU:**       Dual core Intel Core2 CPU 6300 (-MCP-) clocked at 1866.597 MHz 
**Graphics:** ** Card:** NVIDIA GF119 [GeForce GT 610] 
           X.Org: 1.15.1 **drivers:** nouveau (unloaded: fbdev,vesa) **Resolution:** 1920x1080@60.0hz 
           **GLX Renderer:** Gallium 0.4 on NVD9 GLX **Version:** 3.0 Mesa 10.1.3
**Network:**   Card: Marvell 88E8056 PCI-E Gigabit Ethernet Controller **driver:** sky2 
**Drives:**    HDD Total Size: 500.1GB (7.9% used)
**Info:**      Processes: 189 Uptime: 7 min Memory: 790.2/8093.6MB Client: Shell (bash) **inxi:** 1.9.17[/FONT]

---

### Post by howefield on 2016-08-01
Post moved to own thread and to the "*General Help*" forum.

---

