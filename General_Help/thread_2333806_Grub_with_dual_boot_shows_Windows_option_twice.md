---
title: "Grub with dual boot shows Windows option twice"
date: 2016-08-13
forum: General Help
---

### Post by lazy7 on 2016-08-13
I installed Windows, and then I dual booted it with Ubuntu 16.04.01, but in my grub, when I clicked on Windows option, the grub would load again.

So I followed the solution from [https://ubuntuforums.org/showthread.php?t=2230300](https://ubuntuforums.org/showthread.php?t=2230300)  and now Windows can be booted.

But now, in my GRUB, I have two entries. One is old one, which doesn't work, and the other is the new one from 40_custom.

When I turn the OS probe off, my grub does not even load, and my Ubuntu is automatically booted. 

How can I have only one Windows entry in my GRUB?

---

### Post by oldfred on 2016-08-13
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by izznogooood on 2016-08-13
Are you sure its not your recovery boot and your windows?

---

### Post by lazy7 on 2016-08-15
Here is the BootInfo summary report:
[http://paste2.org/kDCYcJa7](http://paste2.org/kDCYcJa7)

---

### Post by oldfred on 2016-08-15
Windows has essential boot code in the NTFS partition boot sector (PBR). You overwrote the Windows boot code by installing grub into the sda1 NTFS  PBR. But you should be able to restore from backup PBR with testdisk.

```
 sda1: _______________________________________________

 File system:       ntfs
Boot sector type:  Grub2 (v1.99-2.00)
Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda1  
     and looks at sector 785480000 of the same hard drive 
   for core.img. core.img is at this location and looks 
   for (,msdos6)/boot/grub. It also embeds following  
 components:
```

       PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
Also check for /boot/grub in addition to /Boot  

      
 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Your will need to install grub correctly to drive's MBR.
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by Cavsfan on 2016-08-15
After you've repaired your windows install and installed the grub on **sda** and not **sda1** as oldfred mentioned, you could create a customized grub that will boot as many systems as you have.

I installed Xubuntu 16.04.1 on my old 15.10 partition that evolved into 16.04 because I wanted to have a fresh installation.
When it installed a new kernel, it went through three update-grub processes, each lasted about 5 minutes. I don't have time for that.

So, this method (in my signature) causes update-grub to take about _1 second_. The link takes you to a thread where you post questions or issues and the community wiki is in the first post.

I have Arch Linux, 2 Xubuntu 16.04 installs and Windows 10. But, my system is not EFI.

In the method in my signature, it uses **/etc/grub.d/40_custom** but then you save it as **/etc/grub.d/06_custom** so that it appears at the very top.
Then you'll modify a couple of lines at the top (even though it says not to) if you want to see any output when you enter **sudo update-grub**. 
All you will ever see is what you put between the quotes, as you have in your current **40_custom**.

Then as you see that it all works properly, you make /etc/grub.d/20_memtest86+, /etc/grub.d/10_linux and /etc/grub.d/30_os-prober unexecutable.

Then all you have is the custom entries. Since you have a EFI system, you could save what you have entered in **/etc/grub.d/40_custom** because you know it works.

Plus you can have a cool background of your choosing. 

Here is my current grub screen on Arch Linux (Arch does not permit 3 colors but, Ubuntu allows a 3rd color that you see as white at the top and bottom of the box):

[[IMG]http://www.zimagez.com/miniature/20160725175516.jpg[/IMG]]("http://www.zimagez.com/zimage/20160725175516.php")

The only thing you ever have to change is the picture if you get bored with it or if you add or remove an OS to the mix.

Here is my current **/etc/grub.d/06_custom** file: (But, as I mentioned I would use the windows boot line in your 40_custom)
```

#!/bin/sh[COLOR=#ff0000]
echo 1>&2 "Adding Arch Linux, Xubuntu Xenial Xerus 16.04 LTS, Xubuntu Xenial Xerus 16.04 (Extra) LTS and Windows 10"[/COLOR]
exec tail -n [COLOR=#ff0000]+4[/COLOR] $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Arch Linux" {
    set root=(hd0,3)
        linux /boot/vmlinuz-linux root=/dev/sda3 rw quiet
        initrd /boot/initramfs-linux.img
}
menuentry "Arch Linux (Recovery Mode)" {
    set root=(hd0,3)
        linux /boot/vmlinuz-linux root=/dev/sda3 rw single
        initrd /boot/initramfs-linux.img
}
menuentry "Xubuntu Xenial Xerus 16.04 LTS" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Xubuntu Xenial Xerus 16.04 LTS (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Xubuntu Xenial Xerus 16.04 (Extra) LTS" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash
        initrd /initrd.img
}
menuentry "Xubuntu Xenial Xerus 16.04 (Extra) LTS (Recovery Mode)" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows 10" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}
```

---

### Post by lazy7 on 2016-08-17
Thanks a lot! My problem is fixed.

Thanks for the customization suggestions. Will try that also!

---

### Post by Cavsfan on 2016-08-19
> **lazy7 said:**
> Thanks a lot! My problem is fixed.

Thanks for the customization suggestions. Will try that also!

Glad you got it fixed! :)

I highlighted in red the two lines in 40_custom that you have to change to be in 06_custom.

The first one is added and it just lists whatever you put between the quotes. 
If you do not enter anything there, you will just get a line that says the picture was found when you do an update-grub.
And if so, you would leave the 2nd red item +3.

The 2nd change is based upon you adding the first echo line.
It is to change the +3 to +4, which tells the script to execute the 4th line down and not the 3rd line.
The 4+ tells the script to execute lines 1, 2, 3 and then 7 and so on...

[LIST=1]
[*][COLOR=#ff0000]#!/bin/sh[/COLOR] 
[*][COLOR=#ff0000]echo[/COLOR] 1>&2 "Adding Arch Linux, Xubuntu Xenial Xerus 16.04 LTS, Xubuntu Xenial Xerus 16.04 (Extra) LTS and Windows 10" 
[*][COLOR=#ff0000]exec[/COLOR] tail -n +4 $0 
[*]# This file provides an easy way to add custom menu entries.  Simply type the 
[*]# menu entries you want to add after this comment.  Be careful not to change 
[*]# the 'exec tail' line above. 
[*][COLOR=#ff0000]menuentry[/COLOR] "Arch Linux" { 
[/LIST]

---

