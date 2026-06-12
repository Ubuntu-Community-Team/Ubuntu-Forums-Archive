---
title: "Updated kernels not seen by Grub - I'm stuck on 5.19 despite 6.5 being installed"
date: 2024-01-12
forum: General Help
---

### Post by blackbird34 on 2024-01-12
Hi everyone. 

I have an issue with kernel updates: they install fine, but Grub does not seem to see them, and so they're not available to load on the next boot. I can't understand why. 

Basically, my laptop obstinately boots the 5.19 kernel, even though the latest 6.2 and 6.5 kernels are installed. I googled a bit and read through a few forum posts, but I didn't find a solution. 

```

nad@gandalf:~$ dpkg -l linux-image* | grep ii
ii  linux-image-5.15.0-91-generic          5.15.0-91.101        amd64        Signed kernel image generic
ii  linux-image-5.19.0-43-generic          5.19.0-43.44~22.04.1 amd64        Signed kernel image generic
ii  linux-image-6.2.0-39-generic           6.2.0-39.40~22.04.1  amd64        Signed kernel image generic
ii  linux-image-6.5.0-14-generic           6.5.0-14.14~22.04.1  amd64        Signed kernel image generic
ii  linux-image-generic                    5.15.0.91.88         amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-22.04          6.5.0.14.14~22.04.7  amd64        Generic Linux kernel image
nad@gandalf:~$ uname -r
5.19.0-43-generic
nad@gandalf:~$ sudo ls /boot/initrd.img-*
/boot/initrd.img-5.15.0-91-generic  /boot/initrd.img-6.2.0-39-generic
/boot/initrd.img-5.19.0-43-generic  /boot/initrd.img-6.5.0-14-generic
nad@gandalf:~$ 

```

```
nad@gandalf:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/99_breeze-grub.cfg'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found theme: /boot/grub/themes/breeze/theme.txt
Found linux image: /boot/vmlinuz-6.5.0-14-generic
Found initrd image: /boot/initrd.img-6.5.0-14-generic
Found linux image: /boot/vmlinuz-6.2.0-39-generic
Found initrd image: /boot/initrd.img-6.2.0-39-generic
Found linux image: /boot/vmlinuz-5.19.0-43-generic
Found initrd image: /boot/initrd.img-5.19.0-43-generic
Found linux image: /boot/vmlinuz-5.15.0-91-generic
Found initrd image: /boot/initrd.img-5.15.0-91-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
nad@gandalf:~$ 


```

I'm running KDE Neon 5.27.10 which is based on Ubuntu 22.04 LTS.

---

### Post by jeremy31 on 2024-01-12
What results for ```
sudo parted -l
```

---

### Post by blackbird34 on 2024-01-12
There's only one system installed on this laptop. 

```
[FONT=monospace][COLOR=#54ff54]**nad@gandalf**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo parted -l [/COLOR]
[sudo] password for nad:  
Model: OM3PDP3-AD NVMe KDI 512GB (nvme) 
Disk /dev/nvme0n1: 512GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End    Size    File system     Name  Flags 
 1      2097kB  317MB  315MB   fat32                 boot, esp 
 2      317MB   494GB  494GB   ext4            root 
 3      494GB   512GB  17,7GB  linux-swap(v1)        swap


[/FONT]
```

---

### Post by Doug S on 2024-01-12
Could you post the files: `/etc/default/grub' and `/etc/default/grub.d/99_breeze-grub.cfg' and `/etc/default/grub.d/init-select.cfg'

---

### Post by jeremy31 on 2024-01-12
I was going to say ```
sudo grub-install
```
Then reboot

---

### Post by blackbird34 on 2024-01-14
> **jeremy31 said:**
> I was going to say ```
sudo grub-install
```
Then reboot

Thanks. Just tried this, no difference, after rebooting I'm still on the 5.19 kernel. Only 5.19 and 5.15 showed up in the "advanced options" section of the Grub menu when I rebooted.

> **Doug S said:**
> Could you post the files: `/etc/default/grub' and  `/etc/default/grub.d/99_breeze-grub.cfg' and  `/etc/default/grub.d/init-select.cfg'

Yeah now you mention it the problem could be coming from `/etc/default/grub' (below). A while back i tried to get hibernation working (I'm not sure it ever did work, but in the end with KDE's session restore feature it doesn't matter). 

**Edit: **Should I remove the "resume" portion of  GRUB_CMDLINE_LINUX_DEFAULT ?

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash iommu=soft resume=UUID=e5084516-4a48-4aa8-9f51-5c36c8a7240c"
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash mem_sleep_default=deep"
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

`/etc/default/grub.d/99_breeze-grub.cfg' and  `/etc/default/grub.d/init-select.cfg' seem to be unmodified from defaults.

```
# Work around a bug in the obsolete init-select package which broke
# grub-mkconfig when init-select was removed but not purged.  This file does
# nothing and will be removed in a later release.
#
# See:
#   https://bugs.debian.org/858528
#   https://bugs.debian.org/863801

```

```
GRUB_THEME=/boot/grub/themes/breeze/theme.txt


```

---

### Post by blackbird34 on 2024-01-18
:(

---

### Post by BicyclerBoy on 2024-01-18
Need to see more info on the mountpoints for /boot & /boot/efi and then to discover the actual /boot folder that grub is using..

$ lsblk -o name,label,fstype,size,UUID,mountpoint

Please remove the snap loop spam.

---

### Post by MAFoElffen on 2024-01-19
To do what he suggested, that would be 
```

lsblk -e7 -o name,label,fstype,size,UUID,mountpoint

```
The "-e7" flag removes displaying the loop dev's.

How about this?
```

sudo mokutil --sb-stat

```

---

