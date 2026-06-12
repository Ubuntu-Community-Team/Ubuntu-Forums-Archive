---
title: "Cannot change brightness of the screen Ubuntu 18.04 LST"
date: 2019-02-11
forum: General Help
---

### Post by rafaczd on 2019-02-11
I've installed Ubuntu Budgie alongside with Windows and Linux Mint on  my laptop a few months ago, but haven't been using it since then.  Today, as I crashed Mint, I decided to try out this system. But soon I  found out that I cannot control brightness of the screen. I dug through  all system setting but there is nothing like this, function keys at my  keyboard also don't work (but keys to controlling sound work just fine).

  I've tried installing nvidia drivers instead of those provided by xorgs.
  I've tried adding "acpi_backlight=vendor" to grub defaults for Linux.
  I've tried [this]("https://itsfoss.com/fix-brightness-ubuntu-1310/"),  but I don't have anything in my /sys/class/backlight/ folder. I also  don't have Graphics page in System Settings. However, I've tried  creating files in /usr/share/X11/xorg.conf.d/, but it resulted in GUI  not starting after logging out.
  I've tried installing xbacklight and using it, but it has no effect, it even doesn't show any error.
  I've tried creating some scripts, which was decribed in other posts  (sorry, I opened so many pages that I cannot find it) but it all also  failed, as it demands backlight drivers. It seems to me I don't have  them and I don't know how to obtain them.

  I would like to also mention that on Windows and Linux Mint there was no problem with light.
  I would be really grateful for help as my eyes hurt due to too bright light.

---

### Post by Autodave on 2019-02-11
Can you please give us some information on your laptop?

---

### Post by rafaczd on 2019-02-12
Of course :) 

Output of lshw -short

```
H/W path       Device      Class          Description
=====================================================
                           system         GL62 6QE (Default string)
/0                         bus            MS-16J5
/0/0                       memory         64KiB BIOS
/0/3d                      memory         128KiB L1 cache
/0/3e                      memory         128KiB L1 cache
/0/3f                      memory         1MiB L2 cache
/0/40                      memory         6MiB L3 cache
/0/41                      processor      Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz
/0/42                      memory         8GiB System Memory
/0/42/0                    memory         8GiB SODIMM DDR4 Synchronous 2133 MHz (0,5 ns)
/0/42/1                    memory         [empty]
/0/100                     bridge         Skylake Host Bridge/DRAM Registers
/0/100/1                   bridge         Skylake PCIe Controller (x16)
/0/100/1/0                 display        GM107M [GeForce GTX 950M]
/0/100/2                   display        HD Graphics 530
/0/100/14                  bus            Sunrise Point-H USB 3.0 xHCI Controller
/0/100/14/0    usb1        bus            xHCI Host Controller
/0/100/14/0/a              communication  Bluetooth wireless interface
/0/100/14/0/c              generic        USB2.0-CRW
/0/100/14/1    usb2        bus            xHCI Host Controller
/0/100/14.2                generic        Sunrise Point-H Thermal subsystem
/0/100/16                  communication  Sunrise Point-H CSME HECI #1
/0/100/17                  storage        Sunrise Point-H SATA Controller [AHCI mode]
/0/100/1c                  bridge         Sunrise Point-H PCI Express Root Port #1
/0/100/1c/0    wlp2s0      network        Wireless 3165
/0/100/1c.3                bridge         Sunrise Point-H PCI Express Root Port #4
/0/100/1c.3/0  enp3s0      network        QCA8171 Gigabit Ethernet
/0/100/1f                  bridge         Sunrise Point-H LPC Controller
/0/100/1f.2                memory         Memory controller
/0/100/1f.3                multimedia     Sunrise Point-H HD Audio
/0/100/1f.4                bus            Sunrise Point-H SMBus
/0/1           scsi3       storage        
/0/1/0.0.0     /dev/sda    disk           1TB WDC WD10JPVX-22J
/0/1/0.0.0/1   /dev/sda1   volume         449MiB Windows NTFS volume
/0/1/0.0.0/2   /dev/sda2   volume         99MiB Windows FAT volume
/0/1/0.0.0/3   /dev/sda3   volume         15MiB reserved partition
/0/1/0.0.0/4   /dev/sda4   volume         149GiB Windows NTFS volume
/0/1/0.0.0/5   /dev/sda5   volume         797MiB Windows NTFS volume
/0/1/0.0.0/6   /dev/sda6   volume         5119MiB Windows NTFS volume
/0/1/0.0.0/7   /dev/sda7   volume         976MiB Linux swap volume
/0/1/0.0.0/8   /dev/sda8   volume         190GiB EXT4 volume
/0/1/0.0.0/9   /dev/sda9   volume         103GiB EXT4 volume
/0/1/0.0.0/a   /dev/sda10  volume         119GiB Windows NTFS volume
/0/1/0.0.0/b   /dev/sda11  volume         160GiB Windows NTFS volume
/0/1/0.0.0/c   /dev/sda12  volume         95GiB EXT4 volume
/0/1/0.0.0/d   /dev/sda13  volume         55GiB EXT4 volume
/1                         power          To Be Filled By O.E.M.
```

Output of uname -a
```
Linux DRLT 4.15.0-45-generic #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

I also tried to look at nvidia-settings, but I just received errors
```


ERROR: NVIDIA driver is not loaded


ERROR: Unable to load info from any available system


(nvidia-settings:6447): GLib-GObject-CRITICAL **: 11:57:52.161: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 11:57:52.164: PRIME: No offloading required. Abort
** Message: 11:57:52.164: PRIME: is it supported? no


```


Tell me if I should give you any more info.

---

