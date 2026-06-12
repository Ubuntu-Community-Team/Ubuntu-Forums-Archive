---
title: "NVRM: Your system is not currently configured to drive a VGA console"
date: 2018-08-23
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2018-08-23
from dmesg
```
[    6.197541] NVRM: Your system is not currently configured to drive a VGA console
               on the primary VGA device. The NVIDIA Linux graphics driver
               requires the use of a text-mode VGA console. Use of other console
               drivers including, but not limited to, vesafb, may result in
               corruption and stability problems, and is not supported.
```
i found this:
[https://devtalk.nvidia.com/default/topic/827139/linux/uefi-nvidia-vga-console-complaints-/2](https://devtalk.nvidia.com/default/topic/827139/linux/uefi-nvidia-vga-console-complaints-/2)
So i need to disable csm to get to make the nvidia driver/card happy
requires disabling fast boot to get csm options
disabled it and i have no boot devices...
the only sub csm setting that lets lets me have boot devices is setting the video one to legacy only...

Motherboard Manual: [http://asrock.pc.cdn.bitgravity.com/Manual/Fatal1ty%20Z97%20Killer.pdf](http://asrock.pc.cdn.bitgravity.com/Manual/Fatal1ty%20Z97%20Killer.pdf) Page 97 (aka 105) is where CSM is covered

When the video option is on uefi option it uses my HDMI display instead of my DVI display (DVI display is a assist monitor, so that is great, but no boot devices...)

---

### Post by pqwoerituytrueiwoq on 2018-08-25
So i found this:
[https://www.vanstechelman.eu/content/creating-an-uefi-bootable-linux-usb-stick#Converting_Ubuntu_into_UEFI_mode](https://www.vanstechelman.eu/content/creating-an-uefi-bootable-linux-usb-stick#Converting_Ubuntu_into_UEFI_mode)
but it requires i boot in efi mode 1st before i can make it boot in efi

So i tried booting my multi boot flash drive and while it shows a uefi boot option in my bios for it, though it does not work

---

### Post by pqwoerituytrueiwoq on 2018-08-25
I made a second USB flash drive using startup dish creator
that was able to boot in uefi mode
i was then able to go through without error
however it told me to do this:
sudo chroot "/mnt/boot-sav/nvme0n1p2" apt-get install -y grub-efi-amd64-signed shim-signed linux-headers-generic linux-signed-generic
instead i did this as i do not use secure boot:
sudo chroot "/mnt/boot-sav/nvme0n1p2" apt-get install -y grub-efi-amd64 linux-headers-generic linux-generic

I was hoping that would have gotten the boot splash or dmesg output on screen during boot though

---

