---
title: "Unable to Boot Raspberry Pi from GPT Disk"
date: 2024-08-14
forum: General Help
---

### Post by Crsh on 2024-08-14
I'm having a little trouble booting Ubuntu 20.04 from a WD Purple 4TB hard drive. I've heard that running the OS on a microSD card is not recommended for a surveillance system with 24x7 uptime and so am attempting to just run off a drive connected to a USB SATA adapter. I've updated the firmware so that it will boot from USB. Now the preinstalled image that I have is MBR, so imaging with dd and creating a partition to fill the remaining space didn't work. I tried deleting the partitions and recreating them on a new GPT volume, then copying over the files from the microSD card using the method described [here]("https://raspberrypi.stackexchange.com/questions/120525/is-it-possible-to-boot-a-raspberry-pi-4-from-a-gpt-usb-connected-disk") and [here]("https://forums.raspberrypi.com/viewtopic.php?t=319435#p1912314") twice. Both times when I tried to reboot with only the HDD connected, I got the kernel errors seen below.

[[img]https://i.ibb.co/8KCgtng/IMG-20240809-153059.jpg[/img]](https://ibb.co/5M0hwXh)

---

