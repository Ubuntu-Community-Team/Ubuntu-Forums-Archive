---
title: "Ubuntu hangs at bios screen..Windows doesn't."
date: 2013-02-26
forum: General Help
---

### Post by hrd2plz on 2013-02-26
Dual booting Win7 & Ubuntu 12.10 using EasyBCD. When I use the 'restart' to reboot from ubuntu everything shuts down fine and reboot starts....then hangs at the bios before getting to the easybcd boot menu. I do not have a reset button, only Power on/off. I can quickly tap the power button on and off and cause the system to restart and all is well. This is not a problem when rebooting from within Windows..only Ubuntu. I've tried disabling ACPI in bios and kernel parameter with no luck. I've turned off the splash screens watching for errors and searched the log files with no luck. Since the system shuts down properly and boots properly after I hit the power button I can't find any errors. Is something not getting flushed clean or a process still running ??

Thanks for any replies.

---

### Post by fuorviatos on 2013-02-26
Did you overwrite GRUB with EasyBCD ?

---

### Post by hrd2plz on 2013-02-26
I don't think EasyBCD overwrites GRUB. It writes Win7/Vista back into the MBR and gives ya its own boot menu..then chainloads GRUB from there.  Everything works fine with a 'Hard Reset' . Only when allowing ubuntu to perform a restart from within the OS.

---

### Post by fuorviatos on 2013-02-26
Maybe this will help 

[http://neosmart.net/forums/showthread.php?t=9895](http://neosmart.net/forums/showthread.php?t=9895)

---

### Post by hrd2plz on 2013-02-26
I tried that but didn't help. I also tried the boot-repair from pp:yannubuntu with no luck. I did get the bootup splash screen disabled and have more details. Upon boot it Auto detects my hdd then my disc drive then trying to access the hdd it hangs. I first thought my drive could be going bad but this only happens rebooting from ubuntu...wierd. Oh..I have EasyBCD 2.2.0.182.

---

### Post by hrd2plz on 2013-02-27
SOLVED: Ethernet card died now all is well...thanks for the replies fuorviatos.

---

### Post by fuorviatos on 2013-02-28
Good. Can you mark the thread as [SOLVED] please?

---

### Post by hrd2plz on 2013-03-02
I would love too..but Thread Tools doesn't give me that option.

---

