---
title: "adding win 7 to grub menu"
date: 2015-10-07
forum: General Help
---

### Post by robert71 on 2015-10-07
Hi can anyone help with adding win 7 to my boot menu ?

The following is my bootloader information:

[http://paste.ubuntu.com/12703118/](http://paste.ubuntu.com/12703118/)

I know my win 7 is located on /dev/sdb

Any way to add it to the current boot menu ?

Thanks

---

### Post by oldfred on 2015-10-07
I like to have each system installed on separate drives. And then install boot loader to the MBR of the drive. Then from BIOS I can also choose to boot any of the other systems directly if needed.
But keep BIOS set to boot main working install. 

Do not use Boot-Repair's autofix as that just installs one grub to all drive's MBR. Better to use advanced mode and choose each system and then the drive to install boot loader into.

Are you booting from sda or the grub in sdd?
Are you having to use nomodeset or is nouveau working. System may work better with nVidia driver, but install from repository or add ppa to get very newest version. Do not use download from nVidia.

Have you booted from sdd and just run this?
sudo update-grub

If that does not find Windows then you have some issue with Windows that is not shown. Grub only boots working Windows and you sometimes need the Windows repairCD or flash drive to run chkdsk or make other repairs.

Is sda an SSD? But you have no system installed into it? Real advantage of SSD is boot speed & program loading time. Loading data does not save much at all.

---

### Post by robert71 on 2015-10-07
Hi Fred, 

       i Believe i am botting from sda .

The following is the output from sudo update-grub

```
tom@Tubuntu:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
Found Ubuntu 14.04.3 LTS (14.04) on /dev/sdd5
done

```

I can see the windows entry but for some reason its not including it in the menu entry on the boot screen. 



Yes SDA is a SSD, but it host the virtual HD for my vm cuz it is faster than the typical drives. 

Can the win 7 entry be added manually  or can we force grub to add it cuz it sees it in update-grub ?

---

### Post by oldfred on 2015-10-07
If it is in your update-grub, then it should be on grub menu when you boot.

Or are you not booting first entry in grub menu. When you have multiple installs you can be updating one version but booting the other grub which has not been updated. Part of why I suggest each install has its grub on its drive, so you can control from BIOS which drive you boot from.

---

### Post by robert71 on 2015-10-07
okay, can you advise how i would go about booting first entry in grub menu. 
Or finiding out which drive i am booting from and change it to the correct one ?? 
Any advise there.

---

### Post by oldfred on 2015-10-07
First entry should be default unless you changed it.
And if you have lots of entries in grub menu you may have to scroll down to find the Windows entry as it is usually last or at bottom.

In BIOS you specify boot drive and perhaps boot order where if first drive is not bootable it tries a second drive or other drive.

I would use Boot-Repair and make sure you have installed correct grub from install you want to boot in the MBR of the drive you have that install in. Then go into BIOS or one time boot key like f10 or f12 and boot that drive.

---

### Post by robert71 on 2015-10-12
> **oldfred said:**
> 

I would use Boot-Repair and make sure you have installed correct grub from install you want to boot in the MBR of the drive you have that install in. Then go into BIOS or one time boot key like f10 or f12 and boot that drive.

Hi Oldfred i have tried that but still not seeing windows on the boot menu, not sure how to proceed,

---

### Post by oldfred on 2015-10-12
Which Linux are you booting, first in grub menu or last, sdd5?
And which drive are you booting, sdd?

---

