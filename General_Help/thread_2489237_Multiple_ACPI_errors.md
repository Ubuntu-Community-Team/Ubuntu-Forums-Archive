---
title: "Multiple ACPI errors"
date: 2023-07-23
forum: General Help
---

### Post by Autodave on 2023-07-23
Got my laptop out for the first time in a few months.  While booting, numerous ACPI errors were show on the screen.  The laptop did boot normally though and everything worked.  Got a box saying that 22.04 was available and I let it update.  Everything seemed to have updated OK, but still multiple ACPI errors.  I can find answers for those errors on Windows, but nothing in Ubuntu.  Any ideas what to look for?

---

### Post by MAFoElffen on 2023-07-24
What version where you on previously? Is your BIOS upgraded to latest?

Then try these:
> 
[h=3]Trouble Booting[/h] For detailed instructions regarding how to modify boot parameters see [DebuggingKernelBoot]("https://wiki.ubuntu.com/DebuggingKernelBoot"). 

[LIST=1]
[*]Try booting with the "acpi=off" kernel parameter 
[LIST]
[*]This will disable ACPI support.  If the error is the same with ACPI enabled and disabled, this may not be an ACPI issue. 
[/LIST]

[*]If "acpi=off" allows the system to boot, try to isolate the ACPI issue with the following boot parameters 
[LIST]
[*]Try booting with "acpi=ht" 
[LIST]
[*]This  disables all of ACPI except just enough to enable Hyper Threading.  If  acpi=off works and acpi=ht fails, then the issue is in the ACPI table  parsing code itself, or perhaps the SMP code.  
[/LIST]

[*]Try booting with "pci=noacpi" 
[LIST]
[*]This disables ACPI for IRQ routing and PCI scanning. 
[/LIST]

[*]Try booting with "acpi=noirq" 
[LIST]
[*]This disables ACPI for IRQ routing.  
[/LIST]

[*]Try booting with "pnpacpi=off" 
[LIST]
[*]This disables the ACPI component of the Linux Plug and Play code.  
[/LIST]

[*]Try booting with "noapic" 
[LIST]
[*]Disables the IO-APIC for IRQ routing or PCI scanning.  
[/LIST]

[*]Try booting with "nolapic" 
[LIST]
[*]Disables the local APIC. 
[/LIST]
[/LIST]
[/LIST]
 


---

### Post by ActionParsnip on 2023-07-24
Does the laptop have a make and model?

---

