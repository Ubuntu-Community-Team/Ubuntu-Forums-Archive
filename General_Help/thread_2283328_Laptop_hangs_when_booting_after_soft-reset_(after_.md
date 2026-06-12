---
title: "Laptop hangs when booting after soft-reset (after hard-booting to GNU/Linux)"
date: 2015-06-21
forum: General Help
---

### Post by El Potro on 2015-06-21
Hello GNU-Linux/Ubuntu experts.

This is a dual booting (GRUB 2) UEFI 64-bit laptop.

If I hard-boot (shut-down the computer and turn it on manually) to GNU/Linux (Debian, Ubuntu, different versions and different kernels, up to 4.0.4) the system works fine, but if I reboot (shutdown -r now, reboot, init 6), when the computer starts again it will ALWAYS hang when loading the operative system (it doesn't matter if I choose GNU/Linux or Windows 8.1).

When booting GNU/Linux it hangs at "loading initial ramdisk...", or sometimes it passes it but hangs right afterwards, at the first line of systemd. When booting Windows 8.1 it doesn't display any message, it hangs shortly after showing the Windows logo.

Now here's an interesting thing: If I hard-boot into Windows 8.1 and I soft-reset, then the computer will boot to any system without any problems. And not only once, I can reboot for an unlimited amount of times any system. But this ends if I shutdown or sleep the computer. Then the problem is here again, unless I hard-boot to Windows again.

To put it more graphically, the boot order can be WIN->ANY-OS->ANY-OS, etc. But it can never be GNU/LINUX->ANY OS.

I compared the outputs of fwts (Firmware Test Suite) after hard-booting to Ubuntu, and after hard-booting to Windows and soft-booting to Ubuntu and they are exactly the same. Also the dmesg output seems to be the same. If only I knew what I'm looking for!

I don't know why this happens. I've been reading a lot but I haven't found info of anything like this anywhere so I hope someone here can tell me where the problem might be. I'm ready to do any suggested tests or post any outputs needed. All ideas will be much appreciated.

---

