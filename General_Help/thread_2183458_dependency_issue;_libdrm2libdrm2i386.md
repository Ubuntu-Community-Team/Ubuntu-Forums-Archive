---
title: "dependency issue; libdrm2/libdrm2:i386"
date: 2013-10-24
forum: General Help
---

### Post by RHogskin on 2013-10-24
[COLOR=#222222][FONT=Century Schoolbook L][SIZE=3]I am unable to install updates to my laptop running 12.04. I receive the following error message "[/SIZE][/FONT][/COLOR][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]ErrorBroken count >0"[/SIZE][/FONT][/COLOR]
[COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]
I have tried to disable all third party repositories, but it has not affected the problem.[/SIZE][/FONT][/COLOR]
[COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]Following recommendations in other threads, I have copied below the outputs of the following terminal commands:[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]sudo apt-get upgrade
[/SIZE][/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]sudo lshw -C display[/SIZE][/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]lspci | grep VGA[/SIZE][/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]lspci -nnk | grep -iA3 vga[/SIZE][/FONT][/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono]**[COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]Output:[/SIZE][/FONT][/COLOR]**[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]sudo apt-get upgrade[/SIZE][/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]#Readingpackage lists... DoneBuilding dependency tree [/FONT][/COLOR][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]Reading state information... Done[/FONT][/COLOR][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]You might want to run 'apt-get -f install' to correct these.[/FONT][/COLOR][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]The following packages have unmet dependencies:[/FONT][/COLOR][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]libdrm2: Breaks: libdrm2:i386 (!= 2.4.43-0ubuntu0.0.3) but2.4.43-0ubuntu0.0.2 is installed[/FONT][/COLOR][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]libdrm2:i386: Breaks: libdrm2 (!= 2.4.43-0ubuntu0.0.2) but 2.4.43-0ubuntu0.0.3 isinstalled[/FONT][/COLOR][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]E:Unmet dependencies. Try using -f.[/FONT][/COLOR]
**[COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]Output:[/SIZE][/FONT][/COLOR]**
[COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]sudolshw -C display[/SIZE][/FONT][/COLOR]
[COLOR=#212733] [FONT=Century Schoolbook L][SIZE=3]*-display              [/SIZE][/FONT][/COLOR]
[COLOR=#212733]      [FONT=Century Schoolbook L][SIZE=3]description:VGA compatible controller[/SIZE][/FONT][/COLOR]
[COLOR=#212733]      [FONT=Century Schoolbook L][SIZE=3]product:Core Processor Integrated Graphics Controller[/SIZE][/FONT][/COLOR]
[COLOR=#212733]      [FONT=Century Schoolbook L][SIZE=3]vendor:Intel Corporation[/SIZE][/FONT][/COLOR]
[COLOR=#212733]      [FONT=Century Schoolbook L][SIZE=3]physical id: 2[/SIZE][/FONT][/COLOR]
[COLOR=#212733]      [FONT=Century Schoolbook L][SIZE=3]businfo: pci@0000:00:02.0[/SIZE][/FONT][/COLOR]
[COLOR=#212733]      [FONT=Century Schoolbook L][SIZE=3]version:02[/SIZE][/FONT][/COLOR]
[COLOR=#212733]      [FONT=Century Schoolbook L][SIZE=3]width:64 bits[/SIZE][/FONT][/COLOR]
[COLOR=#212733]      [FONT=Century Schoolbook L][SIZE=3]clock:33MHz[/SIZE][/FONT][/COLOR]
[COLOR=#212733]      [FONT=Century Schoolbook L][SIZE=3]capabilities:msi pm vga_controller bus_master cap_list rom[/SIZE][/FONT][/COLOR]
[COLOR=#212733]      [FONT=Century Schoolbook L][SIZE=3]configuration:driver=i915 latency=0[/SIZE][/FONT][/COLOR]
[COLOR=#212733]      [FONT=Century Schoolbook L][SIZE=3]resources:irq:41 memory:d0000000-d03fffff memory:c0000000-cfffffffioport:3050(size=8)[/SIZE][/FONT][/COLOR]
**[COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]Output:[/SIZE][/FONT][/COLOR]**
[COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]lspci | grep VGA
[/SIZE][/FONT][/COLOR]
[COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)[/SIZE][/FONT][/COLOR]

**[COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]Output:[/SIZE][/FONT][/COLOR]**
[COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]lspci -nnk | grep -iA3 vga
[/SIZE][/FONT][/COLOR]
[COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
[/SIZE][/FONT][/COLOR]
[COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]    Subsystem: Acer Incorporated [ALI] Device [1025:0601]
[/SIZE][/FONT][/COLOR][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]    Kernel driver in use: i915
[/SIZE][/FONT][/COLOR][COLOR=#212733][FONT=Century Schoolbook L][SIZE=3]    Kernel modules: i915
[/SIZE][/FONT][/COLOR]

---

### Post by zombienerd1 on 2013-10-24
Try

sudo apt-get -f install 

This will fix broken packages and dependencies.

Disclaimer: I'm not a linux expert, but have seen similar issues fixed in this manner.

---

