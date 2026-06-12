---
title: "Create new partitions from existing ext4 partition"
date: 2014-08-15
forum: General Help
---

### Post by Jack Harper on 2014-08-15
Greetings,

I want to make 1 maybe 2 new partitions from an existing partition, my system has 1 NTFS partition with Windows (for games), 1 swap partition, 1 Ubuntu partition and 1 ext4 partition for my files.

I would like to create 1-2 new partitions from my "files" partition, what is the best course of action? I could back up the partition, then delete it and create new partitions but is there a way to make new partitions from my files partition without losing my files? As in resize it and use the free space for making new partitions? I am thinking that backing up my files, deleting partition, creating new ones and restoring my files is safer and easier. If I do that will I have to manually add new partitions to fstab? Should I use live CD with gparted or using gparted directly from Ubuntu is good enough?

I want to make those new partition(s) in order to have LTS and other versions of Ubuntu installed at the same time.

---

### Post by mikewhatever on 2014-08-15
You should add a screenshort of Gparted (doesn't matter from where), as the original discription lacks in info.

---

### Post by kc1di on 2014-08-15
Hi Jack Harper Welcome to Ubuntu and the World of Linux.
You can do what you want with partitions , [COLOR="#FF0000"]**BUT I ALWAYS WARN BACK UP ANY IMPORTANT DATA FIRST TO EXTERNAL MEDIA - JUST IN CASE.**[/COLOR]

[Here is a tutorial ]("http://www.howtoforge.com/partitioning_with_gparted")on how to do what you want. Good Luck!

---

### Post by Jack Harper on 2014-08-15
> **kc1di said:**
> Hi Jack Harper Welcome to Ubuntu and the World of Linux.
You can do what you want with partitions , [COLOR=#FF0000]**BUT I ALWAYS WARN BACK UP ANY IMPORTANT DATA FIRST TO EXTERNAL MEDIA - JUST IN CASE.**[/COLOR]

[Here is a tutorial ]("http://www.howtoforge.com/partitioning_with_gparted")on how to do what you want. Good Luck!

Thanks I will check the tutorial. I think I will opt for backuping the partition and then deleting it and creating new partitions instead of resizing, because I need to backup files when resizing as well, as you noted yourself, and "clean" partitioning seems like a better choice to me than resizing :)

---

### Post by kc1di on 2014-08-15
I think that may be a good move :) 

Remember you can only have 4 primary partition on a machine. So you'll need to use an extended partion to make more than four :)

---

### Post by JKyleOKC on 2014-08-15
Jack already has four partitions, so once he removes that "files" partition he's going to have to replace it with an extended partition in order to keep going.

But that's ONLY if his system uses the old standard MBR format; many if not most newer machines use GPT format instead (sometimes called EFI; they're not the same but often show up together). With GPT, the four-partition limit no longer applies, but modification gets quite complicated. OldFred is the most knowledgeable of the folk hereabouts when it comes to EFI/GPT matters...

Jack: this "extended partition" we're mentioning is simply a container, not a true partition. It occupies one slot in the quite small Master Boot Record's partition table, and points to another table that can hold many more true partition entries. The MBR table's small size dates from the very first hard-drive-equipped IBM PC some 30-plus years ago; memories were much smaller then and saving space was essential to making things work at all. Since then, we've been saddled with "backward compatibility" until drives got so huge that a totally new design became necessary.

---

### Post by Jack Harper on 2014-08-15
What I worry about more than partitioning is how to configure multiboot properly as I never had more than 2 operating systems installed, I always had Windows for games and Ubuntu for everything else, now I will add another Ubuntu installation and possibly one more installation for experimentation with other distributions. Any good step by step tutorials on how to do that? As in what to do with Grub when installing second and third distribution, how to make LTS handle the booting process etc. Thanks :)

---

### Post by JKyleOKC on 2014-08-15
Grub should handle all the different systems for you automagically; each time you run update-grub the program will scan all partitions and add each bootable o/s that it finds to its menu. The only tricky part is making sure which copy of Grub is launched at boot time, since each different distribution you install will include its own copy (and run update-grub as the final step of that installation process), and there are a number of different versions out that may or may not be totally compatible with each other. There are configuration settings you can tweak to force selection of your desired version at boot time, but I'm not totally familiar with them so someone else will have to provide the details of using them...

---

### Post by Jack Harper on 2014-08-15
> **JKyleOKC said:**
> Grub should handle all the different systems for you automagically; each time you run update-grub the program will scan all partitions and add each bootable o/s that it finds to its menu. The only tricky part is making sure which copy of Grub is launched at boot time, since each different distribution you install will include its own copy (and run update-grub as the final step of that installation process), and there are a number of different versions out that may or may not be totally compatible with each other. There are configuration settings you can tweak to force selection of your desired version at boot time, but I'm not totally familiar with them so someone else will have to provide the details of using them...

Thanks for the information on grub, I would like LTS to handle multiboot if possible, I will wait for a link to a detailed tutorial or someone with experience in this to provide more information as I would like to play it safe, dont want to mess up my existing Ubuntu installation or end up with a system that wont boot anything :lolflag:

---

### Post by oldfred on 2014-08-16
You will need to learn about grub as you can greatly simplify booting with mulitple systems. But you need to edit grub and modify where second installs of grub are installed and where grub updates automatically reinstall to.

I really only know Ubuntu which is Debian based, so other Debian based system should apply. 

You always want to install with Something Else so you have a choice on the partitioning screen on where to install grub. If you have a working grub in the MBR, then you may want to install second install's grub to  a partition which otherwise is never recommended. It is more as a throwaway so not really used. But Ubuntu does not give a choice not to install grub.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

If after the fact you can change grub2's default reinstall.
      
 [http://askubuntu.com/questions/503417/how-to-prevent-ubuntu-from-overwriting-grub-bootloader-after-update/503446#503446](http://askubuntu.com/questions/503417/how-to-prevent-ubuntu-from-overwriting-grub-bootloader-after-update/503446#503446)
#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

