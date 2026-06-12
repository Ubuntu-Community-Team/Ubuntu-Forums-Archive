---
title: "Boot issue"
date: 2020-01-13
forum: General Help
---

### Post by emanual4real on 2020-01-13
I'm new to Ubuntu so please be gentle :)

Running Ubuntu 18.04 server.  Last thing I did, I enabled the firewall ```
sudo ufw enable
``` and rebooted.  Couldn't ssh in so figured I must not have that port open and connected a monitor.  PC hadn't booted back to a prompt yet but was stuck on the Ubuntu splash screen with the 4 dots.  After a while, it wanted the password for the IP address of my shared Win10 PC drive on the network.  There is no password and the root password doesn't work.

If I reboot I can get back to the grub loader.  Ubuntu Recovery Mode locks up on `Starting Load/Save RF Kill Switch Status`.  PC rythmic sound, maybe hard disk spinning not sure.


[LIST]
[*]Ryzen 7 2700 3.2 GHz
[*]Gigabyte B450 I Aorus Pro Wifi mini ITX
[*]G.Skill Trident Z Neo 32GB DDR4-3600
[*]Seagate Constellation ES 3TB x 4
[*]HP EX900 500 GB m.2-2280 NVME SSD (Ubuntu installed here)
[*]Gigabyte Geforce GTX 1650 4GB Mini Itx oc
[*]550W power supply
[/LIST]

---

### Post by emanual4real on 2020-01-16
I've no idea what to do.

If i do a fresh Ubuntu install, it works for a little while.  I don't know what breaks it.  Eventually I'll reboot and get the emergency boot page.

Attempted to user Boot Repair tool and still not working:

[http://paste.ubuntu.com/p/thSVY498b7/](http://paste.ubuntu.com/p/thSVY498b7/)

---

### Post by emanual4real on 2020-01-17
So I figured out what was wrong but opens up new questions.  I had created a raid and mounted it.  After reboot, the mount disappears.  So my /etc/fstab was bad and I loaded the boot repair tool and commented out the raid line and was able to boot normally.

Now why is my raid disappearing?

---

### Post by oldfred on 2020-01-17
do not know RAID.

But you show 2.7TB drives using MBR(msdos). So you have crippled drives to be only 2TB. See line 442 in Summary Report.
MBR was created in the 1980's when KB was standard, MB very large and GB unheard of. So they set the max to 2TiB.
You need to use gpt partitioning. And then have to have either the ESP - efi system partition for UEFI boot or a 1 or 2MB unformatted partition with bios_grub flag for BIOS boot. Otherwise grub will not correctly install.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

