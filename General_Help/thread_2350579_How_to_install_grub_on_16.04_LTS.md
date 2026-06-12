---
title: "How to install grub on 16.04 LTS"
date: 2017-01-25
forum: General Help
---

### Post by wbmpertdsbcglobal on 2017-01-25
Since I cannot get into grub while holding down the shift key when booting up, I apparently haven't grub installed.
Any help would be greatly appreciated.

---

### Post by ajgreeny on 2017-01-25
Is this a new machine using UEFI instead of BIOS?

If so, try repeat tapping of Esc when you power-on, though that may or may not work, depending on the current **fast-start** and **secure-boot** settings in your UEFI.

Can you boot into Ubuntu at present?  If you can boot the system you obviously do have grub installed; without it you would not get to the boot system for the whole OS.

---

### Post by wbmpertdsbcglobal on 2017-01-27
Yes, I can boot into Ubuntu. If this means I have grub installed then I am puzzled why I can't get into the recovery screen by holding down and/or tapping the shift and or esc keys.

---

### Post by oldfred on 2017-01-27
Is this an UEFI system?

UEFI has a fast boot setting that assumes your hardware and configuration has not changed and immediately jumps to booting system.
Usually then you do not have time to press any key before operating system is booting. Makes system faster in total boot time.

Some will boot normally if you cold boot. Or full power down, if laptop remove battery, and then hold power switch for 10 sec or so to totally drain all power.
Then reboot and press correct key(s) to get into UEFI or UEFI boot menu or grub menu.

---

### Post by wbmpertdsbcglobal on 2017-01-29
I do not have fast boot selected in bios.

Also, I do not have Windows installed. Only Ubuntu 14.04 LTS

And thank your for your help.

---

### Post by Impavidus on 2017-01-29
> **wbmpertdsbcglobal said:**
> Yes, I can boot into Ubuntu. If this means I have grub installed then I am puzzled why I can't get into the recovery screen by holding down and/or tapping the shift and or esc keys.

When not dual booting, the grub menu is by default invisible. Getting it by hitting shift or escape may be a little tricky, but you can make it visible by default. Modify /etc/default/grub (with root permissions) and then update grub:```

# Modify the file

sudo nano /etc/default/grub

# Apply the new configuration

sudo update-grub
```

I configured grub to display the menu for 3 seconds by setting:```
GRUB_TIMEOUT=3
```

Or do you have to get into recovery mode to reset your password? In that case, I think you can also use a live disk to unhide the menu. If I'm not mistaken, the default repair of Boot-Repair does that.

---

