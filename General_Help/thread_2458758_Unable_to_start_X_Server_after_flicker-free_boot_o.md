---
title: "Unable to start X Server after flicker-free boot on Ubuntu 20.04"
date: 2021-03-03
forum: General Help
---

### Post by uveta on 2021-03-03
**Issue**

Trying to run *startx* from terminal, after a flicker free boot, results in error. Complete Xorg log can be found here [https://docdro.id/TvABHHA](https://docdro.id/TvABHHA), but I believe the following lines show what is causing the issue

    ```

[    17.034] (II) Loading sub module "fb"
[    17.034] (II) LoadModule: "fb"
[    17.034] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.037] (II) Module fb: vendor="X.Org Foundation"
[    17.037]     compiled for 1.20.9, module version = 1.0.0
[    17.037]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.037] (EE) modeset(0): drmSetMaster failed: Permission denied
[    17.037] (EE) Fatal server error:
[    17.037] (EE) AddScreen/ScreenInit failed for driver 0

```

**Setup**

This is an independent UpBoard device with only a display attached. I am using it to run Chromium in kiosk mode and nothing more. After finding out that Ubuntu 20.04 allows flicker free boot with OEM logo always displayed, I tried upgrading the system from Ubuntu 18.04. Thus, it is a vanilla Ubuntu server 20.04 installation with default plymouth configuration, using new BGRT theme as default.

User *kiosk*, which is used to run *startx* and subsequently Chromium, is logged in automatically to default terminal (tty1) via a custom *getty@tty1* daemon. His *.profile* configuration contains only 

```
startx -- :0
```

Running Chromium via OpenBox session is done using script in *.xinintrc*.

**Problem**

When Plymouth is not used during boot, by using only "quiet" option in *GRUB_CMDLINE_LINUX_DEFAULT* in */etc/default/grub*, everything works as expected, meaning system is configured properly and there are no permission issues for *kiosk *user. But after adding "splash" option to grub, thus enabling Plymouth, X Server is simply never started after boot, and OEM logo is shown indefinitely.

This, and messages from Xorg log, leads me to believe that something is blocking X Server from obtaining needed access to video subsystem. Is there a way to check what could be preventing it, or has anyone else had similar issues with BGRT theme and *startx*?

---

