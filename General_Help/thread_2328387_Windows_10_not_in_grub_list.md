---
title: "Windows 10 not in grub list"
date: 2016-06-20
forum: General Help
---

### Post by babs-keeley on 2016-06-20
I know this has been asked and solved a few times but I can't get Windows 10 in the Grub list.
I don't have raid installed so it's not a metadata issue. I have BIOS not UEFI. I've tried Boot-Repair but still no go (unless i'm doing something wrong!).
I can mount the Windows partition in Ubuntu and can access the file system.
I've tried mounting the partition and updating grub but still nothing.
I've tried a custom grub, shows the photo background ok but not Windows 10.


_**result of fdisk -l**_

```
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1       209717248 488374271 278657024 132.9G  7 HPFS/NTFS/exFAT
/dev/sda2  *    488376320 972728319 484352000   231G 83 Linux
/dev/sda3       972728320 976771071   4042752     2G 82 Linux swap / Solaris

```
_**result of bootinfo script**_

```
============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 962597032 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 16.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda3: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 
```


_**Boot-Repair paste**_

[http://paste2.org/Fp3FMH2y](http://paste2.org/Fp3FMH2y)



I do get the grub on boot and can boot Ubuntu no problem, just can't get Windows 10 on grub or boot it.  
I think that's it, I would be so grateful for any help.
Thank You

---

### Post by kolibri on 2016-06-20
After running boot-repair, sometimes i have to run "sudo update-grub" in the terminal to get my windows OS to show up in the grub menu.

---

### Post by babs-keeley on 2016-06-20
Tried that, all I get is
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-24-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-24-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-22-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-22-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-21-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-21-lowlatency
done

---

### Post by yancek on 2016-06-20
I don't know what the 'low latency' message means but I see that you have the Ubuntu partition marked as active which is not necessary.  It is necessary for windows so changing that might have some effect.

---

### Post by Cavsfan on 2016-06-20
> **babs-keeley said:**
> I know this has been asked and solved a few times but I can't get Windows 10 in the Grub list.
I don't have raid installed so it's not a metadata issue. I have BIOS not UEFI. I've tried Boot-Repair but still no go (unless i'm doing something wrong!).
I can mount the Windows partition in Ubuntu and can access the file system.
I've tried mounting the partition and updating grub but still nothing.
I've tried a custom grub, shows the photo background ok but not Windows 10.


_**result of fdisk -l**_

```
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1       209717248 488374271 278657024 132.9G  7 HPFS/NTFS/exFAT
/dev/sda2  *    488376320 972728319 484352000   231G 83 Linux
/dev/sda3       972728320 976771071   4042752     2G 82 Linux swap / Solaris

```

The boot flag (shown as *) should be on your sda1 windows partition. 
You should be able to open up gparted, right click on sda1. 
Then click on manage flags and put a check mark by boot like this:
 [ATTACH=CONFIG]269678[/ATTACH]

And right click on sda2 and remove the boot flag from that partition.
Your **/etc/grub.d/30_os-prober** file might not be executable as I don't see windows listed in the output of update-grub.

Try ```
sudo chmod +x /etc/grub.d/30_os-prober && sudo update-grub
``` and see if that makes it show up.

---

### Post by babs-keeley on 2016-06-20
When changing boot flags in gparted you don't need to remove the boot flag from sda2 as it does it automatically, you can only have one partition with a boot flag.

But I changed it and it made no difference
 
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *    209717248 488374271 278657024 132.9G  7 HPFS/NTFS/exFAT
/dev/sda2       488376320 972728319 484352000   231G 83 Linux
/dev/sda3       972728320 976771071   4042752     2G 82 Linux swap / Solaris

os prober doesn't return anything, I should've said that originally but there's so much to remember (what I've tried and what it can't be).

sudo chmod +x /etc/grub.d/30_os-prober && sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-24-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-24-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-22-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-22-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-21-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-21-lowlatency
done

---

### Post by oldfred on 2016-06-20
Windows knows which partition to boot from by the boot flag. It must  be on a primary NTFS formatted partition with the boot flag.
Grub does not use boot flag nor uses it to find a Windows install.  It looks for the two Windows boot files in the boot partition.

 Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe  

Did you delete a 100MB boot partition? That would have had bootmgr & the BCD which you do not show anywhere.

You do not have to create a new boot partition, but will have to use Windows to repair the install in sda1. You first must have boot flag on sda1, or the Windows repair disk or installer will not work.

Windows repairs may also restore the Windows boot loader to MBR, so make sure you can still run Boot-Repair or know how to reinstall grub to MBR.
      
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

[/URL]
 Windows Repair Console ------------
f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html) 

[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by babs-keeley on 2016-06-20
Maybe you were replying the same time I was oldfred, I had already changed sda1 to boot and didn't make any difference.
I  haven't deleted anything, I can see the /windows/System32/winload.exe is there and guess that's why bootinfoscript picks it up, it also says no errors in boot sector info.
Not sure about /bootmgr/boot/bcd bit but would have thought bootinfoscript would say something if anything was missing, maybe ??
I looked at some of the links you posted, I don't have the restore MBR option on boot-repair and there's nothing on the MBR options tab.
I tried booting from Ubuntu disc tonight but it's going straight to grub for some reason, never had a problem b4! I'll try the Windows disc tomorrow and see what happpens.

A big Thank you all for your help up to now and hope we can find the solution tomorrow.

---

### Post by oldfred on 2016-06-20
Boot-Repair does not fix many Windows issues. As most is copyrighted by Microsoft.

The missing Windows boot files are not something Boot-Repair looks for. And since grub2's os-prober does not find them, it will  not add a boot stanza for Windows.
 
And can only be fixed from a Windows repair flash drive or DVD. Or from a Windows installer's repair console.

How Windows BIOS systems boot:
 Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by babs-keeley on 2016-06-22
Sorted it. I created a custom grub again. This time it listed Windows 10 but when I clicked on it it said missing mbr (as we expected). I been having trouble booting from disc so went back in BIOS and figured out that since BIOS update cd/dvd is now called upgrade bay (even tho cd/dvd id still listed!) so I set upgrade bay to 1st in boot list and it booted to dvd, fixed mbr and i'm now in Windows 10, fingers crossed it hasn't messed up Ubuntu! 
Thanks everyone for your help

---

### Post by ventrical on 2016-06-22
I use Grub_Rescue CD. About a 90% success rate of getting Windows back.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Regards..

---

