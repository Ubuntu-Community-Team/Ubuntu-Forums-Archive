---
title: "System freeze at logout"
date: 2006-12-17
forum: General Help
---

### Post by pressman57 on 2006-12-17
I'm having a problem logging out of Xubuntu Edgy. Seemingly at random the system freezes immediately after the selection panel disappears. 

While searching the forums I've seen quite a few posts suggesting this may be due to the splash screen misbehaving, so I removed usplash with no luck. I also ran  sudo dpkg-reconfigure -phigh xserver-xorg to clean up xorg.confg. I saw numerous suggestions to edit /boot/grub/menu.lst to disable the splash screen but none were very specific about how to accomplish this. My menu.lst mentions it once here:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

I'd assume one would replace “quiet splash” with something, but with what?

My wife and I share the computer and Linux is the only operating system on it (we have Kubuntu Breezy on another hard drive that doesn't freeze at all), so we're constantly logging in and out. When the system freezes the only way to kill it is with the power button, and that can't be good for the filesystem.

Thanks for looking. Any help or hints would be greatly appreciated.

---

### Post by adaptr on 2006-12-17
Read your menu.lst file; it should have the "splash" option set at the end of the "kernel=" line.
Remove it.
Reboot.

---

### Post by pressman57 on 2006-12-17
Are you talking about this line?

kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb3 ro quiet splash

---

### Post by pressman57 on 2006-12-17
bump

---

