---
title: "Ubuntu boot in BIOS not going away"
date: 2015-01-13
forum: General Help
---

### Post by Andrew_Paulus on 2015-01-13
I recently installed Ubuntu to my laptop but then deleted it (I will reinstall it again eventually) but I just want to get rid of the option to boot up to it in my BIOS, seeing as it is unnecessary because I deleted it off my laptop.

There were four "Ubuntu" listings, but with the help of EasyBCD, I got rid of three. Now the fourth seems so be stuck for no apparent reason, even after trying to delete it in EasyBCD multiple times.

Here is a picture of my BIOS, THANKS!!:

EDIT: Sorry the pic is so big :/

[SIZE=1][IMG]http://i.imgur.com/MjRFJXw.jpg[/IMG][/SIZE]

---

### Post by phidia on 2015-01-13
You're using the windows boot manager I think-try the instructions [here]("http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu"). Hope that helps.

---

### Post by Andrew_Paulus on 2015-01-13
Ubuntu doesn't come up on the list.

---

### Post by phidia on 2015-01-13
try? > bcdedit /delete {ST9750420AS}

---

### Post by Andrew_Paulus on 2015-01-13
No luck :(

---

### Post by oldfred on 2015-01-14
With UEFI, there is no reason to use EasyBCD for booting, but it may be useful for editing BCD. Windows has its own tools also.

Do you still have an Ubuntu folder in the efi partition. You need to delete that first.
Then you should be able to use efibootmgr from live installer to remove any extra entries in UEFI. UEFI has its own NVRAM and remembers entries. And Windows does something about syncing UEFI & its own BCD which adds confusion.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
modprobe efivars
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by konrad6 on 2015-01-14
You can always take the BIOS battery out for a minute, and it'll reset the boot menu to the default. If you feel comfortable ripping open your laptop that is...

---

### Post by Andrew_Paulus on 2015-01-14
> **oldfred said:**
> 

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
modprobe efivars
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.


So I do this all when I insert the Ubuntu disk, boot to it, try it (but not download it), and use the Terminal etc.?

---

### Post by oldfred on 2015-01-14
That is correct.

---

