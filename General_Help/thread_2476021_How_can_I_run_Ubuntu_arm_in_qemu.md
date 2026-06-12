---
title: "How can I run Ubuntu arm in qemu?"
date: 2022-06-14
forum: General Help
---

### Post by zentian on 2022-06-14
I'm trying to run Ubuntu 20.04 in an arm cortex-a53 environment on 21.04. I downloaded focal-desktop-arm64.iso from [https://cdimage.ubuntu.com/focal/daily-live/current/](https://cdimage.ubuntu.com/focal/daily-live/current/). I've installed qemu and tried passing the iso to it, but haven't had any luck in getting it to boot. I'm currently trying

qemu-system-aarch64 -M xlnx-zcu102 -cpu cortex-a53 -smp 4 -m 8G -nographic focal-desktop-arm64.iso

but this gives the error

qemu-system-aarch64: focal-desktop-arm64.iso: machine type does not support if=ide,bus=0,unit=0

to get past this, I tried

qemu-img create -f raw armdisk.img 8G

and ran

qemu-system-aarch64 -M xlnx-zcu102 -cpu cortex-a53 -smp 4 -m 8G -nographic -drive file=armdisk.img focal-desktop-arm64.iso

but this gave the error

qemu-system-aarch64: focal-desktop-arm64.iso: drive with bus=0, unit=0 (index=0) exists

I'm not sure where to proceed from here. Is there anyone that can give advice on how to get Ubuntu 20.04 running in qemu emulating a cortex-a53 on an Ubuntu 21.04 host?

---

### Post by Skaperen on 2022-06-14
maybe.  most people are running an LTS on their hardware and thus would be running *qemu* on 22.04 or 20.04.  the methodology of getting *qemu* to run (such as command arguments) should be pretty much the same from 20.04 to 22.04.

---

### Post by guiverc on 2022-06-14
Be aware your HOST OS is **EOL** (*end of life*).

[https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/](https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/)

> As of January 20, 2022, Ubuntu 21.04 is no longer supported. No more  package updates will be accepted to 21.04, and it will be archived to  old-releases.ubuntu.com in the coming weeks.


Very soon your *release-upgrade* path for the 21.04 system will disappear too, with the [notice on its EOL already out]("https://fridge.ubuntu.com/2022/06/01/ubuntu-21-10-impish-indri-reaches-end-of-life-on-july-14-2022/"), and when 21.10 reaches EOL your *release-upgrade* path will be gone.

---

