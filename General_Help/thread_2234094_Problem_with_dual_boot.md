---
title: "Problem with dual boot"
date: 2014-07-12
forum: General Help
---

### Post by aryakaran on 2014-07-12
Hello,
I have installed lubuntu along with windows 7 (with GRUB dual boot).
Everything was working fine until I had to resize the / partition of lubuntu with gparted.
Since then when I try to boot from Windons 7, it just comes back to the grub menu and I can only boot with linux.

I have tried to fix it with $sudo update-grub, which gives the output:
Generating grub configuration file ...
    Found linux image: /boot/vmlinuz-3.13.0-30-generic
    Found initrd image: /boot/initrd.img-3.13.0-30-generic
    Found linux image: /boot/vmlinuz-3.13.0-24-generic
    Found initrd image: /boot/initrd.img-3.13.0-24-generic
    Found memtest86+ image: /boot/memtest86+.elf
    Found memtest86+ image: /boot/memtest86+.bin
    Found Windows 7 (loader) on /dev/sda1
    done

I hope there is a way to fix this. Thanks!

---

### Post by Bucky Ball on 2014-07-12
Well, the update-grub command gave no errors and found everything, by the looks of it. 

When you boot the machine, hold down the shift key after the BIOS screen. Does that bring up a grub menu list to select from or are you already selecting Windows from that list? (I'm guessing you must be, but just to confirm).

Are you using UEFI and is Win on sda1?

---

### Post by aryakaran on 2014-07-12
I'm already selecting fromt hat very same list. In the list I have the same options as before. But the Windows 7 option takes me back to the list itself.

Thanks for your help Bucky Ball.

---

### Post by aryakaran on 2014-07-12
Regarding UEFI I'm not sure,
In the bios says that both Legacy and UEFI are enable and that the priority is to use Legacy first. So i guess it is legacy. And Win7 is on sda1 as it was installed first.

---

### Post by Bucky Ball on 2014-07-12
You could try running Boot Repair and see if that fixes things. Nine times out of ten it does, but your case is slightly different. Give it a whirl. Try the second option here:

[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

Once installed, launch and try 'Recommended Repair' (big button, can't miss it). ;)

---

### Post by aryakaran on 2014-07-12
Thanks Bucky Ball!
It worked perfecly.
Apparently Windows was not on sda1 but on sda2. But as there is a recovery partition on sda1, it looks something went wrong and GRUB thought windows was there. Boot-Repair fixed it in a second.

---

### Post by Bucky Ball on 2014-07-12
Excellent news! To help future travelers please mark thread as solved by using the instructions in the second link in my signature. Enjoy. ;)

---

