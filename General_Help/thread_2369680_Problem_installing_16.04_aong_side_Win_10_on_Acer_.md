---
title: "Problem installing 16.04 aong side Win 10 on Acer laptop"
date: 2017-08-25
forum: General Help
---

### Post by Tom_Carr on 2017-08-25
I just did an install of ubuntu 16.04 on an Acer laptop running Win 10.  I did the install that leaves Win 10 on the computer and lets you select Ubuntu or Win 10.  When I did the restart at the end of the install, Win  10 came up and I got no option to run Ubuntu.  I  have turned it on and off several times with the same results.  Win 10 comes up with no option to run Ubuntu.  What  happened?  What should I do?

---

### Post by Tom_Carr on 2017-08-26
No replies.  Am I asking in the wrong place, or have I not given enough information, or what?

---

### Post by oldfred on 2017-08-26
Standard issue with all Acer.
Acer has a unique requirement of setting a UEFI supervisory password and enabling "trust" from inside UEFI on the grub/ubuntu .efi boot files.
Also make sure you have newest UEFI from Acer. Some older threads may mention downgrading UEFI, but newer threads say newest UEFI from Acer works. Not sure what models.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

### Post by Tom_Carr on 2017-08-26
What if I don't care about dual boot and just  want to make it an ubuntu laptop.  Do I  have  to go through [COLOR=#000000] setting a UEFI supervisory password and enabling "trust" from inside UEFI on the grub/ubuntu .efi boot files?[/COLOR]

---

### Post by oldfred on 2017-08-27
As I understand the posts from those with Acer, yes.
Acer only automatically allows Windows to boot, others require the user to allow them.

One of the other work arounds is to use the "Windows Boot Manager" as the description to boot shimx64.efi. If Acer is like HP & others and only uses description, not actual boot files that would be another way to boot. If you want details on that it is in the link in my signature.

And another is to use fallback or default hard drive entry. Not seen an Acer user use that as the trust setting works. Other brands require one of many other work arounds.

       Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi) 
            Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

