---
title: "Firmware takes 1min to load"
date: 2024-09-19
forum: General Help
---

### Post by adrian-tres on 2024-09-19
Hi all, 

I've had this issue for a few months now and I eventually just accepted the pain of having to wait 1.5mins to boot up my computer. I feel like I'm loading windows sometimes. Until now, I put off this issue but I am now tired of it. I am on a Thinkpad P16.

So systemd-analyze shows: ```
Startup finished in 1min 8.319s (firmware) + 3.336s (loader) + 2.307s (kernel) + 14.119s (userspace) = 1min 28.083s 
graphical.target reached after 13.840s in userspace
```

And systemd-analyze blame shows:
```
12.090s plymouth-quit-wait.service
10.146s gpu-manager.service
 3.666s NetworkManager-wait-online.service
 1.159s docker.service
  749ms mysql.service
  692ms snapd.seeded.service
  661ms fwupd.service
  569ms snapd.service
  526ms tor@default.service
  460ms dev-nvme0n1p2.device
  452ms boot-efi.mount
  403ms tailscaled.service
  314ms freeradius.service
  291ms systemd-resolved.service
  265ms dev-loop23.device
  264ms dev-loop28.device
  263ms dev-loop32.device
  263ms dev-loop22.device
  263ms dev-loop40.device
  263ms dev-loop30.device
  263ms dev-loop39.device
  263ms dev-loop31.device
  262ms dev-loop36.device
  262ms dev-loop41.device
  262ms dev-loop35.device
  262ms dev-loop12.device
  262ms dev-loop27.device
  262ms dev-loop25.device
  262ms dev-loop24.device
  262ms dev-loop15.device
  262ms dev-loop16.device
  262ms dev-loop19.device
  262ms dev-loop21.device
  261ms dev-loop29.device
  261ms dev-loop14.device
  261ms dev-loop11.device
  261ms dev-loop13.device
  261ms dev-loop20.device
  261ms dev-loop34.device
  261ms dev-loop43.device
  261ms dev-loop42.device
  260ms dev-loop26.device
  258ms dev-loop33.device
  257ms dev-loop38.device
  256ms dev-loop37.device
  246ms dev-loop18.device
  246ms dev-loop17.device
  241ms dev-loop1.device
  241ms dev-loop2.device
  241ms dev-loop3.device
  240ms dev-loop4.device
  240ms dev-loop7.device
  240ms dev-loop6.device
  239ms dev-loop5.device
  239ms dev-loop0.device
  233ms dev-loop10.device
  213ms tlp.service
  203ms systemd-udev-trigger.service
  193ms dev-loop9.device
  180ms lm-sensors.service
  169ms accounts-daemon.service
  155ms networkd-dispatcher.service
```

Just now I upgraded to a different nvidia driver to see if maybe that would be the issue and it wasn't. I'm not sure where to go from here, so any thoughts/suggestions would be greatly appreciated

---

### Post by oldfred on 2024-09-19
UEFI systems have a fast boot setting. 
Often causes issues when users are changing configuration as fast boot assumes no changes. Or system is not scanned for what hardware you have and then written to drive for operating system.
If you turn fast boot on, you need to know how to get back into UEFI/BIOS.
Some work with grub entry or a systemd entry. Others require "cold" boot or full power down, so system scan is redone and you have just a few seconds to press correct key to get into UEFI/BIOS or UEFI one time boot key,

Check UEFI settings.

Also seen user without floppy drive and UEFI configured to look for floppy drive. Of course not found, but has to time out. 

Check UEFI settings.

---

