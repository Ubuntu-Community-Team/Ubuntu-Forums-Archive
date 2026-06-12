---
title: "Ubuntu on Lenovo g50"
date: 2014-10-21
forum: General Help
---

### Post by charitosha on 2014-10-21
Hello everyone.
I got a lenovo g50 today and wanted to install 14.04 lts in it.
at the last steps of the installation, the instalaation would crash saying something about error 5 i/o. i tried 2 usb's and put them in two "ports". All 4 times i got the same errror.
then i tried 12.04 lts and installed it at the first time.
however each time that i switch on the laptop i get the error:
this product is covered by one or more of the following patents: us6,570,884, us6,115,776 and us6,327,625
then it mentiones the client mac address the guid and the dchp 
it takes some time there and then it loads into ubuntu. my boot order is: 1st-hdd, 2nd-odd, 3rd-network boot.
ubuntu is under EFI. If i remember correctly while installing i could choose between usb and efi usb (or something), i chose the latter...

If i reinstall ubuntu in the non efi way, will i still get this error?
if yes what then should i do???

i was messing around in the bios and fixed the problem here is what i changed:
basically only 2 things:
under boot tab and in the boot priority i chose UEFI first, while boot mode i left it as legacy support.
and the 2nd thing, which i think made the actual deference, is under the exit tab in the OS Optimazed Defaults i chose other OS

---

