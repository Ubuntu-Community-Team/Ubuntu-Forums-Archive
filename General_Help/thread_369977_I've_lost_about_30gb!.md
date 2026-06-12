---
title: "I've lost about 30gb!"
date: 2007-02-25
forum: General Help
---

### Post by UltimaDude on 2007-02-25
I need help, i've been running qemu emulating Ubuntu and I had to run this CMD:

.\QemuManager\qemu\qemu-img create .\QemuManager\images\ubuntu6.img 10gb

.\QemuManager\qemu\qemu -hda .\QemuManager\media\ubuntu6.iso -L .\QemuManager\qemu -m 512 -usb -cdrom .\QemuManager\images\ubuntu6.img

pause

I went back on windows today, and It says I have 32gb!
What happened,  to my space before it I had 62gb.

Should it be fine if i run this?:

.\QemuManager\qemu\qemu-img create .\QemuManager\images\ubuntu6.img -30G

.\QemuManager\qemu\qemu -hda .\QemuManager\media\ubuntu6.iso -L .\QemuManager\qemu -m 512 -usb -cdrom .\QemuManager\images\ubuntu6.img

pause

---

### Post by GrumpyBob on 2007-02-25
How many img files have you created?

Robert

---

### Post by UltimaDude on 2007-02-25
3, one broke and another I deleted.
I was also planning to install it again.

Oh and my computer has messed up and I can't delete anything my recycle bin, I can't even see whats in the recycle bin.
And i'm getting random BSOD's, i'm planning to install Ubuntu on the hard drive soon.

---

### Post by GrumpyBob on 2007-02-25
I am probably misunderstanding something here, but if you are running
.\QemuManager\qemu\qemu-img create .\QemuManager\images\ubuntu6.img 10gb
each time you use qemu, you are probably making a 10Gb img file each time.  That would eat up your disk space pretty quickly.  I've been using qemu to run Win98SE in Ubuntu, with a 2Gb img file.

Robert

---

### Post by UltimaDude on 2007-02-25
Thanks, oh and my CMD worked.

---

