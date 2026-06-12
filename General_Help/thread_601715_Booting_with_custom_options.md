---
title: "Booting with custom options"
date: 2007-11-03
forum: General Help
---

### Post by mivo on 2007-11-03
I've decided to spend some more time on my "Gutsy and new desktop" problems (in a nutshell, it does not like the Abit board).

I got Gutsy installed just fine, I only needed to boot the Live CD with the irqpoll option. After installation, I press ESC when the Grub countdown shows up, "e"dit the options, remove "quiet" and add "irqpoll", and press "b"oot. Now the machine completely restarts -- it does not boot with the custom options. With Fedora installed, or with the Gutsy Live CD, the system continues to boot after the custom options are added.

Should Grub behave the way it does on the Gutsy box? (restarting the system completely) If not, how can I prevent this? I think if I found a way to boot with custom kernel options, the rest of my problems could be solved quickly.

---

### Post by mivo on 2007-11-03
Fixed it!  Booted into the Live CD, mounted the drive with the "real" Ubuntu installation, edited /boot/grub/menu.lst (added nosplash and irqpoll to the kernel options), saved the file, rebooted -- and it worked. Downloading Nvidia drivers now, and perhaps now I will finally be able to use Ubuntu on the new machine as well. Phew! :)

Looking at the options in Grub's ESC menu still does not show the options I added, nor do I have a glue why it behaves the way it acts, but at least I got this to work. At last!

---

