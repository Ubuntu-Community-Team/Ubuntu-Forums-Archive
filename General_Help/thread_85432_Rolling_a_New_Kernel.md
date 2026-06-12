---
title: "Rolling a New Kernel"
date: 2005-11-02
forum: General Help
---

### Post by Drifter on 2005-11-02
I gave rolling a new kernel a try and it all went well.  It finished and I rebooted then checked the version and it gave me the old version.  I used the new vanilla kernel and the patch.  Does anyone know why it gave me the old version after doing all this.  I used a guide that is posted in this forum.

---

### Post by suRoot on 2005-11-02
Are you sure grub was configured to boot the new kernel?  If you followed the instructions, it should have been...

Try again.  This time when you reboot, hit esc at the grub prompt & arrow up or down to choose your new kernel.  Then hit enter.  See what happens.

---

### Post by Drifter on 2005-11-02
Thanks I don't recall that, I will try again later today, I am at work and not at my computer.  will let u know if it worked.

---

### Post by Drifter on 2005-11-05
Well it has been a day or so since I tried to put the new 2.6.14 kernel on, but I just tried again.  This is the error message itgives.

drivers/usb/media/se401.c:1: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[4]: *** [drivers/usb/media/se401.o] Error 1
make[3]: *** [drivers/usb/media] Error 2
make[2]: *** [drivers/usb] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.14cK1'
make: *** [stamp-build] Error 2

How do I correct these errors, I have never been able to get past this part of the how to.  Can someone help please.

---

