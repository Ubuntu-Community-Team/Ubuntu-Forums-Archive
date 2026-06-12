---
title: "Boot: Wrong hdd device?"
date: 2007-07-24
forum: General Help
---

### Post by akb on 2007-07-24
Hi there,

I tried to get Wubi running and ran into a problem that seems like it doesn't get the correct disk device or something.

At its first boot after installation it hung at the splash, so I removed the "quiet splash" parameters from menu.lst and rebooted. After this I've been hit back to the prompt, telling me it couldn't find the virtual disk file. So I navigated to /media/host/ and noticed that there was not the data from my first hdd (wubi is installed on), but the content of my usb stick. So I unplugged the usb stick and rebooted, but now once again it took an other device. Now it was mounted to my second device, D: in Windows.

If it's not simply a thing of assigning to correct hdd device (is this possible through windows?) I assume it's got something to do with the RAID my first device is made of. Windows and now Wubi/Ubuntu too are installed on an nforce4 raid0 (stripe). As you can see Wubi/Ubuntu installs fine, but it doesn't mount the device where it should for further going.

So... any idea how I could solve this (still using the same drive)?

Thx in advance

Arne

---

