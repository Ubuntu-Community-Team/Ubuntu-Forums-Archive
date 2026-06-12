---
title: "Grub Rescue Prompt Help"
date: 2018-01-08
forum: General Help
---

### Post by cathect2 on 2018-01-08
I am running Ubuntu 16.04. The whole disk is encrypted, which I performed long ago upon installation. There is no other OS on the machine. After an update this week to the kernel, grub somehow got broken. When I boot up I get the Grub Rescue prompt after a "no such partition" error.

When I run the ls command I get:

(hd0) (hd0,msdos1) (hd1)

What should I do at the grub rescue prompt to get boot working properly?

Thanks!

---

### Post by yancek on 2018-01-08
The error 'no such partition' generally means Grub is looking for a partition which is improperly named or does not exist.  When you see the error, there is usually a UUID appended to it which is a long series of numbers/letters.  Make a note of it.  At the Grub prompt, run this command and make a note of the files or take a photo of the screen if you can to find the kernels (vmlinuz files) as well as initrd files:

> ls (hd0,msdos1)/boot/

Then run the following command to see the grub.cfg file and compare the UUID in the Ubuntu menuentries to the one you see in the error message.

> cat (hd0,msdos1)/boot/grub/grub.cfg

I would not expect this behavior after an update of a kernel as update-grub should be run but, who knows?

You can manually boot from a grub prompt (grub>) and probably from grub rescue.  The following is an example booting from a root partition on sda1.  You need to get the info from the ls command above for the exact vmlinuz and initrd files. The entries below use an older kernel and initrd so you will need to change those to fit your system.  Type each line in and hit the enter key after entering each line.  You should then get another grub prompt to enter the next line. 

> set root=(hd0,msdos1)
linux /boot/vmlinuz-3.13.0-24-generic root=/dev/sda1
initrd /boot/initrd.img-3.13.0-24-generic
boot

---

### Post by cathect2 on 2018-01-09
I have no UUID numbers/letters after the error message. It just announces:

error: no such partition.
Entering rescue mode
grub rescue >

Issuing your first command gives:

error: unknown filesystem
grub rescue>

---

