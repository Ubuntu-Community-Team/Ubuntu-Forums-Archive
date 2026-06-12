---
title: "'Input/output error' on serial port"
date: 2013-12-29
forum: General Help
---

### Post by hadrien15 on 2013-12-29
Hello,

The objective is to calibrate my monitor (connected via VGA) with the colorimeter X-Rite Colormunki Display connected via usb.
The device is recognized :
```
$ lsusb 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 003 Device 005: ID 0765:5020 X-Rite, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2c01 Sunplus Innovation Technology Inc. 
```

but when I run the program (Argyll) I get the following error message:
```
dispcal -r 
dispcal: Error - tcgetattr failed with 'Input/output error' on serial port '/dev/ttyS0'
```

my environment: 
Sony Vaio SVE14A2C5E
Ubuntu 12.04 (precise) 64-bit
Kernel Linux 3.5.0-44-generic
GNOME 3.4.2

Some weeks ago, I had windows 8 on this laptop without problem with the calibrator and Argyll.
I spent my last days reading the numerous topics about it without success.  
 

 I show you the outputs of some command lines:
 

 ```
$ lspci -v                          
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
    Subsystem: Sony Corporation Device 9095
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device 9095
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Sony Corporation Device 9095
    Flags: bus master, medium devsel, latency 0, IRQ 40
    Memory at f7e00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Sony Corporation Device 9095
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f7e1a000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Sony Corporation Device 9095
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7e18000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Sony Corporation Device 9095
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f7e10000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: f7d00000-f7dfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: f7c00000-f7cfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Sony Corporation Device 9095
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7e17000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
    Subsystem: Sony Corporation Device 9095
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Sony Corporation Device 9095
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f060 [size=32]
    Memory at f7e16000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Sony Corporation Device 9095
    Flags: medium devsel, IRQ 4
    Memory at f7e15000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]
    Kernel modules: i2c-i801

01:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7d00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

02:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 07)
    Subsystem: Sony Corporation Device 9095
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7c01000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

02:00.1 System peripheral: Ricoh Co Ltd Device e232 (rev 04)
    Subsystem: Sony Corporation Device 9095
    Flags: bus master, fast devsel, latency 0, IRQ 4
    Memory at f7c00000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
    Subsystem: Sony Corporation Device 9095
    Flags: bus master, fast devsel, latency 0, IRQ 41
    I/O ports at e000 [size=256]
    Memory at f0004000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169
VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01
            Status:    NegoPending- InProgress-
    Capabilities: [160 v1] Device Serial Number 01-00-00-00-68-4c-e0-00
    Kernel driver in use: r8169
    Kernel modules: r8169
```
 ```
$ dmesg | grep usb  
 [ 1.282660] ACPI: bus type usb registered  
 [ 1.282674] usbcore: registered new interface driver usbfs  
 [ 1.282681] usbcore: registered new interface driver hub  
 [ 1.282697] usbcore: registered new device driver usb  
 [ 1.362543] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002  
 [ 1.362545] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1  
 [ 1.362547] usb usb1: Product: EHCI Host Controller  
 [ 1.362549] usb usb1: Manufacturer: Linux 3.5.0-44-generic ehci_hcd  
 [ 1.362550] usb usb1: SerialNumber: 0000:00:1a.0  
 [ 1.378508] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002  
 [ 1.378511] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1  
 [ 1.378514] usb usb2: Product: EHCI Host Controller  
 [ 1.378527] usb usb2: Manufacturer: Linux 3.5.0-44-generic ehci_hcd  
 [ 1.378528] usb usb2: SerialNumber: 0000:00:1d.0  
 [ 1.378887] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002  
 [ 1.378889] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1  
 [ 1.378891] usb usb3: Product: xHCI Host Controller  
 [ 1.378892] usb usb3: Manufacturer: Linux 3.5.0-44-generic xhci_hcd  
 [ 1.378894] usb usb3: SerialNumber: 0000:00:14.0  
 [ 1.379044] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003  
 [ 1.379046] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1  
 [ 1.379047] usb usb4: Product: xHCI Host Controller  
 [ 1.379049] usb usb4: Manufacturer: Linux 3.5.0-44-generic xhci_hcd  
 [ 1.379050] usb usb4: SerialNumber: 0000:00:14.0  
 [ 1.379235] usbcore: registered new interface driver libusual  
 [ 1.674231] usb 1-1: new high-speed USB device number 2 using ehci_hcd  
 [ 1.806413] usb 1-1: New USB device found, idVendor=8087, idProduct=0024  
 [ 1.806421] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0  
 [ 1.917974] usb 2-1: new high-speed USB device number 2 using ehci_hcd  
 [ 2.050270] usb 2-1: New USB device found, idVendor=8087, idProduct=0024  
 [ 2.050278] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0  
 [ 2.217597] usb 3-2: new low-speed USB device number 2 using xhci_hcd  
 [ 2.237791] usb 3-2: New USB device found, idVendor=046d, idProduct=c05a  
 [ 2.237799] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0  
 [ 2.237803] usb 3-2: Product: USB Optical Mouse  
 [ 2.237806] usb 3-2: Manufacturer: Logitech  
 [ 2.238084] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes  
 [ 2.241896] usbcore: registered new interface driver usbhid  
 [ 2.241898] usbhid: USB HID core driver  
 [ 2.243331] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input3  
 [ 2.243515] hid-generic 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:14.0-2/input0  
 [ 2.309748] usb 1-1.3: new high-speed USB device number 3 using ehci_hcd  
 [ 2.726801] usb 1-1.3: New USB device found, idVendor=1bcf, idProduct=2c01  
 [ 2.726809] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0  
 [ 2.726813] usb 1-1.3: Product: USB2.0 Camera  
 [ 2.726816] usb 1-1.3: Manufacturer: 93010G000-289-G29R8DG  
 [ 3.016963] usb 2-1.5: new full-speed USB device number 3 using ehci_hcd  
 [ 3.111383] usb 2-1.5: New USB device found, idVendor=0765, idProduct=5020  
 [ 3.111391] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0  
 [ 3.111394] usb 2-1.5: Product: ColorMunki Display  
 [ 3.111398] usb 2-1.5: Manufacturer: X-Rite, Inc.  
 [ 3.113082] hid-generic 0003:0765:5020.0002: hiddev0,hidraw1: USB HID v1.11 Device [X-Rite, Inc. ColorMunki Display] on usb-0000:00:1d.0-1.5/input0  
 [ 14.806093] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input7 
 [ 14.806205] usbcore: registered new interface driver uvcvideo 
```
 ```
$ dmesg | grep tty  
 [ 0.000000] console [tty0] enabled  
 [ 1.390157] tty ttyS15: hash matches 
```
 

 ```
$ cat /proc/devices | grep tty  
 4 tty  
 4 ttyS  
 5 /dev/tty  
 5 ttyprintk 
```


 

 ```
 $ dmesg | egrep -i 'serial|ttys' [ 1:25AM]  
 [ 1.346939] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled  
 [ 1.362695] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1  
 [ 1.362701] usb usb1: SerialNumber: 0000:00:1a.0  
 [ 1.378661] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1  
 [ 1.378677] usb usb2: SerialNumber: 0000:00:1d.0  
 [ 1.379037] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1  
 [ 1.379041] usb usb3: SerialNumber: 0000:00:14.0  
 [ 1.379194] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1  
 [ 1.379199] usb usb4: SerialNumber: 0000:00:14.0  
 [ 1.806585] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0  
 [ 2.050317] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0  
 [ 2.235979] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0  
 [ 2.421802] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0  
 [ 2.914224] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
```
 

 ```
$ setserial -g /dev/ttyS*  
 /dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4  
 /dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3  
 /dev/ttyS10, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS11, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS12, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS13, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS14, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS15, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS16, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS17, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS18, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS19, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4  
 /dev/ttyS20, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS21, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS22, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS23, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS24, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS25, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS26, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS27, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS28, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS29, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3  
 /dev/ttyS30, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS31, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS4, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS5, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS6, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS7, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS8, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS9, UART: unknown, Port: 0x0000, IRQ: 0 
```
 

 

 ```
 statserial /dev/ttyS1  
 statserial: TIOCMGET failed: Input/output error
```
 

 The problem seems to come from the UART: unknown. So I tried to do:
 

 ```
 $ sudo setserial /dev/ttyS0 uart 16550A 
```
 then
 ```
$ setserial -g /dev/ttyS* [12:21PM]  
 /dev/ttyS0: No such device 
 /dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3  
 /dev/ttyS10, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS11, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS12, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS13, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS14, UART: unknown, Port: 0x0000, IRQ: 0  
 ... 
```
 

 ```
$ sudo more /proc/tty/driver/serial [12:22PM]  
 serinfo:1.0 driver revision:  
 0: uart:16550A port:000003F8 irq:4 tx:0 rx:0 CTS|DSR|CD|RI  
 1: uart:unknown port:000002F8 irq:3  
 2: uart:unknown port:000003E8 irq:4  
 3: uart:unknown port:000002E8 irq:3  
 4: uart:unknown port:00000000 irq:0  
 ... 
```
 

 

 After a reboot UART is unknown again.  
 

 ```
 $ setserial -g /dev/ttyS*  
 /dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4  
 /dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3  
 /dev/ttyS10, UART: unknown, Port: 0x0000, IRQ: 0  
 /dev/ttyS11, UART: unknown, Port: 0x0000, IRQ: 0  
 ... 
```
 

 If I create a file /etc/udev/rules.d/60-serial.rules with:  
 KERNEL=="ttyS0", MODE="0666"
 after each reboot, UART is kept 16550A but  
 ```
$ setserial -g /dev/ttyS*  
 /dev/ttyS0: No such device 
```
 and the device is still not working.
 

 The command below changes apparently nothing.  
 ```
 $ sudo setserial /dev/ttyS4 autoconfig
```
 

 

 I also tried  
 ```
$ sudo minicom -s 
```
 In the Serial port setup menu I get:  
 | A - Serial Device : /dev/tty8  
 | B - Lockfile Location : /var/lock  
 | C - Callin Program :  
 | D - Callout Program :  
 | E - Bps/Par/Bits : 115200 8N1  
 | F - Hardware Flow Control : Yes  
 | G - Software Flow Control : No  
 

 I changed tty8 by ttyS0 but it changes nothing
 In some discussions the users where modifying some files system, but as I do not understand well what they are doing and if it is appropriate to my case, I prefer to stop here and wait for your advises.  
 

 Thank you very much for you help.

