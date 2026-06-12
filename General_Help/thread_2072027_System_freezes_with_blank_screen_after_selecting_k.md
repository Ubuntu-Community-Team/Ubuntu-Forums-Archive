---
title: "System freezes with blank screen after selecting kernel version at bootup"
date: 2012-10-16
forum: General Help
---

### Post by makeyre on 2012-10-16
I have an Ubuntu 12.04 system that is freezing every boot-up after I select a kernel version from the startup menu. It does not respond to CTRL-ALT-DEL. Is there something I can check from the recovery console, some log or something that will indicate why it's not booting up to the log-in screen?

---

### Post by searchfgold6789 on 2012-10-16
How long is it taking to do this? Does anything happen before it crashes?

Can you describe exactly what happens?

And does it actually boot into the recovery console?

---

### Post by makeyre on 2012-10-17
As soon as I select a kernel, the screen goes blank (actually a very dark purple, probably set by the Ubuntu theme), and stays blank, presumably frozen.

If instead of a normal kernel I select a kernel version that's a recovery console, it boots to a prompt successfully, but without mounting any drives, so I'm not sure where I would look to get at a log file to see what's going wrong.

---

### Post by searchfgold6789 on 2012-10-22
My apologies for the delay in replying. 
Can you press ctrl+alt+F1 to get into a text-based login screen?

---

### Post by makeyre on 2012-11-09
No, after I select the kernel version from the boot menu list, the screen goes black and doesn't respond to any common key presses. I'm aware of CTRL-ALT-F1 and that doesn't get me to a text login screen; whatever is causing the freezing happens before that point.

Right now, I think my best means of diagnosis is using a boot image on a USB stick. But what should I be looking at/for? Is there a log file that will reveal the issue?

---

### Post by searchfgold6789 on 2012-11-09
Try selecting "recovery mode", and observe the output of the kernel. Then see if anything wrong happens after selecting "resume" or "failsafex" (if they still have that).

---

### Post by rnerwein on 2012-11-09
> **searchfgold6789 said:**
> Try selecting "recovery mode", and observe the output of the kernel. Then see if anything wrong happens after selecting "resume" or "failsafex" (if they still have that).

i think i got a similar problem before.
when i select the 10.04 kernel and hit return --> dark screen.
the next i did was ( after reboot) i select the kernel ( no return) hit "e" to edit the line

linux /boot/vmblabla ......

change the "ro" to "rw" and insert "single" in that line.  hit "crtl x" to boot. notice these changes not permanet.
login and run as super user: apt-get update && apt-get install --fix-missing
reboot - and everything works - why - i don't know. i am using a nvidia graphic card and
i think there was a problem.
bye

---

### Post by makeyre on 2012-11-10
Well, for some reason now even the recovery console doesn't seem to respond. I'm attaching a photo of the screen that it freezes at; I cannot type anything at that last line (initramfs).

Again, should I look for something after booting in with a USB key with the Ubuntu 12.10 image on it? I'd rather not reformat and reinstall though.

---

### Post by makeyre on 2012-11-14
Well I guess my only recourse is to boot in with an Ubuntu 12.10 flash drive, back up my home directory, and reformat and reinstall the operating system. I don't see a better way of fixing this problem.

---

### Post by searchfgold6789 on 2012-11-19
makeyre,
Try reinstalling Grub by booting from Live media and using [boot-repair]("https://help.ubuntu.com/community/Boot-Repair").

---

### Post by YannBuntu on 2012-11-19
Hello
The problem seems located in the kernel (or the graphic driver), not the bootloader (GRUB).

@makeyre: please run Boot-Repair --> Create BootInfo, and indicate the URL that will appear.

---

### Post by searchfgold6789 on 2012-11-19
My hint is that something failed to mount on /root. If it were a graphical driver issue, the kernel would get a lot farther than it did, and...
```
Target filesystem does not have requested /sbin/init.
```Possibly the wrong boot option was passed, or something is wrong in /etc/fstab.

---

