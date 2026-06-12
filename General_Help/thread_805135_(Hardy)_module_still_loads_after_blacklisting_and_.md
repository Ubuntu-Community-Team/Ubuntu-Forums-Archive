---
title: "(Hardy) module still loads after blacklisting and removing .ko file"
date: 2008-05-23
forum: General Help
---

### Post by Lieter on 2008-05-23
Hi guys, this is(for me) a strange problem.

I compiled the r8168 driver from source cause it works better then the r8169 driver in the kernel.

Now i've put "blacklist r8169" in /etc/modprobe.d/blacklist but it still loads.

So next is removed the file /lib/modules/2.6.24-16-generic/kernel/drivers/net/r8169.ko

but the module still loads on boot and its conflicting with the(also loaded) r8168 driver.

When i rmmod them both and modprobe r8168 it works fine.. but i dont want the r8169 driver loading in the first place. So how can this be done?

Thank you guy in advance :)

---

### Post by Lieter on 2008-05-23
Ok, as it appeared the module r8169 was loaded in the initrd

issueing a sudo update-initramfs -u solved that for me :)

---

