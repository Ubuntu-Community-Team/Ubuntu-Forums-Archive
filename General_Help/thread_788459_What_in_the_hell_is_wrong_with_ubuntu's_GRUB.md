---
title: "What in the hell is wrong with ubuntu's GRUB??"
date: 2008-05-09
forum: General Help
---

### Post by jamieh on 2008-05-09
I have Ubuntu installed on an external hard drive, the internal has Windows. Whenever the ext. drive is turned off or unplugged, GRUB gives me an "Error 21" and won't boot anything, even though the internal Windows drive is damn-well bootable!!

I am NOT going to plug in my external drive every time I want to boot Windows!

(NOTE: I am speaking for a friend, I love my Ubuntu and wouldn't dream of booting into Windows more than once a month for "Windows-Only" stuff) :)

Can this be fixed?

---

### Post by grazed on 2008-05-09
> **jamieh said:**
> I have Ubuntu installed on an external hard drive, the internal has Windows. Whenever the ext. drive is turned off or unplugged, GRUB gives me an "Error 21" and won't boot anything, even though the internal Windows drive is damn-well bootable!!

I am NOT going to plug in my external drive every time I want to boot Windows!

(NOTE: I am speaking for a friend, I love my Ubuntu and wouldn't dream of booting into Windows more than once a month for "Windows-Only" stuff) :)

Can this be fixed?

no.

I would suggest reading into how grub works before you rant about it.

grub needs to read the boot files on your external hard disk to work properly / boot into windows. that's where most of grub is contained.

EDIT: I guess it's also worth mentioning, unless that drive has one hell of a fan in it, running an OS off of it is going to kill it pretty quick.

---

### Post by herrdoktor330 on 2008-05-09
> **jamieh said:**
> I have Ubuntu installed on an external hard drive, the internal has Windows. Whenever the ext. drive is turned off or unplugged, GRUB gives me an "Error 21" and won't boot anything, even though the internal Windows drive is damn-well bootable!!

I am NOT going to plug in my external drive every time I want to boot Windows!

(NOTE: I am speaking for a friend, I love my Ubuntu and wouldn't dream of booting into Windows more than once a month for "Windows-Only" stuff) :)

Can this be fixed?
one thing that always seems to through the grub off is the presence of extra hard drivers. I always have this problem whenever I do a fresh install. For some odd reason, the HD detection won't list my primary SATA port as the main hard drive, so it makes an IDE hard drive running off an IDE PCI Raid card the main drive and attaches a boot flag to it. Once I remove the boot flag and tweak my boot priorities it works fine.

Are you trying to boot with the external windows drive hooked up? You might want to try booting without that connected. Maybe my issue might give you insight into yours?

---

### Post by gali98 on 2008-05-09
It seems grub is installed on the internal hard drive (the windows one) which is kinda wierd since ubuntu is on the external one....
Hm....
Kory

---

### Post by wabbster on 2008-05-09
Nothing wrong with GRUB... it's just the fact that most of what's required for GRUB to *work* is in the external drive.

---

### Post by Herman on 2008-05-09
All boot loaders come in two or three parts.

The first part is extremely small, and fits inside the first 466 bytes os a hard disk's MBR, or inside the boot sector of a partition.
That's normally called 'stage1' of a boot loader.
The main job of the a boot loader's 'stage1', is to point to the boot loader's main files, which are normally too big to fit in the MBR, (which is only 512 bytes in size, including the 64 byte partition table). The 'stage2 files of the boot loader do the work of either directly loading an operating system's kernel and booting it, or else relaying the boot to some other boot loader. That is normally done by 'chainloading' the other operating system by its boot sector.

When you installed Ubuntu in your external hard disk, if you had known what to do, you could have chosen to install GRUB's 'stage1' to the MBR in the external hard drive.
Unfortunately, you or whoever performed the installation didn't know how to do that, so GRUB was installed to MBR in your first hard disk, which is the default behaviour of the installer since that's what most people would want.
Now when you boot with your external hard disk plugged in, your BIOS finds the MBR in your first hard disk, and from there GRUB's stage1 file directs to to GRUB's stage2 file inside Ubuntu. 
GRUB's stage2 which uses your /boot/grub/menu.lst to let you choose to boot either Ubuntu or Windows.
When you try to boot with your external hard drive unplugged, your BIOS looks in your MBR of your first hard disk and GRUB's stage1 file points it to your external hard disk, but that's not there, so you get an error.

You can fix this problem by creating a small partition in your computer's hard drive and using it for a 'dedicated GRUB partition and re-installing GRUB to MBR from the new GRUB partition. Here's how, [How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").

Otherwise, if you don't want to do that, you can re-install GRUB in your external USB hard disk to MBR in your USB hard disk, and re-install the stage1 file for your Windows boot loader in the MBR of your computer's internal hard disk.
**See lswest's and bodhi.zazen's thread**, [HOW-TO restoring XP and Vista Bootloader & Restoring GRUB ]("http://ubuntuforums.org/showthread.php?t=740221")
In that case, you will need to boot your external hard drive from your BIOS, [How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key") with my F12 key (or F8 key in most PCs).
       
Regards, Herman :)

EDIT:
> I guess it's also worth mentioning, unless that drive has one hell of a fan in it, running an OS off of it is going to kill it pretty quick. I agree with grazed, as heat is the number 1 killer of hard disc drives, not to mention hard drives being dropped or jarred while they are still spinning, the best place for a hard disk drive with an operating system in it is in a hard drive bay inside a computer, held in place with screws, with air flow from the case's vents and fans for cooling the hard disk when it is working hard as it will when it's running an operating system.
An external hard disk drive is great for storing backups, and normally when you only use it for that is doesn't spin for very long, and so most of them rely on the thermal conductivity of the case to dissipate the heat. That may or may not be adequate for long term use with an operating system in it. It's okay for an emergency recovery disc or something like that maybe. An external flash memory disk is okay though, because they work a different way.
I haven't yet seen any external hard disc drive enclosures fitted with case fans for sale anywhere, but maybe if you live in a cold country like Canada or somewhere like that it will be okay. Here in Australia where the ambient temperatures can reach 47 degress celcius or more, an external hard disk drive would likely die quick with an operating system running in it for very long. Of course, we do have air conditioning, but in my house that's only able to reduce the heat by about 10 degress, still too hot for an external; hard disc drive probably.

---

### Post by z|x on 2008-05-12
> **Herman said:**
> All boot loaders come in two or three parts.

The first part is extremely small, and fits inside the first 466 bytes os a hard disk's MBR, or inside the boot sector of a partition.
That's normally called 'stage1' of a boot loader.
The main job of the a boot loader's 'stage1', is to point to the boot loader's main files, which are normally too big to fit in the MBR, (which is only 512 bytes in size, including the 64 byte partition table). The 'stage2 files of the boot loader do the work of either directly loading an operating system's kernel and booting it, or else relaying the boot to some other boot loader. That is normally done by 'chainloading' the other operating system by its boot sector.

When you installed Ubuntu in your external hard disk, if you had known what to do, you could have chosen to install GRUB's 'stage1' to the MBR in the external hard drive.
Unfortunately, you or whoever performed the installation didn't know how to do that, so GRUB was installed to MBR in your first hard disk, which is the default behaviour of the installer since that's what most people would want.
Now when you boot with your external hard disk plugged in, your BIOS finds the MBR in your first hard disk, and from there GRUB's stage1 file directs to to GRUB's stage2 file inside Ubuntu. 
GRUB's stage2 which uses your /boot/grub/menu.lst to let you choose to boot either Ubuntu or Windows.
When you try to boot with your external hard drive unplugged, your BIOS looks in your MBR of your first hard disk and GRUB's stage1 file points it to your external hard disk, but that's not there, so you get an error.

You can fix this problem by creating a small partition in your computer's hard drive and using it for a 'dedicated GRUB partition and re-installing GRUB to MBR from the new GRUB partition. Here's how, [How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").

Otherwise, if you don't want to do that, you can re-install GRUB in your external USB hard disk to MBR in your USB hard disk, and re-install the stage1 file for your Windows boot loader in the MBR of your computer's internal hard disk.
**See lswest's and bodhi.zazen's thread**, [HOW-TO restoring XP and Vista Bootloader & Restoring GRUB ]("http://ubuntuforums.org/showthread.php?t=740221")
In that case, you will need to boot your external hard drive from your BIOS, [How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key") with my F12 key (or F8 key in most PCs).
       
Regards, Herman :)

EDIT:
 I agree with grazed, as heat is the number 1 killer of hard disc drives, not to mention hard drives being dropped or jarred while they are still spinning, the best place for a hard disk drive with an operating system in it is in a hard drive bay inside a computer, held in place with screws, with air flow from the case's vents and fans for cooling the hard disk when it is working hard as it will when it's running an operating system.
An external hard disk drive is great for storing backups, and normally when you only use it for that is doesn't spin for very long, and so most of them rely on the thermal conductivity of the case to dissipate the heat. That may or may not be adequate for long term use with an operating system in it. It's okay for an emergency recovery disc or something like that maybe. An external flash memory disk is okay though, because they work a different way.
I haven't yet seen any external hard disc drive enclosures fitted with case fans for sale anywhere, but maybe if you live in a cold country like Canada or somewhere like that it will be okay. Here in Australia where the ambient temperatures can reach 47 degress celcius or more, an external hard disk drive would likely die quick with an operating system running in it for very long. Of course, we do have air conditioning, but in my house that's only able to reduce the heat by about 10 degress, still too hot for an external; hard disc drive probably.
Would this work for my problem here: [http://ubuntuforums.org/showthread.php?t=791553](http://ubuntuforums.org/showthread.php?t=791553)

---

