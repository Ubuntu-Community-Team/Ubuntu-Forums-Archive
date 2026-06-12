---
title: "No splash screen"
date: 2017-03-13
forum: General Help
---

### Post by kaleem4 on 2017-03-13
Split off from [https://ubuntuforums.org/showthread.php?t=2331312](https://ubuntuforums.org/showthread.php?t=2331312)


[s]I have same Problem, as [/s]i am using ubuntu-gnome 16.4lts
i do not see Graphical boot up just only grey frame white blank screen since i fresh installed Gnome os 
 
can any one of you figure out and Help me please

```
kaleem@4:~$ uname -a
Linux ayat 4.4.0-66-generic #87-Ubuntu SMP Fri Mar 3 15:29:05 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
kaleem@4:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
```
```
kaleem@4:~$ lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07)
    Subsystem: Hewlett-Packard Company Skylake Integrated Graphics
    Kernel driver in use: i915_bpo
kaleem@4:~$ dpkg -l | grep fglrx*
kaleem@4:~$ lsmod | grep fglrx
kaleem@4:~$ 

```
sudo gedit /etc/default/grub
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
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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

**kaleem@4:~$** lspci -vnn | grep VGA -A 12
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Sky Lake Integrated Graphics [8086:1916] (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Skylake Integrated Graphics [103c:81ec]
    Flags: bus master, fast devsel, latency 0, IRQ 125
    Memory at b0000000 (64-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915_bpo
    Kernel modules: i915_bpo

00:04.0 Signal processing controller [1180]: Intel Corporation Skylake Processor Thermal Subsystem [8086:1903] (rev 08)
    Subsystem: Hewlett-Packard Company Skylake Processor Thermal Subsystem [103c:81ec]
**kaleem@4:~$** lspci -nnk | grep -i vga -A3 | grep 'in use'
    Kernel driver in use: i915_bpo
```
**kaleem@4:~$** sudo lshw -C display 
 ```
 *-display               
       description: VGA compatible controller
       product: Sky Lake Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:125 memory:b0000000-b0ffffff memory:a0000000-afffffff ioport:6000(size=64)
```
**kaleem@4:~$** cat /etc/default/grub
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
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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

HP i5 6200U, 1tb, 8gb ram,

---

### Post by vasa1 on 2017-03-13
I have moved your post from [No Splash Screen During Boot?]("https://ubuntuforums.org/showthread.php?t=2331312") to its own thread.

---

