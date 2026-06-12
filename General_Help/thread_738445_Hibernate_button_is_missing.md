---
title: "Hibernate button is missing"
date: 2008-03-28
forum: General Help
---

### Post by TheLions on 2008-03-28
I can't hibernate because hibernate button is missing at showdown screen!!!
How to fix it???:confused::confused::confused:

---

### Post by pointone on 2008-03-29
Do you have a swap partition? What's the output of "sudo cat /proc/swaps" and "sudo cat /etc/fstab"?

---

### Post by TheLions on 2008-03-30
Sorry for no response, I had no electricity, didn't paid the bills!!:lolflag: 

[COLOR="DarkOrange"]"sudo cat /proc/swaps":[/COLOR]
[PHP]Filename                                Type            Size    Used    Priority
/dev/hda3                               partition       1020116 13776   -1
/media/hda5/swap_file                   file            1023992 0       -2
[/PHP]

[COLOR="DarkOrange"]"sudo cat /etc/fstab":[/COLOR]
[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e3c52024-45f0-41fb-8978-54095b564b8a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=66D87A38D87A0699 /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=E824B79424B7646A /media/hda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda7
UUID=D0107A7E107A6B7C /media/hda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=131FDA30FFF32C01 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=4C7F694B911A4A24 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=AC1EAE1B0D6ACFE1 /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=023A53A8C7465810 /media/sda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=de949df1-b23e-4e4c-a21b-a5e4f111b105 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/media/hda5/swap_file       none            swap    sw              0       0
[/PHP]

---

### Post by pointone on 2008-03-30
A bit of a random guess here, but try disabling the swap file. Hibernate only works with swap partitions, not swap files. Now, you have both a swap partition and a swap file. However, I'm thinking the GNOME power manager is detecting the swap file and deciding "Uh oh... Hibernate isn't going to work!" and removing the button.

Edit fstab, comment out the very last line and try again after rebooting.

---

### Post by TheLions on 2008-03-30
You were right! After disabling the swap file hibernate button is there as it should be!

Now I have a new problem, after disabling swap file i don't have enough swap to hibernate and I don't want to mess around with partitions!

Is there any way to force hibernation with swap file?

---

### Post by nnamdi on 2008-03-30
yeah also have the same problem too i dont know how fix it mine is the shutdown and restart buttons are no longer therestill very confused pls i hope it will be able to get fix

cos to turn off my system i have press the button on my system down i dont think that is health 
hellppppppp lol

---

### Post by nnamdi on 2008-03-30
yeah also have the same problem too i dont know how fix it mine is the shutdown and restart buttons are no longer therestill very confused pls i hope it will be able to get fix

cos to turn off my system i have press the button on my system down i dont think that is health 
hellppppppp lol

---

### Post by TheLions on 2008-03-30
try here:
[https://wiki.ubuntu.com/DebuggingGNOMEPowerManager](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager)

---

### Post by nnamdi on 2008-03-30
yeah also have the same problem too i dont know how fix it mine is the shutdown and restart buttons are no longer therestill very confused pls i hope it will be able to get fix

cos to turn off my system i have press the button on my system down i dont think that is health 
hellppppppp lol

---

### Post by nnamdi on 2008-03-30
yeah also have the same problem too i dont know how fix it mine is the shutdown and restart buttons are no longer therestill very confused pls i hope it will be able to get fix

cos to turn off my system i have press the button on my system down i dont think that is health 
hellppppppp lol:lolflag:

---

### Post by pointone on 2008-03-30
nnamdi, please don't hijack threads like this. Your problem is likely very different, as it has nothing to do with swap. Start a new thread for yourself.

I think suspend2 allows you to use a swap file, but I've never tried replacing the suspend/hibernate solution in Ubuntu. Poking around on [their website]("http://www.tuxonice.net/") might yield some clues, but personally, I think the easist solution would be to simply expand your swap partition.

---

### Post by nnamdi on 2008-04-01
am so sorry about that i shouldn't taking over your complain once again sorry about that 
thanks

---

### Post by Nathan.Flow on 2008-04-20
hey I think after installing xserver-xgl this causes the other buttons in the log out menu to go MIA so if you uninstall xserver-xgl the missing buttons should come back. At least they did for me..

sudo apt-get remove xserver-xgl
or use the GUI package manager of your choice.

---

