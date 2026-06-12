---
title: "Logout splash screen missing!"
date: 2007-05-03
forum: General Help
---

### Post by keithk50 on 2007-05-03
Recently installed 7.04 (clean install) on my laptop.   The install went well and things seem to work okay in the more important areas but when I logout I don't get the boot down screen with the Ubuntu logo (as the login screen shows).   Instead it shows all the scripts for closing down.
The live CD did show the splash screen on logout.   This is not the most important question in the world of Ubuntu but can anyone help me get the splash screen to work?   Thanks.:)

---

### Post by bashologist on 2007-05-03
It's a kernel option in your /boot/grub/menu.lst. Try adding "splash" to the end of the kernel you use.

For example here's my menu.lst:
kernel		/boot/vmlinuz-2.6.18-4-k7 root=/dev/sdb4 ro noapic 

You would add "splash" to the end like this:
kernel		/boot/vmlinuz-2.6.18-4-k7 root=/dev/sdb4 ro noapic splash

---

### Post by kaamos on 2007-05-03
You could try regenerating the initrd

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

### Post by keithk50 on 2007-05-04
Thanks for the tips guys however unfortunately they did not work.   Oh well, there are worst problems.   Thanks for trying anyway.

---