---

### Post by steeldriver on 2013-12-29
I don't have any experience with these devices but the most likely issue would seem to be that it's not actually connecting on /dev/ttyS0 surely? 

AFAIK real-time udev messages go to /var/log/syslog rather than /var/log/dmesg, so I'd suggest running

```
tail -f /var/log/syslog
```

in a terminal and then plugging the device in - you should see exactly what tty file it is attaching to - if it's connecting via /dev/tty**USB***n* for example but the software insists on using /dev/tty**S***n* then it may be a question of providing a udev rule to create the desired symlink

---

### Post by hadrien15 on 2013-12-29
Thanks for your help. 
here the output, I added the symbols (----) when I plugged the device. 

```

$ tail -f /var/log/syslog           
Dec 29 18:20:26 hadrien-SVE14A2C5E kernel: [ 6396.492822] usb 2-1.5: USB disconnect, device number 4
Dec 29 18:23:37 hadrien-SVE14A2C5E kernel: [ 6587.344468] type=1400 audit(1388352217.424:34): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1116 comm="cupsd" pid=1116 comm="cupsd" capability=36  capname="block_suspend"
Dec 29 18:24:20 hadrien-SVE14A2C5E wpa_supplicant[2299]: WPA: Group rekeying completed with c4:3d:c7:c8:5b:6c [GTK=CCMP]
Dec 29 18:34:20 hadrien-SVE14A2C5E wpa_supplicant[2299]: WPA: Group rekeying completed with c4:3d:c7:c8:5b:6c [GTK=CCMP]
Dec 29 18:44:20 hadrien-SVE14A2C5E wpa_supplicant[2299]: WPA: Group rekeying completed with c4:3d:c7:c8:5b:6c [GTK=CCMP]
Dec 29 18:54:20 hadrien-SVE14A2C5E wpa_supplicant[2299]: WPA: Group rekeying completed with c4:3d:c7:c8:5b:6c [GTK=CCMP]
Dec 29 19:02:01 hadrien-SVE14A2C5E CRON[7259]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Dec 29 19:04:20 hadrien-SVE14A2C5E wpa_supplicant[2299]: WPA: Group rekeying completed with c4:3d:c7:c8:5b:6c [GTK=CCMP]
Dec 29 19:14:20 hadrien-SVE14A2C5E wpa_supplicant[2299]: WPA: Group rekeying completed with c4:3d:c7:c8:5b:6c [GTK=CCMP]
Dec 29 19:17:01 hadrien-SVE14A2C5E CRON[8418]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
----------------
Dec 29 19:23:56 hadrien-SVE14A2C5E kernel: [10202.473277] usb 2-1.5: new full-speed USB device number 5 using ehci_hcd
Dec 29 19:23:56 hadrien-SVE14A2C5E kernel: [10202.568040] usb 2-1.5: New USB device found, idVendor=0765, idProduct=5020
Dec 29 19:23:56 hadrien-SVE14A2C5E kernel: [10202.568048] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec 29 19:23:56 hadrien-SVE14A2C5E kernel: [10202.568052] usb 2-1.5: Product: ColorMunki Display
Dec 29 19:23:56 hadrien-SVE14A2C5E kernel: [10202.568055] usb 2-1.5: Manufacturer: X-Rite, Inc.
Dec 29 19:23:56 hadrien-SVE14A2C5E kernel: [10202.570435] hid-generic 0003:0765:5020.0004: hiddev0,hidraw1: USB HID v1.11 Device [X-Rite, Inc. ColorMunki Display] on usb-0000:00:1d.0-1.5/input0
   
```

