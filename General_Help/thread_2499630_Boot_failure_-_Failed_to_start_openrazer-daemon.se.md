---
title: "Boot failure - Failed to start openrazer-daemon.service"
date: 2024-08-05
forum: General Help
---

### Post by markyzz on 2024-08-05
hello
i am having trouble booting into my desktop
My login screen froze after entering my password and was given an authentication error
i had to force reboot and i am now stuck on this screen
[https://imgur.com/a/oyr99m8](https://imgur.com/a/oyr99m8)
i uploaded the boot-repair info here:
[https://paste.ubuntu.com/p/znksS6Vp2Q/](https://paste.ubuntu.com/p/znksS6Vp2Q/)
any help would be appreciated thank you
ubuntu version is 24.04

Edit:
I removed the service that was failing but now it's just a blinking line in place of that failed message with everything else showing OK above it

https://imgur.com/a/UN4mjzf

---

### Post by tea for one on 2024-08-05
> **markyzz said:**
> My login screen froze after entering my password and was given an authentication error
i had to force reboot and i am now stuck on this screen
By force reboot, I assume you used the power button for an ungraceful exit?
This could lead to file system corruption.

Remove/isolate/de-activate all disks other than nvme0n1
Boot into a "Try Ubuntu" live session
Open a terminal and run fsck on nvme0n1p1 and nvme0n1p2

Power off and boot without attaching other disks.
Any progress?

---

### Post by currentshaft on 2024-08-05
Good

---

