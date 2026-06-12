---
title: "Xubuntu-20.04 dual boot with Arcolinux-20-06-12"
date: 2020-07-06
forum: General Help
---

### Post by ajgreeny on 2020-07-06
I have a problem having just added an installation of Arcolinux to my main Xubuntu-20.04 system, and I am baffled.

I can get both systems to run very well from the UEFI device menu or from the Arcolinux grub, but if Xubuntu is set as the priority boot device in the UEFI setup, or using ***efibootmgr -o*** command, I am unable to get Arcolinux to boot.

Both OSs appear in Xubuntu's grub menu, and I have run ***sudo update-grub*** several times just to be sure, but choosing Arcolinux goes nowhere; the system freezes and it just shows the grub background image which remains till I shutdown holding the power-button.

If I set the Arcolinux as priority in UEFI, Arcolinux's grub appears, as expected, again with both OSs showing in the menu, but from this grub menu both OSs will boot with no problem.
What I wish for is the have Xubuntu as boot priority, and managing grub but to be able to boot Arcolinux from that when I need it.

Incidentally, I am getting the same problem on both my desktop and laptop machines, both with the same two OSs, making me wonder if this is perhaps something specific to Arcolinux.

The Boot-info script has given me the following output.
[https://paste.ubuntu.com/p/3zm4RDPyfq/](https://paste.ubuntu.com/p/3zm4RDPyfq/)

---

### Post by dragonfly41 on 2020-07-06
Perhaps try installing rEFInd into your EFI partition? I find that it scans multiple loaders well with its own GUI which can be tweaked to suit.
Study also options in refind.conf.
This will be installed as /efi/refind/ ... alongside your other loaders as listed.

---

### Post by Dennis N on 2020-07-06
I use a custom menu entry employing chainloader command for booting non-Ubuntu OS in a multiboot system. 

Example: To Boot Manjaro GNOME:

```
menuentry 'Manjaro GNOME sdc' {
insmod part_gpt 
insmod fat
search --no-floppy --fs-uuid --set=root 3B32-882D
chainloader /EFI/Manjaro/grubx64.efi 
}

```
(It works for other Ubuntu too, but in that case, you need a 2nd EFI system partition)

---

### Post by ajgreeny on 2020-07-07
Thank you Dennis N; that did it!

I chain linked from my Xubuntu grub to the Arcolinux grub menu using your entry, edited obviously to my own EFI folder contents, adding that section at the bottom of ***/etc/grub.d/40_custom*** and it worked fine.

I used to do something similar to this a very long time ago, in an old BIOS machine with two HDDs, but I admit I had forgotten all about that until you mentioned it here, so many thanks for setting me off in the right direction.

I still can not figure out why the Arcolinux menu allows me to boot to both OSs but the Xubuntu grub menu just froze if I chose Arcolinux, and went nowhere, until I added that extra chainlink.

---

