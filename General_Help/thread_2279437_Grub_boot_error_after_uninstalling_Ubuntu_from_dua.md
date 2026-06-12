---
title: "Grub boot error after uninstalling Ubuntu from dual boot with Windows 8.1"
date: 2015-05-23
forum: General Help
---

### Post by michael285 on 2015-05-23
Hello! I have recently uninstalled ubuntu from my windows 8.1 dual boot by going into disk manager and deleting the three partitions (Home, swap space, and root), then I went into command line and entered in the bootrec.exe /fixboot command, as well as the other bootrec command line you have to enter in as well, and restarted my computer but on reloading, I get this 
[h=2][SIZE=2]Minimal BASH-like line editing is supported-[/SIZE][/h]
And I cannot boot back into Windows. Currently I have put in my Ubuntu LiveCD usb and opened up gparted, but I don't know which partitions to delete to fix the grub loader error. I have tried just about everything to fix my boot loader. I went into BIOS but it won't let me do anything with Windows boot order. I saw from somewhere in these forums that you can use Gparted to fix it, but I don't want to accidentally mess anything up. I tried using the recovery drive to automatically fix the error, but Windows said it was unable to. Here's what my partition table looks like



[IMG]http://i.imgur.com/6afMqcR.png?1[/IMG]

---

### Post by oldfred on 2015-05-23
If you get grub, try typing "exit" without quotes.

But since you have UEFI, it has NVRAM and saves its boot entries. And it updates from the ESP - efi system partition. You should just be able to go into UEFI and reset Windows as default boot.

To fully houseclean, you also need to delete the ubuntu folder in /EFI/ubuntu but keep /EFI/Microsoft and if you have it /EFI/Boot. You have to do that first, then delete entries in UEFI with efibootmgr.

I do not know how to do that from Windows, I am sure there is a way. I do not think Windows normally mounts the efi partition and should have its own efibootmgr. Or maybe just edits of its BCD.

You can easily make the edits with Ubuntu live installer in live mode. Details in link in my signature below if interested in using live installer.

---

### Post by michael285 on 2015-05-23
You beautiful genius. It worked!! 


I clicked on your sig and followed the "Really UEFI boot menu edits" UEFI menu cleanup instructions. Then I noticed I had two instances of ubuntu in the boot order, one of them being above Windows Boot Manager, so I just deleted both


[TABLE]
[TR]
[TD="class: votecell"]Thank you!!![/TD]
[TD="class: answercell"][/TD]
[/TR]
[/TABLE]




P.S: The main reason I got rid of Ubuntu was that my laptop wasn't fast enough to handle the dual boot, incase you needed an inquiry or something.

---

### Post by oldfred on 2015-05-23
Glad that worked.

But operating system really depends on what software you want to run.

I have Ubuntu on my 2006 laptop with 1.5GB of RAM and whatever default Intel video it has.
But it cannot run Full Ubuntu with Unity, so I install fallback or gnome panel which is lighter weight gui like older gnome2.
Others suggest Lubuntu or Xubuntu if system does not have a lot of RAM or video capabilities.

---

