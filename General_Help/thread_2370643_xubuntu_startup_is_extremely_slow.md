---
title: "xubuntu startup is extremely slow"
date: 2017-09-05
forum: General Help
---

### Post by nshusa on 2017-09-05
hello,

i just got into linux and i really like xubuntu but it takes forever to startup. ive tried several other distros and none of them took more than 10 seconds to startup. mine for some reason takes like 2 minutes. if someone has an idea how to fix this would be much appreciated.

i ran the following command

```
systemd-analyze blame
```

prints

```
          9.434s NetworkManager-wait-online.service
          1.009s mysql.service
           607ms systemd-resolved.service
           363ms lightdm.service
           362ms dev-sda5.device
           362ms plymouth-quit-wait.service
           300ms apt-daily.service
           115ms systemd-timesyncd.service
            87ms bluetooth.service
            66ms systemd-rfkill.service
            55ms keyboard-setup.service
            55ms networking.service
            51ms snapd.service
            51ms upower.service
            50ms NetworkManager.service
            47ms ModemManager.service
            45ms grub-common.service
            40ms teamviewerd.service
            35ms accounts-daemon.service
            35ms systemd-udevd.service
            34ms systemd-udev-trigger.service
            28ms thermald.service
            26ms systemd-fsck@dev-disk-by\x2duuid-781C\x2dCC89.service
lines 1-23


```

i looked at this too

```

[COLOR=#111111][FONT=Consolas]dmesg[/FONT][/COLOR]

```

prints

[https://pastebin.com/UrVjtMUm](https://pastebin.com/UrVjtMUm)

looks like

```

[COLOR=#333333][FONT=Consolas][   92.583751] kauditd_printk_skb: 12 callbacks suppressed[/FONT][/COLOR]

```

is causing the slow startup but i have no idea why it does that.

---

### Post by BenginM on 2017-09-06
Hiya, welcome to the forums .

the audit_skb_entries in your logs are just the  last thing the kernel happened to log. it's the AppArmor processes before & after it that might be the cause ..

Also, any reason you've set profile as a kernel boot parameter option.. your dmesg shows:
```

[    0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-4.10.0-33-generic.efi.signed  root=UUID=0d30c9f3-bf2e-4a7a-9eb1-c04d570a2983 ro quiet splash profile  vt.handoff=7

```

Does the kernel boot faster if you boot without "profile"? remove it and try bootin' without it!

You may also wish to see a graphical detailed view of your system boot procedure you can generate a plot bootshart image. in a terminal run: $ systemd-analyze plot > bootchart.svg
the .svg file will be saved in your home directory and you can view it with an image viewer.

Also, how many cores your cpu has ! and are they all running ..
what's the output of $ sudo blkid , and $ cat /etc/fstab

---

### Post by Bucky Ball on 2017-09-06
Welcome. And also, which release of Xubuntu are you using? 16.04 LTS?

---

