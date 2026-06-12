---
title: "USB booting via CD on PCs without BIOS support for USB"
date: 2008-06-26
forum: General Help
---

### Post by CarstenA on 2008-06-26
Hi

I was wondering if anyone know of a bootable CD that could be used to get a machine to boot on USB dongle for PCs where there is no option to boot on USB in the BIOS?

I have been kind of fascinated by the idea of basicly running around with a persistent ubuntu installation on a USB dongle to be able to boot my OS anywhere :)

I havent found anything like this for Ubuntu and nothing really general, I did however find a floppy disk image for feather linux though -> [http://featherlinux.berlios.de/download.htm](http://featherlinux.berlios.de/download.htm) and tried to burn it on a cd, but I havent been able to get anywhere with that.

I did write to the creator of Ultimate Boot CD and his reply was this:
AFAIK, there is no generic way of booting a USB
device without BIOS support. All these floppy-assisted USB booting are quite specific to a certain OS or distribution.

Thus my question if anyone know of something like this for Ubuntu? Or got a general idea that could be used for other distroes aswell?

Thanks in advance :)

---

### Post by Psykotik on 2008-06-26
Why don't you give a try to slax? [http://www.slax.org](http://www.slax.org) 

I'm pretty sure it would completely fit your needs. There is a specific (not a general) boot cd you could use.

Slax is specifically portability orientated. I don't know why so many people bother to install other linux flavors on their USB key.

---

### Post by CarstenA on 2008-06-26
Hi

I am afraid you misunderstood me, what I am looking for is a CD that will allow to boot futher on USB for PCs where it is not directly supported to boot over USB in the BIOS.

And unless I am mistaken then putting Slax on a USB pin in a PC that dosent support USB booting in the BIOS will not do alot, or did I miss something? :)

---

### Post by issih on 2008-06-26
The basic trick that these boot cds use is they have a bootloader (e.g. grub or syslinux), and a copy of a linux kernel on them. The systm works by booting the kernel directly from the cd like a live cd. Once the kernel is up and running the system then has access to the usb drives and the root of the distribution is set to the usb drive, and X and the DE are booted from there.

Consequently the kernel never changes, your system will always boot with the one on the cd regardless of what you do (uness you recreate the boot disk). They do therefore tend to be quite tied to a specific distro.

Other than that, it is relatively simple to create one for ubuntu, indeed i did once do so to get my macbook working from usb (macs hate booting from usb).

I used the eltorito version of grub, and copied the latest vmlinuz and initrd.gz files from the /boot directory. After that its just a case of setting the kernel boot parameters correctly, I just nicked the ones from the live cd and changed the root to use the usb drive(identified by uuid so it is found regardless of machine).

Hope that helps

---

### Post by CarstenA on 2008-06-26
It actually helps alot, thank you :)

Can you give me the link to the Eltorito version you used?

Then I want to try and make a bootable CD with that and make the changes you wrote :)

Then after that if it works, I want to try to get it on that Ultimate boot CD because in my search for this I stumbled upon "a few" posts where people are asking about a CD that can do this :)

Then in theory this CD could be used to boot any distro or OS on USB, even XP :)

---

### Post by issih on 2008-06-26
I've attached the barebones of what I used...

The current files in the iso folder "linux" and "initrd.gz" are just empty placeholders. You need to copy across the kernel you are going to use and name it linux, and the corresponding initrd file and name it initrd.gz.

The eltorito version of grub is already on there, as is my menu.lst, lurking in the boot folder.

You will need to change the bit in menu.lst:

root=UUID=4828-40DB

so that the uuid refers to your usb drive (use ls /dev/disk/by-uuid when the flash drive is plugged in)

Whether you need the boot=casper and the persistent options is going to depend on how you do your install to the flash disk.

To make the iso for burning to a cd you will need to run something like:

      ```
mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot \
         -boot-load-size 4 -boot-info-table -o grub.iso iso
```

Hope you follow that

---

