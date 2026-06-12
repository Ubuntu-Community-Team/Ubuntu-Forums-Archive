---
title: "RAID 1 on Raspberry Pi 3 B+"
date: 2018-09-03
forum: General Help
---

### Post by Robert_Boutin on 2018-09-03
So I'm working on a new project with a Raspberry Pi 3 B+.

I installed Ubuntu 18.04 Server using these instructions:  [https://wiki.ubuntu.com/ARM/RaspberryPi](https://wiki.ubuntu.com/ARM/RaspberryPi)

It took some work but seems to be running properly.  I added two 32 GB USB drives and I'm trying to set up a RAID 1 array using this guide:

[https://www.youtube.com/watch?v=IWXBRy3Gg6Y](https://www.youtube.com/watch?v=IWXBRy3Gg6Y)

I set up two arrays using these instructions on a pc-based server, they both have been rock solid. On the Pi though, when I run the *update-initramfs -u* command, I get the following error:

[I]update-initramfs: Generating /boot/initrd.img-4.15.0-1021-raspi2
Unsupported platform.
run-parts: /etc/initramfs/post-update.d//flash-kernel exited with return code 1

[/I]I'm assuming this means when I reboot, my array won't exist because I'm not using the correct kernel for Pi 3 B+ (I had to download the Pi 2 image and make some adjustments to get it to work on 3 B+).   Does anyone have a suggestion of how to handle this for my Pi?

Thanks!

---