But I do not see where the ttyUSB connection is indicated. 
Moreover, if I do 
```

$ ls -l /dev/tty*                   [ 8:04PM]
crw-rw-rw- 1 root tty     5,  0 Dec 29 19:35 /dev/tty
crw--w---- 1 root tty     4,  0 Dec 29 16:33 /dev/tty0
crw-rw---- 1 root tty     4,  1 Dec 29 16:34 /dev/tty1
crw--w---- 1 root tty     4, 10 Dec 29 16:33 /dev/tty10
crw--w---- 1 root tty     4, 11 Dec 29 16:33 /dev/tty11
crw--w---- 1 root tty     4, 12 Dec 29 16:33 /dev/tty12
crw--w---- 1 root tty     4, 13 Dec 29 16:33 /dev/tty13
crw--w---- 1 root tty     4, 14 Dec 29 16:33 /dev/tty14
crw--w---- 1 root tty     4, 15 Dec 29 16:33 /dev/tty15
crw--w---- 1 root tty     4, 16 Dec 29 16:33 /dev/tty16
crw--w---- 1 root tty     4, 17 Dec 29 16:33 /dev/tty17
crw--w---- 1 root tty     4, 18 Dec 29 16:33 /dev/tty18
crw--w---- 1 root tty     4, 19 Dec 29 16:33 /dev/tty19
crw-rw---- 1 root tty     4,  2 Dec 29 16:34 /dev/tty2
crw--w---- 1 root tty     4, 20 Dec 29 16:33 /dev/tty20
crw--w---- 1 root tty     4, 21 Dec 29 16:33 /dev/tty21
crw--w---- 1 root tty     4, 22 Dec 29 16:33 /dev/tty22
crw--w---- 1 root tty     4, 23 Dec 29 16:33 /dev/tty23
crw--w---- 1 root tty     4, 24 Dec 29 16:33 /dev/tty24
crw--w---- 1 root tty     4, 25 Dec 29 16:33 /dev/tty25
crw--w---- 1 root tty     4, 26 Dec 29 16:33 /dev/tty26
crw--w---- 1 root tty     4, 27 Dec 29 16:33 /dev/tty27
crw--w---- 1 root tty     4, 28 Dec 29 16:33 /dev/tty28
crw--w---- 1 root tty     4, 29 Dec 29 16:33 /dev/tty29
crw-rw---- 1 root tty     4,  3 Dec 29 16:34 /dev/tty3
crw--w---- 1 root tty     4, 30 Dec 29 16:33 /dev/tty30
crw--w---- 1 root tty     4, 31 Dec 29 16:33 /dev/tty31
crw--w---- 1 root tty     4, 32 Dec 29 16:33 /dev/tty32
crw--w---- 1 root tty     4, 33 Dec 29 16:33 /dev/tty33
crw--w---- 1 root tty     4, 34 Dec 29 16:33 /dev/tty34
crw--w---- 1 root tty     4, 35 Dec 29 16:33 /dev/tty35
crw--w---- 1 root tty     4, 36 Dec 29 16:33 /dev/tty36
crw--w---- 1 root tty     4, 37 Dec 29 16:33 /dev/tty37
crw--w---- 1 root tty     4, 38 Dec 29 16:33 /dev/tty38
crw--w---- 1 root tty     4, 39 Dec 29 16:33 /dev/tty39
crw-rw---- 1 root tty     4,  4 Dec 29 16:34 /dev/tty4
crw--w---- 1 root tty     4, 40 Dec 29 16:33 /dev/tty40
crw--w---- 1 root tty     4, 41 Dec 29 16:33 /dev/tty41
crw--w---- 1 root tty     4, 42 Dec 29 16:33 /dev/tty42
crw--w---- 1 root tty     4, 43 Dec 29 16:33 /dev/tty43
crw--w---- 1 root tty     4, 44 Dec 29 16:33 /dev/tty44
crw--w---- 1 root tty     4, 45 Dec 29 16:33 /dev/tty45
crw--w---- 1 root tty     4, 46 Dec 29 16:33 /dev/tty46
crw--w---- 1 root tty     4, 47 Dec 29 16:33 /dev/tty47
crw--w---- 1 root tty     4, 48 Dec 29 16:33 /dev/tty48
crw--w---- 1 root tty     4, 49 Dec 29 16:33 /dev/tty49
crw-rw---- 1 root tty     4,  5 Dec 29 16:34 /dev/tty5
crw--w---- 1 root tty     4, 50 Dec 29 16:33 /dev/tty50
crw--w---- 1 root tty     4, 51 Dec 29 16:33 /dev/tty51
crw--w---- 1 root tty     4, 52 Dec 29 16:33 /dev/tty52
crw--w---- 1 root tty     4, 53 Dec 29 16:33 /dev/tty53
crw--w---- 1 root tty     4, 54 Dec 29 16:33 /dev/tty54
crw--w---- 1 root tty     4, 55 Dec 29 16:33 /dev/tty55
crw--w---- 1 root tty     4, 56 Dec 29 16:33 /dev/tty56
crw--w---- 1 root tty     4, 57 Dec 29 16:33 /dev/tty57
crw--w---- 1 root tty     4, 58 Dec 29 16:33 /dev/tty58
crw--w---- 1 root tty     4, 59 Dec 29 16:33 /dev/tty59
crw-rw---- 1 root tty     4,  6 Dec 29 16:34 /dev/tty6
crw--w---- 1 root tty     4, 60 Dec 29 16:33 /dev/tty60
crw--w---- 1 root tty     4, 61 Dec 29 16:33 /dev/tty61
crw--w---- 1 root tty     4, 62 Dec 29 16:33 /dev/tty62
crw--w---- 1 root tty     4, 63 Dec 29 16:33 /dev/tty63
crw--w---- 1 root tty     4,  7 Dec 29 16:34 /dev/tty7
crw--w---- 1 root tty     4,  8 Dec 29 16:33 /dev/tty8
crw--w---- 1 root tty     4,  9 Dec 29 16:33 /dev/tty9
crw------- 1 root root    5,  3 Dec 29 16:33 /dev/ttyprintk
crw-rw-rw- 1 root dialout 4, 64 Dec 29 16:33 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 Dec 29 16:33 /dev/ttyS1
crw-rw---- 1 root dialout 4, 74 Dec 29 16:33 /dev/ttyS10
crw-rw---- 1 root dialout 4, 75 Dec 29 16:33 /dev/ttyS11
crw-rw---- 1 root dialout 4, 76 Dec 29 16:33 /dev/ttyS12
crw-rw---- 1 root dialout 4, 77 Dec 29 16:33 /dev/ttyS13
crw-rw---- 1 root dialout 4, 78 Dec 29 16:33 /dev/ttyS14
crw-rw---- 1 root dialout 4, 79 Dec 29 16:33 /dev/ttyS15
crw-rw---- 1 root dialout 4, 80 Dec 29 16:33 /dev/ttyS16
crw-rw---- 1 root dialout 4, 81 Dec 29 16:33 /dev/ttyS17
crw-rw---- 1 root dialout 4, 82 Dec 29 16:33 /dev/ttyS18
crw-rw---- 1 root dialout 4, 83 Dec 29 16:33 /dev/ttyS19
crw-rw---- 1 root dialout 4, 66 Dec 29 16:33 /dev/ttyS2
crw-rw---- 1 root dialout 4, 84 Dec 29 16:33 /dev/ttyS20
crw-rw---- 1 root dialout 4, 85 Dec 29 16:33 /dev/ttyS21
crw-rw---- 1 root dialout 4, 86 Dec 29 16:33 /dev/ttyS22
crw-rw---- 1 root dialout 4, 87 Dec 29 16:33 /dev/ttyS23
crw-rw---- 1 root dialout 4, 88 Dec 29 16:33 /dev/ttyS24
crw-rw---- 1 root dialout 4, 89 Dec 29 16:33 /dev/ttyS25
crw-rw---- 1 root dialout 4, 90 Dec 29 16:33 /dev/ttyS26
crw-rw---- 1 root dialout 4, 91 Dec 29 16:33 /dev/ttyS27
crw-rw---- 1 root dialout 4, 92 Dec 29 16:33 /dev/ttyS28
crw-rw---- 1 root dialout 4, 93 Dec 29 16:33 /dev/ttyS29
crw-rw---- 1 root dialout 4, 67 Dec 29 16:33 /dev/ttyS3
crw-rw---- 1 root dialout 4, 94 Dec 29 16:33 /dev/ttyS30
crw-rw---- 1 root dialout 4, 95 Dec 29 16:33 /dev/ttyS31
crw-rw---- 1 root dialout 4, 68 Dec 29 16:33 /dev/ttyS4
crw-rw---- 1 root dialout 4, 69 Dec 29 16:33 /dev/ttyS5
crw-rw---- 1 root dialout 4, 70 Dec 29 16:33 /dev/ttyS6
crw-rw---- 1 root dialout 4, 71 Dec 29 16:33 /dev/ttyS7
crw-rw---- 1 root dialout 4, 72 Dec 29 16:33 /dev/ttyS8
crw-rw---- 1 root dialout 4, 73 Dec 29 16:33 /dev/ttyS9
  	 	 	 	   
```
  
