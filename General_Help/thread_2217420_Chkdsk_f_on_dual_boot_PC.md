---
title: "Chkdsk /f on dual boot PC"
date: 2014-04-17
forum: General Help
---

### Post by james104 on 2014-04-17
Hello,

When I first installed Ubuntu my PC ran a chkdsk and naturally improved the performance of my laptop and the loading of my Ubuntu install. Now when I boot into my Win 7 OS and run check disk is states it needs to run on reboot but being dual booted it reboots to grub OS choice screen and doesnt complete its check disk.

Is this normal?

---

### Post by mcduck on 2014-04-17
yes, it's normal. Chkdsk checks the *windows partition* for errors, so you just need to tell Grub to boot to windows for chkdisk to complete it's work.

Also it won't improve the performance or really do anything at all for the Ubuntu system, since it's not using thee Windows partition. (Unless you are running a Wubi install, in which case you'd get much more noticeable benefits by converting that to a proper install instead).

If you want a similar tool for your Ubuntu partiton, then *fsck* is what you are looking for. Although it already runs on every 30th boot by default so you shouldn't need to do anything about it...

---

### Post by james104 on 2014-04-22
Cool ok, I wont worry too much then! lol

---

