---
title: "Ubuntu erased my Windows XP. Possible to recover?"
date: 2013-02-23
forum: General Help
---

### Post by david0723 on 2013-02-23
Hello

I installed Ubuntu for the first time on a secondary hard drive. I can't remember the name of the site that I followed for direction but I remember going to advanced hitting the - minus sign to remove the first hard drive thinking that it would leave it alone. I then hit the + sign to format the 2nd hard drive for ubuntu. After all was done I tested Ubuntu. I rebooted and did not have the option to boot to windows. I installed boot repair and it still doest not show up. I have a feeling that during the Ubuntu install it also reformatted the 1st hard drive where I had my windows.

Does anyone know if I can recover my windows?

Please help.
Thanks.

---

### Post by AngJinhang on 2013-02-23
i'm also afraid that you really erased the windows.
what version of ubuntu you are installing?
you should just choose 'run alongside windows'during the installation. no tweaks are needed for installing ubuntu.
so, the only way to check that your windows are still present is using the home folder. you should see your windows drive on the left... if not, bingo,you need a windows cd to recover it...
otherwise, something can be done to see that your windows system is still working.
in the terminal,type in:
*sudo update-grub*
and it will take up to one minute. it will scan all the OS on your pc. if it is still present, you will see the option to boot windows on your next boot.
hope that helps.

---

### Post by Hodevah on 2013-02-24
You will need to post the output of 
```

grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
```This will show what kernals you have installed and as well if there are any Windows OS installed as well. Please post the output using the code tag ( the "#" in the message box)

If there are any Windows OS, they will be on /dev/sda1 and /dev/sda2

---

### Post by Mark Phelps on 2013-02-24
Sorry for your troubles ... it's generally a good idea, if you have physically separate drives, to disconnect all but the drive you want to use for Ubuntu when you do the install.  

Myself, I prefer to look at the output of "sudo fdisk -lu" (lowercase L, not a one) as long as your PC isn't using UEFI BIOS or GPT formatting.

This will list out the partitions, filesystems, and sizes on all your drives -- and we can then see if the Windows partitions are still there and whether or not they are empty.

---

### Post by Sef on 2013-02-24
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk"), depending on what you did it could help.

---

### Post by bijupp on 2013-02-24
I think u have lost the xp Earlier I do also have the same and lost all even the data files are lost.  try any good partition recovery softwares in windows partedmagic etc

---

