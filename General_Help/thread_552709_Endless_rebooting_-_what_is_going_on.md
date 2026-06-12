---
title: "Endless rebooting - what is going on"
date: 2007-09-16
forum: General Help
---

### Post by Packrat1947 on 2007-09-16
Hi Gents,
I'm a new user of Ubuntu desktop.  It was working fine for one day, and now the Grub flashes, and then the computer reboots – endlessly.    Is there a 'registry' that I can restore?  Do a 'repair install'?  What next if this was your lappy.  

I could 'boot and nuke' and reinstall, but that is cheating.  What is a simple fix.  Thanks for any help.
Packrat1947

---

### Post by gautada on 2007-09-16
It seems like your grub conf is in error.  Load up the livecd mount your drives and see what is going on or set up better logging and reboot.  IF you are new to linux and the above makes no sense then I suggest a reinstall from the live cd.

---

### Post by Stebalien on 2007-09-16
I would reinstall Grub if it is an instant reboot (it doesn't pause on the grub screen).
> remmelt:
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---

### Post by Packrat1947 on 2007-09-16
Hi, Thanks for the quick reply.

I tried the: root (hd0,6) command, but it said no such partition.  I tried 7 too.  Same thing.

I'm going to reinstall like gautada said, and see if this problem comes up again.

Thank you for your detailed replies.

See you on the other side - hopefully.

Packrat1947

---

### Post by Packrat1947 on 2007-09-17
Hi,
Just to let you know that the re-install went OK - after figuring out the partition questions.

Anyhow, my bootup time dropped from about 3 minutes down to 52 seconds; and that includes wireless connecting.  Much better now.

A quick question. from a noob.   How can I boot straight into my desktop with out the logon screens?  I just don't need any such things.  Thanks.

Packrat1947

---

### Post by gautada on 2007-09-17
> **Packrat1947 said:**
> How can I boot straight into my desktop with out the logon screens?  

Checkout System->Administration->Login Window.  What you need is in here.

---

