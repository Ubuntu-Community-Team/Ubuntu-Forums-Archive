---
title: "Unable to boot into Ubuntu/Windows"
date: 2015-12-30
forum: General Help
---

### Post by ido5 on 2015-12-30
Hello, 

I have been running Ubuntu 15.10 on my PC alongside windows 10 for about a month now. I am not a complete beginner but my knowledge is very limited. For the past 3 days I am unable to boot into Ubuntu or windows. Instead of the usual grub menu I get an error message saying no boot device was recognized on restarting the computer. Restarting it a few times might bring up the grub menu eventually but when trying to boot into ubuntu or windows it just gets stuck on a black/purple screen. I was able to boot into windows once after waiting for about an hour for it to load but the system was just so slow it was unusable. I tried booting ubuntu from a live CD and trying many fixes I could find online but none of them worked. I ran boot-repair a few times, although the settings seems to be right and the program reported it successfully completed its task the problem still exists. I tried manually forcing a new installation of grub2 to my efi partition and it didnt work either. At this point I have no idea what to do.

I think it's also worth mentioning I have experienced something similar a month or two ago. Back then I was only running windows. I woke up to a screen saying no boot device was recognized. I had to restart the pc a few times before windows could even load. And when it does it was just slow as hell. I ended up reinstalling the system and a few days later installing Ubuntu as well. Before installing Ubuntu I had to convert my partitions to GPT and change windows to boot on UEFI mode since for some weird reason I was unable to load ubuntu from a live CD on legacy mode. I used this [http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx) tutorial and everything went well. Windows was successfully converted and I was able to install Ubuntu. 

pastebin from boot repair: [http://paste.ubuntu.com/14278998/](http://paste.ubuntu.com/14278998/)

Any help would be very much appreciated.

---

### Post by ido5 on 2015-12-31
bump

---

### Post by ido5 on 2016-01-01
bump

---

### Post by yancek on 2016-01-01
Your boot repair output shows you have windows boot code in the MBR but you also have and EFI partition with both windows and Ubuntu files there.  You can't mix them, needs to be either both EFI or both MBR.   If you use GPT partitioning then with windows you must use EFI.

Generally the boot repair output will show boot files listed by name for both windows and Ubuntu under the partitions near the top of the output.  None showing for either system.  Not sure why that is.  There is also no grub.cfg file shown from the hard drive but only on the flash drive.

It looks like your windows system was hibernated which is why you see all the message about windows being in an unsafe state.  Not sure if this will resolve your problem but if you can access the BIOS, try turning off anything  related to hibernation, fastboot or fast startup .

---

