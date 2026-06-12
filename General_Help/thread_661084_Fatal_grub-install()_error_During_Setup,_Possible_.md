---
title: "Fatal grub-install() error During Setup, Possible Bug?"
date: 2008-01-07
forum: General Help
---

### Post by Computer Guru on 2008-01-07
I was going to post this over in launchpad, but seeing as I haven't experienced it firsthand I figured I'd ask about it here first.

EasyBCD is a program used to configure the Vista bootloader to load up Linux and other operating systems. We wrote an Ubuntu-specific guide, and it seems our users are hitting a bug in Ubuntu setup?

The [current instructions]("http://neosmart.net/wiki/display/EBCD/Ubuntu") on dual-booting Vista and Ubuntu had to be modified because the Ubuntu setup was not installing GRUB correctly to individual partitions for many people attempting a dual-boot.

[The original instructions]("http://neosmart.net/wiki/pages/viewpage.action?pageId=10158085"):
[LIST=1]
[*]Tell Gutsy to install GRUB to the *bootsector* of the Ubuntu partition instead of the MBR
[*]Use EasyBCD to grab the bootsector and chainload it from the Vista bootloader.
[/LIST]

[These steps work fine for Fedora]("http://neosmart.net/wiki/display/EBCD/Fedora").

The problem is, a lot of users encountered a fatal installation error when Ubuntu tried to write GRUB to the bootsector instead of the MBR.
The members were using correct (hdx,y) notation at the GRUB location prompt, and also attempted to reinstall with /dev/sdxy notation as well; neither would work.

Some of the posts about this:
[LIST]
[*][http://neosmart.net/forums/showthread.php?t=1315&highlight=grub+fatal](http://neosmart.net/forums/showthread.php?t=1315&highlight=grub+fatal) (best documented)
[*][http://neosmart.net/forums/showpost.php?p=9249&postcount=26](http://neosmart.net/forums/showpost.php?p=9249&postcount=26)
[*][http://neosmart.net/forums/showthread.php?t=1309&highlight=grub+fatal](http://neosmart.net/forums/showthread.php?t=1309&highlight=grub+fatal)
[*][http://neosmart.net/forums/showthread.php?t=1324&highlight=grub+fatal](http://neosmart.net/forums/showthread.php?t=1324&highlight=grub+fatal)
[/LIST]

[Current instructions]("http://neosmart.net/wiki/display/EBCD/Ubuntu"):
[LIST=1]
[*]Install GRUB to the MBR as default.
[*]Restore Vista MBR.
[*]Use NeoGrub (GRUB4DOS implementation) to find the original Ubuntu menu.lst and use it instead.
[/LIST]

I'm not exactly sure what the error is, but grub-install() is not working correctly for a number of people from within Ubuntu setup when told to install to a partition.

I'd appreciate any tips or advice on this issue; and I apologize if it's already been reported or if there's a mistake in the instructions somewhere.

---

### Post by Computer Guru on 2008-01-08
Launchpad ticket: [https://bugs.launchpad.net/ubuntu/+bug/181276](https://bugs.launchpad.net/ubuntu/+bug/181276)

---

