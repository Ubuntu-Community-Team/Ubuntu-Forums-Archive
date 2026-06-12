---
title: "Where does the boot flag goes on a multipartition SSD ?"
date: 2016-03-02
forum: General Help
---

### Post by Cbhihe on 2016-03-02
I have a dual boot box where I want to get rid of WinXP.
I backed up all I needed, read on `os-uninstaller`, closed all apps and launched it.

In `os-uninstaller`, I selected the OS to be removed, but I have a doubt about where to place the boot flag, using *[Advanced options]*.
The reason is the box I am modifying has `/boot` in /dev/sda2 and `/` in /dev/sda5.

***In which one of those two partitions should I place the boot flag ?***

---

### Post by Dennis N on 2016-03-02
Grub does not need a boot flag to boot an OS when you install in BIOS mode. If you install on a UEFI system, you need to set the boot flag on the EFI system partition. But that does not apply on your computer if it had Windows XP on it. There is no need for a boot partition either. All that is required is a / partition and a swap partition.

---

### Post by oldfred on 2016-03-02
A very few BIOS systems need a boot flag on a primary partition to let anything boot.
Those motherboards must assume you have Windows as Windows requires the boot flag on the primary NTFS partition with its boot files.
So it does not hurt to have boot flag on any primary partition, if using grub or grub2 to boot.

Lilo & Syslinux also use boot flag.

---

### Post by sudodus on 2016-03-02
> **oldfred said:**
> A very few BIOS systems need a boot flag on a primary partition to let anything boot.
Those motherboards must assume you have Windows as Windows requires the boot flag on the primary NTFS partition with its boot files.
So it does not hurt to have boot flag on any primary partition, if using grub or grub2 to boot.

Lilo & Syslinux also use boot flag.

+1

For example many middle-aged HP computers want a boot flag to boot via grub.

---

### Post by Cbhihe on 2016-03-18
Apologies to all for not responding earlier. I had a bad spell during the  last 2 weeks. I am back on my feet/chair and behind the keyboard.

Thanks @Dennis,
Point  well taken on both the boot flag question and on my setup with a  separate boot partition. In fact, way back (about 18 months ago),  @oldfred had already pointed that out for me, responding to another query of mine.  I understand that it is not necessary. I set that box up that way because it was my first dual install and I wanted to experiment with a lot of coexisting lx flavors, all accessible via grub2. So I figured that segregating that play pen would do no harm, while it was not free to grow up past a certain point given by the partition size. It stayed that way even though I am past experimenting on that and now basically use an up-to-date Ubuntu 14.04 LTS on that machine.

Thanks @sudodus and @oldfred, 
indeed the boot flag seems to be required for my BIOS based verrry old HP laptop (8.5 years old and still going strong after a molten GPU replacement).

In the end I chose to place the bootflag on [FONT=century gothic]/dev/sda5 (root partition)[/FONT] while eradicating all traces of Win XP . 
A side note is I also moved and resized practically all my lx partitions around with Gparted from a liveCD session. and rebuilt grub, *fully expecting my system not to boot correctly*. 
It did boot at the first try and its grub menu now only proposes Ubuntu exactly as I wanted it.  :D

I close this thread as answered. Thanks again.

---

### Post by sudodus on 2016-03-18
Congratulations :KS

and thanks for sharing your solution :-)

---

