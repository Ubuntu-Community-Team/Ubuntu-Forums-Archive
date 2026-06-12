---
title: "grub/efi update likely broke my dual boot with win8"
date: 2014-07-29
forum: General Help
---

### Post by fr33z0n3r on 2014-07-29
Hi,  I have a dell xps 18 pc running windows 8.1 and dual booting with Ubuntu 14.04.  There were a bunch of grub/efi updates that were apparently rolled out today and upon reboot, the computer gave an error that "Secure Boot Violation: an invalid signature was detected.  Check secure boot policy in setup".  This is preventing Windows from booting.

Any ideas on how to repair this?  Not sure undoing the updates in Ubuntu is the right way to go.  I am going to check out the bios/efi config to see if it lost its working config.

UPDATE:  Not a huge issue.  It just messed with the boot order in the EFI list.  We moved "Windows Boot Manager" to the first option and it booted right up.  But it leaves 2 "Ubuntu" options, one of which does not work on the computer and leads to the red error I mentioned above.   To prevent the confusion over 2 entries with the same name, I had previously edited one to say "UbuntuGood".  Which Ubuntu took out on me.

---

### Post by oldfred on 2014-07-30
You probably have two entries and one is shim and the other is grub.
Shim will work with Secure boot on, grub will not. Shim is the signed version of grub to be used with the signed kernels for secure boot.

Some show all the detail so you can see which is which.
       sudo efibootmgr -v
    
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

You can change boot order with efibootmgr.

 You would first type sudo efibootmgr -v to get a list of boot options. Note the number associated with the Ubuntu entry -- for instance, it might be Boot0005. You'd then type sudo efibootmgr -o 5 to make "Ubuntu" (actually GRUB) the default boot loader. (You can specify a set of boot loaders to be tried in order, as in sudo efibootmgr -o 5,1,2 to use 5, then 1 if that fails, then 2 if both 5 and 1 fail.)

---

