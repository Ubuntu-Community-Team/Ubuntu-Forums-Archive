---
title: "My computer will not boot from USB!"
date: 2012-10-17
forum: General Help
---

### Post by pandacookie on 2012-10-17
Just last night my computer was able to boot from the live USB I made. Now it won't. I checked the BIOS to make sure it was configured correctly, to boot from USB first. It is configured correctly. The computer goes right into Grub, instead of to the USB. The USB works on other computers. The computer recognizes the USB drive. I tried putting it in other USB ports. That didn't work either.

I changed to Grub 2 2.00 last night while repairing the boot menu with Boot Repair. Could that have something to do with it? What can I do? I tried this: 

root=/dev/sdb1 
linux /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
initrd /casper/initrd.lz boot

It didn't work. It said sdb1 didn't exist. 

Again, what can I do??

---

### Post by pandacookie on 2012-10-17
Never mind. I made a new bootable USB.

---

