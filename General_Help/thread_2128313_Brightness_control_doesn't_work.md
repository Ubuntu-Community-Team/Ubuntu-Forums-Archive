---
title: "Brightness control doesn't work"
date: 2013-03-22
forum: General Help
---

### Post by sugarat on 2013-03-22
Hi All, 

 My brightness control isn't working and its burning my eyeballs out, - help!!

Many thanks

---

### Post by Toz on 2013-03-22
It would be helpful if you could provide some more information. At a base minimum, the make and model of your computer.

The following information would also be useful:

1. The video card and driver that you are using. You can get this information by opening a terminal window, entering in the following command and posting back the results:
```
sudo lspci -vnn | grep -A12 VGA
```

2. Any special kernel boot parameters that you may be using:
```
cat /proc/cmdline
```

That should do for starters.

---

### Post by sugarat on 2013-03-23
Hi Toz, 

 No problem.  The machine is a Dell XPS One 27. Here is the output:

```

00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller [8086:0152] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Dell Device [1028:054b]
	Flags: bus master, fast devsel, latency 0, IRQ 52
	Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915
	Kernel modules: i915

--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GT 640M] [10de:0fd2] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Device [1028:054b]
	Flags: fast devsel, IRQ 16
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	Expansion ROM at f7000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information: Len=14 <?>
	Capabilities: [100] Virtual Channel

```


```

BOOT_IMAGE=/boot/vmlinuz-3.5.0-26-generic root=UUID=c2c89696-4712-46fa-b99c-af9aac981777 ro quiet splash acpi_backlight=vendor vt.handoff=7

```

Many thanks

---

### Post by Toz on 2013-03-23
I notice that you posted in this [thread.]("http://ubuntuforums.org/showthread.php?t=2010298") Where you able to get bumblebee working? Can you switch between the 2 video cards?

> BOOT_IMAGE=/boot/vmlinuz-3.5.0-26-generic root=UUID=c2c89696-4712-46fa-b99c-af9aac981777 ro quiet splash acpi_backlight=vendor vt.handoff=7
You are using the **acpi_backlight=vendor** kernel parameter. Is it any better without that parameter? Have you tried any of the following parameters:
- **acpi_osi=**
- **acpi_osi=Linux acpi_backlight=vendor**
- **acpi_osi=\"!Windows 2012\"**

If neither of those parameters work, you could try directly manipulating the backlight interface to make it more bareable. Run the following command to identify the backlight interfaces and their current values:
```
cd /sys/class/backlight && grep . */*
```

---

### Post by a_m_100 on 2013-03-23
Hello, I've opened a thread for the same problem in the AB section a week ago, but got no answer. I hope it's ok to post here.

c/p from my thread:

I have a typical problem, I can't control the brightness. Neither through the hotkeys or the applet. I've tried the 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor" solution, but it didn't work. 


I'd appreciate if someone could walk me through or point me towards other solutions. 

System details:

Processor - Intel® Pentium(R) CPU P6200 @ 2.13GHz × 2 
Graphics - VESA: PARK
OS type - 32-bit"

video card info
```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series] [1002:68e0] (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:fd00]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d2200000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 5000 [size=256]
    Expansion ROM at d2240000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
```

and the kernel info

```
Kernel modules: fglrx, radeon
alan@alan-Satellite-L670:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-39-generic root=UUID=c322b63f-4b07-4a33-8889-fdf13bf063b6 ro pcie_aspm=force acpi_backlight=vendor
```

---

### Post by Toz on 2013-03-24
@a_m_100, I've replied in your original thread. It would be best to follow-up there for your issue.

---

### Post by cmcanulty on 2013-03-24
try installing xbacklight set the value you want & then have xbacklight as a startup app

---

### Post by matt_symes on 2013-03-24
Hi

Can you post the output of

```
ls /sys/class/backlight/
```

Kind regards

---

### Post by sugarat on 2013-03-24
I'll give those a try.  Silly question - when I edit /boot/grub/grub.cfg, - do those parameters actually need a dash in front of them, or is that just your formatting? :)

```

root@adam-PC:/boot/grub# cd /sys/class/backlight && grep . */*
intel_backlight/actual_brightness:4393
intel_backlight/bl_power:0
intel_backlight/brightness:4393
grep: intel_backlight/device: Is a directory
intel_backlight/max_brightness:4882
grep: intel_backlight/power: Is a directory
grep: intel_backlight/subsystem: Is a directory
intel_backlight/type:raw

```

TOZ - In answer to your question, I was not able to get bumblebee working, but have since reinstalled and on the whole, the desktop performance is acceptable on the Intel card. If I want to play games I'll boot into Windows.. 
Thank you

