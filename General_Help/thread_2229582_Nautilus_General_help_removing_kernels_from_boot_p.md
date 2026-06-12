---
title: "Nautilus General help removing kernels from boot partition"
date: 2014-06-13
forum: General Help
---

### Post by sewbiz on 2014-06-13
To remove kernels from my boot volume on my disc I was told an easy way was to go to Nautilus.... sudo nautilus. Did that...thank you. Now how do I know what is important to save and what to keep...my boot is 100% full....YIKES!

Where is the mounted/boot partition? In the boot folder...then...I have  abi. ,config., initrd.img, memtest,system map,vmcoreinfo,vmlinuz,  kernals......what are they and which are important? Also in the grub...a  ton of music....  .mod  kernals.  : (

---

### Post by deadflowr on 2014-06-13
Removing kernels manually from the files like that is a nice way to cause craziness.
(And has been known to be quite disastrous)
Instead follow this
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)
Note: Do the --dry-run command first, which will tell you exactly which kernels will be removed.
Much safer.

---

### Post by QIII on 2014-06-13
```
sudo apt-get autoremove
```

may get rid of them, not to mention a bunch of other junk that is no longer necessary.

---

### Post by sewbiz on 2014-06-14
Thank you but too late....I took advice to remove files manually using  Nautilus, stupid mistake as I removed .mod files in GRUB....now am in  Grub rescue mode. Another early day for me getting up with the birds to  take some time. It's an internet world and cahd2,msdos1)n't run a  business without it. Somehow, I can't get myself to go back to Window  OS. I'm addicted to Linux!

I am at the beginning....finding where my boot is. Could use some help. My son built my computer to be used with Windows so 
I think that is why you see msdos...if that is what that means.: (

grub rescue> ls
(hd0) (hd0,msdos4) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos7) (hd1,msdos6) (hd1,msdos5) (hd2) (hd2,msdos1)

when  I type in the commands I am not always getting it right...for  instance... (hd2)......."unknown command".....or (hd0)/boot...."unknown  filesystem".......
I am learning...got to type correctly to copy what is on the list. Any help along the way is so appreciated!

---

### Post by sewbiz on 2014-06-14
too late...i crashed....in grub rescue mode....any help.
found where the boot partition is...I think.

ls (hd0,msdos3)/boot)
./ ../

what does that mean?    ./  ../

---

### Post by sewbiz on 2014-06-14
after typing... insmod linux    it tells me on the next command line       error:file not found

Did I loose everything? Is that why I see ./  and   ../    after ls (hd0,smdos3)/boot  ?
YIKES!  : (

---

### Post by coffeecat on 2014-06-14
By deleting .mod files in the /boot/grub/i386-pc folder you may very well have broken grub very badly. The *.mod files are modular ones, code which is loaded when needed by grub. They are not music files. For some reason, nautilus is deciding that .mod files are Amiga format music files. Don't worry because my Ubuntu system is doing the same, which is quite bizarre considering that grub .mod files are part of a normal Ubuntu installation and Amiga music files....

Also - "msdos3" and so on are nothing much to do with Windows, just the grub shorthand for identifying partitions. I'm guessing you see msdos3/msdos4 and so on with a mbr partition table which is also sometimes referred to as a msdos partition table.

As far as repairing your grub goes, I think the only way to be able to do that is to re-install it. And by re-install, I don't mean what you commonly see on the forum which really means reconfiguring grub by re-installing it to the mbr. I mean reinstalling the application grub in order to restore the missing files. And to do that in a system you cannot boot into means chrooting into the system from a live session. Which needs a certain amount of experience. Or perhaps I've missed something and someone has a better idea.

I hate suggesting a complete system re-install for a system which is theoretically repairable, but you may find it quicker and less stressful than trying to repair your broken system. If you have any files in your system that are not backed-up (please say you have a backup strategy for personal files) you can access and copy them from a live Ubuntu session.

I think it hardly needs saying that you have learnt the hard way what a potentially dangerous tool a root-owned file browser is and how ill-advised some information is out there on the internet.

---

### Post by yancek on 2014-06-14
The kernels are the vmlinuz files with the version number telling you which is which.  From reading your posts above, it seems you are unaware of the name of the kernel file.  There will be a corresponding initrd file with the same number.  These files are in the boot directory and not in the grub or i386-pc directory.  There was no reason to delete anything in those directories.  It seems you have deleted all the Grub files which will include your grub.cfg which is the menu.  I'm not sure why you did that when all you wanted to do is delete kernels?  This will be the biggest problem for you to over come.  You could boot your Ubuntu installation medium and copy all the Grub files from it from the /usr/lib/grub directory to your boot partition on the hard drive but that will not include a grub.cfg file.  If you had a backup copy of the grub.cfg to copy to your boot partition you might get it to work.  It will undoubtedly be easier to reinstall Ubuntu.  

The method suggested above by deadflowr may well be better than just deleting, especially when you don't know the name of the file you want to delete??   It might have been useful if he posted a little info on what problems would occur deleting kernels.  I generally don't have more than two or three kernels so have never encountered this problem and I'm curious as to how you managed to get over 30 on your system.  Good luck with it.

---

### Post by deadflowr on 2014-06-14
> **coffeecat said:**
> 
As far as repairing your grub goes, I think the only way to be able to do that is to re-install it. And by re-install, I don't mean what you commonly see on the forum which really means reconfiguring grub by re-installing it to the mbr. I mean reinstalling the application grub in order to restore the missing files. And to do that in a system you cannot boot into means chrooting into the system from a live session. Which needs a certain amount of experience. Or perhaps I've missed something and someone has a better idea.

Yep, you'd have to chroot and reinstall grub just to be able to then deal with kernel removal.
When you remove the kernel via package manager, grub updates after each removed kernel.

> **coffeecat said:**
> 
I hate suggesting a complete system re-install for a system which is theoretically repairable, but you may find it quicker and less stressful than trying to repair your broken system. If you have any files in your system that are not backed-up (please say you have a backup strategy for personal files) you can access and copy them from a live Ubuntu session.
I think it hardly needs saying that you have learnt the hard way what a potentially dangerous tool a root-owned file browser is and how ill-advised some information is out there on the internet.

I agree.
Even though a repair is quite possible through a chroot session, it is extremely painstaking, not to mention will probably give a you a functional system but still would have package manager problems.

> **yancek said:**
>   
The method suggested above by deadflowr may well be better than just deleting, especially when you don't know the name of the file you want to delete??   It might have been useful if he posted a little info on what problems would occur deleting kernels.  I generally don't have more than two or three kernels so have never encountered this problem and I'm curious as to how you managed to get over 30 on your system.  Good luck with it.

The files in boot are not the only files installed from the linux-image packages.
Aside from that, by deleting the files and not removing via apt/dpkg, the package manager still thinks that those packages are in prime state and fully installed. When you go to try and remove them now the package manager is confused and will stop, simply because the files it is going to try and remove have no files to remove. It can't make heads or tails of it.

---

### Post by yancek on 2014-06-14
> The files in boot are not the only files installed from the linux-image packages.
Aside from that, by deleting the files and not removing via apt/dpkg,  the package manager still thinks that those packages are in prime state  and fully installed. When you go to try and remove them now the package  manager is confused and will stop, simply because the files it is going  to try and remove have no files to remove. It can't make heads or tails  of it. 				

Thanks for posting that, useful information.

---

