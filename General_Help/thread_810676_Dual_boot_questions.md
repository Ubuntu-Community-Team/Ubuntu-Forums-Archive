---
title: "Dual boot questions"
date: 2008-05-28
forum: General Help
---

### Post by zay2 on 2008-05-28
Hello!

Forgive me for my bit long description of the problem.

It went like that: Mom bought herself new computer and i installed her windows xp. Knowing how she knows next to nothing about viruses and spyware and such. i set up 2 paritions on hdd so i could just wipe windows system partition and reinstall xp whenever its needed. 

I made small error thought. i accidentally installed xp on larger 70gb partition leaving 10gb partition free. 

At some point i convinced mother to try all this kubuntu goodness and installed hardy heron on that 10gb partition. Install didnt automatically recognize windows on the 70gb part of hdd though and now im facing bit of a problem here - how to set up dual boot system in my current situation? 

If anyone could help me out here i would appreciate it alot. 

Thanks
Alan

---

### Post by logos34 on 2008-05-28
The easiest way of course would be to back up your/her data from windows and reinstall, making sure to get it right this time.  Other than that you could use gparted on the kubuntu livecd to delete the kubuntu partition, expand windows to the left to take up the freed space, then shrink it from the right-hand boundary down to 10gb, make a new ext3 in the new space and put kubuntu there.  You can read/write to ext3 from windows with the fs-driver.  Same vice-versa (8.04 Hardy comes with ntfs-3g driver installed).

If you really want to know the truth, the best thing to do would be to convince her to dump windows and use linux.  KDE4 desktop is pretty slick and looks like a cross between  xp, vista, ubuntu, and kde.  Mandriva 2008.1/MandrivaOne is to my mind the best distro for weaning non-geeky types away from windows.   

My 2 cents anyway

---

### Post by zay2 on 2008-05-28
> **logos34 said:**
> The easiest way of course would be to back up your/her data from windows and reinstall, making sure to get it right this time.  

if i reinstalled windows right now to that 70gb partition would grub suddenly somehow recognize windows and offer me to boot either to windows or linux after windows install is finished?

> **logos34 said:**
> 

Other than that you could use gparted on the kubuntu livecd to delete the kubuntu partition, expand windows to the left to take up the freed space, then shrink it from the right-hand boundary down to 10gb, make a new ext3 in the new space and put kubuntu there.  You can read/write to ext3 from windows with the fs-driver.  Same vice-versa (8.04 Hardy comes with ntfs-3g driver installed).

sounds like awful lot of trouble. expading/deleting partitions and etc. the windows install is intact sitting on that hdd since ive not touched that partition at all since i installed linux. cant i just configure grub somehow to include option of booting from that partition too? no idea how grub works really :) why cant i just skip all this expanding and shrinking and just reinstall linux or configure grub somehow...


> **logos34 said:**
> 
If you really want to know the truth, the best thing to do would be to convince her to dump windows and use linux.  KDE4 desktop is pretty slick and looks like a cross between  xp, vista, ubuntu, and kde.  Mandriva 2008.1/MandrivaOne is to my mind the best distro for weaning non-geeky types away from windows.   

My 2 cents anyway

yeah i would recommend her to use linux too. and most of time she could fulfill all her gaming/music listening/surfing needs using just kubuntu, but there are some occasions when wine fails and she needs to use some windows programs:

she is customer of one webshop that allows you to upload your pictures to their server and then order those digital pictures on paper from them. Unfortunately the application, this shop uses, is not web-based but some windows program that doesnt get past authorization screen when i run it through wine. 

that and few other problems make me and her wish she could boot up windows those few times when she needs to use those programs.

---

### Post by bodhi.zazen on 2008-05-28
> **zay2 said:**
> Hello!

Forgive me for my bit long description of the problem.

It went like that: Mom bought herself new computer and i installed her windows xp. Knowing how she knows next to nothing about viruses and spyware and such. i set up 2 paritions on hdd so i could just wipe windows system partition and reinstall xp whenever its needed. 

I made small error thought. i accidentally installed xp on larger 70gb partition leaving 10gb partition free. 

At some point i convinced mother to try all this kubuntu goodness and installed hardy heron on that 10gb partition. Install didnt automatically recognize windows on the 70gb part of hdd though and now im facing bit of a problem here - how to set up dual boot system in my current situation? 

If anyone could help me out here i would appreciate it alot. 

Thanks
Alan

No need to re-install windows at all, we just need to configure GRUB to boot windows is all.

Can you post the output of :

```
sudo fdisk -l
```From there we just need to add a stanza to /boot/grub/menu.lst to boot windows

```
kdesu kate /boot/grub/menu.lst
```Look or add the appropriate windows stanza :

> Title Windows XP
rootnoverify (hd0,x)
makeactive
chainloader +1
boot

The only thing we need it what to put for "x" in root (hd0,x)

See also :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018")

---

### Post by Fire_Chief on 2008-05-28
You can just configure Grub to handle this.

Since you are already booting into Hardy, this will be quick and pretty easy.

Odds are good that your Windows partition is the first one on the drive so let's edit the Grub menu to add it as a boot entry
```
sudo nano /etc/grub/menu.lst
```

