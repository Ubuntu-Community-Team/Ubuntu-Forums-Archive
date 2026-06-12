---
title: "Huawei E160 3G is being reattached over and over again"
date: 2015-07-24
forum: General Help
---

### Post by marcinkolenda419 on 2015-07-24
Hello dears, I've went into trouble and urgently need your help.
Two days ago I have installed Kubuntu on my girlfriend`s laptop. She have Huawei E160 modem which is her primary source of internet connection.

Device is being reattached over and over again by kernel. Please take a look at this dmesg output

dmesg:
```

[  905.819650] usb 1-1: reset high-speed USB device number 11 using xhci_hcd
[  906.006830] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f790
[  906.006853] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f700
[  906.006869] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c67c8
[  906.006882] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f748
[  906.006895] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6c48
[  906.006908] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6780
[  906.006922] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6e40
[  906.006935] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6c00
[  906.006953] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6e88
[  906.008935] usb-storage 1-1:1.0: USB Mass Storage device detected
[  906.012288] option 1-1:1.0: GSM modem (1-port) converter detected
[  906.012712] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB23
[  906.012799] usb-storage 1-1:1.1: USB Mass Storage device detected
[  906.016455] option 1-1:1.1: GSM modem (1-port) converter detected
[  906.016855] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB27
[  916.063541] option1 ttyUSB23: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[  916.063558] option1 ttyUSB23: usb_wwan_indat_callback: resubmit read urb failed. (-2)                                                                                
[  916.063589] option1 ttyUSB23: usb_wwan_indat_callback: resubmit read urb failed. (-2)                                                                                
[  916.148874] option1 ttyUSB23: GSM modem (1-port) converter now disconnected from ttyUSB23
[  916.148912] option 1-1:1.0: device disconnected
[  916.149283] option1 ttyUSB27: GSM modem (1-port) converter now disconnected from ttyUSB27
[  916.149316] option 1-1:1.1: device disconnected
[  916.263700] usb 1-1: reset high-speed USB device number 11 using xhci_hcd
[  916.450830] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f790
[  916.450857] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f700
[  916.450875] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c67c8
[  916.450890] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f748
[  916.450906] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6c48
[  916.450922] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6780
[  916.450937] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6e40
[  916.450953] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6c00
[  916.450968] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6e88
[  916.452956] usb-storage 1-1:1.0: USB Mass Storage device detected
[  916.453582] option 1-1:1.0: GSM modem (1-port) converter detected
[  916.454219] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB27
[  916.454356] usb-storage 1-1:1.1: USB Mass Storage device detected
[  916.460712] option 1-1:1.1: GSM modem (1-port) converter detected
[  916.461310] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB28
[  933.997435] option1 ttyUSB27: GSM modem (1-port) converter now disconnected from ttyUSB27
[  933.997514] option 1-1:1.0: device disconnected
[  933.997600] option1 ttyUSB28: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[  933.997627] option1 ttyUSB28: usb_wwan_indat_callback: resubmit read urb failed. (-2)                                                                                
[  933.997646] option1 ttyUSB28: usb_wwan_indat_callback: resubmit read urb failed. (-2)                                                                                
[  939.733734] option1 ttyUSB28: GSM modem (1-port) converter now disconnected from ttyUSB28
[  939.733760] option 1-1:1.1: device disconnected
[  939.845760] usb 1-1: reset high-speed USB device number 11 using xhci_hcd
[  940.032758] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f790
[  940.032785] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f700
[  940.032803] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c67c8
[  940.032819] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f748
[  940.032834] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6c48
[  940.032850] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6780
[  940.032865] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6e40
[  940.032887] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6c00
[  940.032892] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6e88
[  940.034734] usb-storage 1-1:1.0: USB Mass Storage device detected
[  940.034988] option 1-1:1.0: GSM modem (1-port) converter detected
[  940.035996] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB27
[  940.036040] usb-storage 1-1:1.1: USB Mass Storage device detected
[  940.038344] option 1-1:1.1: GSM modem (1-port) converter detected
[  940.038911] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB29
[  957.567293] option1 ttyUSB27: GSM modem (1-port) converter now disconnected from ttyUSB27
[  957.567335] option 1-1:1.0: device disconnected
[  957.567396] option1 ttyUSB29: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[  957.567409] option1 ttyUSB29: usb_wwan_indat_callback: resubmit read urb failed. (-2)                                                                                
[  957.567417] option1 ttyUSB29: usb_wwan_indat_callback: resubmit read urb failed. (-2)                                                                                
[  963.752282] option1 ttyUSB29: GSM modem (1-port) converter now disconnected from ttyUSB29
[  963.752363] option 1-1:1.1: device disconnected
[  963.872078] usb 1-1: reset high-speed USB device number 11 using xhci_hcd
[  964.059154] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f790
[  964.059171] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f700
[  964.059182] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c67c8
[  964.059191] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f748
[  964.059201] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6c48
[  964.059210] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6780
[  964.059220] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6e40
[  964.059229] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6c00
[  964.059238] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6e88
[  964.061281] usb-storage 1-1:1.0: USB Mass Storage device detected
[  964.061675] option 1-1:1.0: GSM modem (1-port) converter detected
[  964.062050] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB27
[  964.062125] usb-storage 1-1:1.1: USB Mass Storage device detected
[  964.067466] option 1-1:1.1: GSM modem (1-port) converter detected
[  964.068469] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB29
[  981.649782] option1 ttyUSB27: GSM modem (1-port) converter now disconnected from ttyUSB27
[  981.649873] option 1-1:1.0: device disconnected
[  981.649970] option1 ttyUSB29: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[  981.649997] option1 ttyUSB29: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[  981.650018] option1 ttyUSB29: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[  981.650037] option1 ttyUSB29: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[  987.771176] option1 ttyUSB29: GSM modem (1-port) converter now disconnected from ttyUSB29
[  987.771210] option 1-1:1.1: device disconnected
[  987.886226] usb 1-1: reset high-speed USB device number 11 using xhci_hcd
[  988.073408] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f790
[  988.073418] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f700
[  988.073421] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c67c8
[  988.073424] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88007014f748
[  988.073428] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6c48
[  988.073431] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6780
[  988.073434] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6e40
[  988.073438] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6c00
[  988.073441] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800700c6e88
[  988.075444] usb-storage 1-1:1.0: USB Mass Storage device detected
[  988.077323] option 1-1:1.0: GSM modem (1-port) converter detected
[  988.078651] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB27
[  988.078704] usb-storage 1-1:1.1: USB Mass Storage device detected
[  988.079750] option 1-1:1.1: GSM modem (1-port) converter detected
[  988.080009] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB29

```

Modem is being recognized and I bet usb_modeswitch isn't necessary. I've tried using it however - vainly.

lsusb:
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 008: ID 0bda:579c Realtek Semiconductor Corp. 
Bus 001 Device 007: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 006: ID 13fe:3e00 Kingston Technology Company Inc. Flash Drive
Bus 001 Device 011: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Modem is functioning properly on Windows 8. It isn't on Manjaro Live and probably other distros with this kernel.
How to trace down that pixie? I do have only 2 days to solve this she would have to use Windows 8.

modem-manager-gui should detect this modem?
plasma-nm applet will connect this automatically after adding Mobile Broadband connection?

---

### Post by Vladlenin5000 on 2015-07-24
Hi and welcome.

Some modems are quite problematic in Ubuntu (and others) in general but especially when used in a USB3.0 port. Can you test it in a USB2.0?

---

### Post by marcinkolenda419 on 2015-07-25
Welcome, thank you for response.
I've tried on USB 2.0 and everything seems being the same. Modem is being reattached as it were.
Black despair.

---

