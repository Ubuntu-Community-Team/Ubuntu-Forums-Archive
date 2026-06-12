---
title: "transfer my ubuntu installation to diff drive and dual boot"
date: 2016-05-26
forum: General Help
---

### Post by beba on 2016-05-26
Hi

Apologies if im posting in the wrong section, wasnt really sure where this belonged

My SSD (with windows 10 OS) died a few weeks back. I've always wanted to get into ubuntu so i used that as an opportunity to load Ubuntu on another drive and start using my PC again (my pc has 4 drives, other than the SSD)

Im about to get a new SSD soon and i want to install windows again, but I'd also like to keep my Ubuntu install and do a dual boot. The issue is I'd like both OS's to be on the SSD, so ill be getting a 256gb SSD and having two 128gb partitions for each OS (though i may make the windows partition a lil bigger, havent quite decided yet, if anyone can give me an estimate on a minimum size for ubuntu id appreciate it, im thinking 70gb might be enough for the OS and apps/files, will also be using my other drives to store bigger files)

So to pull this off ill need to make an image of the partition ive got ubuntu set up on, mount it to the SSD, then install windows 10 on the other SSD partition

Just wanted to check two things
firstly what software/app should i use to create the image and put it on the SSD?
secondly, do i have the order right? should i set up ubuntu first and then install windows or should i start with windows? or does it not matter? (i was thinking of installing windows second in the hopes my system would automatically detect the two Operating Systems and set up a dual boot, but im not sure if this is correct)
Its been about 8 years since i last experimented with dual booting (i had previously done a windows/redhat linux dual boot on an older PC, but wasnt ready to use linux at the time so i rarely used it) are there any additional steps to dual booting or is it just as simple as installing the second OS and my system would do the rest?

Any help or additional info about any issues i may face attempting this would be greatly appreciated. Im sure it would be easier to simply start with a fresh install of ubuntu but ive already spent ages setting the system up so its just right, dont wanna have to do all that work again.

Cheers,
Ben

---

### Post by yancek on 2016-05-26
20-25GB should be enough for the Ubuntu system partition.  You can use other space for data on a separate partition to be available from Ubuntu or windows formatted ntfs.

If you want to clone an installed system you can use clonezilla, an online search should take you to their site.

> (i was thinking of installing windows second in the hopes my system  would automatically detect the two Operating Systems and set up a dual  boot

Expecting the windows bootloader to automatically detect a Linux installation?  That is not a very realistic expectation.  About the only way you can do that in windows is to manually create entries after writing the boot code from the Linux partition to a file and using bcdedit.

If you are going to be using windows 10, you need to be informed about UEFI  and dual booting.  See the Ubuntu documentation page below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by beba on 2016-05-26
Thanks yancek, ill definitely study that link before going forward

Im also thinking about using a virtual machine instead of dual boot (my companys IT guy recommended it)
so the question is whether i use linux or windows 10 as my primary OS and the other as my VM

if i made an image of my current linux system (using clonezilla) would i be able to load that image to a VM?

---

### Post by sudodus on 2016-05-27
Linux systems, that only use free drivers (for example no proprietary driver for graphics or wifi), are portable - they work in most computers (of the same architecture (PCs with Intel/AMD processors)). But often is is as easy or easier to make a fresh installation in the new computer (or in this case, in the virtual machine.)

---

