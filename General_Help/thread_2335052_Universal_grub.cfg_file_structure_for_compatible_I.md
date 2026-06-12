---
title: "Universal grub.cfg file structure for compatible ISOs (question)"
date: 2016-08-25
forum: General Help
---

### Post by T2uiYKb7 on 2016-08-25
What are the generals rules so I can boot any compatible ISO without Googling and copying and pasting stuff? (And hoping it's correct, often there isn't exactly the right entry out there and it can take a long time.)

Can any ISO with a intrid and vmlinuz file use the Ubuntu structure? 

What if a Linux ISO doesn't have either file but can be booted from ISO? 

What happens if the vmlinuz and intrid files are in the root do I put boot=/ ?

Any help would be greatly appreciated, cheers.

On a side note is there a way to test these grub2iso sticks in VirtualBox?

---

### Post by T2uiYKb7 on 2016-08-25
The Ubuntu ISO boot.cfg entry

________


[I]menuentry "64bit Ubuntu' {


set isofile="/iso/ubuntu_64bit_file.iso"


loopback loop (hd0,5)$isofile


linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject


initrd (loop)/casper/initrd.lz


}[/I]

---

### Post by Bashing-om on 2016-08-25
andrew.nz; Hello;

Have you seen:
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

The grub.cfg command structure also applies to the grub prompt.
From the grub prompt one can boot  the .iso .

[INDENT][INDENT]more than one path
[INDENT][INDENT]to an end
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by T2uiYKb7 on 2016-08-25
> **Bashing-om said:**
> andrew.nz; Hello;

Have you seen:
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

The grub.cfg command structure also applies to the grub prompt.
From the grub prompt one can boot  the .iso .[INDENT][INDENT]more than one path[INDENT][INDENT]to an end
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Cheers for the response. I boot ISOs regularly. I want to know to learn how to boot any ISO even if there is no documentation available.

Sometimes there is no intrid or vmlinuz files. Different people use different loopback and iso-scan commands. Some people use root= and others use boot= etc.

---

### Post by sudodus on 2016-08-25
Did you see this link:

[Arch Wiki - Multiboot USB drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

It is the most general link I have found.

---

### Post by T2uiYKb7 on 2016-08-25
Yup I posted that in my other thread. I don't want to copy and paste stuff I want to understand when to do what by looking at the files in the ISO.

---

### Post by sudodus on 2016-08-25
I think booting via grub-n-iso is 'cook-book' stuff rather than elegant and exact science with general methods. I think the different architects behind the various linux distros have their own way of thinking and programming, which makes the grub-n-iso things different between the distros and even versions of the same distros.

Most linux iso files today are hybrid iso files, which means that they boot when cloned to a mass storage device, typically a USB pendrive. That method is quite general and robust. And if you look at USB pendrives as temporary devices, you can store the iso files in some directory, and flash one of them into a pendrive, when you want to boot from it.

New versions of the linux distros appear quite frequently, and it is hard to keep a set of iso files up to date. With today's fast internet connections, you can even skip storing iso files, and simply get a fresh one via torrent, when you need it, and then quickly clone it into a fast USB 3 pendrive.

-o-

[mkusb](https://help.ubuntu.com/community/mkusb) is focused on cloning, and it works with all hybrid iso files. It works also with [compressed] image files of installed systems.

*mkusb* has an option to make [persistent live drives](https://help.ubuntu.com/community/mkusb/persistent) for the Ubuntu family flavours, Debian Jessie and ToriOS. The persistent live drives use a method similar to grub-n-iso, and I have no intention to extend it to more linux distros. Because of the 'cook-book' character of the method it would mean a lot a trial and error with new distros as well as with new versions of old distros.

---

### Post by oldfred on 2016-08-25
If I cannot find a good example of a grub stanza, I have mounted the ISO and looked that the paths & boot options it has in its boot, usually syslinux or grub if UEFI.
And many have different file names, so you have to check many common places.

---

### Post by yancek on 2016-08-25
A general rule is what oldfred points out above.  You loop mount the iso and take a look at the grub.cfg file (if one exists) or the isolinux/syslinux directory.  You should see an isolinux.cfg/syslinux.cfg or possibly a txt.cfg file on some systems.  You need to take a look and see which has a menu listing.

> Can any ISO with a intrid and vmlinuz file use the Ubuntu structure? 

No.  Some of the directories and files you see in Ubuntu don't exist in other distributions.  A casper directory for example.  If you look at different examples including the ones I posted in your other thread, you can see this.  The same applies for a 'boot' parameter which is not used or needed on some distributions.

Some distributions do not have a vmlinuz file, Opensuse for example.  They basically have just renamed the kernel from vmlinuz to linux.

You can test in VirtualBox by booting an iso directly.  You would first need to create a virtual machine instance as described at the link below.  Once you have done that, you will just need to make a change in the Storage option to boot any iso you have.  If you can't find a tutorial on that, post back.

  [http://askubuntu.com/questions/142549/how-to-install-ubuntu-on-virtualbox](http://askubuntu.com/questions/142549/how-to-install-ubuntu-on-virtualbox)

---

### Post by T2uiYKb7 on 2016-08-25
Thanks for the responses. Disappointing there's not an accepted grub2iso method. It would be awesome if there was an identical method every distro used, but that would require the Linux Fundation making an official standard (or something along those lines I have no idea how Linux standards or best practice etc works.) Everyone knows the majority of people use USBs but they still make ISOs aimed at optical media. 

Yeah I know how to boot an ISO from VirtualBox I meant using VirtualBox to text an entire grub2iso usb. To test the grub.cfg entries without having to reboot every time.

Will Linux always make ISOs or will a file aimed at USBs be made some day (soon)?

---

### Post by sudodus on 2016-08-26
ISO files are typical for PCs with Intel and AMD processors.

But for other kinds of computers/devices, for example mobile phones and raspberry pi, people are cloning/flashing the installed system directly from image files or compressed image files. That method works for many PCs too, see this link [Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS). It is also possible to use the [One Button Installer](https://help.ubuntu.com/community/OBI), which installs from a tarball.

---

