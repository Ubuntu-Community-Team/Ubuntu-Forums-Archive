---
title: "Asus laptop disables ASPM, even with pcie_aspm=force kernel parameter"
date: 2015-01-29
forum: General Help
---

### Post by chronniff on 2015-01-29
So I have a new asus n550jk laptop, and its been just tearing through the battery on ubuntu 14.10.  So when i looked into it, I noticed that the pcie active state power management was not being enabled.  Output for dmesg | grep -i aspm is

```
[    0.178495] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.231181] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.256808] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.572083] r8169 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control

```

when I use the pcie_aspm=force parameter it makes no difference, I get a similar output, and I can confirm with powertop that all my pcie devices are at 100% power usage. When i google I find a couple of bug reports for asrock boards, but none for mine.  This turns out to be a big deal, since my battery life kinda isn't the best to begin with, and it really is making linux not a viable solution for this laptop.  Am I just out of luck because asus doesn't feel like properly supporting linux, or is there some kind of workaround for this

---

### Post by techvish81 on 2015-01-30
have you tried TLP?

---

### Post by techvish81 on 2015-01-30
```
[COLOR=#000000][FONT=monospace]**sudo add-apt-repository ppa:linrunner/tlp**[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace][B]      sudo apt-get update
[/B][/FONT][/COLOR][COLOR=#000000][FONT=monospace]**      sudo apt-get install tlp tlp-rdw**[/FONT][/COLOR]          [COLOR=#000000][FONT=monospace][B]
[/B][/FONT][/COLOR]
```

put the code above in terminal to install tlp. it is right now the best power management tool for laptops . (in my opinion)

---

### Post by chronniff on 2015-01-30
yeah I have tlp intalled, the problem is that my bios is telling linux that ASPM is not supported, so even when tlp changes the settings so that the pcie components should be entering lower power states, they don't actually do it, and run at 100%. Powertop tells me that all those settings are set correctly:
```
> Bad           VM writeback timeout                                                                                   
   Bad           Autosuspend for USB device Touchscreen [ELAN]
   Good          Wireless Power Saving for interface wlan0
   Good          NMI watchdog should be turned off
   Good          Enable SATA link power Managmenet for host0
   Good          Enable SATA link power Managmenet for host1
   Good          Enable SATA link power Managmenet for host2
   Good          Enable SATA link power Managmenet for host3
   Good          Enable SATA link power Managmenet for host4
   Good          Enable Audio codec power management
   Good          Autosuspend for USB device EHCI Host Controller [usb1]
   Good          Autosuspend for USB device EHCI Host Controller [usb2]
   Good          Autosuspend for unknown USB device 1-1 (8087:8008)
   Good          Autosuspend for unknown USB device 2-1 (8087:8000)
   Good          Autosuspend for USB device USB2.0 UVC HD Webcam [Azurewave]
   Good          Autosuspend for USB device USB2.0-CRW [Generic]
   Good          Autosuspend for USB device xHCI Host Controller [usb3]
   Good          Autosuspend for USB device xHCI Host Controller [usb4]
   Good          Runtime PM for PCI Device Intel Corporation Wireless 7260
   Good          Runtime PM for PCI Device Intel Corporation 4th Gen Core Processor Integrated Graphics Controller
   Good          Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI
   Good          Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1
   Good          Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2
   Good          Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller
   Good          Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1
   Good          Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2
   Good          Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3
   Good          Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4
   Good          Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1
   Good          Runtime PM for PCI Device Intel Corporation HM86 Express LPC Controller
   Good          Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
   Good          Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller
   Good          Runtime PM for PCI Device NVIDIA Corporation GM107M [GeForce GTX 850M]
   Good          Runtime PM for PCI Device Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
   Good          Runtime PM for PCI Device Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
   Good          Runtime PM for PCI Device Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
   Good          Runtime PM for PCI Device Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
   Good          Wake-on-lan status for device wlan0
   Good          Wake-on-lan status for device eth0
   Good          Using 'ondemand' cpufreq governor

```

but it also tells me that my pcie devices are at 100% power usage:
```
           100.0%        Radio device: asus-nb-wmi
  5.33 W     15.6%        CPU misc
  3.08 W     30.0%        Display backlight
  3.08 W     30.0%        Display backlight
  2.58 W     24.7%        Display backlight
  1.68 W     15.6%        DRAM
  457 mW     15.6%        CPU core
  242 mW     94.9 ops/s   GPU core
    0 mW     94.9 ops/s   GPU misc
            100.0%        USB device: xHCI Host Controller
            100.0%        PCI Device: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller
            100.0%        PCI Device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
            100.0%        PCI Device: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI
            100.0%        PCI Device: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1
            100.0%        Radio device: iwlwifi
            100.0%        PCI Device: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4
            100.0%        PCI Device: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3
            100.0%        PCI Device: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
            100.0%        PCI Device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller
            100.0%        USB device: Touchscreen (ELAN)
            100.0%        PCI Device: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
            100.0%        PCI Device: Intel Corporation HM86 Express LPC Controller
            100.0%        PCI Device: Intel Corporation Wireless 7260
            100.0%        PCI Device: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1
            100.0%        PCI Device: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2
              2.5 pkts/s  Network interface: wlan0 (iwlwifi)
              0.0 pkts/s  Network interface: eth0 (r8169)
              0.0%        PCI Device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
              0.0%        PCI Device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
              0.0%        PCI Device: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2
              0.0%        USB device: usb-device-8087-8008
              0.0%        USB device: usb-device-8087-8000
              0.0%        Radio device: asus-nb-wmi
              0.0%        USB device: USB2.0 UVC HD Webcam (Azurewave)
              0.0%        PCI Device: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1
              0.0%        USB device: EHCI Host Controller
              0.0%        PCI Device: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller
              0.0%        PCI Device: NVIDIA Corporation GM107M [GeForce GTX 850M]

```
including my ethernet controller, which I don't even use

---

### Post by techvish81 on 2015-02-01
it could be a hardware specific problem.

---

### Post by chronniff on 2015-03-23
So I thought I would update my progress for anyone who is having battery issues with the same laptop. I eventually got all aspm devices to work using setpci, but tIhat didn't solve my battery issues.  

  As it turns out, I hadn't installed the nvidia driver, or more specifically the bbswitch module. Since its an optimus setup, and it turned out that my laptop was leaving the nvidia card on at all times. Now that I have the bbswitch module loading, it automatically switches off the geforce gtx 850m card and I'm idling at about half the power draw which is something like 10 or 11 watts. While that isn't excellent, this laptop isn't really built for the best battery life available, and I'm getting about as much battery as it does under windows.  I didn't think this was the issue at first because powertop told me that the nvidia card was drawing 0% power, but I guess I was reading its results wrong or something.
  
  It's definitely a relief not having to rely on windows to conserve battery life. Thanks to anyone who tried to help. Sometimes its the stupid things you overlook that turn out to be the culprit

---

