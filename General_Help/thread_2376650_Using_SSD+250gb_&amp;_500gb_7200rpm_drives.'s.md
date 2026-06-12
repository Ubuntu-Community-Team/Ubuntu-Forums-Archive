---
title: "Using SSD+250gb &amp; 500gb 7200rpm drives.??'s"
date: 2017-11-04
forum: General Help
---

### Post by binskipy2u on 2017-11-04
I’m getting a hexcore xeon 3.6ghz/16gb ddr3 ram, nvidia quatro 4000 @ 2gb ddr5 (got it for 249.00 believe it or not) I’m throwing a SSD along with the 2 aforementioned 7200rpm drives. I want to use the ssd as /root & /home while using the 250 & 500 for data/songs/pictures etc…
no need for a swap w/16gb ram.

hows’ this for partitioning… well first of all, when I install 'buntu, should I just install on the ssd drive then add the other 2 later? or hook’em all up and direct install to sdd and add mount-points for 250/500?

/root -30gb SSD
/home /rest of SSD

/mystuff1 250
/mystuff2 500

All ext4

is this a good idea?

the 500 has 52gb of music/data/pics/etc… so I wont format that one
but the 250 will be formated

Would 'buntu run "fast" with these specs and find the correct driver for that video card?

I want to make the MOST use of that video card(workstation card)

Does this look like a good layout? Any suggestions/experiences would be most helpful…thank you…

---

### Post by Bashing-om on 2017-11-04
binskipy2u; Hello;

Sure, looks fine to me that set up with the caveat that on the SSD you will want to set aside disk space for the overprovisioning:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)
And a few tweaks.

With that graphic's card there may be that there is no open source support - where the boot parameter "nomodeset" - will be of benefit - install the proprietary driver once fully installed.  Install release 17.10 for best results.
 
You will have to decide on how you want the storage drives mounted - that comes with time and thought .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2017-11-05
I like to have more than one install so I usually have multiple / (root) partitions on all drives. At least one install on every drive just for emergency boot if needed.
All drives are gpt partitioned and UEFI bootable.

I normally then do not use /home as a partition but use /mnt/data as I want all installs to have same data, but not necessarily same settings or versions of software.

Installer will only let you create typical system partitions like / & /home, plus many others you normally do not need with a standard desktop install.
You then add data partitions to fstab and set ownership & permissions on those partitions so you can easily use them.

You have another drive for backups or at least copy most critical data to flash drives or DVDs?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters

      [/URL]
 from Morbius1-----
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 

    [URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]
[/URL]

---

