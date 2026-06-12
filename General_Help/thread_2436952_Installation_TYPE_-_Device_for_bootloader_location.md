---
title: "Installation TYPE - Device for bootloader location"
date: 2020-02-15
forum: General Help
---

### Post by skoles on 2020-02-15
After getting past a RAID/AHCI issue with my DELL puter, I am now at the point in the UBUNTU install where I am to decide the location of installing UBUNTU. I had already "SHRANK" the SSD to free up 80GB for UBUNTU. The SSD now shows up in the selections as a NVME device...coool....but the pull down menu below has the ENTIRE 256GB SSD as a selection. The unallocated 80GB of free space shows up under the 256GB device. 

The proper selection of the free space is what is not clear to me. A reference to an article would be helpful here for a UBUNTU newbie :-)

---

### Post by skoles on 2020-02-15
This is a DUAL BOOT scenario with WINDOWS 10 already existing...After poking around I noticed that the UBUNTU installer has the "INSTALL UBUNTU ALONGSIDE WINDOWS" option which did not show on my first run through because of the RAID/AHCI issue with the SSD. Is this the proper avenue now for dual boot installation ?

---

### Post by oldfred on 2020-02-15
While that should work if Windows now shown correctly.
But I do not trust automatic processes & many proceed with an auto install when Windows not shown & totally erase drive.

Be sure to have good backups.

More details on UEFI install in link in my signature below.
If a new user you now only need / (root) as ext4. 

If using a bit larger size I would use 25GB for / and rest as /home, but with 80GB some of the 25GB would probably never be used. Only have you have used Ubuntu a bit will you have a better idea of how you are using it and sizes of partitions if you want separate partitions.

---

### Post by skoles on 2020-02-16
Good Deal oldfred....I also felt nervous about the "automatic" method and letting the installer do its thang. I wasnt sure how to run the + CHANGE - thang in the installer. I did find a post where someone actually explained their decisions for the different sizes.

I backed up WINDOWS before I started this process and even setup a recovery flash drive. 

Thanks for the UEFI stuff. Very helpful and somewhat contradicting. Here is why

After I had initially setup /, swap and /home logical partitions, the installer threw up a warning message about UEFI partitioning when I hit the INSTALL button. There is a windows ESP partition on the SSD already. One of the links stated in the "SOMETHING ELSE" manual partitioning, one needs to set the /boot/efi mount point to the UEFI partition BUT in the "CREATING an EFI System partition" section it states there is "no need to set this mount point when using manual partitioning". LOL. So, clarification on this point (no pun intended) would be nice ;-)

This link is dead "UEFI install,windows 8 or newer with Something Else screen shots
    [URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]http://www.everydaylinuxuser.com/201...e-windows.html"



[/URL]

---

### Post by Dennis N on 2020-02-16
> One of the links stated in the "SOMETHING ELSE" manual partitioning, one needs to set the /boot/efi mount point to the UEFI partition BUT in the "CREATING an EFI System partition" section it states there is "no need to set this mount point when using manual partitioning". So, clarification on this point (no pun intended) would be nice.

You can't specify the ESP mount point in the Ubuntu Installer. In a system with a single disk drive, it automatically uses the existing ESP - in this case, the one that Windows uses, and the mount point is automatically set in Ubuntu to /boot/efi. Ubuntu's files will coexist with the Windows boot files on the ESP.

---

### Post by oldfred on 2020-02-16
@skoles
Thanks for info on issues with UEFI install & repair link.
Did some updates, but let me know what does not seem to work.

With one drive install & dual boot with Windows Ubiquity will auto find the existing ESP - efi system partition. You can specify it or not when using Something Else. If not installing on same drive, Ubiquity will only install grub into first drive's ESP which a user may not want. But no way to change. The change options in Something Else only work for BIOS installs. Many bug reports, still not fixed after years. Not a grub issue as it installs to drive you select.

       Posted work around to manually unmount & mount correct ESP during install #23 & #26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

---

### Post by skoles on 2020-02-16
Understood....I reran the installer and the second time through I did NOT get a UEFI warning message. Thanks for the reply !

> **Dennis N said:**
> You can't specify the ESP mount point in the Ubuntu Installer. In a system with a single disk drive, it automatically uses the existing ESP - in this case, the one that Windows uses, and the mount point is automatically set in Ubuntu to /boot/efi. Ubuntu's files will coexist with the Windows boot files on the ESP.

---

### Post by skoles on 2020-02-16
Thanks for your help ! Ubuntu proceeded through the rest of the install without issue on the second attempt. I can boot into both Windows and Ubuntu now ! WooHoooo !!!!! :-)

> **oldfred said:**
> @skoles
Thanks for info on issues with UEFI install & repair link.
Did some updates, but let me know what does not seem to work.

With one drive install & dual boot with Windows Ubiquity will auto find the existing ESP - efi system partition. You can specify it or not when using Something Else. If not installing on same drive, Ubiquity will only install grub into first drive's ESP which a user may not want. But no way to change. The change options in Something Else only work for BIOS installs. Many bug reports, still not fixed after years. Not a grub issue as it installs to drive you select.

       Posted work around to manually unmount & mount correct ESP during install #23 & #26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

---

