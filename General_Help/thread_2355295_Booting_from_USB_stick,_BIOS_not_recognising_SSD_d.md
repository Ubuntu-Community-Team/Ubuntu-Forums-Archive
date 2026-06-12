---
title: "Booting from USB stick, BIOS not recognising SSD disk"
date: 2017-03-11
forum: General Help
---

### Post by linde03 on 2017-03-11
Dear all,
I had the intention setting up an ASUS VivoMini UN45 as a small server (home automation).
The Asus only has M.2 connectors so I purchased a Intel 600P 256 GB M.2 PCiE NVME SSD stick.
However, even with the latest BIOS firmware, the computer BIOS not recognize the SSD.
I can however install Ubuntu  16.10 server to the SSD using a live USB for the installation. The SSD It is fully recognized and functional from that perspective.
So - my query is really.
Would it be possible to create a USB stick boot drive, that loads the kernel, fstab and then mounts the SSD:s partitions, bypassing the fact that the BIOS could not see the drive?
I have kind of been away from Linux for ~20 years. But if I do not remember completely wrong, "back in the days" (using slackware) I used to create "rescue floppys" that contained LILO, a kernel image (vmlinuz) and that rescue disk could then mount the HDD partitions.

Could I use a similar approach with GRUB2, Ubuntu 16.10 and get my "server lite" up and running using a USB stick for the intitial Boot , or am I doomed to actually buy a new computer (or another probably SATA M.2 SSD).

I would be most thankful for any help.
Since this is my first post here, please correct me if I did not follow any forum rules.

Best Regards
/Daniel

---

### Post by yancek on 2017-03-11
> I can however install Ubuntu  16.10 server to the SSD using a live USB  for the installation. The SSD It is fully recognized and functional from  that perspective.

If it is installed and fully functional, why do you need a usb drive with boot files?  You can use a flash drive with a boot or Grub partition to boot something on another drive.  Not sure I  really understand the problem or how you wer able to install Ubuntu to a drive not recognized by the BIOS.

You might check if you are using the server version because the Desktop version of 16.10 is a short term release.  Support ends in July.  Actually it is the same, see the Ubuntu link below.

[https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)

---

### Post by linde03 on 2017-03-11
Yancek,
Thanks for you reply.
Bios does not see the SSD drive. But when using the standard usb image on a USB stick, Ubuntu does recognize the drive during the install. So - that what was I was referring to as "fully functional". However, since GRUB is installed on the SSD, that isn't seen by BIOS - I will be "stuck" at BIOS during a regular start - not using the USB stick. Since I am by no means a computer whiz, I am just guessing that when the kernel is loaded from the USB stick during boot - it somehow sees the SSD and can mount it - even though BIOS does not list it as a device.
So - I was thinking whether it would be possible to create a USB stick, containing the necessary files inluding the kernel, to start the boot process - and when the SSD is seen, mount it as the root file system? That way I could have a fully functional system without having to invest further $ on hardware...

---

### Post by oldfred on 2017-03-11
Kernels require BIOS/UEFI to enumerate the hardware and copy that onto drive so system can boot.
Do not understand BIOS not seeing drive.
Perhaps it sees drive in drive tab, but does not see it for booting in boot tab in BIOS?

Is system BIOS only or UEFI?

If motherboard only has M.2, seems very strange that BIOS does not see drive.
But some brands have had to update UEFI/BIOS to support the newer NVMe devices, especially for booting.

I have seen a few users just install grub to a flash drive for booting.
You can in install, during Something Else choose another flash drive on location for grub.

Or you can just install grub to flash drive and manually configure a grub.cfg for booting install. I often do this in addition as I directly boot ISO. 
So I have grub, ISO and my own boot stanza primarily for the ISO, but add a few other entries for installs on my hard drives. Drive order is an issue, so I often have to edit (hdX,Y) and sdX as I boot as drive order is not always consistent.

---

### Post by linde03 on 2017-03-11
Many thanks for the feedback.Did a new install of 16.04 server, added an additional USB stick prior to the installation process. Put EFI, Grub and /boot on that USB stick. Now the systems boots just fine. The SSD is mounted correctly (root and swap) - and everything seems to be functioning as expected.

---

### Post by oldfred on 2017-03-11
Glad you got it working.

Was second flash drive seen as sda?
Grub has only installed in UEFI mode to ESP on drive seen as sda. Or have they finally fixed it so you can install to another drive?

All my desktop installs to flash drives or sdb have overwritten my main working 16.04 grub in ESP on sda. 
Just installed 17.04 to flash drive and it overwrote my ESP on sda.

---

### Post by linde03 on 2017-03-13
Yes, the second drive was seen as sda.
I am happy this type of setup worked out. Asus Bios for the VivoMini was really terrible from a settings point on view. In principle no settings to fiddle with. The M.2 settings/options field was "greyed out" - and the Bios reported only RAM found.  I appreciate you're right about the "...[COLOR=#000000]have had to update UEFI/BIOS to support the newer NVMe devices...".

[/COLOR]

---

