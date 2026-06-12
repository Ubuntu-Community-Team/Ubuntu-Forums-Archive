---
title: "Ubuntu with Windows 10 in a 256Gb SSD"
date: 2018-03-02
forum: General Help
---

### Post by robbyschuh on 2018-03-02
Hello mates, I bought a new laptop and I tried to install Ubuntu without remove Windows 10. I did it quick and easy the first time, but for some reasons, later I tried to install another Ubuntu version and remove the previous one,  but something crashed. I will explain with steps, I think it will be easy with screenshots as well.

1 In a Windows 10 machine, I installed Ubuntu 17.10 ,  from 256gb SSD , I got 100gb for Ubuntu and 10gb ssd for the SWAP (Windows partition was redimensioned).
2 I tried to install Ubuntu 16.04 removing 17.10 (it is an option from the Ubuntu UI installer).
3 After that Ubuntu stoped working, anyway I tried to run the installation again, but the installer or live CD  always stucks when the ubuntu logo is displayed.

4 A few hours later, I decided to remove (in Windows 10) the Ubuntu partition , and the SWAP as well (10gb ssd). (screenshot attached)
5 After that, I restarted the laptop and I still watching the Ubuntu partition there , how is it possible? (screenshot attached), if I select this option, I see a Grub message, error? 
[https://s14.postimg.org/wru3rss1t/20180302_200626.jpg](https://s14.postimg.org/wru3rss1t/20180302_200626.jpg)
6 I tried to reinstall Ubuntu again with the live cd, but the installation process always stucks when the Ubuntu logo is displayed
7 If I try to start the computer without press "ESC" (in order to show the boot options) I see this message (screenshot attached)

Just in case I attached the BIOS configuration as well.


Thanks for your help :).

---

### Post by kenogo2 on 2018-03-03
You are not seeing the Ubuntu partition in the picture you're providing. In fact, you're seeing very much that it is gone! Grub is a boot manager, which means it is responsible for booting the different operating systems installed on your PC. Grub was installed with your Ubuntu installation and replaced the default windows boot manager (which doesn't support dual boot with Linux AFAIK). Since grub was installed into the master boot record, simply deleting your Ubuntu partition didn't delete it. So when you're trying to boot Ubuntu from grub now, it just won't work since it can't find the partition to boot from. You can still boot Windows, right? So why are you expecting to be able to boot Ubuntu when you removed the partition? ;)

Now on trying to reinstall Ubuntu. Can you boot into the Ubuntu Live CD? If yes, please do that, open a terminal, and post the output of

```
fdisk -l
```

---

### Post by robbyschuh on 2018-03-08
Hello Kenogo2, thanks for your reply. I think I did not explain the issue good, because I cannot run Ubuntu installer from the bootable USB (this usb is working in other laptops), I only can see the Ubuntu logo, but the installation starts, and stucks when the Ubuntu logo appears.
Thanks.

---

### Post by yancek on 2018-03-08
You are using an EFI system which means that you have a separate EFI partition which contains some of the boot files for both windows and Ubuntu.  When you select the formerly installed Ubuntu option on boot, it goes to the Ubuntu EFI files and looks for the rest of the boot files on the partition and can't find them because you deleted that partition.  Since you have obviously installed Ubuntu EFI previously, I would suggest you disable CSM Support in the BIOS as you don't need that.

Not sure why you cannot boot the usb if you used this same usb previously to boot/install.  Set the options in BIOS boot to what they were when you installed.

---

### Post by oldfred on 2018-03-08
What brand/model system?
What video card/chip?

If nVidia you need nomodeset boot parameter and some brands need additional boot parameters.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

