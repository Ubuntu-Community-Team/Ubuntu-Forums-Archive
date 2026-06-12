---
title: "GVFS-Backends Reports a Crash With iPod Touch 5G Plugged In"
date: 2014-03-20
forum: General Help
---

### Post by LillyDragon on 2014-03-20
Hey, everyone! My younger cousin recently replaced his iPod Touch 2G, (Which worked out-of-the-box with Banshee on Ubuntu! Major props to the Open-Source community on that one.) with an iPod 5G. These newfangled iPods are harder to mount on Ubuntu, I know, but there are updated libimobiledevices libraries that allow this now. I think the changes are even included with Ubuntu 13.10?

However, I'm on 12.04 Precise, and even after manually upgrading my libraries with [Precise Pangolin backports from a PPA](https://launchpad.net/ubuntu/+source/libimobiledevice) through Synaptic, Apport tells me that GVFS's Volume Monitor, or gvfs-backends, crashed, so I get another time-out error, instead of it auto-mounting the iPod.

The iPod was also unlocked at the time, and told to trust the PC; that part didn't fail. So I'm thinking I need to update GVFS through the same PPA, but I don't fully understand what GVFS does for the OS, or what the risks of upgrading it are. I don't want to brick my OS and have to reinstall my programs and games again, that would take all week.

Is it safe to upgrade GVFS, or was this actually expected of me to do in the first place with the PPA packages? I could have updated automatically and got everything from the terminal, but I didn't want to upgrade my kernel, otherwise I'd have to compile my wacom tablet's drivers again.

---

### Post by LillyDragon on 2014-03-21
Well, nevermind, installing the latest patch for Ubuntu 12.04 off of Synaptic fixed the crash. (Edit : It was barely a new version number, 1.12.2.ubuntu1.3, versus 1.12.2.ubuntu1.2, but definitely a very helpful bug fix that shouldn't be ignored.) Now that I got to successfully mount, read, and write, I just have to figure out how to get the new iPod to sync again with Rhythmbox or Banshee.

---

