---
title: "Another &quot;Can't Boot&quot; thread"
date: 2015-09-17
forum: General Help
---

### Post by misterbreadcrum on 2015-09-17
So this has happened to me a couple of times but I've always been able to fix it with a combination of Gparted, disk-repair, and boot-repair tools/isos but this time I'm at a loss.  I'm using a Samsung Series 5 ultrabook.

I found Windows 10 to be entirely unsatisfactory given the hype and decided to switch back to my favorite Linux Distro, Ubuntu Gnome.

Last couple of things I did.

-Disable fast BIOS, disable Secure Boot, and rearrange boot priority to boot from my usbs.
-Ran Gparted and formatted my disks (a 24GB flash drive and a ~500GB HDD.)
-Got Ubuntu to boot through the Super Grub Repair disk (which actually won't load anymore) and through that tried installing and running boot-repair, it claimed to have worked but didn't.
-Try to install something else, like Linux Mint and Arch Linux.  Not booting.
-Throw boot-repair onto a usb and boot onto that.  It opened with only the option to create a boot repair summary, which can be found at [http://paste.ubuntu.com/12437962/](http://paste.ubuntu.com/12437962/)

Trying to boot without any usbs or with the Ubuntu live usb plugged in results in an endless boot loop.  I really have never had this much trouble getting an OS installed on my machine, so I'm looking to get some help.  Let me know if anyone can help.

---

### Post by oldfred on 2015-09-17
Your sda drive shows a Windows type boot loader and configured for gpt partitions, but no partitions at all???

As an Ultrabook the 24GB SSD was configured a Intel SRT. And that was seen as RAID by the Ubuntu installer. Some turned off SRT and used the 24GB as / (root) and put /home or /mnt/data partition(s) on hard drive. 

Did you keep systems as UEFI?, or keep gpt and still install in BIOS boot mode? Did you use 24GB as / or was entire install on hard drive?

If you installed other systems, not sure where you are at now?

       Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)

---

### Post by misterbreadcrum on 2015-09-17
I guess I'm really lacking in sleep.  I tried installing Ubuntu using the 'something else option' and it allowed me to select my HDD 500 (which is the only listed non-usb drive in bios) as the boot partition.  Everything works fine now

#-o

---

