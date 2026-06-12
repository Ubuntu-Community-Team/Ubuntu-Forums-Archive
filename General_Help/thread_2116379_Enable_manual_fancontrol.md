---
title: "Enable manual fancontrol"
date: 2013-02-15
forum: General Help
---

### Post by Cyril4133 on 2013-02-15
hi,

I am trying to find a way to slow down my fans, using my own /etc/fanconfig file. It seems however that I cannot get rid of the automatic fan configuration. What can I do? Thanks a lot!

```
sudo !!
sudo pwmconfig
# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0 is acpitz
   hwmon1/device is coretemp
   hwmon2/device is thinkpad
   hwmon3/device is nouveau

Found the following PWM controls:
   hwmon2/device/pwm1
hwmon2/device/pwm1 is currently setup for automatic speed control.
In general, automatic mode is preferred over manual mode, as
it is more efficient and it reacts faster. Are you sure that
you want to setup this output for manual control? (n) y
hwmon2/device/pwm1_enable stuck to 2
Manual control mode not supported, skipping hwmon2/device/pwm1.
There are no usable PWM outputs.

```

---

### Post by Impavidus on 2013-02-15
Have you checked the temperature of different components of your computer? Hot components are the most common cause for noisy fans. Turning the fans down can result in overheating and hardware failure. If your computer is noisier than whilst using a different OS, the problem is more likely in the trottling of the CPU or graphics chip than in fan control.

---

### Post by Yellow Pasque on 2013-02-16
[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)

---

### Post by Cyril4133 on 2013-02-16
I tried thinkfan but it seems that my CPU (a core i7 vpro) goes over 60°C several minutes after turning my T430 on.

I probably need to find a way to lower CPU usage. I have already tried to minimize energy through bios: no apparent difference, the fan go on and on.


```
Adapter: Virtual device
temp1:        +58.0°C  (crit = +104.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +59.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +58.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +56.0°C  (high = +87.0°C, crit = +105.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        3444 RPM

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +56.0°C  (high = +100.0°C, crit = +110.0°C)

```

---

### Post by Yellow Pasque on 2013-02-16
What other hardware is on it (output of lspci please)? Also, you may want to look at htop to see what's using the CPU.
```
lspci
sudo apt-get install htop
sudo htop
```

---

### Post by Cyril4133 on 2013-02-18
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
	Subsystem: Lenovo Device 21f3
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: f0000000-f10fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 21f4
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at f1400000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 6000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
	Subsystem: Lenovo Device 21f3
	Flags: bus master, medium devsel, latency 0, IRQ 42
	Memory at f3920000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Lenovo Device 21f3
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f3935000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:16.3 Serial controller: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller (rev 04) (prog-if 02 [16550])
	Subsystem: Lenovo Device 21f3
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 60b0 [size=8]
	Memory at f393c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: serial

00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
	Subsystem: Lenovo Device 21f3
	Flags: fast devsel, IRQ 20
	Memory at f3900000 (32-bit, non-prefetchable) [disabled] [size=128K]
	Memory at f393b000 (32-bit, non-prefetchable) [disabled] [size=4K]
	I/O ports at 6080 [disabled] [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 21f3
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f393a000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Lenovo Device 21f3
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at f3930000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f3100000-f38fffff
	Prefetchable memory behind bridge: 00000000f1800000-00000000f1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f3000000-f30fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=0b, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f2800000-f2ffffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f27fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 21f3
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f3939000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
	Subsystem: Lenovo Device 21f3
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
	Subsystem: Lenovo Device 21f3
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
	I/O ports at 60a8 [size=8]
	I/O ports at 60bc [size=4]
	I/O ports at 60a0 [size=8]
	I/O ports at 60b8 [size=4]
	I/O ports at 6060 [size=32]
	Memory at f3938000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
	Subsystem: Lenovo Device 21f3
	Flags: medium devsel, IRQ 7
	Memory at f3934000 (64-bit, non-prefetchable) [size=256]
	I/O ports at efa0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [Quadro NVS 5400M] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 21f4
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 5000 [size=128]
	Expansion ROM at f1000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb

02:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 07) (prog-if 01)
	Subsystem: Lenovo Device 21f3
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f3100000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f3000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

