---
title: "Acer Revo R3610 -- Cannot Boot from USB Hard Disk"
date: 2014-12-25
forum: General Help
---

### Post by digixmax on 2014-12-25
I installed 14.04 on a USB hard-disk of my Acer Revo R3610 using the process along the line of the guide posted at [http://engg-haven.blogspot.in/2014/08/install-ubuntu-bodhi-linux-on-external.html](http://engg-haven.blogspot.in/2014/08/install-ubuntu-bodhi-linux-on-external.html).  The installation completed without error (ending at the prompt "..., continue testing or restart?"), but when I tried to boot from that hard-disk (hitting F12 then selecting the hard-disk as boot device) the system would fail to boot: the display would just flash in sync with the blinking cursor seemingly forever.

I should note that I can boot from a USB DVD drive just fine.

I'd like to know if anyone has succeeded in installing and running Linux off a USB hard-disk on a Revo R3610, and if so, can give me some pointers on where I might have made mistakes.

TIA.

---

### Post by phidia on 2014-12-26
It could be the ion gpu or a problem with how grub installed but more specifics are needed. How did you choose to install the bootloader?
There is a thread [here]("http://ubuntuforums.org/showthread.php?t=1381874") in which many people claim to have successfully installed ubuntu to that device. The thread does begin with a complain about the acer revo but nonetheless it appears it can be made to work.
If you google Acer Revo R3610 and ubuntu you will find a lot of discussions about ubuntu with the revo.

---

### Post by C.S.Cameron on 2014-12-26
Does this external hard drive work on other computers?

---

### Post by digixmax on 2014-12-27
> **C.S.Cameron said:**
> Does this external hard drive work on other computers?
The external hard disk booted fine on another computer.

> **phidia said:**
> It could be the ion gpu or a problem with how grub installed but more specifics are needed. How did you choose to install the bootloader?
...

The bootloader was installed on /dev/sdb; I uploaded the results of the boot-info-script (from a repeated installation attempt using Mint 17.1) to [http://www.mediafire.com/view/5ixb85iu66wfyxu/RESULTS.txt](http://www.mediafire.com/view/5ixb85iu66wfyxu/RESULTS.txt).

---

### Post by yancek on 2014-12-27
Do you not have an option to enter BIOS setup to change boot priority?  What options do you have with F12?  You have windows on the 160GB drive and also on its master boot record and Mint on the 60GB drive with its Grub bootloader in the master boot record.  Nothing wrong with the boot files that I can see.  I'm not familiar with your hardware so there may be something I'm not aware of.

---

### Post by digixmax on 2014-12-28
> **yancek said:**
> Do you not have an option to enter BIOS setup to change boot priority?  What options do you have with F12?
...

I tried both changing the boot priority in the BIOS setup and using F12 boot selection menu, the Acer would attempt to boot from the USB hard disk but fail to even load the grub menu.

---