### Post by pantazi on 2023-07-24
This worked for me (post #4)

[https://linux.org/threads/acpi-error-after-installing-ubuntu-22-04.40993/](https://linux.org/threads/acpi-error-after-installing-ubuntu-22-04.40993/)

---

### Post by Autodave on 2023-07-25
I haven't powered it back up again to try any of these suggestions.  However, this machine had no errors at all.  Before updating it is when the errors started: worked fine, put away, errors next time powered on.  Everything still works great, just the errors.

---

### Post by MAFoElffen on 2023-07-25
If there were a way to take a picture of those errors with your phone when they flash by... Then please post those.

I know with recent Linux Kernels, some of my machines came up with BIOS types of error massages that turned out just being warnings or status messages. The kernel thinks that the BIOS should have certain capabilities, when in reality, they do not always have them (especially if on an older machine).

---

### Post by #&amp;thj^% on 2023-07-25
> **Autodave said:**
>   Everything still works great, just the errors.

The bugs/errors you are seeing are harmless. Apparently, because of Microsoft's market dominance, the faulty ACPI implementation from Microsoft has become the de facto industry standard. As a result, Linux and other non-Microsoft operating systems have to reverse engineer the faulty ACPI implementation from MS.
The kernel guys are working on a patch.
Also this one works for me on my Lenovo 540P
```
modprobe.blacklist=nouveau
```
You might be able to show more with:
```
sudo dmesg | grep ACPI
```
Just a few lines with the errors only.

---

### Post by pantazi on 2023-07-30
Solved Autodave?

---

### Post by Autodave on 2023-07-30
Not yet....I just haven't had the time to get back to it and try what has been suggested.  I promise to update this when I get to it!

---

### Post by Autodave on 2023-08-06
Hopefully there will be a pic attached to this reply......and the laptop is a Lenovo Ideapad 80TJ

---

### Post by Autodave on 2023-08-07
bump

---

### Post by Autodave on 2023-08-09
bump

---

### Post by #&amp;thj^% on 2023-08-09
From the Screen shot or photo, I see no problems, unless you can't login anymore.
Is that the case then?
```
[root@arch-me me]# echo 0x4 > /sys/module/acpi/parameters/debug_level
[root@arch-me me]# cat /sys/module/acpi/parameters/debug_layer
Description              	Hex        SET
ACPI_UTILITIES           	0x00000001 [ ]
ACPI_HARDWARE            	0x00000002 [ ]
ACPI_EVENTS              	0x00000004 [ ]
ACPI_TABLES              	0x00000008 [ ]
ACPI_NAMESPACE           	0x00000010 [ ]
ACPI_PARSER              	0x00000020 [ ]
ACPI_DISPATCHER          	0x00000040 [ ]
ACPI_EXECUTER            	0x00000080 [ ]
ACPI_RESOURCES           	0x00000100 [ ]
ACPI_CA_DEBUGGER         	0x00000200 [ ]
ACPI_OS_SERVICES         	0x00000400 [ ]
ACPI_CA_DISASSEMBLER     	0x00000800 [ ]
ACPI_COMPILER            	0x00001000 [ ]
ACPI_TOOLS               	0x00002000 [ ]
ACPI_ALL_DRIVERS         	0xFFFF0000 [ ]
--
debug_layer = 0x00000000 ( * = enabled)

```

---

### Post by Autodave on 2023-08-09
I can log-in and do everything.....no problem at all.  I just never ever saw this nonsense before and wondered why I all of a sudden get this: there are a few more lines that come up, but again, no probs.

---

### Post by #&amp;thj^% on 2023-08-09
> **Autodave said:**
> I can log-in and do everything.....no problem at all.  I just never ever saw this nonsense before and wondered why I all of a sudden get this: there are a few more lines that come up, but again, no probs.
Kernels are going through a bit of growing pains ATM no need to explain all that here.
I don't see them on this machine 
```
 Host: zfs-me Kernel: 6.2.0-26-generic arch: x86_64 bits: 64 Desktop: Xfce
    v: 4.18.1 Distro: Linux Lite 6.4 LTS
Machine:
  Type: Laptop System: LENOVO product: 82B5 v: Lenovo Legion 5 15ARH05
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN
    serial: <superuser required> UEFI: LENOVO v: EUCN37WW date: 04/14/2022

```
But I do on my X1 carbon, I'm guessing your on a lenovo machine, right?

---

### Post by Autodave on 2023-08-09
It is a Lenovo.

---

### Post by Holger_Gehrke on 2023-08-09
The errors in the screenshot have nothing to do with ACPI. The time stamps are all wrong. ACPI problems usually happen within the first second after boot and clearly state ACPI (I know since my ideapad has an AFAIK harmless ACPI problem and greets me with error messages about it every time I power it up). ACPI is normally concerned with stuff that is found on the mainboard, memory, buses, interrupt controllers, power, that kind of stuff.

The first line is just information about the file system on partition sdc5, state (clean), number of files and total number of inodes, number of used blocks and total number of blocks.
The next three lines are about bringing up the Bluetooth interface and complain about a missing firmware patch (search the internet for the filename given, download it and place it in the directory /usr/lib/firmware/brcm/).
The last three lines are about a failed i²c transfer regarding the graphics card. Seems NVidia uses i²c on some of their cards to do some kind of initialization of the GPU. Either your card doesn't do it that way (too old ? too new ?) or there is some kind of failure (bug ? broken hardware ? Since you say the system boots and works, I'd consider this message purely informational, too).

Holger

---

### Post by Autodave on 2023-08-09
That's the best I could do capturing it on my cell phone.  I will try and get a better pick of the ACPI errors....

---

### Post by pantazi on 2023-08-10
Did you try my suggestion in post #4?

---

### Post by Holger_Gehrke on 2023-08-10
ACPI errors normally end up in the kernel ring buffer. Take a look at 'sudo dmesg|less', the errors you see will probably be in there making screenshots unnecessary.

Holger

---

