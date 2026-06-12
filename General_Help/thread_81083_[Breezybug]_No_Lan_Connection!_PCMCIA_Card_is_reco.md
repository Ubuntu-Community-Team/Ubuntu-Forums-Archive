---
title: "[Breezybug] No Lan Connection! PCMCIA Card is recognized but doesnt work."
date: 2005-10-23
forum: General Help
---

### Post by steigweis on 2005-10-23
On Debian, I get a connection.. but on Breezy, I dont :/ 

I have got a PCMCIA ethernet card in my old notebook and it has the rtl8139 chipset. I can't get any network access. No ping, no nuthin.."network is unreachable"


The lanconfig should be ok, but on DMESG an error shows up.

There is a "noIPv6 routers present" message. I don't know, if that has something to do with my trouble..

Any ideas?

---

### Post by LorenzoD on 2005-10-23
First of all, what is the output of ifconfig?

---

### Post by steigweis on 2005-10-23
```

```root@woluni:/home/wol# ifconfig
eth0      Protokoll:Ethernet  Hardware Adresse 00:40:F4:C3:9B:0F
          inet Adresse:192.168.0.4  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::240:f4ff:fec3:9b0f/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294966461 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Basisadresse:0x4800

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16440 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:1231824 (1.1 MiB)  TX bytes:1231824 (1.1 MiB)

root@woluni:/home/wol# ifconfig

---

### Post by LorenzoD on 2005-10-23
At least you have an IP address. Next, what is the output of route?

---

### Post by steigweis on 2005-10-23
this sould be some useful information - the blue section could be interesting according to my trouble. but i dont have no clue how to interpret it and what to do to cure my little baby's ill...

#######ROUTE

root@woluni:/home/wol# route
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0


####### /etc/network/interfaces

root@woluni:/home/wol# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 192.168.0.4
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 217.237.150.97


######### LSPCI

root@woluni:/home/wol# lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1251A
0000:00:02.1 CardBus bridge: Texas Instruments PCI1251A
0000:00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 12)
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
root@woluni:/home/wol#


########## DMESG

