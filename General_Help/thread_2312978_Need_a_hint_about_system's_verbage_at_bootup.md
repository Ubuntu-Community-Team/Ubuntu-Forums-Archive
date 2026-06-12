---
title: "Need a hint about system's verbage at bootup"
date: 2016-02-08
forum: General Help
---

### Post by Grigoriy on 2016-02-08
Hello!

 I've got a dual boot W10/Ubuntu 14.04 laptop. I use GRUB2 as a boot  loader. In the BIOS I chose "Legacy BIOS" option (the laptop was  purchased with EUFI enabled system and W8 OEM). I don't know, maybe it's  something wrong that I did during the installation or something else...  Right now, I probably won't run and start changing or re-installing  stuff, but at least I'd like to know what it's all about. What happens  is that when I try to get into Ubuntu, quite often I end up in BusyBox  shell environment. Then I re-boot the machine and get to Ubuntu at last.  What is even stranger to me is that it doesn't always happen. Sometimes  everything is kosher and I get normally to the Ubuntu login screen  (it's a desktop environment -- Unity). Now...I would present here the  verbage I see on the screen while I try to get to Ubuntu, but end up in  shell. sdb being the Ubuntu HDD (usually).

 [      2.978708] usd 1-1.1: string descriptor 0 read error: -22
[      3.660632] sd 6:0:0:0: [sdb] No Caching mode page found
[      3.660665] sd 6:0:0:0: [sdb] Assuming drive cache: write through
 Gave up waiting for root device  Common problems:
 - Boot args (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
 ALERT!  /dev/disk/by-uuid/c6d0a763-50c0-4072-a72f-6286ec73709b does not exist.
 Dropping to a shell!
    
 BusyBox v1.21.1 (ubuntu...) built-in shell (ash)
(initramfs)_   (curson is blinking here)...

---

### Post by grahammechanical on 2016-02-08
The first thing that I would like to point out is that with a UEFI boot system & Windows 8 installed and then upgraded to Windows 10 it is very likely that Windows was installed in EFI mode and that means Ubuntu should have been installed in EFI mode as well. But you switched to BIOS/Legacy mode. You 
should be having problems loading Windows 10. 

If you can get to a working Ubuntu desktop then I would suggest that you update Grub

```
sudo update-grub
```

This message says that Grub cannot find the hard drive that Ubuntu is installed on.

> ALERT!  /dev/disk/by-uuid/c6d0a763-50c0-4072-a72f-6286ec73709b does not exist.

Provided that long string of alpha-numeric characters is the unique identification number of the Ubuntu drive and not some other number.

Regards

---

### Post by Grigoriy on 2016-02-09
Thanks for your reply!

Yes, that UUID is my Ubuntu's root partition, according to /etc/fstab

Who said I did the upgrade from W8 to 10? I never said that! I've purchased boxed W7 Pro and I was using it all the time till W10 has arrived. So the upgrade was from W7 to W10. And if I remember correctly, I made a switch in BIOS Setup regarding EUFI and Legacy BIOS exactly when I was about to install W7 (it was a clean install after formatting the W8 partition).

W10 loads fine! As long as I can get to GRUB2 to choose it there. It's the Ubuntu that often can't boot normally. As per updating GRUB... Yes, I would definitely look into that.

---

