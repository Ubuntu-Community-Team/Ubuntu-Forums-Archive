---
title: "Grub problem"
date: 2007-03-09
forum: General Help
---

### Post by Syncman on 2007-03-09
Hi,

I decided to re-install (i mess up with the nvidia installation) kubuntu edgy in my 80 gb Sata drive (sda?), it went flawless. So after rebooting, the problem occur. The screen when like this:

```
 Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub ...
```
... endlessly 

So i reset the pc i decided to boot up in my 40 gb PATA drive, instead of showing the windows screen it show me the grub menu. i remember that grub are install in hd0.

So how do i fix the Grub grub grub problem in my SATA drive, and how do i replace the grub in pata and let it stay in SATA???

Thanks in Advance
syncman

---

### Post by Support the 2nd on 2007-03-09
> **Syncman said:**
> Hi,

I decided to re-install (i mess up with the nvidia installation) kubuntu edgy in my 80 gb Sata drive (sda?), it went flawless. So after rebooting, the problem occur. The screen when like this:

```
 Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub Grub ...
```
... endlessly 

So i reset the pc i decided to boot up in my 40 gb PATA drive, instead of showing the windows screen it show me the grub menu. i remember that grub are install in hd0.

So how do i fix the Grub grub grub problem in my SATA drive, and how do i replace the grub in pata and let it stay in SATA???

Thanks in Advance
syncman

I had a problem simular to this the other day during my first attempt at running linux.  So bare with me as I am not promising this will work....or is even correct.

For the Windows drive, just to get one of your drives to boot, you could put your windows installer CD in and boot from that, then use the recovery console and type "fixboot" and then "fixmbr" in to the console.

That make Windows at least boot.  As for fixing your linux drive, that is something I am trying to do now too because my GRUB and boot stuff is on my PATA with the Windows install, and I want to run with just the SATA so I can take my Windows HD to another comp....but that is beside the point.  Good luck.

---

