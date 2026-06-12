---
title: "Wireless LAN while booted under noapic"
date: 2007-02-25
forum: General Help
---

### Post by wersdaluv on 2007-02-25
In [this thread]("http://ubuntuforums.org/showthread.php?p=2123265#post2123265"), I have asked and figured out how to make Edgy run my USB Devices with my laptop.

The solution was to boot under noapic
> **Koybe said:**
> It deals with the way your kernel is handling you material. I'm not expert enough to tell you more.

What you have to do when grub menu loads :
- Hit 'e', it will show you the configuration for this booting option.
- Move to the kernel line with the arrows. It should look like this : 
kernel          /vmlinuz-2.6.15-28-k7 root=/dev/mapper/vghda6-lvslash ro vga=791 quiet splash
- Hit 'e' once again and add the option to this line :
kernel          /vmlinuz-2.6.15-28-k7 root=/dev/mapper/vghda6-lvslash ro vga=791 quiet splash noapic
- Hit 'enter', it should show you back the whole config with your modification for this boot only
- Hit 'b' to boot using this configuraiton

If it works then you can set it permanently to your /boot/grub/menu.lst but it's better this way for testing purpose.

Under noapic, my USB devices worked but for some reason, my Wireless LAN does not work under it. I tried to enable it in the "Network Settings" in Kubuntu, but it cannot be enabled.

In my laptop, like many other laptops, there is an LED indicator that lights up when the wireless LAN is enabled. It does not light up under noapic even if I pressed Fn+F1 which is supposed to turn it on.

What could make my wireless LAN work?

---

### Post by wersdaluv on 2007-02-25
When I tried to enable my wireless lan a while ago, a dialog box stated 
> Could not parse the XML output from the network configuration backend.

This is wierd. Right now, The Wireless LAN light is turned on but I still cannot enable it.

---

