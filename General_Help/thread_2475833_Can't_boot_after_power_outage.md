---
title: "Can't boot after power outage"
date: 2022-06-09
forum: General Help
---

### Post by ray field on 2022-06-09
Full disclosure: this is on PopOS 21.10.

Had a power outage this morning; once I saw the lights go out and heard the backup battery unit kick in, I shut down the (Gigabtye/Ryzen) desktop.

Now I am stuck on a CLI screen on bootup. Can boot to maintenance partition just fine, so maybe it's not a hardware error.

At first, the last error the bootup process threw up before stopped was a bunch of "Kvm disabled by bios" errors. I didn't really think that was the root cause, nevertheless I changed the BIOS setting to enable SVM mode - still doesn't boot, though I can't see those error messages anymore.

Have double checked fstab and tried nomodeset in grub, no joy.

How to diagnose?

---

### Post by ray field on 2022-06-09
When I press Ctl-D I get:

Reloading system manager configuration
Stating default target
[then in red]
Failed to start default target: Transaction for graphical.target/start is destructive (emergency target has 'start' job queued, but 'stop' is included in transaction.)

---

### Post by #&amp;thj^% on 2022-06-09
About your only option now is>>>You can run fsck booting from live usb.
From live usb you can do all operations on the disk , even install grub and update grub install kernel.
More here: [https://linux-tips.us/repair-your-linux-filesystem-with-a-live-usb-or-dvd/](https://linux-tips.us/repair-your-linux-filesystem-with-a-live-usb-or-dvd/)
It's always recommended to back up your most wanted data while using the live-installer.

---

