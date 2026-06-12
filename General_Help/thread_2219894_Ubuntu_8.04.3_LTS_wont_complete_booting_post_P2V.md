---
title: "Ubuntu 8.04.3 LTS wont complete booting post P2V"
date: 2014-04-25
forum: General Help
---

### Post by Gigi_Mathews on 2014-04-25
I am very new to Ubuntu and would appreciate some pointers or assistance.

I have converted a Physical Server running "Ubuntu 8.04.3 LTS" to a Virtual Machine on VMware ESXi 5.5.0, using VMware vSphere Converter. Physical server had console direction enabled, so after P2V conversion, I booted up VM in single user mode and took following actions
1. Updated /boot/grub/menu.lst <= Removed "console=ttyS0,9600"
2. Updated /etc/inittab and commented "T0:23:respawn:/sbin/getty -L ttyS0 9600 vt102"
3. Moved /etc/event.d/ttyS0 file to /root

Now, when i boot (default runlevel is set to 2) the VM, i see that all (almost all) services starts OK but the boot process (init) stops showing OK / Failed message at the second last process in /etc/rc2.d. Server responds when i hit Enter key on console. I can ssh to the Virtual Machine and access everything. But i dont see login prompt at the console. Please refer "[COLOR=#000000]Ubuntu-Boot.png" [/COLOR]below for reference.

I am not sure if this is because of console redirection (if yes, what did i miss from whats mentioned above) or it could be something else.

Any assistance is highly appreciated.

Thank You very much.

---

### Post by mörgæs on 2014-04-26
8.04 is out of support. I recommend that you install the 14.04 server.

---

