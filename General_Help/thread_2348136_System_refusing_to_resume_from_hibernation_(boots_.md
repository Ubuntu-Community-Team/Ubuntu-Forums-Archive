---
title: "System refusing to resume from hibernation (boots cold)"
date: 2017-01-01
forum: General Help
---

### Post by tsjswimmer on 2017-01-01
[CENTER][COLOR=#3F005E]

[LIST]
[*]
[*]
[/LIST]
[/COLOR]

[COLOR=#3F005E]
  [/COLOR][/CENTER]

Hello, fellow Ubuntu users!

I can't seem to get my system to resume from hibernation for some reason. I'm running 16.04 x64, with systemd as my init system. My system will enter into hibernation just fine. However, when I reboot, the system boots cold, as if I had shutdown without hibernating. I have a fairly large swap partition, so I doubt that's the issue.

I've checked **/etc/initramfs-tools/conf.d/resume**, and found that the UUID is 100% correct, so I doubt that's the issue. I also have the same partition entered in **/etc/fstab**. Here's exactly what the file says:```
RESUME=UUID=4c49f8c3-1356-44b5-a641-8e66a534c6c1
```I've tried re-running update-initramfs to rebuild the image, but that didn't help at all. There's no resume argument in either **/boot/grub/grub.cfg**, or **/proc/cmdline**, so that can't be the problem.

IDK if it's relevant, but when I hibernate the machine, I usually do so with the **systemctl hibernate** command. [COLOR=#ff0000]Edit:[/COLOR] Immediately after submitting this post, I tested hibernation with pm-hibernate, and got the same results.

Any ideas?

PS: I recently re-installed Ubuntu from the Ubuntu-Minimal CD. Ubuntu-Minimal does not automatically install the nice **plymouth-theme-ubuntu-logo** package, so I decided to install it manually, and use it as my default splash screen. I don't think I had this problem before installing said package, so maybe that messed something up. Before installing the **plymouth-theme-ubuntu-logo** package, I accidentally installed (and subsequently removed) the **plymouth-theme-ubuntu-gnome-logo** and **plymouth-theme-ubuntu-gnome-text** packages (I guess I need to pay more attention next time).

---

