---
title: "Problem with installing from USB"
date: 2017-06-24
forum: General Help
---

### Post by siggen on 2017-06-24
Hi!

I installed ubuntu on my laptop with 0 problems a couple of weeks ago. Today i used the same usb boot drive to install on my desktop computer. I got to the boot menu where i can choose if i want to try ubuntu or install it. I tried both options and ended up with the same result. After pressing the screen goes black and thereafter a split second of |||| in a row over the screen and then the screen shuts off. I know it sounds wierd but i would really apprechiate some help. 

I turned off fast boot, that didnt help, but i cant seem to find the secure boot option. 
My motherboard is a MSi B85M-E45.

Thanks in advance.

---

### Post by ajgreeny on 2017-06-24
More info on the hardware, particularly the graphic card may help us to give you more advice.

Is this a BIOS or UEFI system?
Are you trying to dual boot with another OS eg. Windows?

---

### Post by johndough2 on 2017-06-26
Hi

I feel that this is similar to problems with SuSE 11 when the nomodeset command was needed. I will search and try and find the details and come back if successful.

AAND here we are, and I used it for openSuSE 11.4

With openSUSE 11.3 we switched to KMS (Kernel Mode Setting) for Intel,  ATI and NVIDIA graphics, which now is our default. If you encounter  problems with the KMS driver support (intel, radeon, nouveau), disable  KMS by adding nomodeset to the kernel boot command line. To set this permanently, add it to the kernel command line in /boot/grub/menu.lst. This option makes sure the appropriate kernel module (intel, radeon, nouveau) is loaded with modeset=0 in initrd, i.e. KMS is disabled.

So I had to edit grub at boot time and it then worked.  So for Ubuntu try...

[http://grumpymole.blogspot.co.uk/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.co.uk/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

