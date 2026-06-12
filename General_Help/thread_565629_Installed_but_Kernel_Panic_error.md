---
title: "Installed but Kernel Panic error"
date: 2007-10-02
forum: General Help
---

### Post by pchardware on 2007-10-02
I installed via WUBI fine and rebooted it installed all the software and restarted now I get APIC time doesnt update no apic, then Kernel Panic not syncing apic=debug

What can I change to try and fix this?
Thanks

---

### Post by kast on 2007-10-02
have you tried searching the forum?

[http://ubuntuforums.org/showthread.php?t=500884&highlight=noapic](http://ubuntuforums.org/showthread.php?t=500884&highlight=noapic)

---

### Post by Jussi Kukkonen on 2007-10-02
Exact error messages please (just like you see them on the screen).

---

### Post by pchardware on 2007-10-02
ok the below shows on screen after selecting Ubuntu from the boot menu:

filesystem is ntfs partion type 0x7
[linux bzimage setup=0x1000 sizw ox1n82cc]
[linux-initrd @ 0x1f81b7000, 0x738203 bytes]
[30.098677 mpbios bug: 8254 timer not connected to 10-apic
[30.266523] kernel panic not syncing: 10-apic + timer doesnt work!

Boot with apic-debugand send a report
Then try booting with noapic option
[30.266548

---

### Post by kast on 2007-10-02
Boot with apic-debugand send a report
Then try booting with noapic option
[30.266548

Have your tried the noapic option?

---

### Post by pchardware on 2007-10-02
Where do I try and run it from? As I'm not booting from the iso burnt to disk can I change a setting in the Wubi folder?

---

### Post by ago on 2007-10-02
You need to edit /wubi/boot/grub/menu.lst and append it to the line that starts with "kernel"

---

### Post by pchardware on 2007-10-03
Thanks works great now :)

---

