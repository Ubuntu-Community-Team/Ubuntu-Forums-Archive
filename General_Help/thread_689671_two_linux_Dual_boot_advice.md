---
title: "two linux Dual boot advice"
date: 2008-02-06
forum: General Help
---

### Post by maineman2 on 2008-02-06
Hi  I have a Dell 1505 laptop with Ubuntu installed I would like to have a dual boot  with open suse but I have some questions. 

 1 On my hard drive I have a linux swap file 1.23 Gb do I need to create a second swap file  for suse?        
     is a swap file the same as a boot file?

 2 Ubuntu is located at /dev/Hda6. So I create A new partition /dev/Hda7 for suse?

 3 I might like to put XP on in the future should I create a third partition for XP now or latHi I’m pretty new to linux and I have a Dell 1505 with ubuntu installed I would like to do a dual booter ? 
  
 4 Do I just let the suse grub over write the ubuntu grub?

  so in short is that all I have to do is create hda7 and then install suse?

  Any other advice would be appreciated Thanks Dan

---

### Post by upthelum on 2008-02-06
Someone correct me if this is wrong but when you run the disc to install the 2nd OS, if it's Suse it should set up the boot grub, Suse as far as i'm to believe is quite good at this.

---

### Post by eggdeng on 2008-02-06
> a swap file the same as a boot file
A swap partition is not the same as a boot partition.
 
A swap partition is space on the hard disk reserved for the OS to use as virtual memory when it needs a little extra (like pagefile.sys in W*nd*ws). It's recommended but not absolutely essential to have a swap partition (usually about 2x the size of installed memory). SuSE should be able to share the swap partition but I expect you will have to tell her where to find it.
 
A boot partition is a partition reserved for the boot loader (GRUB in the case of Ubuntu). This is the program which loads your operating system when you turn on the computer. You can have a separate boot partition or have the bootloader install to a primary partition.
 
At the moment, your GRUB is almost certainly installed to the MBR, a block on the first sector of the first hard disk. You can either install SuSE over Ubuntu as you set out above or tell SuSE to install her bootloader to the SuSE partition and then make a simple edit to the Ubuntu boot/grub/menu.lst to tell GRUB where to find SuSE.

As for installing XP, the best way is to install first XP, then make space to install the Linux distros because XP believes it has the inalienable right to take up the whole disk.

In any case, back up all your files before you touch anything! If nothing else, it'll give you a freer hand to experiment a little.

---

### Post by seventhc on 2008-02-06
I had a dual boot between backtrack and ubuntu, with only one swap partition, and both found the swap on their own. :) I think it can tell by the file type (linux-swap);)

---

