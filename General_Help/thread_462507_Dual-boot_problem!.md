---
title: "Dual-boot problem!"
date: 2007-06-02
forum: General Help
---

### Post by Erky on 2007-06-02
I recently installed Ubuntu via Wubi and it would not work. After I changed the X server settings, I restarted and when I got to the Ubuntu boot screen it froze and gave me the following:

"BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)

/bin/shi can't access tty; job control turned off"

Then, I tried to reboot in windows, and as soon as I got to the boot-up screen, it gave me a blue screen of death with and UNMOUNTABLE_BOOT_LOAD error.

Please help! This is urgent!

---

### Post by Azakus on 2007-06-02
You saw GRUB load right?
Grab an Ubuntu cd and run it as a live cd.
Then paste the output of your /boot/grub/menu.lst file.

---

### Post by michaelzap on 2007-06-02
I'm a Linux noob also, but thet quickest way that I know to get back into XP is to boot off of your Windows CD, choose Repair at the first menu, and then type fixmbr at the command prompt. That should get you back to normal as far as Windows goes (I'm assuming you're using XP; if not, search for a similar method for your OS). As long as you didn't mess up the partition table or something like that, your system and files should all be fine.

---

