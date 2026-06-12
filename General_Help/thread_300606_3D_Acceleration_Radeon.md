---
title: "3D Acceleration Radeon"
date: 2006-11-15
forum: General Help
---

### Post by SigmaX on 2006-11-15
I'm using Edgy, and 3D Acceleration with my Radeon 7200 isn't working.  I'm using the "radeon" driver.  
```
$ glxinfo | grep rendering
direct rendering: No

```

```
$ lspci | grep ATI
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R100 QD [Radeon 7200] (rev 01)
```
/etc/X11/xorg.conf
```
        Driver          "radeon"
        BusID           "PCI:2:0:0"

```

```
$ more /var/log/Xorg.0.log | grep WW
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32

```

There was a similar issue [here]("https://features.launchpad.net/distros/ubuntu/+ticket/2254") which was resolved by installing Edgy from scratch.  I did update from Dapper, but this is the first noteworthy issue I've seen, and I'd really like to avoid a reinstall.  In fact, I won't reinstall just for 3D support.  

Any help?
SigmaX

---

### Post by igknighted on 2006-11-15
Check out [this]("https://help.ubuntu.com/community/RadeonDriver") page for directions on setting up that driver.  Also, see [this]("http://doc.gwos.org/index.php/BerylOnEdgy") page for even more options you can enable.

---