---

### Post by sugarat on 2013-03-24
xbacklight doesn't seem to make any difference. I've tried a number of parameters and the brightness isn't changing..

---

### Post by Toz on 2013-03-24
> **sugarat said:**
> I'll give those a try.  Silly question - when I edit /boot/grub/grub.cfg, - do those parameters actually need a dash in front of them, or is that just your formatting? :)
Its just formatting. Use the parameters without the leading dashes. But you shouldn't edit /boot/grub/grub.cfg, instead edit **/etc/default/grub**. Add the parameter to the line starting ***GRUB_CMDLINE_LINUX***, save the file, then run:
```
sudo update-grub
```

> 
```

root@adam-PC:/boot/grub# cd /sys/class/backlight && grep . */*
intel_backlight/actual_brightness:4393
intel_backlight/bl_power:0
intel_backlight/brightness:4393
grep: intel_backlight/device: Is a directory
intel_backlight/max_brightness:4882
grep: intel_backlight/power: Is a directory
grep: intel_backlight/subsystem: Is a directory
intel_backlight/type:raw

```

Does the following command decrease brightness?
```

echo 2400 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

---

### Post by sugarat on 2013-03-25
Ok.  I have tried booting with each of those parameters but there is no change. 

Similarly, echo 2400 | sudo tee /sys/class/backlight/intel_backlight/brightness is having no effect...

---

### Post by Toz on 2013-03-25
> **sugarat said:**
> Ok.  I have tried booting with each of those parameters but there is no change. 

Similarly, echo 2400 | sudo tee /sys/class/backlight/intel_backlight/brightness is having no effect...

Which kernel parameters were you using when you ran that command:
```
cat /proc/cmdline
```

Did you have the same one backlight interface?
```
cd /sys/class/backlight && grep . */*
```

---

### Post by sugarat on 2013-03-27
I'm not sure what I was running in the past. 

Right now I have the following:

```

adam@adam-PC:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-26-generic root=UUID=c2c89696-4712-46fa-b99c-af9aac981777 ro quiet splash "acpi_osi=!Windows 2012" acpi_backlight=vendor vt.handoff=7

```

And

```

adam@adam-PC:~$ cd /sys/class/backlight && grep . */*
intel_backlight/actual_brightness:4882
intel_backlight/bl_power:0
intel_backlight/brightness:4882
grep: intel_backlight/device: Is a directory
intel_backlight/max_brightness:4882
grep: intel_backlight/power: Is a directory
grep: intel_backlight/subsystem: Is a directory
intel_backlight/type:raw

```

---

### Post by Toz on 2013-03-27
Can you post back the contents of your /etc/default/grub file? Something doesn't look right in there.

---

### Post by sugarat on 2013-03-28
Sure,  here it is:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\" acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by Toz on 2013-03-28
Change this line:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\" acpi_backlight=vendor"
...to read:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\""
```
...then run:
```
sudo update-grub
```
...and reboot.

Once rebooted, post back again:
```
cat /proc/cmdline
```
...and
```
cd /sys/class/backlight && grep . */*
```
...and test brightness.

---

### Post by sugarat on 2013-03-29
Okay, I now have

```

BOOT_IMAGE=/boot/vmlinuz-3.5.0-26-generic root=UUID=c2c89696-4712-46fa-b99c-af9aac981777 ro quiet splash "acpi_osi=!Windows 2012" vt.handoff=7

```

```

intel_backlight/actual_brightness:3222
intel_backlight/bl_power:0
intel_backlight/brightness:3222
grep: intel_backlight/device: Is a directory
intel_backlight/max_brightness:4882
grep: intel_backlight/power: Is a directory
grep: intel_backlight/subsystem: Is a directory
intel_backlight/type:raw

```

---

### Post by Toz on 2013-03-29
Do the brightness keys work? 

Does the following command affect brightness:
```
echo 2400 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

Can I see your dmesg log?
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by sugarat on 2013-03-29
I don't have any brightness keys on my keyboard,  so I have loaded the 'Brightness and Lock' program from Settings.  When I drag the slider down from its default 'full on' position, the brightness does not change. 

Running the code you gave has no effect.

[http://paste.ubuntu.com/5658969/]("http://paste.ubuntu.com/5658969/")

---

### Post by Toz on 2013-03-29
Well, it doesn't seem that **acpi_osi=\"!Windows 2012\"** is helping. It seems that both this parameter and **acpi_backlight=vendor** expose the intel backlight interface, but we are unable to manipulate it. I wonder if the dual video cards are affecting this. I don't have any experience with dual video cards so I will have to step back (in case someone else can assist) and/or suggest you open a bug report for this issue.

---

