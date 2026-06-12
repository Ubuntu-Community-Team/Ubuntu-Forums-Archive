---
title: "Windows Loader?"
date: 2007-05-10
forum: General Help
---

### Post by ardencaple on 2007-05-10
Hi, I don't know if this is the right place to post, but I'm looking for something that will do the following:

I have a (bootable) installation of the  Ubuntu Live-CD on a USB stick, but the PC I'm trying to boot has no facility to boot from USB.

Years ago, I used to use a utility called LOADLIN, that would boot linux while  running Win95/DOS.
I wondered if it is possible to use WUBI like this, on a win32 machine? 

The advantage would be that there would not need to be any changes made to the target machine whatsoever.

Alternatively, does anyone know of anything similar that already exists?

Ardencaple

---

### Post by JCakeC on 2007-05-10
i remember there was a distro that you would run linux as an application, but actually would reboot your PC and load linux on it, and it only worked on NTFS. Wubi as far as I have been testing can be used to do what you need, al you have to do is a few(actually many) modifications to the loader and that's it... and its NON invasive.

---

### Post by ardencaple on 2007-05-16
Interesting - 

Sounds like it's not available yet, though, and I don't have the skills to make the changes.

I have since tried QEMU/KQEMU and this works, but it's not quite what I want. Using QEMU, the linux distro
runs as a virtual system. The problem with this is that it runs rather slowly. As I said, I don't mind rebooting,
but if there is no facility to boot off USB, then I'm stuck.

Thanks for the interest

Ardencaple

---

### Post by ago on 2007-05-16
USB installation is untested. 

From wubi select the usb drive and install on it. IF it works you should be almost there:

1. copy C:\menu.lst, C:\grldr and C:\grub.exe to the root of the USB drive
2. follow the instructions on grub4dos wiki in order to put grub on the MBR of the USB HD.

The above should make your USB bootable and grldr.mbr in there should be able to load the wubi installation.

Again, this is completely uncharted territory... If it works let us know.

---

### Post by ecology2007 on 2007-05-16
You can search for supergrub, it is a cd that will allow you to boot the usb key.
You can also do that with grub4dos, by adding an entry in the windows boot.ini.

Give us more details (drives names, partitions, windows revision, what is the setup on your usb key, and anything you can find relevant) we will give you the procedure.

---

