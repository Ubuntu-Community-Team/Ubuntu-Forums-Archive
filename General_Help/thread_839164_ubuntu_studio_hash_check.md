---
title: "ubuntu studio hash check"
date: 2008-06-24
forum: General Help
---

### Post by jejeman on 2008-06-24
Hello,


I've downloaded iso image from here:


[http://cdimage.ubuntu.com/ubuntustudio/releases/8.04/release/ubuntustudio-8.04-alternate-i386.iso](http://cdimage.ubuntu.com/ubuntustudio/releases/8.04/release/ubuntustudio-8.04-alternate-i386.iso)

iso hash was ok. i compared with hash from here [http://cdimage.ubuntu.com/ubuntustudio/releases/8.04/release/MD5SUMS](http://cdimage.ubuntu.com/ubuntustudio/releases/8.04/release/MD5SUMS)

i burn it.

then i did chcksum from md5sum.txt on dvd with md5summer.exe from [http://www.md5summer.org/](http://www.md5summer.org/)

the results were fine except:

./install/netboot/pxelinux.0     hash did not match.

./install/netboot/ubuntu-installer/i386/pxelinux.cfg/default   does not exists.  the path is wrong it should be without /default

./pool/main/l/linux/firewire-core-modules-2.6.24-16-generic-di_2.6.24-16.30_i386.udeb  does not exists.  the extension for this file on dvd is .ud

./pool/main/l/linux/pcmcia-modules-2.6.24-16-generic-di_2.6.24-16.30_i386.udeb does not exists. the extension for this file on dvd is .ude

./pool/main/x/xfree86-driver-synaptics/xserver-xorg-input-synaptics_0.14.7~git20070706-1ubuntu4_i386.deb  does not exists. the extension for this file on dvd is .de

./pool/restricted/l/linux-restricted-modules-2.6.24/nic-restricted-modules-2.6.24-16-generic-di_2.6.24.12-16.34_i386.udeb does not exists. the extension for this file on dvd is .34_i38  obviosly not full file name was entered


./pool/restricted/l/linux-restricted-modules-2.6.24/nic-restricted-firmware-2.6.24-16-generic-di_2.6.24.12-16.34_i386.udeb does not exists. the extension for this file on dvd is .34_i386  obviosly not full file name was entered


I just wanted to know if this is normal or its bad iso. And if its bad from where should i download next time?

---

### Post by rubicon on 2008-06-24
Seems to be porblem with burning &#8212; filenames are just trimmed. What tool do you use for burning dvd? Anyways, just be sure to uncheck something like 'Windows compatibility mode' and 'Restrict filenames to XX characters'. Then try again.

---

### Post by rubicon on 2008-06-24
Well, in an addition to my previous comment, *md5summer* may be just failing to read long names. The best way to test ISO for readability and usefulness is boot it up and select 'Check disk integrity' from Ubuntu boot menu. I believe your iso should fine as long as its md5 is fine.

---

### Post by Kevbert on 2008-06-24
The other thing you should do when burning the CD is to set the burn speed to the lowest possible setting to minimize errors.

---

### Post by jejeman on 2008-06-24
Thanks for the replyies. 

I forgot to say that even when i mount iso in deamon tools the file names are trimed, so the burning didn't do the damage. But I agree that using the self check will make final decision.

---

### Post by jejeman on 2008-06-24
I did the cd integrity check. And the test said that cd is valid. So, I will accept that result, but still be puzzled with that trimmed filenames in windows.

thanks again for the replyies.

---