Go to the bottom of the file and add these lines```
title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

type Ctrl X to exit and save the file. Then when you reboot, you should see a new entry in the Grub boot menu called "Windows XP". Select it and see if it boots into XP properly.

The only reason that would not work is if Windows is not the first partition on the drive or your BIOS does some drive swapping mess (not common).

Cheers!

Edit: Gah!!  Always too slow :(

---

### Post by logos34 on 2008-05-28
> **bodhi.zazen said:**
> No need to re-install windows at all, we just need to configure GRUB to boot windows is all

If all you want to do is fix the boot, then follow bodhi.zazen's suggestion.

However if you would like to get windows arranged like you originally intended, you'll have to reinstall or resize.  The latter isn't a big deal.

---

### Post by zay2 on 2008-05-28
sudo fdisk -l:


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x842ec0af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        9728    78140128+   f  W95 Ext'd (LBA)
/dev/sda5             805        9728    71681998+   7  HPFS/NTFS
/dev/sda6               1          62      497920+  82  Linux swap / Solaris
/dev/sda7              63         804     5960083+  83  Linux

Partition table entries are not in disk order

Right now that menu.lst fail contains such lines in the end of it:

## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=0e65b06f-59d3-42e7-b40b-95bf00db6499 ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=0e65b06f-59d3-42e7-b40b-95bf00db6499 ro single
initrd          /boot/initrd.img-2.6.24-17-generic

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=0e65b06f-59d3-42e7-b40b-95bf00db6499 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=0e65b06f-59d3-42e7-b40b-95bf00db6499 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

and i add: ?

Title Windows XP
root noverify (hd0,x)
makeactive
chainloader +1
boot

---

### Post by zay2 on 2008-05-28
ah i read the first post of bodhi again. i need to replace the x with something. i dont understand that fdisk -l enough to know that to use instead of that x though...

---

### Post by logos34 on 2008-05-28
it's either (hd0,0) or (hd0,1)

---

### Post by zay2 on 2008-05-28
strangest thing happened now. i tried to code with hd0,0 and it didnt work when i chose windows xp in grub. said it couldnt find the partition. 

but now there is no /etc/grub/menu.lst there is no /etc/grub even.

---

### Post by Fire_Chief on 2008-05-28
look in /boot

:)

---

### Post by zay2 on 2008-05-28
right. thanks.

---

### Post by logos34 on 2008-05-28
> /dev/sda5 805 9728 71681998+ 7 HPFS/NTFS

oops, try (hd0,4)

how did it end up as a logical?

---

### Post by zay2 on 2008-05-28
no idea...

but neither hd0,0 hd0,1 nor hd0,4 worked though..

end of the menu.lst looks like that atm :

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=0e65b06f-59d3-42e7-b40b-95bf00db6499 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title           Windows XP
root            (hd0,4)
savedefault
makeactive
chainloader     +1

---

### Post by bodhi.zazen on 2008-05-28
rootnoverify is all one word

Looks like windows is (hd0,4), you can try it. I do not think windows likes to be on a logical partition , I think it needs to be on a primary partition.

> Title Windows XP
**rootnoverify (hd0,4)**
makeactive
chainloader +1
boot

If that fails we will likely need to move your windows partition. This can be done with gparted, from the live CD but can get a little messy.

Still, considering the data on Windows and the time it takes to install, configure, update, and then add applications to windows, changing your partitions (resizing) is likely faster.

---

### Post by zay2 on 2008-05-28
does boot need to be written in that menu.lst too?

anyways. changing root for rootnoverify didnt help either. guess that next up is resizing partitions. not today though. im too tired for it atm. need to go to bed now. Thank you everybody and ill probably bother you more when im with this resizing partitions stuff.

Thanks again!

---

### Post by Fire_Chief on 2008-05-28
> **bodhi.zazen said:**
> rootnoverify is all one word

Doh! I always forget that it's using rootnoverify...  sorry for misleading :(

---

### Post by bodhi.zazen on 2008-05-28
> **zay2 said:**
> does boot need to be written in that menu.lst too?

anyways. changing root for rootnoverify didnt help either. guess that next up is resizing partitions. not today though. im too tired for it atm. need to go to bed now. Thank you everybody and ill probably bother you more when im with this resizing partitions stuff.

Thanks again!

no, "boot" is not need

---

### Post by louieb on 2008-05-28
You have a problem.  That being Windows is installed in a logical partition. GRUB is not going to be able to boot Windows.
The only way that will work is if you also have a second install of windows on a primary partition. Windows is weird that way.  
Heres a couple of links I found on Herman's dual boot site that explains  the whys and wherefores.   
[Multi-Booting with Windows in an Extended Partition]("http://www.goodells.net/multiboot/principles.htm")
[Understanding MultiBooting]("http://www.goodells.net/multiboot/index.htm")

At this point I think Logos34 is right when he wrote:
> 
        The easiest way of course would be to back up your/her data from windows and reinstall, making sure to get it right this time.
I'd probably think about how I want my partitions  set up. Set up the partitions.  Install Windows then Linux. Good Luck.

---

