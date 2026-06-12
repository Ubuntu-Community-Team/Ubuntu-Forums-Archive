---
title: "Install Windows 7 when Ubuntu is already installed"
date: 2017-09-28
forum: General Help
---

### Post by SnuKies on 2017-09-28
The story is a little bit more complicated than it appears.
I want to reinstall my W7 (only keep it for some games) on my laptop (Sony Vaio - Dual boot W7 & Ubuntu 14.04.5). Because I misread [this topic]("https://askubuntu.com/a/163249/573936") on StackOverflow, I deleted with GParted my W7 Partition, thinking Grub will let me boot from DVD.
Now I have only the Ubuntu installed and a free partition. What can I do to boot from DVD and install Windows 7?

---

### Post by RobGoss on 2017-09-28
From what I can gather from your post you'll need to install Windows 7 first then, install Ubuntu

I'm almost certain Windows will wipe your entire drive including Ubuntu. The Windows boot manager will override any other boot loader including the grub menu

Im sure other will have other opinions on how to approach this installation

---

### Post by oldfred on 2017-09-28
You normally boot operating system DVD or flash drive installers from UEFI/BIOS.

If system is newer UEFI hardware and you want UEFI install, you have to convert Windows 7 DVD to flash drive and copy/rename a couple of files to make it UEFI bootable.
If BIOS you should be able to directly boot DVD or flash drive from BIOS, often f10 or f12, check your manual.

If BIOS Widnows only installs to a NTFS formatted primary partition (sda1 thru sda4) with boot flag. 
Default install is entire drive and a small 100MB boot partition and then main install partition.
Windows on installs & major updates "forgets" to see and include any logical Linux partitions when it rewrites partition table.
Make sure you have good backup of all your data in Linux and your configurations.
And make a separate backup of partition table structure and copy to another device.

 backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print

---

### Post by SnuKies on 2017-09-28
Well, in that case, I'll take @RobGross' advice and reinstall Windows 7, followed by Ubuntu.
But what should I do so my CD will be read? I cannot chose "boot from DVD" from my BIOS. The only thing I can do is to change the order, which I already did. Should I remove GRUB, since I will fully reinstall both ?

Also, my table looks like this :
[IMG]http://i67.tinypic.com/1zl5csz.jpg[/IMG]

(/dev/sda1 -> Windows,  /dev/sda3 extended partition where Ubuntu is, /dev/sda4 -> shared partition, where I keep most of my files)


If I reinstall them, Windows 7 won't affect my table, right? I am interested in that "shared" partition ( /dev/sda4), because there are most of my files.

---

### Post by kurt18947 on 2017-09-28
Old Fred is the authority on these things. I was faced with your situation - wanting to reinstall Windows while keeping *buntu. I only have BIOS systems. I had no problem getting Windows to install to the proper partition after I had formatted it to NTFS with Gparted. My difficulty came when the Windows installer overwrote GRUB so I could only boot Windows. I was able to restore normal function using the boot-repair disk. I don't know if the current boot-repair disk is functioning properly or not.

---

### Post by RobGoss on 2017-09-28
>  Should I remove GRUB, since I will fully reinstall both ?  

There's no need t remove the grub, once you've installed it will be overriding by the MBR boot loader for Windows



> If I reinstall them, Windows 7 won't affect my table, right? I am interested in that "shared" partition ( /dev/sda4), because there are most of my files.


If I were you I would make a backup or copy, any important data and documentations to a **USB** or external hard drive for safe keeping. This way if anything goes wrong you at least your data

---

### Post by oldfred on 2017-09-28
Anytime you have data on a drive and are making major changes, you must have good backups. Then any sort of hiccup is not the end of the world.

You have to boot from BIOS and that should boot DVD before you even get to grub.
Unless DVD is not bootable or ISO not correct installed (not copied) to DVD or flash drive.

---

### Post by SnuKies on 2017-09-29
I followed @kurt18947's advice and checked the DVD... it wasn't bootable.
Now I made a truly bootable one, and I'm backing up my files.
Keep this open, please. I'm sure I'm gonna need help with GRUB's repair

---

### Post by oldfred on 2017-09-29
Boot-Repair is often easier to restore grub2's boot loader, but it really is only a couple of commands.

 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by wheatpenny2 on 2017-09-29
The other day, I had to reinstall Windows 10 on a computer that had been dial-booting until some of my windows files became corrupted.  II thought I would have to reinstall Ubuntu as well. So I reinstalled Windows in the Windows partition and when  I finished, I was surprised to find my Ubuntu installation intact.  So if you know which partition Ubuntu is installed in, don't touch that one when you get to the part of the Windows install where it asks which partition to install it in. Select the empty partition that presumably had windows in it before. (but back up all your Ubuntu stuff just to be safe).

---

