---
title: "what to disable on live usb pen to prevent accidental live installation damage"
date: 2017-11-25
forum: General Help
---

### Post by kerrygee on 2017-11-25
Hi,

i am running a live session ubuntu from a pen drive with persistence to work with. as experience show me in the past, doing stuff like kernel updates with a casper-rw file lead to a corrupted system. so my question here is: what binaries and packages do i have to put on "apt hold" or remove the x-bit from them to disable their execution and or update on the system? I still want to be able to do basic updates on applications, but not (system) stuff that could break my system. any help on this would be great.

thanks in advance

k.

---

### Post by C.S.Cameron on 2017-11-25
With the size of flash drives nowadays there is little reason to use a Persistent install as a working drive.
A persistent drive only lasts a few months even if you do not try to update/upgrade it.

I have been using a Full install to flash drive for over a year now with no problems or corruption.
The previous Persistent install to the same drive only lasted four months before fragmentation of the NTFS partition and corruption of the casper-rw partition.

Once a few programs have been installed and some data saved, the Persistent install is not as efficient in the use of space as a Full install, nor does it boot as fast or is it as secure.

---

### Post by kurt18947 on 2017-11-26
+1 to C.S. Camerons's advice to simply create a 'real' install on a flash drive. I have a couple, Xubuntu & Mint. They're a little slower due to the USB speed limitations but I find them perfectly usable. I'm not using them for 'heavy' applications, just web browsing, office stuff and the like. Being a coward (and having gotten bit by installing to the wrong partition) I disconnect the hard drive and plug in 2 USB drives, one with the live installer and the other blank. I find a  32 GB USB 3 target drive adequate for my purposes, my full installs are <10 GB. My perception is that a USB 3 drive is faster than a USB 2 drive even when plugged into a USB 2 port.

---

### Post by C.S.Cameron on 2017-11-26
+1 for disabling the internal drive before proceeding, this also prevents adding the internal drives grub stuff to the flash drives grub.

---

### Post by kerrygee on 2017-11-27
> **C.S.Cameron said:**
> +1 for disabling the internal drive before proceeding, this also prevents adding the internal drives grub stuff to the flash drives grub.

Thank you all for all the answers. I would also point out, that putting a GRUB_DISABLE_OS_PROBER=true in grub or removing the entire os-prober package will skip the detection of other os and putting them to boot menu. Here is how: [https://unix.stackexchange.com/questions/56004/how-to-stop-update-grub-from-scanning-all-drives](https://unix.stackexchange.com/questions/56004/how-to-stop-update-grub-from-scanning-all-drives)

But what about the final pendrive? Will the pendrive only be startable from a UEFI system once created on a UEFI system or can it be started from a legacy BIOS system as well and vice versa? :confused:

---

### Post by C.S.Cameron on 2017-11-28
My Lexar 128GB with a Full install boots from everything I have plugged it into, both BIOS and UEFI.
It is easy enough to tryout, but install takes a little longer than Persistent to install and the bootable drive is not much good at installing Ubuntu to another computer.

Edit:
Best not to install any proprietary drivers, (ie Nvidia graphics), if you want it to work on multiple computers.

---

