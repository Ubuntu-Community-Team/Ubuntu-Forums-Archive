---
title: "USB Device not recognised?"
date: 2007-08-09
forum: General Help
---

### Post by hmind on 2007-08-09
[SIZE="3"]Hey guys, I need some help. Ive been trying to get my Dlink G122-A2 usb wireless card working but when i use "lsusb" it returns "Bus 003 Device 001: ID 0000:0000" and same with "Bus 002" as if it were not connected, any ideas? 

Thanks in advance,
hmind[/SIZE]

EDIT: here is the output of dmesg |grep usb :
[   28.564380] usbcore: registered new interface driver usbfs
[   28.564407] usbcore: registered new interface driver hub
[   28.564438] usbcore: registered new device driver usb
[   28.565780] usb usb1: configuration #1 chosen from 1 choice
[   28.672717] usb usb2: configuration #1 chosen from 1 choice
[   28.780627] usb usb3: configuration #1 chosen from 1 choice
[   28.894299] usb usb4: configuration #1 chosen from 1 choice
[   28.916230] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   29.243973] usb 4-2: new high speed USB device using ehci_hcd and address 2
[   29.384773] usb 4-2: configuration #1 chosen from 1 choice
[   44.460992] usb 4-2: USB disconnect, address 2
[   44.460996] p54usb: reset failed!
[   44.461006] prism54usb: probe of 4-2:1.0 failed with error -108
[   44.461379] usbcore: registered new interface driver prism54usb
[   44.741415] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   44.893263] usb 1-2: not running at top speed; connect to a high speed hub
[   44.924352] usb 1-2: configuration #1 chosen from 1 choice
[   46.931927] p54usb: reset failed!
[   46.931947] prism54usb: probe of 1-2:1.0 failed with error -110
[   46.931993] usb 1-2: device_add(1-2:1.0) --> -110
[   46.932039] usb 1-2: USB disconnect, address 3
[   46.932117] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device()
[   46.932141]  [<f0881255>] usb_autopm_do_device+0xd5/0xe0 [usbcore]
[   46.932180]  [<f087b622>] usb_disconnect+0x122/0x130 [usbcore]
[   46.932214]  [<f087b674>] hub_pre_reset+0x44/0x70 [usbcore]
[   46.932236]  [<f087c152>] hub_thread+0xc2/0xc20 [usbcore]
[   46.932315]  [<f087c090>] hub_thread+0x0/0xc20 [usbcore]
[   60.274903] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device()
[   60.274935]  [<f0881255>] usb_autopm_do_device+0xd5/0xe0 [usbcore]
[   60.274979]  [<f08877d5>] usbdev_release+0x75/0xc0 [usbcore]
[  110.620607] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device()
[  110.620645]  [<f0881255>] usb_autopm_do_device+0xd5/0xe0 [usbcore]
[  110.620695]  [<f08877d5>] usbdev_release+0x75/0xc0 [usbcore]
[  119.958420] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device()
[  119.958452]  [<f0881255>] usb_autopm_do_device+0xd5/0xe0 [usbcore]
[  119.958500]  [<f08877d5>] usbdev_release+0x75/0xc0 [usbcore]
[  349.325999] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device()
[  349.326036]  [<f0881255>] usb_autopm_do_device+0xd5/0xe0 [usbcore]
[  349.326084]  [<f08877d5>] usbdev_release+0x75/0xc0 [usbcore]
[  412.391057] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device()
[  412.391094]  [<f0881255>] usb_autopm_do_device+0xd5/0xe0 [usbcore]
[  412.391142]  [<f08877d5>] usbdev_release+0x75/0xc0 [usbcore]
[  451.532367] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device()
[  451.532404]  [<f0881255>] usb_autopm_do_device+0xd5/0xe0 [usbcore]
[  451.532453]  [<f08877d5>] usbdev_release+0x75/0xc0 [usbcore]
[  455.865432] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device()
[  455.865464]  [<f0881255>] usb_autopm_do_device+0xd5/0xe0 [usbcore]
[  455.865510]  [<f08877d5>] usbdev_release+0x75/0xc0 [usbcore]
[  752.259508] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device()
[  752.259541]  [<f0881255>] usb_autopm_do_device+0xd5/0xe0 [usbcore]
[  752.259587]  [<f08877d5>] usbdev_release+0x75/0xc0 [usbcore]
[ 1613.169091] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device()
[ 1613.169124]  [<f0881255>] usb_autopm_do_device+0xd5/0xe0 [usbcore]
[ 1613.169171]  [<f08877d5>] usbdev_release+0x75/0xc0 [usbcore]
[ 1626.883713] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device()
[ 1626.883745]  [<f0881255>] usb_autopm_do_device+0xd5/0xe0 [usbcore]

---

### Post by hmind on 2007-08-09
I have updated to the latest kernel with no luck. Same dmesg. Anyone have suggestions?

---

### Post by santhana on 2008-05-13
> BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device()
> [ 412.391094] [<f0881255>] usb_autopm_do_device+0xd5/0xe0 [usbcore]


1. check whether the module for ACM is loaded. 

$ modprobe cdc-acm

2. Now after connecting the mobile/modem, please check if there is a new device at /dev/ttyACM0 corresponding to the mobile phone. 

3. Now you could access your mobile from here.. I had this problem when connecting a Nokia 5300 in the Nokia mode when we had to send SMS/MMS using Gnokii.. 

hope it helps. 
- santhana

---

