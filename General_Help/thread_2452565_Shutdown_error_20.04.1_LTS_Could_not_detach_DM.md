---
title: "Shutdown error 20.04.1 LTS Could not detach DM"
date: 2020-10-24
forum: General Help
---

### Post by Deep_Peasant on 2020-10-24
Hello people,

After searching my duck (duckduckgo) to no end, finding a few questions looking similar but no solutions,

This is my current install of Xubuntu,

> ```
lsb_release -a
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal


> ```
name -r
```

5.4.0-52-generic

When shutting down there's an error on screen before shutdown, I had to record it in slomotion with a camera, that says,

> [    57.834296] systemd-shutdown[1]: Could not detach DM /dev/dm-0: Device or resource busy
[    57.910454] systemd-shutdown[1]: Failed to finalize  DM devices, ignoring
[    58.417887] reboot: Power down

All I understand is that my /dev/dm-0 is causing the problem. I figured out how to list the dm-0 with  
```
sudo dmsetup info /dev/dm-0
```

> Name:              sda3_crypt
State:             ACTIVE
Read Ahead:        256
Tables present:    LIVE
Open count:        2
Event number:      0
Major, minor:      253, 0
Number of targets: 1
UUID: CRYPT-LUKS2

Which seems to be my installation drive.
And now I dont know what to do.

Any help, bug report (is it a bug?), wil be appreciated :)

---

### Post by Deep_Peasant on 2020-10-27
Since the posted question, I don't like 'not finalized'  drives on shutdown I started a few experiments,

Reinstalled system to my dedicated drive, Xubuntu 18.04, no problems on shutdown.
Reinstalled system Xubuntu 20.04.1, initially no problems on shutdown.

Now the problem came back after updating the system and installing my usual software that did not gave a problem on 18.04.
And no, there's nothing in the 'journals' the problem is the system shuts down and the journals can't seem to record it.
:confused:

On a side note, I also had the 20.04 'initramfs unpacking failed: Decoding failed' at boot which now does not occur with the fresh install.
And there' s the infamous ' Blueman' error trying to keep sending error reports on and off, even with the removal of blueman (my pc does not have bluetooth :rolleyes:)

---

