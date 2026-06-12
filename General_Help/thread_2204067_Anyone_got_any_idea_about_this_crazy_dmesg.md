---
title: "Anyone got any idea about this crazy dmesg"
date: 2014-02-06
forum: General Help
---

### Post by kaspar_silas on 2014-02-06
I am getting the message 

AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0013 address=0x0000000000001000 flags=0x0000]

at a rate of about 300 a second. Does anyone have any idea what this is, how to fix it or hell even just suppress it so dmesg returns to a useful command again.

---

### Post by ajgreeny on 2014-02-06
What of your hardware is AMD, and do you get any other problems with it?

For example, if you have an AMD graphic card, do you get any errors showing in **~/.xsession-errors** file or in **/var/log/Xorg.0.log**?

---

### Post by kaspar_silas on 2014-02-06
Only my processor is AMD specifically a "FX 4100/ 3.6GHz Quad Core" one
I am not aware of any other problems thou I rarely press it to anywhere near it's limits. 

I do actually have errors in the xsession file:
```

openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd respawning too fast, stopped

```

there are no error just two warning lines in the Xorg.0.log namely:
[    29.995] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.143] (WW) "xmir" is not to be loaded by default. Skipping.

---

### Post by plucky on 2014-02-06
> AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0013 address=0x0000000000001000 flags=0x0000]


Post output for ```
lspci
``` in a terminal.

Looks like an I/O device is giving page faults.

Have you added any new devices?

---

### Post by kaspar_silas on 2014-02-06
Hhhmm oh dear. I haven't added new devices in a while but then again I don't know how long this dmesg issue has been going on for.

$ lspci 
gives:
```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: NVIDIA Corporation GT215 [GeForce GT 240] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
04:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)

```

I guess tomorrow I could start stripping off bits and rebooting until I find the sick part.

---

### Post by plucky on 2014-02-07
> [color=red]01:00.0[/color] VGA compatible controller: NVIDIA Corporation GT215 [GeForce GT 240] (rev a2)

That is the device at the address that is page faulting.Probably worth giving it a good clean and reseat.

Could also be the a driver problem

Can you post output for ```
sudo lshw -class display
```

Good Luck

---

### Post by kaspar_silas on 2014-02-07
Thanks that is really helpful and saves me unplugging too much. Am I right in assuming you got that from the "address=0x0000000000001000" part of dmesg and the 01:00.0 part of lspci?

I'll try and reseat the graphics card over the weekend (currently the whole thing is encapsulated in a baby-proof enclosure so I can't do it today). The graphics card is a bit old and it came from another computer so this could well be the issue.


The "lshw -class display" command hung for a second or two at PC (sysfs) then gave this:

```

  *-display               
       description: VGA compatible controller
       product: GT215 [GeForce GT 240]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:24 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fe000000-fe07ffff

```

---

### Post by plucky on 2014-02-07
> driver=nvidia

Under Additional drivers,you should check if you are using the recommended driver for your video card.

What version of Ubuntu are you using?

---

### Post by kaspar_silas on 2014-02-08
Hi, 

No luck with removing and reseating the graphics card. Still getting the errors.

I am using ubuntu 13.10

I looked under Additional Drivers and it informs me I am using the recommended NVIDIA binary Xorg nvidia-319 one. I tried using some others but it didn't seem to solve the dmesg issue.

---

### Post by plucky on 2014-02-09
Found this on [Launchpad Answers](https://answers.launchpad.net/ubuntu/+question/234598)

Doesn't seem to have an answer.

Could not find a bug report about this logged event.

You should report a bug on Launchpad and see if there is any response.

Good Luck

---

