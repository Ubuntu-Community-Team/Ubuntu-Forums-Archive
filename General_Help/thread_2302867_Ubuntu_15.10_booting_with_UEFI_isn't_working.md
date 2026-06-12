---
title: "Ubuntu 15.10 booting with UEFI isn't working"
date: 2015-11-14
forum: General Help
---

### Post by sebastiaan5 on 2015-11-14
system specs: Lenovo y50-70 I7 16gb ram GTX 860M

I want to install ubuntu in UEFI mode because previously I was using  linux with legacy boot mode and the boot time was a little long.

The things I did to try installing ubuntu in UEFI:

I burned ubuntu 15.10 with K3B on a dvd RW 4,7gb.
Enabled UEFI boot mode in BIOS.
Made a new partition table: GPT.
Installed ubuntu in 4 partitions:

500mib ESP (Efi system parition)
300GB /
500GB /home
20GB SWAP


When I boot my pc it gives an error: EFI NETWORK 0 FOR IPV4 (xx-xx-xx-xx-xx-xx) boot failed.

What did I do wrong?
ps. I don't dual boot, I want only ubuntu on my laptop.


greetings,

Sebastiaan

---

### Post by sebastiaan5 on 2015-11-14
Update:

-

---

### Post by oldfred on 2015-11-14
Either network boot is first  in UEFI boot order, or it is not finding anything before network boot that works and that is first that gives an error message.
Possibly some other UEFI setting, see other Lenovo threads below.

Post this from live installer:
sudo efibootmgr -v

You also will need a boot parameter until you install proprietary video drivers. If only Ubuntu, then press escape at end of UEFI/BIOS screen, but before grub loads. With one install it normally skips menu as it assumes you want to boot the one system you have.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

At least some Lenovos now are like HP & Sony in that they have modified UEFI to also use desription in UEFI to boot. And only description allowed is "Windows".  That is supposedly not allowed per UEFI standard.
There are multiple work arounds. If only Ubuntu you can rename the ubuntu entry in UEFI to be Windows but reallly boot shimx64.efi file. If dual booting, you can rename /EFI/Boot/bootx64.efi which is the fallback UEFI boot entry or just a drive boot entry. That same entry is used for external drives and even booting a Windows installer so it still works.

Details in link in my signature.


 Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)

 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)

---

### Post by sebastiaan5 on 2015-11-16
I installed it without partitioning so the default:

swap, ESP, and /

and It worked

---

