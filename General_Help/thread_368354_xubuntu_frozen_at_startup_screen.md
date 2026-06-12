---
title: "xubuntu frozen at startup screen"
date: 2007-02-23
forum: General Help
---

### Post by Ginga on 2007-02-23
Hello

I have just installed Xubuntu on a pentium 2 and I have two problems:

1 - The screen resolution of the "startup screen" (between grub menu and login screen) is not correct: pictures are blurry and my LCD screen tells me that the "video mode is not supported". I would like then to know how to set this value (or simply remove this screen). I have the same problem when I shutdown the computer. I have to say that the end of the install was painful: at first startup, the screen was not recognized, refresh and synchro frequencies not set, graphic card (ATI RAGE PRO) not well configured.

2 - The second problem is simply that Xubuntu does not start from a powered off computer. However, it restarts correctly (except for the 1st problem). After the GRUB menu, the start up freezes between the "first and 2nd rectangles" (sorry for the lack of precision, but I don't see what is happening during the mean time). Then, I have to restart the computer (reset button) and the everything goes fine until the end. Once Xubuntu is started, the reboot command works well too.

Thanks in advance for your help

---

### Post by cronholio on 2007-02-23
You can edit your /boot/grub/menu.lst and change "splash" to "nosplash" for your default kernel (should be the top one). The boot sequence will stay in text mode. If you know the correct resolution, keep "splash" and add "vga=xxx" at the end of the line, where "xxx" depends on your desired resolution:
```
# VESA framebuffer console @ 1024x768x64k
# vga=791
# VESA framebuffer console @ 1024x768x32k
# vga=790
# VESA framebuffer console @ 1024x768x256
# vga=773
# VESA framebuffer console @ 800x600x64k
# vga=788
# VESA framebuffer console @ 800x600x32k
# vga=787
# VESA framebuffer console @ 800x600x256
# vga=771
# VESA framebuffer console @ 640x480x64k
# vga=785
# VESA framebuffer console @ 640x480x32k
# vga=784
# VESA framebuffer console @ 640x480x256
# vga=769
```

---

### Post by Ginga on 2007-02-23
Thank you for your help

I could change the resolution to a lower one and see that my monitor accepted it. But the splash screen was not centered....
Moreover, the default option was VGA=791, which is normally accepted by both my monitor and my graphic card. This is not only a resolution problem. So I ended up removing the splash screen.

This allowed me to see where the startup freezes. Some strange messages can be read:

input: PC speaker as /class/input/input1
unable to register OSS PCM device 0:0
usbcore : registered new driver hiddev
**BUG: soft lockup detected on CPU #0 !**
<c01491cf> softlockup_tick +0x9f/0xf0  <c....   > update_process_times + 0x31/0x80
<...          > timer_interrupt + 0x7c/0xb0<c....   > handle_IRQ_event + 0x33/0x60
...

What is strange is that everything is fine when I reboot. I have this log instead:

PCI Ethernet driver v1.2 (Mar 22, 2004)
PCI: Found IRQ 12 for device 0000:00:0a.0
unable to register OSS PCM device 0:0
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x080F
usbcore: registered new driver libusual
usbcore: registered new driver hiddev
input: Cypress Sem Cypress USB Mouse as /class/input/input2
input: USB HID v1.00 Mouse [Cypress Sem Cypress USB Mouse] on usb-0000:00:04.2-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver

This problem is discussed [here]("http://ubuntuforums.org/showthread.php?t=251944"), but I don't have the same configuration (no wireless card).

---