[4294716.806000] Yenta: CardBus bridge found at 0000:00:02.0 [1014:00eb]
[4294716.806000] Yenta: Enabling burst memory read transactions
[4294716.806000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294716.806000] Yenta: Routing CardBus interrupts to PCI
[4294716.806000] Yenta TI: socket 0000:00:02.0, mfunc 0xfba97543, devctl 0x62
[4294716.907000] Yenta TI: socket 0000:00:02.0 probing PCI interrupt failed, trying to fix
[4294717.008000] Yenta TI: socket 0000:00:02.0 no PCI interrupts. Fish. Please report.
[4294717.128000] Yenta: ISA IRQ mask 0x0438, PCI irq 0
[4294717.128000] Socket status: 30000020
[4294717.159000] ACPI: PCI Interrupt Link [LNKB] disabled and referenced, BIOS bug.
[4294717.160000] ACPI: PCI Interrupt Link [LNKB] BIOS reported IRQ 0, using IRQ 10
[4294717.160000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[4294717.160000] PCI: setting IRQ 10 as level-triggered
[4294717.160000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[4294717.160000] Yenta: CardBus bridge found at 0000:00:02.1 [1014:00eb]
[4294717.160000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294717.160000] Yenta: Routing CardBus interrupts to PCI
[4294717.160000] Yenta TI: socket 0000:00:02.1, mfunc 0xfba97543, devctl 0x62
[4294717.861000] irq 10: nobody cared (try booting with the "irqpoll" option.
[4294717.861000]  [<c012de13>] __report_bad_irq+0x31/0x74
[4294717.861000]  [<c012deeb>] note_interrupt+0x7d/0xa2
[4294717.861000]  [<c012da10>] __do_IRQ+0x85/0xb1
[4294717.861000]  [<c0104ca5>] do_IRQ+0x19/0x24
[4294717.861000]  [<c01038b6>] common_interrupt+0x1a/0x20
[4294717.861000]  [<c0119058>] __do_softirq+0x2c/0x7d
[4294717.861000]  [<c01190cb>] do_softirq+0x22/0x26
[4294717.861000]  [<c0104caa>] do_IRQ+0x1e/0x24
[4294717.861000]  [<c01038b6>] common_interrupt+0x1a/0x20
[4294717.861000]  [<c012dbee>] setup_irq+0x9d/0xc1
[4294717.861000]  [<cc9fbe79>] yenta_probe_handler+0x0/0x3a [yenta_socket]
[4294717.861000]  [<c012dd07>] request_irq+0x72/0x8b
[4294717.861000]  [<cc9fbf1c>] yenta_probe_cb_irq+0x69/0xeb [yenta_socket]
[4294717.861000]  [<cc9fbe79>] yenta_probe_handler+0x0/0x3a [yenta_socket]
[4294717.861000]  [<cc9fb3fb>] ti12xx_irqroute_func1+0x9e/0x1f3 [yenta_socket]
[4294717.861000]  [<cc9fb937>] ti12xx_override+0x124/0x13d [yenta_socket]
[4294717.861000]  [<cc9fc228>] yenta_probe+0x131/0x1f9 [yenta_socket]
[4294717.861000]  [<c01a2cdd>] pci_device_probe_static+0x2e/0x41
[4294717.861000]  [<c01a2d0f>] __pci_device_probe+0x1f/0x32
[4294717.861000]  [<c01a2d3e>] pci_device_probe+0x1c/0x31
[4294717.861000]  [<c01ebfe6>] driver_probe_device+0x36/0x54
[4294717.861000]  [<c01ec0be>] driver_attach+0x39/0x6a
[4294717.861000]  [<c01ec444>] bus_add_driver+0x5e/0x80
[4294717.861000]  [<c01ec7a5>] driver_register+0x23/0x25
[4294717.861000]  [<c01a2f01>] pci_register_driver+0x5f/0x72
[4294717.861000]  [<cc89000a>] yenta_socket_init+0xa/0xc [yenta_socket]
[4294717.861000]  [<c0129682>] sys_init_module+0xb5/0x172
[4294717.861000]  [<c0102e9f>] sysenter_past_esp+0x54/0x75
[4294717.861000] handlers:
[4294717.861000] [<cc9fbe79>] (yenta_probe_handler+0x0/0x3a [yenta_socket])
[4294717.861000] Disabling IRQ #10
[4294717.963000] Yenta TI: socket 0000:00:02.1 probing PCI interrupt failed, trying to fix
[4294718.659000] irq 10: nobody cared (try booting with the "irqpoll" option.
[4294718.659000]  [<c012de13>] __report_bad_irq+0x31/0x74
[4294718.659000]  [<c012deeb>] note_interrupt+0x7d/0xa2
[4294718.659000]  [<c012da10>] __do_IRQ+0x85/0xb1
[4294718.659000]  [<c0104ca5>] do_IRQ+0x19/0x24
[4294718.659000]  [<c01038b6>] common_interrupt+0x1a/0x20
[4294718.659000]  [<c0119058>] __do_softirq+0x2c/0x7d
[4294718.659000]  [<c01190cb>] do_softirq+0x22/0x26
[4294718.659000]  [<c0104caa>] do_IRQ+0x1e/0x24
[4294718.659000]  [<c01038b6>] common_interrupt+0x1a/0x20
[4294718.659000]  [<c012dbee>] setup_irq+0x9d/0xc1
[4294718.659000]  [<cc9fbe79>] yenta_probe_handler+0x0/0x3a [yenta_socket]
[4294718.659000]  [<c012dd07>] request_irq+0x72/0x8b
[4294718.659000]  [<cc9fbf1c>] yenta_probe_cb_irq+0x69/0xeb [yenta_socket]
[4294718.659000]  [<cc9fbe79>] yenta_probe_handler+0x0/0x3a [yenta_socket]
[4294718.659000]  [<cc9fb4bd>] ti12xx_irqroute_func1+0x160/0x1f3 [yenta_socket]
[4294718.659000]  [<cc9fb937>] ti12xx_override+0x124/0x13d [yenta_socket]
[4294718.659000]  [<cc9fc228>] yenta_probe+0x131/0x1f9 [yenta_socket]
[4294718.659000]  [<c01a2cdd>] pci_device_probe_static+0x2e/0x41
[4294718.659000]  [<c01a2d0f>] __pci_device_probe+0x1f/0x32
[4294718.659000]  [<c01a2d3e>] pci_device_probe+0x1c/0x31
[4294718.659000]  [<c01ebfe6>] driver_probe_device+0x36/0x54
[4294718.659000]  [<c01ec0be>] driver_attach+0x39/0x6a
[4294718.659000]  [<c01ec444>] bus_add_driver+0x5e/0x80
[4294718.659000]  [<c01ec7a5>] driver_register+0x23/0x25
[4294718.659000]  [<c01a2f01>] pci_register_driver+0x5f/0x72
[4294718.659000]  [<cc89000a>] yenta_socket_init+0xa/0xc [yenta_socket]
[4294718.659000]  [<c0129682>] sys_init_module+0xb5/0x172
[4294718.659000]  [<c0102e9f>] sysenter_past_esp+0x54/0x75
[4294718.659000] handlers:
[4294718.659000] [<cc9fbe79>] (yenta_probe_handler+0x0/0x3a [yenta_socket])
[4294718.659000] Disabling IRQ #10
[4294718.862000] Yenta TI: socket 0000:00:02.1 no PCI interrupts. Fish. Please report.
[4294718.982000] Yenta: ISA IRQ mask 0x0038, PCI irq 0
[4294718.982000] Socket status: 30000006
[COLOR="Blue"][4294719.737000] 8139too Fast Ethernet driver 0.9.27
[4294719.756000] PCI: Enabling device 0000:02:00.0 (0000 -> 0003)
[4294719.756000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[4294719.756000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[4294719.761000] eth0: RealTek RTL8139 at 0x4000, 00:40:f4:c3:9b:0f, IRQ 9
[4294719.761000] eth0:  Identified 8139 chip type 'RTL-8139C'
[4294719.988000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294721.233000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[4294723.106000] create - never read codec ready from AC'97
[4294723.106000] it is not probably bug, try to use CS4236 driver
[4294723.106000] ACPI: PCI interrupt for device 0000:00:06.0 disabled
[4294723.106000] Sound Fusion CS46xx: probe of 0000:00:06.0 failed with error -5[4294724.446000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[4294724.446000] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!
[4294724.446000] piix4_smbus: probe of 0000:00:07.3 failed with error -1
[4294726.084000] Floppy drive(s): fd0 is 1.44M
[4294726.096000] FDC 0 is a National Semiconductor PC87306
[4294726.911000] irda_init()
[4294726.911000] NET: Registered protocol family 23
[4294727.567000] pnp: Device 00:07 activated.
[4294727.584000] gameport: NS558 PnP Gameport is pnp00:07/gameport0, io 0x200, speed 685kHz
[4294728.508000] input: PC Speaker
[4294729.691000] Real Time Clock Driver v1.12
[4294731.744000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294749.744000] NETDEV WATCHDOG: eth0: transmit timed out
[4294749.744000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[4294749.744000] eth0: Tx queue start entry 4  dirty entry 0.
[4294749.744000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[4294749.744000] eth0:  Tx descriptor 1 is 0008a03c.
[4294749.744000] eth0:  Tx descriptor 2 is 0008a03c.
[4294749.744000] eth0:  Tx descriptor 3 is 0008a03c.
[4294749.744000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294761.744000] NETDEV WATCHDOG: eth0: transmit timed out
[4294761.744000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[4294761.744000] eth0: Tx queue start entry 4  dirty entry 0.
[4294761.744000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[4294761.744000] eth0:  Tx descriptor 1 is 0008a03c.
[4294761.744000] eth0:  Tx descriptor 2 is 0008a03c.
[4294761.744000] eth0:  Tx descriptor 3 is 0008a03c.
[4294761.744000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294773.744000] NETDEV WATCHDOG: eth0: transmit timed out
[4294773.744000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[4294773.744000] eth0: Tx queue start entry 4  dirty entry 0.
[4294773.744000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[4294773.744000] eth0:  Tx descriptor 1 is 0008a03c.
[4294773.744000] eth0:  Tx descriptor 2 is 0008a03c.
[4294773.744000] eth0:  Tx descriptor 3 is 0008a03c.
[4294773.744000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294774.604000] ACPI: AC Adapter [AC] (on-line)
[4294774.858000] ACPI: Battery Slot [BAT0] (battery present)
[4294774.960000] ACPI: Power Button (FF) [PWRF]
[4294774.960000] ACPI: Lid Switch [LID0]
[4294774.960000] ACPI: Sleep Button (CM) [SLPB]
[4294775.480000] ibm_acpi: ec object not found
[4294776.048000] ACPI: Video Device [VID0] (multi-head: yes  rom: no  post: no)
[4294795.835000] IBM machine detected. Enabling interrupts during APM calls.
[4294795.835000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294795.835000] apm: overridden by ACPI.
[4294799.033000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294799.034000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294799.037000] cs: IO port probe 0xc00-0xcf7: clean.
[4294799.037000] cs: IO port probe 0xc00-0xcf7: clean.
[4294799.038000] cs: IO port probe 0xa00-0xaff: clean.
[4294799.038000] cs: IO port probe 0xa00-0xaff: clean.
[4294801.655000] Bluetooth: Core ver 2.7
[4294801.655000] NET: Registered protocol family 31
[4294801.655000] Bluetooth: HCI device and connection manager initialized
[4294801.655000] Bluetooth: HCI socket layer initialized
[4294801.734000] Bluetooth: L2CAP ver 2.7
[4294801.734000] Bluetooth: L2CAP socket layer initialized
[4294801.804000] Bluetooth: RFCOMM ver 1.5
[4294801.804000] Bluetooth: RFCOMM socket layer initialized
[4294801.804000] Bluetooth: RFCOMM TTY layer initialized
[4295046.317000] NET: Registered protocol family 10
[4295046.317000] Disabled Privacy Extensions on device c02eb280(lo)
[4295046.318000] IPv6 over IPv4 tunneling driver
[4295056.432000] eth0: no IPv6 routers present
[4295073.778000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4295074.585000] ISO 9660 Extensions: RRIP_1991A[/COLOR]

---

### Post by steigweis on 2005-10-24
*bump* my goodness... still no solution

---

### Post by shartrec on 2005-10-24
Don't know if it will help, but on my Thinkpad A21e, I can only get the ethernet network to work if I turn acpi off in the boot options.  That is, add acpi=off to the GRUB config.

---

### Post by steigweis on 2005-10-25
To all, who can understand German: THE SOLUTION [http://www.ubuntuusers.de/viewtopic.php?...e+thinkpad+770x](http://www.ubuntuusers.de/viewtopic.php?...e+thinkpad+770x)

To all, who dont, here is the solution also: At least the Thinkpad 600E seems to have problems with the ACPI function. It looks like there is a IRQ conflict, because of the ACPI management. Dont ask further questions! ;)
The key however is to turn off acpi in the grub bootmanager config file.

1. open /boot/grub/menu.lst
2. go to the line with the kernel entry and add this:  acpi=force pci=noacpi 

Now your LAN Connection should work

---

### Post by tnilsson on 2005-11-07
Hello,
I have the same problem with a Thinkpad 600X together with
a D-Link DFE-690TXD (uses the same realtek chipset).

Everything seems to work, except that I do not get any IP address from
the DHCP server. Actually my DHCP server do assign an IP address to my thinkpad, but the machines does not pick upp the address from the DHCP 
server.
I am soon giving up!!

I found the solution yesterday... the problem was bad TP cable! :-)
I can new report that D-Link DFE-690TXD works just perfect in Ubuntu Breezy.



:confused: 


[QUOTE=steigweis]To all, who can understand German: THE SOLUTION [http://www.ubuntuusers.de/viewtopic.php?...e+thinkpad+770x](http://www.ubuntuusers.de/viewtopic.php?...e+thinkpad+770x)

To all, who dont, here is the solution also: At least the Thinkpad 600E seems to have problems with the ACPI function. It looks like there is a IRQ conflict, because of the ACPI management. Dont ask further questions! ;)
The key however is to turn off acpi in the grub bootmanager config file.

1. open /boot/grub/menu.lst
2. go to the line with the kernel entry and add this:  acpi=force pci=noacpi 

Now your LAN Connection should work[/QUOTE]

---

### Post by Gaylord Focker on 2005-11-26
adding grub lines --> It worked for me.

But I think this should be corrected in 2.6.12 kernels.... More info: 
"rtl8139 (8139too) net problem in linux 2.6.10"
[http://www.ussg.iu.edu/hypermail/linux/kernel/0502.0/1404.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0502.0/1404.html)

---

