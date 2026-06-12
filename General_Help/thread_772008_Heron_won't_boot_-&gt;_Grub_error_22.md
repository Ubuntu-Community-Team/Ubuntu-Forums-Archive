---
title: "Heron won't boot -&gt; Grub error 22"
date: 2008-04-28
forum: General Help
---

### Post by Dennis Beekman on 2008-04-28
I installed heron without any problems on my laptop and it worked absolutely fine for me... even the desktop effects worked out off the box with my ati card (amazingly enough).

However when i wanted to install Ubuntu 8.04 LTS on my normal Desktop Machine it refused to boot after installing it onto my hardrive.

My Machine:
- Asus G-Surf 365 Gaming Motherboard.
- Asus Radeon 3850 256MB PCI-E Graphics Card.
- AMD Atlhon 64 X2 6400+ Black Edition.
- 2 GB G.E.I.L DDR2-800
- PCI Sata Raid Controller
- Samsung Spinpoint Harddrives 1x250GB 2x1TB Sata
- Maxtor Harddrive 1x 300GB IDE
- 1x Samsung DVD-RAM IDE

I installed the 2 Terrabyte drive via the raid controller and installed ubuntu onto the 250GB one this is /dev/hdc

the partitions on it are as follows:

- HDC0=> 2GB => Swap
- HDC1=> 25GB => /home
- HDC2=> 133GB => /

When i booted my machine it gave the normal grub boot loader and then failed stating "error 22 -> the partition does not exist"
When i press enter it gives me the menu options that i am used to  but when i press them again it says the above error has occured.

I tried reinstalling grub using the live cd by doing the following (suggested on the net):

```
sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit
```

this has not solved the problem, what can i do now ?

---

### Post by justleen on 2008-04-28
on the menu you can press 'e' to edit the hoglighted option.. you can then change the disk where grub is looking for the kernel. just try some different paths. 

Another option would be [supergrub,]("http://supergrub.forjamari.linex.org/") i had some very good result with that

---

### Post by Dennis Beekman on 2008-04-28
I solved it !!

When i installed ubuntu under the livecd my first obboard hardrive was hd2 because my 2 sata hardrives on a pci controller where seen as hd0 and hd1 by the livecd system.

When i rebooted the machine finds my oboard controller first and used the / drive as hd0 instead of hd2 and therefore the grub settings are incorrect.

When i manually change the grub entry like the above poster suggests i was able to actually get it to boot normally and 8.04 works absolutly fine for me but the same happens as in the livecd my harddrive is found as hd2 again so when trying to do the 'find' command under grub is still find my root as (hd2,2) wich would be correct for the os but not for grub... so this command won't fix the problem and root=(hd0,2) is not accepted by grub because it says "the file or partition does not excist." wich is true aswell :-)

The answer is to simply change the entry's for all tree boot option from hd2,2 to hd0,2 in /boot/grub/menu.lst ones you have initially booted by using e (edit) command in grub when it fails.

i hope this helped anyone ho has a similar problem !!

---

