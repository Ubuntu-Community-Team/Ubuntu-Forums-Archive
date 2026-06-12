---
title: "Issues booting Ubuntu after updating 14.04 to 15.04 and installing graphics drivers"
date: 2015-07-01
forum: General Help
---

### Post by Jocbe on 2015-07-01
Hello!

A few days ago I upgraded from 14.04 to 14.10 and immediately to 15.04. Things seemed to go well initially. I had some smaller problems booting: when booting from a system that was powered off, the screen would remain black after GRUB, Ubuntu wouldn't seem to start. Rebooting the computer with Ctrl+Alt+Del fixed this every time and Ubuntu booted.

Yesterday I tried switching to AMD proprietary graphics drivers (no idea if this is relevant but this happened immediately before my current problem). After a reboot and trying the drivers for a little bit I found them to have a worse performance than the open-source drivers. Hence I switched back. I didn't manage to reboot the system to apply these changes any more and haven't been able to boot it since. 

I have a couple of encrypted drives (including sdf2, which is mounted at /). I am prompted to enter the password to decrypt sdf2 on boot but after that I get error messages and no further prompts for decrypting the other hard drive. Initially I got dropped into 'emergency mode' a couple of times but that doesn't happen any more. Now I just get an error, shortly followed by Ubuntu flashing further log messages to the screen and finally I end up at a black screen with a blinking cursor in the top-left corner. Nothing else seems to happen afterwards.

Also, the prompt to enter my decryption password already seems to be in some fallback-mode, as it is text-based and doesn't look as pretty as it does when everything is fine. 

If I choose to start Ubuntu in 'recovery mode' in GRUB it displays messages about the sdf2_crypt setup being successful, lvm not being available and then "Begin: Waiting for encrypted source device" 

If I choose to start Ubuntu in 'ubstart' mode in GRUB then I get a pretty (non-fallback?) prompt to enter my decrypt password but when I enter it I just get a "cryptsetup: lvm is not available" error again.

Attached is an image of the error message I get after entering my decryption password at boot (with the default boot entry in GRUB). ata11 refers, I believe to sdf (with sdf2 mounted to / and sdf1  to /boot). (sdf2 is an SSD, by the way).

I am not sure what other information is relevant, so before I blow up this post too much, please let me know what other information is necessary to debug this!


Do you have an idea of where this problem could originate and how to solve it?

Many thanks in advance!
Jocbe


Edit: I forgot to mention that when I boot from a live system then I seem to be able to access all partitions without problems.

---

