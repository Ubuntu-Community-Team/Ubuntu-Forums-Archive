---
title: "Ubuntu &quot;stops&quot; after a while"
date: 2008-02-09
forum: General Help
---

### Post by gibblegobble on 2008-02-09
I'll start by letting you know what I did
1. I started fresh with Gutsy formatting both my / and my /home partitions
2. I then compile a custom kernel (2.6.24 - following the "Master kernel Thread")
3. Then I set up ndiswrapper using the linksys driver (I have a Linksys WMP54GS -- so a broadcom 4306) [I was hoping to have better luck with this, my previous installs used variety of the firmware for bcm43xx and although it worked, it worked poorly - and back in 2004 I ran a Fedora Core install where ndiswrapper actually out-performed my windows install]
3b. To get this to work I had to write a little bash script that stopped ndiswrapper, and ssb, and then start ndiswrapper again (I didn't tell it to start ssb again) - also at this point I disabled the avahi service - since it was failing at startup
4. I then installed the nvidia drivers via Envy and configured my mouse (Logitech MX510)

now for the problem

after a spontaneous amount of time (from say 10 minutes to 90 minutes) my wireless will "die" - I'm still connected (however poorly (50% signal) since I have the 7dbi antenna on my wireless card, as well as on my router [which is the WRT54GS - with DD-WRT and I have the transmit power jacked to 70mw - and there is only 1 wall separating me from the router {my laptop, and the other computer in this room all have excellent signals}]) but I have zero internet or netwrok access, if I wait a little while longer I won't be able to launch programs by any means, not even a terminal and I have to hard reboot :(

does anyone have any ideas as to what can be done to fix this? -- by the way, I'd consider myself in between Linux noob to intermediate - saying I know how to fallow instructions and tutorials and tweak them usually enough to suit my needs, so if you need any more information just let me know 

thanks plenty in advance for any comments

---

### Post by nemarasu on 2008-02-09
what does /var/log/messages say after you bring the system back up?

---

### Post by gibblegobble on 2008-02-09
Quite a bit actually (can't seem to post it here soe I uploaded it)
[http://www12.brinkster.com/gibble/index.htm]("http://www12.brinkster.com/gibble/index.htm")

--there you go -- I hope it helps :D ( I can't make anything of it :S )

---

### Post by nemarasu on 2008-02-09
maybe try disabling acpi at boot. For some reason, from the looks of it, something calls for the network card (which is, I'm assuming eth1), but that interrupt:  0000:00:09.0 has been disabled. From that point on it looks like it tries to "reload" or "load" if it wasn't there before and dies because the interrupt was disabled.

---

Feb  8 19:02:52 cr0 kernel: ACPI: PCI interrupt for device 0000:00:09.0 disabled
Feb  8 19:03:45 cr0 kernel: ndiswrapper version 1.52 loaded (smp=no, preempt=no)
Feb  8 19:03:45 cr0 kernel: ndiswrapper: driver wmp54gs (Linksys,12/22/2004, 3.100.46.0) loaded
Feb  8 19:03:45 cr0 kernel: ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Feb  8 19:03:45 cr0 kernel: ndiswrapper: using IRQ 5
Feb  8 19:03:45 cr0 kernel: wlan0: ethernet device 00:12:17:93:bb:00 using NDIS driver: wmp54gs, version: 0x3642e00, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
Feb  8 19:03:45 cr0 kernel: wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Feb  8 19:03:45 cr0 kernel: ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Feb  8 19:03:45 cr0 kernel: usbcore: registered new interface driver ndiswrapper
Feb  8 19:03:45 cr0 kernel: ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  8 19:06:14 cr0 kernel: ndiswrapper: device eth1 removed
Feb  8 19:06:14 cr0 kernel: ACPI: PCI interrupt for device 0000:00:09.0 disabled
Feb  8 19:06:14 cr0 kernel: usbcore: deregistering interface driver ndiswrapper
Feb  8 19:06:42 cr0 kernel: ndiswrapper version 1.52 loaded (smp=no, preempt=no)
Feb  8 19:06:42 cr0 kernel: ndiswrapper: driver wmp54gs (Linksys,12/22/2004, 3.100.46.0) loaded
Feb  8 19:06:42 cr0 kernel: ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Feb  8 19:06:42 cr0 kernel: ndiswrapper: using IRQ 5
Feb  8 19:06:43 cr0 kernel: wlan0: ethernet device 00:12:17:93:bb:00 using NDIS driver: wmp54gs, version: 0x3642e00, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
Feb  8 19:06:43 cr0 kernel: wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Feb  8 19:06:43 cr0 kernel: usbcore: registered new interface driver ndiswrapper
Feb  8 19:06:43 cr0 kernel: ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Feb  8 19:06:43 cr0 kernel: ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  8 19:11:27 cr0 exiting on signal 15
Feb  8 19:12:23 cr0 syslogd 1.4.1#21ubuntu3: restart.
Feb  8 19:12:23 cr0 kernel: Inspecting /boot/System.map-2.6.24
Feb  8 19:12:23 cr0 kernel: Loaded 22757 symbols from /boot/System.map-2.6.24.
Feb  8 19:12:23 cr0 kernel: Symbols match kernel version 2.6.24.
Feb  8 19:12:23 cr0 kernel: No module symbols loaded - kernel modules not enabled. 
Feb  8 19:12:23 cr0 kernel: Linux version 2.6.24 (root@cr0) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Fri Feb 8 16:39:51 AST 2008
Feb  8 19:12:23 cr0 kernel: BIOS-provided physical RAM map:
Feb  8 19:12:23 cr0 kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  8 19:12:23 cr0 kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  8 19:12:23 cr0 kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  8 19:12:23 cr0 kernel:  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
Feb  8 19:12:23 cr0 kernel:  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
Feb  8 19:12:23 cr0 kernel:  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
Feb  8 19:12:23 cr0 kernel:  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Feb  8 19:12:23 cr0 kernel: 127MB HIGHMEM available.
Feb  8 19:12:23 cr0 kernel: 896MB LOWMEM available.

--

So here at boot time we can see that the address is enabled and set to IRQ 5. We can also see later down in the boot process where USB takes up IRQ 5 as well. This *may* be the cause. It could be your hammering usb and the network, the network card has to wait too long, times out, puts itself into a suspend state (like a WOL) and doesn't wake up when its time is called, locking up the machine. I'm probably way off. But there you go, it is what it is.

--

Feb  8 19:12:23 cr0 kernel: ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Feb  8 19:12:23 cr0 kernel: ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Feb  8 19:12:23 cr0 kernel: ssb: Sonics Silicon Backplane found on PCI device 0000:00:09.0
Feb  8 19:12:23 cr0 kernel: SCSI subsystem initialized
Feb  8 19:12:23 cr0 kernel: usbcore: registered new interface driver usbfs
Feb  8 19:12:23 cr0 kernel: usbcore: registered new interface driver hub
Feb  8 19:12:23 cr0 kernel: usbcore: registered new device driver usb
Feb  8 19:12:23 cr0 kernel: via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Feb  8 19:12:23 cr0 kernel: via-rhine: Broken BIOS detected, avoid_D3 enabled.
Feb  8 19:12:23 cr0 kernel: USB Universal Host Controller Interface driver v3.0
Feb  8 19:12:23 cr0 kernel: ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Feb  8 19:12:23 cr0 kernel: ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb  8 19:12:23 cr0 kernel: uhci_hcd 0000:00:10.0: UHCI Host Controller
Feb  8 19:12:23 cr0 kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  8 19:12:23 cr0 kernel: uhci_hcd 0000:00:10.0: irq 11, io base 0x0000d400
Feb  8 19:12:23 cr0 kernel: usb usb1: configuration #1 chosen from 1 choice
Feb  8 19:12:23 cr0 kernel: hub 1-0:1.0: USB hub found
Feb  8 19:12:23 cr0 kernel: hub 1-0:1.0: 2 ports detected
Feb  8 19:12:23 cr0 kernel: ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Feb  8 19:12:23 cr0 kernel: uhci_hcd 0000:00:10.1: UHCI Host Controller
Feb  8 19:12:23 cr0 kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  8 19:12:23 cr0 kernel: uhci_hcd 0000:00:10.1: irq 5, io base 0x0000d800
Feb  8 19:12:23 cr0 kernel: usb usb2: configuration #1 chosen from 1 choice
Feb  8 19:12:23 cr0 kernel: hub 2-0:1.0: USB hub found
Feb  8 19:12:23 cr0 kernel: hub 2-0:1.0: 2 ports detected

--

I'm old school, so if you can, move the wireless card to the lowest pci slot on your motherboard, that might change the IRQ for you. If something else is in there move it. If you kill your computer because you didn't take proper precautions, don't blame me. I didn't force you.  :)

---

### Post by gibblegobble on 2008-02-11
thank you very much for looking into this - I'll definitely take this into consideration when I rebuild -- unfortunately I didn't get the opportunity to kill my computer by being neglectful, but one of my hard drives disc-labels seems to have decided to cut itself to pieces (it was about 8 yrs old), so until I can get a new hard drive for this box I'll be Linux-less :(

although i still find the issue odd since I've had gutsy/feisty installed before, would ndiswrapper versus bcm43xx firmware make that much of a difference? (the problem was persistent on both kernels the default and custom)

---

