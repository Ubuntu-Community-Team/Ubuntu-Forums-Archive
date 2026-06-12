---
title: "Re-install Bootloader / grub?"
date: 2005-10-22
forum: General Help
---

### Post by justBE on 2005-10-22
Hello there,

I've been running xp + ubuntu for some while now and grub was my bootloader, and I had to re-install xp for some dubios reasons... however, after the installation, xp overwrote grub and it only boots directly into windows now.

Is there any way to get grub back as bootloader?

Best regards and thanks,
-J

---

### Post by Crazy Man on 2005-10-22
I think you'll have to reinstall Ubuntu. As far as I know, that's the only way around it.

---

### Post by justBE on 2005-10-22
wah seriously! isn't there a way around?

---

### Post by ronin_ar on 2005-10-22
[QUOTE=justBE]wah seriously! isn't there a way around?[/QUOTE]

[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

That uses Fedora as example, but should work on ubuntu too.
Take a look at the floppy method at the bottom of the page.

---

### Post by Xian on 2005-10-22
You can use the Ubuntu InstallCD to reinstall grub.
Just navigate to that step in the install menu.

Cancel/Exit when finished.

Or you can use a LiveCD and chroot into Ubuntu.
Then issue the command:

# grub-install /dev/hda

Assuming the partition syntax is correct on your machine.

---

### Post by Nasir Amra on 2005-10-22
Well I have the same problem and desperately seeking to reinstall grub. However, I have LVM2 installed so when I boot my system in a knoppix livecd, I see only sda1 partition which contains the boot and grub directories  (here is ls or viewable partition:
knoppix@1[knoppix]$ mount /mnt/sda1
knoppix@1[knoppix]$ ls /mnt/sda1
System.map-2.6.12-8-386  config-2.6.12-9-386      memtest86+.bin
System.map-2.6.12-9-386  grub                     vmlinuz-2.6.12-8-386
abi-2.6.12-9-386         initrd.img-2.6.12-8-386  vmlinuz-2.6.12-9-386
boot                     initrd.img-2.6.12-9-386
config-2.6.12-8-386      lost+found
knoppix@1[knoppix]$

and here is menu.lst stanza for kernel to boot to :
title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /vmlinuz-2.6.12-9-386 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd          /initrd.img-2.6.12-9-386
savedefault
boot

I've tried 
grub-install --root-directory=/mnt/sda1 /dev/sda

from within a root terminal using a knoppix live cd but that doesnt not work.. I suspect it would have worked if lvm2 was not there. Anyway, does anyone know the magical incantation to get grub installed again in my sata hard drive ? 
Thanks,

---

### Post by Nasir Amra on 2005-10-27
well I've spent a week to try to revive my ubuntu system after windows xp messed with the hard disk MBR. My meandering on my trial and error approach to getting it back up is below. In summary , I had to install ubuntu linux without LVM on my second hard drive ( don't have a floppy drive to use in my present system since usb based floppy is not recognized) reconfigure the bios to boot from my sata hard drive ( /dev/sdb) and added the exact same stanza in menu.lst that is the exact same one used to boot the original os on hard disk 1 /dev/sda.  So although I am able to boot to my original ubuntu installation on hard disk 1 /dev/sda from /dev/sdb, I am unable to boot straight from /dev/sda even after reinstalling grub. Now the error is "error 15 " which is can't find the file grub error. The grub in /dev/sda MBR  is version 0.95 while the dev/sdb MBR version is the original grub that comes with the ubuntu installation disk. Hopefully, this may help other people out. 

>>>>>>>>>> trial and error notes <<<<<<<<<<<<<<<<<<<<<<
10-27-2005
    I'm finally back. While trying to install xp into a vmware virtual machine , I had left the cd in the computer when rebooting and it scrambled my pc. because I have a usb based floppy drive which the os don't recognize, I couldn't just make a grup install disk. I've tried a variety of commands to restore the mbr using knoppix hacks books and read up on grub ,but still could not get the mbr to work even after booting up a live cd of ubuntu and installing grub from the live cd. Whenever, I reboot , it just shows a blinking cursor and does not start up grub. Finally the only way to boot the system was to install ubuntu on my second hard drive and then going to the bios and making the second hard drive the first one to boot from. Then I had to reboot and access the grub command line. I then was able to run the following commands gotten from my menu.lst of the os that won't boot:
> root (hd0,0)
> kernel /vmlinuz-2.6.12-9-386 root=/dev/mapper/Ubuntu-root ro quiet splash
> initrd /initrd-2.6.12-9-386 
> boot

The only hypothesis as to way the masterboot record with the reinstalled grub from ubuntu live cd not working is that there is some version conflict here. Anyway, I can try to setup a menu.lst configuration  on second hard drive for the second ubuntu os so that it boots the os from the first until I figure out my problem with mbr. The next thing is if I ever do solve my problem with mbr, I should back it up so I can restore it with dd.

I setup the configuration menu.lst on the 2nd drive and when I rebooted it came up in a grub command line. ( I don't know why its not automatically reading the config file , but I got it to do so with 
“configfile (hd1,0)/boot/grub/menu.lst”
which worked. 

I ran :
root@amd:/home/namra# grub-install /dev/sda
 
to see if this fixes MBR on sda disk. I reconfigured the boot hard desk in the bios and still the bootup froze at the point where normally grub loaded. I rebooted under the ubuntu os on the 2nd hard drive and rerun grub-install and now it automatically boots with default kernel instead of dropping me into the grub commandline. So what is with the MBR on the first drive? 

Tried the following:
root@amd:/home/namra# dd if=/dev/zero of=/dev/sda bs=446 count=1
1+0 records in
1+0 records out
446 bytes transferred in 0.000971 seconds (459304 bytes/sec)
root@amd:/home/namra# grub-install /dev/sda
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
(hd1)   /dev/sdb

When I reconfigured the bios to start up from sda, grub started but gave me an error #15 , identifying this line in configuration file as unreachable:
kernel  /vmlinuz-2.6.12-9-386 root=/dev/mapper/Ubuntu-root ro quiet splash

However, that exact same configuration stanza is reachable when I boot from sdb ( 2nd hard drive). Tried within grub to do the following:
grub> root(hd0,0)/boot
grub> install 
but that did not work. Could the problem be to having 2 different grub versions?
The version on hard disk 1 (sda) is 0.95 and hard disk 2 (sdb) is 0.93. Should I downgrade to this grub and try reinstalling grub? Right now I have solved my booting problem this way ( by booting from sdb).

---

### Post by Nasir Amra on 2005-10-27
10-28-2005
  Continueing to work on why grub does not work correctly, I've come to the conclusion that some of the confusion is the bios swapping of which hard drive to boot from changes which drive gets labeled (hd0,0). Now , I've let the bios hard drive order be sata3 , sata1 drive and that got the sata1 drive ( which is my original ubuntu updated installation) to be considered (hd0,0). Now, I'm able to reinstall grub using this command:

grub> install (hd0,0)/boot/grub/stage1 (hd0) (hd0,0)/boot/grub/stage2 p (hd0,0)/grub/menu.lst

NOTE: because the boot is on a primary partition, grub sees /grub/menu.lst when it reads the boot filesystem ,but when this partition is mounted under the ubuntu os the path is /boot/grub/menu.lst.
So (hd0,0) is mapped to /boot under ubuntu linux.
This solves my problem.

---

