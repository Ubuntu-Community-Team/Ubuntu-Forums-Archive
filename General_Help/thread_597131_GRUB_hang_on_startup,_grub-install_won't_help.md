---
title: "GRUB hang on startup, grub-install won't help"
date: 2007-10-30
forum: General Help
---

### Post by sammael666 on 2007-10-30
hi

i left my Kubuntu Gutsy box on overnight, there must've been a power surge or something, cause when i woke up, system was hanged in booting stage. it should say 

GRUB loading stage 1.5

and then continue booting, instead i see only

GRUB

and that's it.

so i figured it might have to do something with grub being corrupted or something, so i did these steps which once helped me when windows installation overwrited my MBR.

i booted from live-cd and in terminal run these:

sudo -s
mkdir /mnt/haha
mount /dev/sda2 /mnt/haha       <------ /dev/sda2 is my boot disk
mount -o bind /dev /mnt/haha/dev
mount -o bind /proc /mnt/haha/proc
chroot /mnt/haha
grub-install /dev/sda2

everything went fine, grub installer said there were no errors, so i rebooted and there it is again.

GRUB

and flashing cursor. now the machine isn't locked up, keyboard leds are working, i can ctrl-alt-del, it just hangs when starting grub.

now i run out of ideas and have to go to work, so hopefully till i get back at evening someone maybe can come with a fix.

---

