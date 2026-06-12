---
title: "I want to resize my partition and install windows, how do I do that?"
date: 2015-05-22
forum: General Help
---

### Post by Jean_Rose on 2015-05-22
okay so I installed ubuntu on my 1gb hard drive using the automatic settings which resulted in 3 partitions like so: 

/dev/sda1 fat32 512 MiB flags: boot, esp
/dev/sda2 ext4 923.13 GiB
/dev/sda3 linux-swap 7.88 GiB

so i figured the first one is for efi, the second one for the actual stuff and third for swap.

not i wanna make some space of 500 GiB or so to install windows 8.1 so I can do stuff with windows, now how do I go about doing that? I assume the first step would be to resize the partition but because it is mounted, I can't do that. Then I would need to install windows, i assume it would use the existing efi space no problem, am i right in this?

and how would I choose which OS to load when I boot?

thanks

---

### Post by oldfred on 2015-05-22
You have to use live installer, so all partitions are unmounted. It has gparted on it which works well for resizing Linux partitions. 
But as with any major system change be sure to have good backups.

Best to also create a separate NTFS shared data partition, so you are not directly writing into Windows system partition.
You must turn off Windows fast startup or always on hibernation.

Be sure to boot in UEFI boot mode, so it installs in UEFI mode.
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

If creating Windows partitions in advance, be sure to include the extra partitions Windows needs for UEFI.
      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by monkeybrain20122 on 2015-05-22
Unless you want it for gaming why not just install it in virtualbox/

---

### Post by Kpenguin on 2015-05-22
> **Jean_Rose said:**
>  and how would I choose which OS to load when I boot?  thanks  I think you could use Boot Repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) after you have installed everything to install GRUB, which will give you an OS selection screen every time you turn your computer on.

---

### Post by oldfred on 2015-05-23
With UEFI you can also choose from UEFI's own boot menu or most systems have a one time boot key, often f10 or f12 to show that UEFI boot menu.
With UEFI the install of the Windows boot files to the ESP efi system partition does not overwrite the grub boot files like a BIOS/MBR install does since with MBR you only have one per drive. 
With the ESP you can have an unlimited number of different folders for booting different systems.

And from Ubuntu booted with UEFI, you can run this to add Windows to grub's boot menu.
sudo update-grub

But you must install Windows in UEFI boot mode by booting Windows installer in UEFI mode, or it will convert drive to MBR and BIOS boot erasing Ubuntu.

---

### Post by Jean_Rose on 2015-05-23
Why do I need to turn off windows fast startup and always on hibernation?

How do I boot in UEFI mode?

Do I have to create the windows partition in advanced or will the windows installer do it for me?

Will I still be able to boot into ubuntu? Will the bootloader be replaced by window's?

---

### Post by Jean_Rose on 2015-05-23
> **monkeybrain20122 said:**
> Unless you want it for gaming why not just install it in virtualbox/

I need it so others can use the machine to do their stuff and they are used to windows.

---

### Post by Jean_Rose on 2015-05-23
This UEFI thing is confusing to me. A lot of the material on the net is based on the old MBR BIOS system.

---

### Post by oldfred on 2015-05-23
You have to ignore all the old BIOS/MBR info and only look at newer UEFI with gpt partitioning info.
Never installed UEFI  Windows, last install was XP in 2006.

       WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast startup
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by Jean_Rose on 2015-05-23
so windows 8 deletes stuff when coming off hibernation.

But only on the windows partition?

---

### Post by oldfred on 2015-05-23
Generally best to not write directly into the Windows system partition anyway. You can set mount to be read only. Then have another NTFS partition set as read/write. The Linux NTFS driver exposes all the hidden files & folders that Windows normally hides and that leads to accidents.
But Windows does not seem to have an easy way to unmount. So you still have to keep hibernation off. And it restores the file structure, so any new files disapper.

---

