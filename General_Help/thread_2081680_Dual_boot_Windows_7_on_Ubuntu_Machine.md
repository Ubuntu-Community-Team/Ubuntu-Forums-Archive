---
title: "Dual boot Windows 7 on Ubuntu Machine"
date: 2012-11-07
forum: General Help
---

### Post by gflam on 2012-11-07
Hi I have a machine with Ubuntu 12.04 installed. The machine came without an os on it so I installed Ubuntu. I now would like to install windows which in the past I've had a windows machine and then installed Ubuntu with no problem, however, I haven't found much for doing the opposite.

What Ive done so far is install gparted which i used to format my external hdd and put a ntfs partition on it. Then using UNetbootin I wrote my iso to my hdd after following the instructions in the following link. [http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I've tried winusb and the tool microsoft provides for creating a bootable usb hdd which was windows only which i ran in a vm however even though the vm showed my external hdd in computer on windows none of the programs would recognize the usb external hdd. 

Anyway what I now need to know is how I can partition my computers hdd in ubuntu and preserve my data in Ubuntu, and then I know to press f7 as my computer is booting up and run the windows setup.

I just need to know mainly how I can partition my drive without losing data as well as if there is anything else i need to worry about. For instance, I've read I'll need to reinstall grub which I don't know much about so any help on what i should do from here would be greatly appreciated so I don't lose any data or mess anything up :)

---

### Post by oldfred on 2012-11-07
Windows only installs to, repairs boot, or boots from a NTFS formatted primary partition (sda1 thru sda4) with the boot flag.

Windows 7 will install to one partition, but if empty drive or free space will use two partitions. A hidden 100MB boot/repair partition and the main install. The main purpose of the boot partition is so you can encrypt the main install. But sometimes you can boot repair from boot partition if main install needs repair. So if installed to just one partition be sure to have a Windows repairCD in case you need chkdsk or other repairs.

Windows will automatically put its boot loader into the MBR. So you need an Ubuntu liveCD or USB to repair/reinstall grub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by gflam on 2012-11-07
Okay my main issue is just creating the NTFS partition. While booted into Ubuntu I open gparted but then I'm not sure what to do from there really. I right click my partition and then normally I would click unmount and then delete the unmounted partition and then finally right click the unallocated section and select new and create something there but I'm not sure what to do to preserve my data nor can I unmount for obvious reasons. Sorry for being such a noob :P

**Edit** after a little googling think i found my answer here
[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

Will have to play more when i get back to my linux machine after class

---

### Post by gflam on 2012-11-08
My thinking is that I should do this

Boot from a Live CD and install gparted
Resize my hdd and create a partition for windows to install to
Install windows to that new partition
Use the live cd to reinstall grub

Hope this is right will do it tomorrow

---

### Post by gflam on 2012-11-08
Well couldn't wait till tomorrow and stayed up late ha installation of windows after having ubuntu went very well didn't lose any data and was able to partition my hdd for windows as well as reinstall grub2 thank you very much for the links they were very helpful especially [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by oldfred on 2012-11-08
Glad you got it to work. :)

---