there is no ttyUSB :confused:

---

### Post by steeldriver on 2013-12-29
In that case you likely need a udev rule to even recognize the device - I dug up this page on the argyllcms.com website which looks promising - it says it's for Ubuntu 10.10 but unless you can find a newer version it may be your best bet

[http://www.argyllcms.com/doc/Installing_Linux.html#udev1](http://www.argyllcms.com/doc/Installing_Linux.html#udev1)

There are instructions for creating the file and for adding yourself to the plugdev group (which may not be necessary, but won't do any harm)

---

### Post by hadrien15 on 2013-12-30
I followed the instructions, I copy / past the 55-Argyll.rules gave the right permissions and added myself to the plugdev group. 
As proposed I checked whether the instrument is being recognized by running **ls -l -R /dev/bus/usb** without     and then with the instrument plugged in.

```
$ ls -l -R /dev/bus/usb             [10:51AM]
/dev/bus/usb:
total 0
drwxr-xr-x 2 root root 100 Dec 30 09:28 001
drwxr-xr-x 2 root root  80 Dec 30 09:28 002
drwxr-xr-x 2 root root  80 Dec 30 10:52 003
drwxr-xr-x 2 root root  80 Dec 30 09:28 004

/dev/bus/usb/001:
total 0
crw-rw-r-- 1 root root 189, 0 Dec 30 09:28 001
crw-rw-r-- 1 root root 189, 1 Dec 30 09:28 002
crw-rw-r-- 1 root root 189, 2 Dec 30 09:28 003

/dev/bus/usb/002:
total 0
crw-rw-r-- 1 root root 189, 128 Dec 30 09:28 001
crw-rw-r-- 1 root root 189, 129 Dec 30 09:28 002

/dev/bus/usb/003:
total 0
crw-rw-r-- 1 root root 189, 256 Dec 30 09:28 001
crw-rw-r-- 1 root root 189, 258 Dec 30 09:28 003

/dev/bus/usb/004:
total 0
crw-rw-r-- 1 root root 189, 384 Dec 30 09:28 001
crw-rw-r-- 1 root root 189, 385 Dec 30 09:28 002


$ ls -l -R /dev/bus/usb             [10:52AM]
/dev/bus/usb:
total 0
drwxr-xr-x 2 root root 100 Dec 30 09:28 001
drwxr-xr-x 2 root root  80 Dec 30 09:28 002
drwxr-xr-x 2 root root 100 Dec 30 10:52 003
drwxr-xr-x 2 root root  80 Dec 30 09:28 004

/dev/bus/usb/001:
total 0
crw-rw-r-- 1 root root 189, 0 Dec 30 09:28 001
crw-rw-r-- 1 root root 189, 1 Dec 30 09:28 002
crw-rw-r-- 1 root root 189, 2 Dec 30 09:28 003

/dev/bus/usb/002:
total 0
crw-rw-r-- 1 root root 189, 128 Dec 30 09:28 001
crw-rw-r-- 1 root root 189, 129 Dec 30 09:28 002

/dev/bus/usb/003:
total 0
crw-rw-r-- 1 root root 189, 256 Dec 30 09:28 001
crw-rw-r-- 1 root root 189, 258 Dec 30 09:28 003
crw-rw-r-- 1 root root 189, 260 Dec 30 10:52 005

/dev/bus/usb/004:
total 0
crw-rw-r-- 1 root root 189, 384 Dec 30 09:28 001
crw-rw-r-- 1 root root 189, 385 Dec 30 09:28 002

```

It means that the device is located at /dev/bus/usb/003 isn't it?
As they propose on the link, I ran spotread to test whether the device is accessible:
```
$ spotread -c
Read Print Spot values, Version 1.3.3
Author: Graeme W. Gill, licensed under the GPL Version 2 or later
usage: spotread [-options] [logfile]
 -v                   Verbose mode
 -s                   Print spectrum for each reading
 -S                   Plot spectrum for each reading
 -c listno            Set communication port from the following list (default 1)
    1 = '/dev/ttyS1'
    2 = '/dev/ttyS10'
    3 = '/dev/ttyS11'
    4 = '/dev/ttyS12'
    5 = '/dev/ttyS13'
    6 = '/dev/ttyS14'
    7 = '/dev/ttyS15'
    8 = '/dev/ttyS16'
    9 = '/dev/ttyS17'
    10 = '/dev/ttyS18'
    11 = '/dev/ttyS19'
    12 = '/dev/ttyS2'
    13 = '/dev/ttyS20'
    14 = '/dev/ttyS21'
    15 = '/dev/ttyS22'
    16 = '/dev/ttyS23'
    17 = '/dev/ttyS24'
    18 = '/dev/ttyS25'
    19 = '/dev/ttyS26'
    20 = '/dev/ttyS27'
    21 = '/dev/ttyS28'
    22 = '/dev/ttyS29'
    23 = '/dev/ttyS3'
    24 = '/dev/ttyS30'
    25 = '/dev/ttyS31'
    26 = '/dev/ttyS4'
    27 = '/dev/ttyS5'
    28 = '/dev/ttyS6'
    29 = '/dev/ttyS7'
    30 = '/dev/ttyS8'
    31 = '/dev/ttyS9'
 -t                   Use transmission measurement mode
 -d                   Use display measurement mode (absolute results)
 -db                  Use display white brightness relative measurement mode
 -dw                  Use display white relative measurement mode
 -p                   Use projector measurement mode (absolute results)
 -pb                  Use projector white brightness relative measurement mode
 -pw                  Use projector white relative measurement mode
 -e                   Use emissive measurement mode (absolute results)
 -a                   Use ambient measurement mode (absolute results)
 -f                   Use ambient flash measurement mode (absolute results)
 -y c|l               Display type (if emissive), c = CRT, l = LCD
 -i illum             Choose illuminant for print/transparency spectral data:
                      A, C, D50 (def.), D65, F5, F8, F10 or file.sp
 -o observ            Choose CIE Observer for spectral data:
                      1931_2 (def), 1964_10, S&B 1955_2, shaw, J&V 1978_2
                      (Choose FWA during operation)
 -F filter            Set filter configuration (if aplicable):
    n                  None
    p                  Polarising filter
    6                  D65
    u                  U.V. Cut
 -E extrafilterfile   Apply extra filter compensation file
 -x                   Display Yxy instead of Lab
 -h                   Display LCh instead of Lab
 -T                   Display correlated color temperatures and CRI
 -N                   Disable auto calibration of instrument
 -H                   Start in high resolution spectrum mode (if available)
 -X file.ccmx         Apply Colorimeter Correction Matrix
 -W n|h|x             Override serial port flow control: n = none, h = HW, x = Xon/Xoff
 -D [level]           Print debug diagnostics to stderr
 logfile              Optional file to save reading results as text


```

Again, the /dev/ttyUSB* are not listed. I tried spotread -c /dev/bus/usb/003 but it gave the same message. 
I did a reboot, but the device is still not accessible. 
Hadrien

---

### Post by steeldriver on 2013-12-30
Let's try to get some info from the udev subsystem

```
udevadm info -q all -p /sys/bus/usb/devices/usb[COLOR=#0000ff]**3**[/COLOR]/[COLOR=#0000ff]**3**[/COLOR]-[COLOR=#0000ff]**5**[/COLOR]
```

where the #s correspond to the lsusb listing i.e.

```

$ lsusb 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
[B]Bus [COLOR=#0000ff]003[/COLOR] Device [COLOR=#0000ff]005[/COLOR]: ID 0765:5020 X-Rite, Inc. 
[/B]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2c01 Sunplus Innovation Technology Inc.

```

(if you may have moved the device to a different USB slot, then rerun lsusb to check)

---

### Post by hadrien15 on 2013-12-30
now the device is located at **Bus 003 Device 009: ID 0765:5020 X-Rite, Inc.**
```
$ udevadm info -q all -p /sys/bus/usb/devices/usb3/3-9
device path not found

```
It works neither for the colorimaeter nor the mouse (bus 3 device 3)
```
$ udevadm info -q all -p /sys/bus/usb/devices/usb3/3-3
device path not found

```


for 3-1 it recognize the device 009 :confused:
```
udevadm info -q all -p /sys/bus/usb/devices/usb3/3-1
P: /bus/usb/devices/usb3/3-1
N: bus/usb/003/009
E: BUSNUM=003
E: DEVNAME=/dev/bus/usb/003/009
E: DEVNUM=009
E: DEVPATH=/bus/usb/devices/usb3/3-1
E: DEVTYPE=usb_device
E: DRIVER=usb
E: GCM_COLORIMETER=1
E: GCM_KIND=i1-display3
E: GCM_TYPE_DISPLAY=1
E: GCM_TYPE_PROJECTOR=1
E: GCM_TYPE_SPOT=1
E: ID_BUS=usb
E: ID_MODEL=ColorMunki_Display
E: ID_MODEL_ENC=ColorMunki\x20Display
E: ID_MODEL_ID=5020
E: ID_REVISION=0001
E: ID_SERIAL=X-Rite__Inc._ColorMunki_Display
E: ID_USB_INTERFACES=:030000:
E: ID_VENDOR=X-Rite__Inc.
E: ID_VENDOR_ENC=X-Rite\x2c\x20Inc.
E: ID_VENDOR_FROM_DATABASE=X-Rite, Inc.
E: ID_VENDOR_ID=0765
E: MAJOR=189
E: MINOR=264
E: PRODUCT=765/5020/1
E: SUBSYSTEM=usb
E: TYPE=0/0/0
E: UDEV_LOG=3
E: USEC_INITIALIZED=19593066502


```

---

### Post by steeldriver on 2013-12-30
Apologies - I was wrong about the meaning / mapping of the udevadm path, it looks like the right way to map the lsusb 'Bus' and 'Device' numbers is via the udevadm **name** rather than **path** e.g.

```
udevadm info -q all **-n** **/dev/bus/usb/003/009**
```

Every time I try to use udevadm I find myself relearning everything

I'm not sure where to go from here - you could try running 'udevadm monitor' while you plug the device in, but I don't know if that will give any more information. Maybe it's a driver issue? Does 'lsmod | grep serial' show anything (e.g. a dependent 3rd part module loaded by the device)?

---

### Post by hadrien15 on 2013-12-30
no problem, thanks to you I am learning too.
except the first line, the output is the same.
```
$ udevadm info -q all -n /dev/bus/usb/003/009
P: /devices/pci0000:00/0000:00:14.0/usb3/3-1
N: bus/usb/003/009
E: BUSNUM=003
E: DEVNAME=/dev/bus/usb/003/009
E: DEVNUM=009
E: DEVPATH=/devices/pci0000:00/0000:00:14.0/usb3/3-1
E: DEVTYPE=usb_device
E: DRIVER=usb
E: GCM_COLORIMETER=1
E: GCM_KIND=i1-display3
E: GCM_TYPE_DISPLAY=1
E: GCM_TYPE_PROJECTOR=1
E: GCM_TYPE_SPOT=1
E: ID_BUS=usb
E: ID_MODEL=ColorMunki_Display
E: ID_MODEL_ENC=ColorMunki\x20Display
E: ID_MODEL_ID=5020
E: ID_REVISION=0001
E: ID_SERIAL=X-Rite__Inc._ColorMunki_Display
E: ID_USB_INTERFACES=:030000:
E: ID_VENDOR=X-Rite__Inc.
E: ID_VENDOR_ENC=X-Rite\x2c\x20Inc.
E: ID_VENDOR_FROM_DATABASE=X-Rite, Inc.
E: ID_VENDOR_ID=0765
E: MAJOR=189
E: MINOR=264
E: PRODUCT=765/5020/1
E: SUBSYSTEM=usb
E: TYPE=0/0/0
E: UDEV_LOG=3
E: USEC_INITIALIZED=19593066502


```

```
$ udevadm monitor                   [ 5:13PM]
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[27953.459055] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1 (usb)
KERNEL[27953.459371] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0 (usb)
KERNEL[27953.459919] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/0003:0765:5020.0009 (hid)
KERNEL[27953.460284] add      /class/usb (class)
KERNEL[27953.460486] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/usb/hiddev0 (usb)
UDEV  [27953.460884] add      /class/usb (class)
KERNEL[27953.460942] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/0003:0765:5020.0009/hidraw/hidraw0 (hidraw)
UDEV  [27953.466998] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1 (usb)
UDEV  [27953.472944] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0 (usb)
UDEV  [27953.473843] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/0003:0765:5020.0009 (hid)
UDEV  [27953.474610] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/0003:0765:5020.0009/hidraw/hidraw0 (hidraw)
UDEV  [27953.479536] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/usb/hiddev0 (usb)

```

unfortunatly **lsmod | grep serial **returns nothing.
Find below the **lsmod** output in case it may help. 
```
$ lsmod                             [ 5:20PM]
Module                  Size  Used by
bnep                   18240  2 
rfcomm                 47562  0 
bluetooth             212001  10 bnep,rfcomm
parport_pc             32867  0 
ppdev                  17114  0 
binfmt_misc            17541  1 
snd_hda_codec_hdmi     32532  1 
snd_hda_codec_realtek    79855  1 
xt_hl                  12522  6 
ip6t_rt                12559  3 
nf_conntrack_ipv6      14107  7 
nf_defrag_ipv6         13413  1 nf_conntrack_ipv6
ipt_REJECT             12577  1 
xt_LOG                 17454  9 
xt_limit               12712  12 
xt_tcpudp              12604  26 
xt_addrtype            12714  4 
snd_hda_intel          34063  5 
xt_state               12579  14 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               78117  0 
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
joydev                 17694  0 
ip6table_filter        12816  1 
ip6_tables             27686  2 ip6t_rt,ip6table_filter
videobuf2_core         33025  1 uvcvideo
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
nf_conntrack_netbios_ns    12666  0 
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
arc4                   12530  2 
nf_conntrack_broadcast    12590  1 nf_conntrack_netbios_ns
nf_nat_ftp             12705  0 
iwlwifi               399614  0 
mac80211              555272  1 iwlwifi
snd                    83674  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15092  1 snd
nf_nat                 25646  1 nf_nat_ftp
nf_conntrack_ipv4      14531  9 nf_nat
nf_defrag_ipv4         12730  1 nf_conntrack_ipv4
nf_conntrack_ftp       13453  1 nf_nat_ftp
nf_conntrack           83300  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12811  1 
ip_tables              27474  1 iptable_filter
x_tables               29892  12 xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
videobuf2_memops       13405  1 videobuf2_vmalloc
i915                  539443  3 
lpc_ich                17145  0 
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
ghash_clmulni_intel    13221  0 
aesni_intel            51134  3 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
drm_kms_helper         49259  1 i915
cfg80211              208382  2 iwlwifi,mac80211
sony_laptop            54939  0 
mei                    41410  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
drm                   290595  4 i915,drm_kms_helper
psmouse               102541  0 
i2c_algo_bit           13565  1 i915
microcode              23030  0 
serio_raw              13216  0 
lp                     17800  0 
mac_hid                13254  0 
video                  19653  1 i915
parport                46563  3 parport_pc,ppdev,lp
usb_storage            49288  0 
hid_generic            12541  0 
usbhid                 47259  0 
hid                   105241  2 hid_generic,usbhid
ahci                   25869  2 
libahci                27338  1 ahci
sdhci_pci              18749  0 
sdhci                  33145  1 sdhci_pci
r8169                  62741  0 

```

---

### Post by steeldriver on 2013-12-30
I wonder if the version of the argyll package in the repository just doesn't support this device? I noticed on this page --> [http://www.argyllcms.com/doc/ChangesSummary.html](http://www.argyllcms.com/doc/ChangesSummary.html) that it says "Added support for X-Rite ColorMunki Smile colorimeter" under **[V1.4.0 -> V1.5.0] 1st March 2013** but the version I pulled on my 12.04 box says

```

$ apt-cache policy argyll
argyll:
  Installed: 1.3.3-0ubuntu4
  Candidate: 1.3.3-0ubuntu4

```

---

### Post by hadrien15 on 2013-12-30
Oh, this clue was the good one!  It finally works with the last version. 

My colorimeter (Colormunki display) was added in the version 1.3.4, the version in the repository is effectively the 1.3.3. 
In windows I was working with the last version (1.6.2) downloaded from Argyll website... it's why I firstly thought that the problem did not come from the Argyll executable files.  
Always check the version in the repositories, I'm still not used to do it. 

   Again thank you for your help, beside this simple solution I learned some useful commands.  
Hadrien

---

### Post by steeldriver on 2013-12-30
Happy to help! sorry to lead you round the houses first

---

