---
title: "Uninstall Ubuntu 16.04 from win 10 dual boot, install apricity os"
date: 2016-08-06
forum: General Help
---

### Post by uyohn on 2016-08-06
Hey there

So I had Win 10 and Ubuntu 16.04 LTE dual boot, but then I decided to uninstall Ubuntu and install Apricity OS. So I deleted Ubuntu partitions, but I can't get rid of GRUB. I tried ```
bootrec.exe /fixmbr
```. Didn't work, grub still there. I made Installation CD for Apricity OS, but when I try to boot from it, it says: "EFI DVD/CDROM (MATSHITA DVD-RAM UJ8FBS) has been blocked by the current security policy."

Please, what can I do from there ? 

-uyohn

---

### Post by grahammechanical on 2016-08-06
With the UEFI boot system and hard drives with GPT partitioning scheme there will be efi boot files in an efi_boot partition. That efi_boot partition will hold Windows 10 efi boot files & also Ubuntu/Linux efi boot files.

I am guessing that the Ubuntu efi boot files are still there and that is why you have not got rid of Grub. You may also find that the UEFI boot system utility has an entry for Ubuntu. So, you may need to edit the listing in the UEFI boot system.

I am not speaking from personal experience in any of this but I have picked up a little bit of knowledge from reading threads on the forum. As for Apricity OS. It is none of my business.

Regards.

---

### Post by uyohn on 2016-08-06
Thank you. So what exactly should I do?

So will anybody please help me ? This PC is important for me - I have to do my job so please ... :(

---

### Post by oldfred on 2016-08-06
If an UEFI system, you just go into UEFI and change to make Windows first in boot order. Or you should be able to use one time boot key like f10 or 12. If you left fast boot on in UEFI you may have trouble getting into UEFI. Try cold boot.

It sounds like you have UEFI Secure boot on. Turn it off in UEFI. It may not be called Secure boot, but just "Windows" or "Other" or similar setting.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

You also need to remove /EFI/ubuntu folder in the ESP - efi system partition.

 Delete Ubuntu
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743) 

[URL="http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD"]
[/URL]

---

### Post by uyohn on 2016-08-06
Thank you I'll try it right now.

---

