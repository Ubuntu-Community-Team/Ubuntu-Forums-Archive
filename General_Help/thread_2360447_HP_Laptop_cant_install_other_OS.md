---
title: "HP Laptop cant install other OS"
date: 2017-05-04
forum: General Help
---

### Post by dragonslayer4832 on 2017-05-04
Ok so my HP Laptop (HP Pavillion Sleekbook) Came with Windows 8. I installed Ubuntu and my retarded self let it overwrite all my partitions. Now whenever i boot into recovery mode, it just boots into ubuntu. Ive tried putting windows 10 on a bootable usb, but it gets 99% moving the iso and then i get an error. ive also tried putting windows 10 on my usb from the Startup Disk Creator. also an error. Any ideas? I just want windows or OSX back.

---

### Post by mastablasta on 2017-05-05
> **dragonslayer4832 said:**
> Ok so my HP Laptop (HP Pavillion Sleekbook) Came with Windows 8. I installed Ubuntu and my retarded self let it overwrite all my partitions. Now whenever i boot into recovery mode, it just boots into ubuntu..
because you told it to.

is recovery partition actually still there? can you see it in gpartred?

>  Ive tried putting windows 10 on a bootable usb, but it gets 99% moving the iso and then i get an error. ive also tried putting windows 10 on my usb from the Startup Disk Creator. also an error. Any ideas? I just want windows or OSX back.

this seems to be a window issue or a download issue. make sure the iso you downloaded is good. check for md5sum of the iso.


for future reference this is how you can safely and easilly install linux or other os on a windows PC: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

you can safely run OS in live session if you only want to try it out and not install it.

if you didn't do any work yet on the laptop, you might be able to use testdisk and photorec to recover old partitions.

---

### Post by RobGoss on 2017-05-05
>   let it overwrite all my partitions.   

Why do you say this did you choose use ( entire disk ) option?

It is recommend to always install Windows first then Ubuntu,  this will avoid any boot issues you will run in to if you install Windows after Ubuntu

---

### Post by yancek on 2017-05-05
How have you tried putting windows on a usb to boot, what method?  I don't think the usb creator will work for that.  What recovery mode are you booting into, Ubuntu?
Do you have a windows recovery or installation disk?  Did you check to see if you still have windows partitions on the drive?  If you have the windows 10 iso, you can put it on a flash drive and boot it from the installed Ubuntu using the instructions at the link below.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by oldfred on 2017-05-05
If originally Windows 8, did you install Ubuntu in UEFI or BIOS boot mode
Windows 8 was UEFI with gpt partitioning and you have your HP version of Windows Product key in UEFI. But that is only for UEFI and probably only HP's version as it probably includes extra HP drivers.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c) 

And Windows only installs in UEFI boot mode to gpt partitioned drives. If you forced Ubuntu to install in BIOS/CSM/Legacy boot mode, then it may have converted to MBR. Or if still gpt, you need the ESP and could convert Ubuntu from BIOS to UEFI.

 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

