---
title: "PXE boot an ISO on a UEFI Secureboot enabled system"
date: 2016-04-27
forum: General Help
---

### Post by collisionystm on 2016-04-27
I'm not sure if this is the right place to post this so if it's not - I apologize.

Back story:
I have a several computers that have UEFI secureboot enabled ( I cannot change this ). Due to SecureBoot being enabled, I can obviously only boot secure signed images. I need to be able to boot a CA Arcserve D2D BMR restore disk. It's essentially a live disk that loads into a WindowsPE environment and allows you to perform a bare metal restore of backups.

What I have tried:
I've tried to manipulate windows deployment services into using this boot.wim file but I'm not having any luck. I decided it may be best to just boot the .ISO itself via PXE.

On a standard non EFI machine I can use pxelinux.0 and everything works fine (its slow because TFTP but it works) but on a UEFI secureboot enabled computer, pxelinux.0 is not an option.

I've looked into iPXE so I could utilize booting over HTTP but unfortunately they do not pack a certificate (due to cost) that would allow it to pass a secureboot check.

What I hope to accomplish:
SO! Since Ubuntu purchased the necessary cert so it will pass a secure boot check, I am hoping to use it as a bootloader of sorts to load the .ISO image. Has anyone tried something similar? Does this just sound like a terrible idea that won't work?

I've been looking over this guide, [https://wiki.ubuntu.com/UEFI/PXE-netboot-install](https://wiki.ubuntu.com/UEFI/PXE-netboot-install)

I tried to compile an EFI signed image using the iPXE iso available on their site but that didn't work out so well.
-- Alternative method to create a boot image (all-in-one file)


I just need to pass secureboot and load an .ISO (hopefully via HTTP). Has anyone out there tried anything like this?

---

