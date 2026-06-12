---
title: "Need Help, Accessing Partitions On HD"
date: 2006-09-01
forum: General Help
---

### Post by noob_Lance on 2006-09-01
Hey

Im lookin for help getting soe partitions which are unformatted and inaccessable to me right now... accessable :p i have tried VMWare and like it so i wish to  now activate a 15gig partition on my hard drive and use that for my windows VM. How can i go about doing this??

~Lance

---

### Post by ifokkema on 2006-09-02
I'm not sure I understand - You're using VMWare just to get to partitions on your hard drive?!!?? If you want to format a partition and mount it, you can do so through System -> Administration -> Disks.

---

### Post by exxcomm on 2006-09-02
lance,

IF you're talking about how would you take your present windows vmware installation and install it on an actual physical partition instead of vmware virtual disk files, it's a long and drawn out process.

Boot the vmware guest OS with a cd boot solution (I recommend a [Barts PE CD]("http://www.nu2.nu")).
You will need the i386 directory from your windows install disk copied to the hard drive of the windows machine you build the CD with (if you can, use the windows 2003 i386 instead of the XP one. It has a native driver for the virtual LSI Logic SCSI card vmware uses.

Use a windows partition imaging solution (ghost, image for windows, driveimage XML, etc.) to make an image file of the installation and save it to a samba share of your host OS (linux machine).

Shutdown Barts.

Configure a new virtual machine in vmware on the host machine. Use the custom option. When asked use the Raw Disk (Advanced) option for your virtual machine.
Here you will specify the disk and partition you want to use for the vmware virtual machine to use as it's disk.

Boot the NEW virtual OS w/ the boot CD (Barts) and apply the image file  from the samba share (Barts is network aware and you can use network drives with it. Net use works there too.)to the partition that vmware is using for the virtual OS (DO NOT use this same partition for your virtual machine settings files!!!)

Reboot the virtual machine without the boot CD.

Enjoy your new vmware virtual machine on a raw partition.

DO NOT alter the files on the raw partition when the guest OS is running!!!!!!!

You can MAYBE copy them when it's running, but I always shutdown the virtual machine before doing so. You can copy/write files to that partition when the virtual machine IS NOT RUNNING (and stay away from playing w/ windows system files unless you know what you're doing).

---

### Post by noob_Lance on 2006-09-02
What do i put for the access path? leave it as /boot?

? 

~Lance


and Exx.. i can install it, i have already.. its ust now i want to put it on its own partition that is yet to be formatted

---

