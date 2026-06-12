---
title: "Modify /boot/grub/grub.conf"
date: 2013-02-25
forum: General Help
---

### Post by mc0001 on 2013-02-25
Hi,
I'm trying to set up console IPMI access on a server running Ubuntu 12.10 which is using GRUB2, but the instructions I have are for GRUB, and I can't see how to port the required changes. Basically I need to add two lines to GRUB's /boot/grub/grub.conf and delete one line, namely:

# add:
serial --unit=1 <more stuff>
terminal --timout=10 <more stuff>
# delete
splashimage=(hd0,0)/grub/splash.xpm.gz

However, that file doesn't even exist with GRUB2. Any ideas where this changes need to be made with GRUB2 please?

---

### Post by schragge on 2013-02-25
/boot/grub/grub.[color=red]cfg[/color] is generated automatically each time *update-grub* gets invoked, e.g. when installing a new kernel. Do not edit it directly. Instead, either change defaults in */etc/default/grub* or add your script to */etc/grub.d/*

---

