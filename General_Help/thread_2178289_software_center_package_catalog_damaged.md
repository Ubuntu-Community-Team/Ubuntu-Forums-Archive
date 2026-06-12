---
title: "software center package catalog damaged"
date: 2013-10-02
forum: General Help
---

### Post by tommy_strasberger on 2013-10-02
i cannot install anything,there is somthing wrong with linux-image-3.5.0-41-generic. this became a problem after i did all of the updates

---

### Post by grahammechanical on 2013-10-02
It would help if you posted the error message. How do you know there is something wrong with that kernel? What error message do you get when you try to install something or run Update Manager or sudo apt-get update and sudo apt-get upgrade in the terminal?

Without this kind of information anything we might suggest could do more damage than good.

---

### Post by tommy_strasberger on 2013-10-02
i was looking in forums and it said (sudo apt-get -f install) and it returns
(Reading database ... 185962 files and directories currently installed.)
Unpacking linux-image-3.5.0-41-generic (from .../linux-image-3.5.0-41-generic_3.5.0-41.64~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-41-generic_3.5.0-41.64~precise1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-41-generic /boot/vmlinuz-3.5.0-41-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-41-generic /boot/vmlinuz-3.5.0-41-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.5.0-41-generic_3.5.0-41.64~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by oldos2er on 2013-10-02
Can you please tell us your hardware specs?

---

### Post by tommy_strasberger on 2013-10-02
1gb ram
Intel® Pentium(R) M processor 1300MHz processor 
unknown graphics
32 bit os
20gb hdd
...hope that helps im not sure if thats what u needed and if it helps the laptop is a ibm thinkpad

---

### Post by Yellow Pasque on 2013-10-02
What kernel are you running now?
```
uname -a
```

---

### Post by tommy_strasberger on 2013-10-02
Linux tommy-laptop 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux

---

### Post by mörgæs on 2013-10-03
The Pentium M 1,3 GHz does not display the PAE flag, which is required for recent Buntus, as is confirmed in the error message: 

*This kernel does not support a non-PAE CPU*

You can try a fresh install of Bodhi (link in my signature) or work around the [PAE]("https://help.ubuntu.com/community/PAE") problem while staying with the Buntu family, if you prefer that. Would be interesting to know if you can salvage the installation by adding Fake-PAE.

---

### Post by tommy_strasberger on 2013-10-03
so is that the only way is to do a fresh install =(?

---

### Post by Yellow Pasque on 2013-10-03
@mörgæs, I'm trying to figure out how the user got a 3.5 kernel installed without PAE and why it's starting to complain now :?

---

### Post by tommy_strasberger on 2013-10-03
im unsure i made a disc of ubuntu loaded it in windows to help create a way to boot from the disc because without the custom boot menu it wouldent boot from the disc. and everything was fine untill i did updates

---

### Post by mörgæs on 2013-10-04
> **Temüjin said:**
> @mörgæs, I'm trying to figure out how the user got a 3.5 kernel installed without PAE and why it's starting to complain now :?

Yes, it also puzzles me. I don't have a good explanation to why some 3.5-kernels work but not all of them.

---

### Post by tommy_strasberger on 2013-10-04
so is it a yes that i need to put a diffrent version on my laptop?

---

### Post by mörgæs on 2013-10-05
The answer to #9 and #13 is: 

> **mörgæs said:**
> Would be interesting to know if you can salvage the installation by adding Fake-PAE.

Temüjin has deeper technical knowledge than me. Maybe he has other suggestions.

---

### Post by tommy_strasberger on 2013-10-05
im not sure why but my laptop will not boot from the bodhi linux disc or even a windows disc  the only way i know to get it to boot is from the boot helper that came  with my ubuntu its wubi. but because im in ubuntu every time i try to  run wubi in Wine it tells me permission denied and i need the boot  helper to downgrade to work with my older hardware. someone tell me if i can get wubi to run in wine

---

### Post by Yellow Pasque on 2013-10-05
> **mörgæs said:**
> Temüjin has deeper technical knowledge than me. Maybe he has other suggestions.

Not when it comes to PAE. I've been running 64-bit for 7-8 years now...
Anyway, I wonder if one could simply spoof the pae support by making /proc/cpuinfo writable and adding 'pae' to the flags. Of course, it wouldn't work on pre-Pentium II machines or any hardware that isn't PAE-capable, but it may do the trick to allow kernel upgrades on Pentium M's or other CPU's that support PAE, but don't advertise it.

---

### Post by mörgæs on 2013-10-05
Yes, that's exactly what Fake-PAE does.

---

### Post by tommy_strasberger on 2013-10-05
any ideas on how to get wubi to work in wine

---

### Post by mörgæs on 2013-10-05
I wouldn't go that direction :-) but I might be able to help with a fresh install of Bodhi.

Do you early in the boot process get the option of entering BIOS by pressing an F-key or Delete?

---

### Post by tommy_strasberger on 2013-10-05
yes but when i have it set to boot the cd drive first it goes to a black dos screen and does nothing for a few then it just freezes thats why i needed a boot manager to help me to install bodhi

---

### Post by mörgæs on 2013-10-06
We need more information here.

Does the computer boot from USB?
Have you verified that the CD works by booting in another computer? 
Have you tried boot options like NOMODESET? 
Are you able to boot a [12.04 minimal ISO]("http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/mini.iso") (the non-PAE version)?
and everything else you deem relevant, especially information (or guesses) about why the Windows CD stopped working.

---

### Post by tommy_strasberger on 2013-10-07
it says that it can boot from usb flash drives or a usb cd drive.
yes i have tried the bodhi disc on my old dell latitude and it booted with no problems.
i looked there was no option called NOMODESET.
i will make a cd of the minimal ISO and test that out
and sorry im such a noob all i know is that when i went to install ubuntu the laptop wouldent boot from the disc when i had windows as the OS so i ran WUBI to help boot from the cd and when it booted it gave a boot menu that enabled me to be able to boot from ubuntu.
also i have tried making a usb of bodhi and used my usb cd drive and neither has worked

---

### Post by tommy_strasberger on 2013-10-07
ok i got the bodhi disc to load but when i click to load it then it becomes frozen

---

### Post by mörgæs on 2013-10-09
> **tommy_strasberger said:**
> 
also i have tried making a usb of bodhi and used my usb cd drive and neither has worked

Again, we need much more information. "Didn't work" is not much of a foundation for giving advice. 

What exactly happens when you try booting Bodhi and the mini.iso from a USB stick (not a USB-connected CD drive)? We need all details you can possible provide.

---

### Post by tommy_strasberger on 2013-10-16
sorry i had to put windows on as a temp fix and the computer wont allow me to boot from a usb its just not an option in bios. as for what i ment for it dident work when i would click the first option which is boot live os from cd and when i select that one it looks like its loading for a few but after that it stays on the same screen but does nothing and i have tried booting into ram but again it just froze. and im really sorry that its taken me a week to get back on here but ive been job hunting like crazy sorry everyone

---