```

```
 2467 nbougach   20   0 30900  3092  1428 R  1.0  0.0  0:00.34 htop
 1519 nbougach   20   0  361M 16244 10652 S  1.0  0.2  0:01.19 tilda
 2120 nbougach   20   0  937M  140M 22184 S  1.0  1.8  0:06.36 /usr/lib/chromium-browser/chro
 1536 nbougach   20   0  625M 20676 14536 S  0.0  0.3  0:04.83 psensor
    1 root       20   0 24444  2460  1372 S  0.0  0.0  0:00.84 /sbin/init
  350 root       20   0 17232   636   460 S  0.0  0.0  0:00.20 upstart-udev-bridge --daemon
  353 root       20   0 21992  1820   836 S  0.0  0.0  0:00.15 /sbin/udevd --daemon
  531 messagebu  20   0 24852  2060   928 S  0.0  0.0  0:00.57 dbus-daemon --system --fork
  553 root       20   0 21776  1132   344 S  0.0  0.0  0:00.00 /sbin/udevd --daemon
  554 root       20   0 21776  1124   336 S  0.0  0.0  0:00.00 /sbin/udevd --daemon
  567 root       20   0 19300  1940  1628 S  0.0  0.0  0:00.01 /usr/sbin/bluetoothd
  591 syslog     20   0  243M  1624  1124 S  0.0  0.0  0:00.04 rsyslogd -c5
  598 syslog     20   0  243M  1624  1124 S  0.0  0.0  0:00.00 rsyslogd -c5
  599 syslog     20   0  243M  1624  1124 S  0.0  0.0  0:00.02 rsyslogd -c5
  583 syslog     20   0  243M  1624  1124 S  0.0  0.0  0:00.10 rsyslogd -c5
  593 avahi      20   0 32300  1744  1444 S  0.0  0.0  0:00.02 avahi-daemon: running [nbougach-ThinkPad-T430.local]
  596 avahi      20   0 32176   468   216 S  0.0  0.0  0:00.00 avahi-daemon: chroot helper
  616 root       20   0 69656  3072  2284 S  0.0  0.0  0:00.01 /usr/sbin/cupsd -F
  770 root       20   0 83304  3420  2580 S  0.0  0.0  0:00.10 /usr/sbin/modem-manager
  812 root       20   0  248M  7244  5476 S  0.0  0.1  0:00.00 NetworkManager
 1721 root       20   0  248M  7244  5476 S  0.0  0.1  0:00.00 NetworkManager
  802 root       20   0  248M  7244  5476 S  0.0  0.1  0:00.56 NetworkManager
  827 root       20   0  191M  4348  2936 S  0.0  0.1  0:00.11 /usr/lib/policykit-1/polkitd --no-debug
  817 root       20   0  191M  4348  2936 S  0.0  0.1  0:00.26 /usr/lib/policykit-1/polkitd --no-debug
  832 root       20   0 15188   636   416 S  0.0  0.0  0:00.00 upstart-socket-bridge --daemon
  966 root       20   0 19988   976   812 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty4
  973 root       20   0 19988   972   812 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty5
  982 root       20   0 19988   976   812 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty2
  983 root       20   0 19988   968   812 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty3
  985 root       20   0  4336   304   208 S  0.0  0.0  0:00.00 /usr/sbin/autolog
  988 root       20   0 19988   972   812 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty6
  993 root       20   0  4992  1332   564 S  0.0  0.0  0:00.00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
  995 daemon     20   0 16908   152     0 S  0.0  0.0  0:00.00 atd
  997 root       20   0 19112   988   756 S  0.0  0.0  0:00.00 cron

```

---

### Post by Yellow Pasque on 2013-02-18
```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])

01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [Quadro NVS 5400M] (rev a1) (prog-if 00 [VGA controller])
```

You have an Optimus/hybrid graphics setup. Follow the instructions here to disable the discrete GPU when it's not needed (it's probably generating a good bit of heat even when idle).  [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Calinou on 2013-02-18
>laptops
>cool hardware

Nope, your fans are running at that speed for a reason. Slowing them down will likely result in an overheat.

lol'd at the Quadro 5400M. :D

---

### Post by Yellow Pasque on 2013-02-18
> lol'd at the Quadro 5400M

Why? Some people want/need powerful GPU's in a mobile system, and there's nothing wrong with that as long as they shut off when not needed. That's what Optimus is all about, and it currently needs Bumblebee to make it work as intended (because of political differences between kernel devs and Nvidia).

---

### Post by Cyril4133 on 2013-02-19
Of course.

Thanks for your help

---

