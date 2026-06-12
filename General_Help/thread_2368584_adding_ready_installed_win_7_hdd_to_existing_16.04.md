---
title: "adding ready installed win 7 hdd to existing 16.04 win10 dual boot"
date: 2017-08-12
forum: General Help
---

### Post by columbus2012 on 2017-08-12
Hi all. 
I have a functioning 16.04 / win10 dual boot on one drive. 
I also have a separate hdd boot-able drive with win 7, (installed for the same pc). I have been swapping the drives by physically plugging / unplugging to boot from either the win 7 installation or ubuntu / win10
Is there any way I can add the win7 drive to the the existing grub boot options without having to reinstall the already boot-able & operating win 7 install on the separate drive.

Needless to say this causes some problems. 
Bob

---

### Post by dragonfly41 on 2017-08-12
You can purchase a USB container for your dual boot drive.
Place your dual boot drive in container.
Connect external container to your PC via USB cable.
Select USB drive from BIOS.
You will see grub menu.
Choose win 10 / Ubuntu.

---

### Post by oldfred on 2017-08-12
Can you add the drive internally?
Windows checks to see if booting internally or not and will not work with USB drives. It should work if you have an eSata connection or internal SATA connection.

If installed internally grub will find the separate Windows installs and offer to boot them.
Most Windows installs like and are configured to be first drive, so that may be an issue, but you have to try first.

---

### Post by columbus2012 on 2017-08-13
Thanks dragonfly41, but not the answer. 

    @oldfred thanks.  Yes the drive is installed internally.  
I tried with both it and the Ubuntu/win10 drives connected and recognised by the BIOS. I hoped Ubuntu / Grub  would find the extra win7 boot drive automatically - but it does not.     

So I wondered if there were some way to force / edit Grub to do so. (It is a pain swapping cables to boot the alternative, with the resultant BIOS objections).

---

### Post by johndough2 on 2017-08-13
Hi

If installed and recognised and will boot when the other drive is unplugged, makes me wonder if there is some sort of cable or drive conflict.

Not likely with SATA, but possible with PATA.

However 

askubuntu  com / questions/77439/  how-to-add-windows-7-loader-to-grub

may give apointer.

---

### Post by columbus2012 on 2017-08-13
@ johndough2  Both drives SATA

---

### Post by VMC on 2017-08-13
With both drives plugged in, what's the output of ```
sudo os-prober
```

osprober will detect partitions/drives.

```
sudo grub-mkconfig
``` Will build a grub.cfg output on the screen. You can redirect to a file of choosing. Both info would be helpful here.

EDIT:
For example, when I insert my external sata hd,  osprober can see it as sdb drive. Here's the result:
```
$ sudo os-prober
 
/dev/sda1:Windows 10 (loader):Windows:chain
/dev/sda7:Ubuntu Artful Aardvark (development branch) (17.10):Ubuntu:linux
/dev/sdb6:Fedora release 25 (Twenty Five):Fedora:linux
/dev/sdb7:unknown Linux distribution:Linux:linux
/dev/sdb8:CentOS Linux release 7.3.1611 (Core) :RedHat:linux

$ lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda       8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1    8:1    0 101.4G  0 part 
&#9500;&#9472;sda2    8:2    0   440G  0 part 
&#9500;&#9472;sda3    8:3    0     1K  0 part 
&#9500;&#9472;sda5    8:5    0     2G  0 part [SWAP]
&#9500;&#9472;sda6    8:6    0  98.6G  0 part /
&#9500;&#9472;sda7    8:7    0  68.9G  0 part 
&#9492;&#9472;sda8    8:8    0 220.7G  0 part 
sdb       8:16   0 596.2G  0 disk 
&#9500;&#9472;sdb1    8:17   0     1K  0 part 
&#9500;&#9472;sdb5    8:21   0   3.9G  0 part 
&#9500;&#9472;sdb6    8:22   0  97.7G  0 part 
&#9500;&#9472;sdb7    8:23   0  97.7G  0 part 
&#9500;&#9472;sdb8    8:24   0  97.7G  0 part 
&#9500;&#9472;sdb9    8:25   0  97.7G  0 part 
&#9492;&#9472;sdb10   8:26   0 201.6G  0 part
```

So if osprober doesn't see the second hd, then something else is amiss.

---

### Post by columbus2012 on 2017-08-13
Thanks all ! it turned out to be easier than I thought, -  so obvious that I overlooked it 

 Sudo update-grub 

 All boot options shown now  - Ubuntu . . Win10 loader, win7 loader.

---

### Post by columbus2012 on 2017-08-13
I can't find the ***"Mark thread solved"*** option - I remember seeing it but not where :confused::redface:

***FOUND IT ***! - Think I win the Dummy of the day award :-((

---

