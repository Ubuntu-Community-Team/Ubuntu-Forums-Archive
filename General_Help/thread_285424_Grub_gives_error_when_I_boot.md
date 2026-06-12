---
title: "Grub gives error when I boot"
date: 2006-10-26
forum: General Help
---

### Post by wr0x2 on 2006-10-26
When I boot my machine, I get error 15 from grub. I removed a drive earlier, but checked my menu.lst file and device.map file and changed everything several ways. Here is the layout of my system:

/boot: raid 1, 100mb partition on /dev/sda1 and /dev/sdb1
/: raid 0, ~600gb partition on /dev/sda2 and /dev/sdb2
swap, 3 partition of my sata drives, raid0

being raid1, the /boot acts as an individual partition and can be read on boot. I have been booting this way for a few months now and have not had any problems. The drive I removed was IDE, and my the drives I use now are sata. Also, I put the other drive back in (reformatted) to see if that would make the machine boot, but no luck. What could the issue be here?

---

### Post by Herman on 2006-10-27
> Grub error 15 : File not foundThis error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.Probably there is still some small mistake in your menu.lst file which means grub can't find the exact kernel you specified by the exact path you specified. 

Try using grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
 to find your kernels and boot up that way, then edit your menu/lst with the correct details.
 
Regards, Herman :D

---

### Post by wr0x2 on 2006-10-27
The path to my kernel as stated in menu.lst is /vmlin..... and matches up exactly with the kernel in my boot partition.

---

### Post by Herman on 2006-10-27
Well okay then, it's up to you, no-one's forcing you. Grub's Command Line Interface is a great way to troubleshoot Grub problems though, because you have the advantage of all kinds of useful feedback. For example, if you have removed a hard disk, Grub may be designating your remaining hard disks differently now. You would pick that up in CLI grub right away. But never mind, it's your computer.  I won't bother you any more now, bye.

---

### Post by tagginannie on 2006-10-27
Try [Super  Grub]("http://adrian15.raulete.net/grub/tiki-index.php") With it you can fix various boot problems boot Linux you
can also fix your dual boot with that other evil OS and Linux:D and you can also reinstall Grub and install Lilo. but a word of cauton  do try the Lilo option because it is still beta



Hope this helps
Suzy

---

### Post by wr0x2 on 2006-10-29
Herman - I misread the grub cli to mean grub's setup tool. I can't use the cli that you mean because grub does not even get to that on boot - error 15 is printed and I do not get my grub menu. Sorry I did not make this clear.

Suzy - thanks, I'll try the grub disk.

---

### Post by Herman on 2006-10-30
I'm glad Suzy posted that link to [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php"), thanks Suzy! :D
wr0x2,
You can use Super Grub Disk in either the [Super (menu) mode]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"), or press 'c' from a menu for Grub's [COLOR=#33FF33][/COLOR][Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), whichever will be the most useful to you for the job you want to do. :D

Regards, Herman.

---

