---
title: "Need help in enabling AMDGPU on my system"
date: 2021-01-16
forum: General Help
---

### Post by deadlockfarell on 2021-01-16
Howdy all! i would like to enable AMDGPU instead of Radeon because i need dxvk to play LoL and other games that sadly require Dxvk,heres the output of ```
lspci -k 
```:
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h (Models 30h-3fh) Processor Root Complex
    Subsystem: Hewlett-Packard Company Family 16h (Models 30h-3fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] (rev 05)
    DeviceName: Onboard IGD
    Subsystem: Hewlett-Packard Company Mullins [Radeon R4/R5 Graphics]
    Kernel driver in use: radeon
    Kernel modules: radeon, amdgpu


```
Basically i think that my card is supported is an APU processor AMD A8-6410 so i would like to have some help in enabling AMDGPU on Ubuntu 20.04.1 64bits btw according Wikipedia the R5 330M that my laptop has is "Caribbean Islands" or "Sea Islands" dunno which i assume the 1st.
Here's a screenshot of the Ubuntu settings and Thanks in advance!:
[https://imgur.com/a/fkzGT7Z](https://imgur.com/a/fkzGT7Z)

---

### Post by #&amp;thj^% on 2021-01-16
Good Luck :) Link: [https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation](https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation)

---

### Post by deadflowr on 2021-01-16
Looks like you may need to try setting the module loading order.
See: [https://wiki.archlinux.org/index.php/AMDGPU#Enable_Southern_Islands_(SI)_and_Sea_Islands_(CIK)_support]("https://wiki.archlinux.org/index.php/AMDGPU#Enable_Southern_Islands_(SI)_and_Sea_Islands_(CIK)_support")
or something like that.

This is under the impression that Mullins fall under the Sea Islands family of gpus.
Based on The Xorg Radeonfeature wiki here: [https://www.x.org/wiki/RadeonFeature/]("https://www.x.org/wiki/RadeonFeature/")

---

### Post by deadlockfarell on 2021-01-17
Hello all OP here i followed both guides and successfully enabled AMDGPU i modified my grub file with the command ```
sudo gedit /etc/default/grub


```
and left it like this:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.si_support=0 radeon.cik_support=0 amdgpu.si_support=1 amdgpu.cik_support=1"
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
Then i executed the ```
sudo update-grub
```
but before rebooting i opened nautilus using the sudo command and modified the file "Modules" which in my case was in /etc/initramfs-tools to look like this:
```
# List of modules that you want to include in your initramfs.
# They will be loaded at boot time in the order below.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
radeon.si_support=0
amdgpu.si_support=1
```
and afterwards removed a blacklist file that was for some reason stopping AMDGPU (it's was AMDGPU_blacklist or something like that) from being used the file was in /etc/modprobe.d/ and created a file named amdgpu.conf with this written:
```
options amdgpu si_support=1
```
This because my card is a Sea Islands and of course as final step i executed ```
sudo update-initramfs -u
``` and rebooted my laptop
now the output of ```
lspci -v | grep -i VGA -A 12
``` is
```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] (rev 05) (prog-if 00 [VGA controller])
    DeviceName: Onboard IGD
    Subsystem: Hewlett-Packard Company Mullins [Radeon R4/R5 Graphics]
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=8M]
    I/O ports at f000 [size=256]
    Memory at fea00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: amdgpu
    Kernel modules: radeon, amdgpu

```
¡Now i have Vulkan and i can use Dxvk so far so good all! thanks @deadflowr and 1fallen!
Btw no need of adding padoka or any bleeding edge repos for drivers (that broke my system :lolflag:)
¡Cheers!

---

