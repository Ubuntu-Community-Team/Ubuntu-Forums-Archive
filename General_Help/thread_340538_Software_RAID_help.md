---
title: "Software RAID help"
date: 2007-01-17
forum: General Help
---

### Post by nash_rm on 2007-01-17
I am having problems starting my software RAID devices on boot.  I have installed a rocket raid 133 pci ide card, and created some arrays.  However, upon reboot the mdadm starts up and builds the raid arrays before the devices attached to the pci card have been created in the /dev/sdx.... structure.

As a consequence the resulting arrays are missing their 3rd partitions.  I have configured my /etc/modprobe.d to load the module for the pci card before loading the mdadm stuff, but still have been unable to determine where in the boot process the devices /dev/sda and /dev/sdb on the controller are being created.

I am using kernel found in the ubuntu package linux-image-2.6.15-27-686 and have compiled the driver against the headers relating to that package.

If anyone has any input it would be greatly appreciated.

---

### Post by souki on 2007-01-17
this is confusing,
you are setting up a software array on a hardware array ?
why don't you use hardware only ?

---

### Post by nash_rm on 2007-01-17
I'm not using the hardware array feature at all and discluded it from my module when compiling.

I am using a software array built with 2 drives on the pci ide card and with 2 drives on the ide controllers on the mother board.

The problem again is that the system starts the mdadm module and builds the arrays before it creates the /dev/sda and /dev/sdb device files.  So they are not being included in the arrays they belong to.

---

### Post by souki on 2007-01-17
I understand the problem now,

what happens if you disable the mdadm on boot ? can you see the partitions ?
if so, can you try starting mdam manually ?

maybe there's a delay before the pci card get initialized, if so, you can try to delay the mdam script by modifying the links in "/etc/rc?.d/"

---

### Post by nash_rm on 2007-01-18
> **souki said:**
> I understand the problem now,

what happens if you disable the mdadm on boot ? can you see the partitions ?
if so, can you try starting mdam manually ?

maybe there's a delay before the pci card get initialized, if so, you can try to delay the mdam script by modifying the links in "/etc/rc?.d/"


I can't disable the mdadm on boot because I am using a mirrored raid array for my root partition.  I have made the pci card's module a dependancy for the mdadm module so it installs and initializes before the mdadm does.  If I can find which init script  is responsible for automagically creating the /dev/sda & /dev/sdb devices I can have that run before the mdadm stuff and I think that will solve my problem.  However, to this point I have been unsuccessful in that.  I think it is udev that does that but again I am not sure.

Basically I think that I could have two possible solutions:  

1.) Configure mdadm to build my root array and then wait till later in the boot process to assemble my other arrays. 

2.) Find a way to have those device files created before mdadm tries to auto configure the arrays.

---

