---
title: "After installed ubuntu as second OS i cant use win7 anymore."
date: 2013-02-08
forum: General Help
---

### Post by Solarwin on 2013-02-08
Hello.
After i installed Ubuntu 12.10 i cant use win7 anymore, but the system files are still in the same hdd partition. I have to hard disk partitions, but i cant use win7 anyway. In boot selection it shows only ubuntu. What can i do? I tried everything that i found on net nothing helps.:/

Please please help, i am student and i really need to get my win7 back ;/

---

### Post by papibe on 2013-02-08
Hi olarwin. Welcome to the forums ):P

Did you install Ubuntu using Wubi or the media installer (CD/USB)?

Regards.

---

### Post by GameX2 on 2013-02-08
> **Solarwin said:**
> Hello.
After i installed Ubuntu 12.10 i cant use win7 anymore, but the system files are still in the same hdd partition. I have to hard disk partitions, but i cant use win7 anyway. In boot selection it shows only ubuntu. What can i do? I tried everything that i found on net nothing helps.:/

Please please help, i am student and i really need to get my win7 back ;/

In case you have to use your Windows 7 quickly, you might want to download and burn Super GRUB 2 Disk.  The ISO is bootable:

[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)

Pop in the CD, boot from it (Make sure your BIOS is configured to boot from the CD-ROM drive), and you'll get to the Super GRUB 2 menu.  Select "Detect any OS".  GRUB should detect your Windows 7 installation, and you'll be able to boot from it (This CD also is really useful to restore GRUB or boot on Linux when Windows deleted GRUB).

Remember, that only help you to boot on Windows 7, that won't fix the bootloader problem.
Generally, that's not hard to fix, but as Papibe said, we need additional details to help.

---

### Post by Solarwin on 2013-02-09
> **papibe said:**
> Hi olarwin. Welcome to the forums ):P

Did you install Ubuntu using Wubi or the media installer (CD/USB)?

Regards.

i used usb flash drive, but i burn these files into flash drive with program (there was flower icon,so it might  be Wubi)

---

### Post by Mark Phelps on 2013-02-09
> **Solarwin said:**
> Hello.
After i installed Ubuntu 12.10 i cant use win7 anymore, but the system files are still in the same hdd partition. I have to hard disk partitions, but i cant use win7 anyway. In boot selection it shows only ubuntu. What can i do? I tried everything that i found on net nothing helps.:/

Please please help, i am student and i really need to get my win7 back ;/

Do NOT install anything -- we don't know enough to give you details at this point, and if you install stuff, that will only make matters worse.

When you installed Ubuntu, if you installed to its own partition, it added GRUB to the drive MBR -- thus now, it boots directly into Ubuntu.  Win7 is most likely NOT harmed in any way.

So, boot into Ubuntu, open a terminal using Dash, and enter "sudo update-grub" (without the quotes).  That will regenerate the default GRUB config file, and as it runs, you should see it find Windows 7.  When you reboot, you should be seeing a GRUB menu.

If this does not work, we will need more info.

---

### Post by Solarwin on 2013-02-09
> **Mark Phelps said:**
> Do NOT install anything -- we don't know enough to give you details at this point, and if you install stuff, that will only make matters worse.

When you installed Ubuntu, if you installed to its own partition, it added GRUB to the drive MBR -- thus now, it boots directly into Ubuntu.  Win7 is most likely NOT harmed in any way.

So, boot into Ubuntu, open a terminal using Dash, and enter "sudo update-grub" (without the quotes).  That will regenerate the default GRUB config file, and as it runs, you should see it find Windows 7.  When you reboot, you should be seeing a GRUB menu.

If this does not work, we will need more info.
I did that, but when i restarted my system it showed me four options (2ubuntu,linux and 2memory tests). What info do u need?
[IMG]http://imageshack.us/photo/my-images/13/screenshotfrom201302091.png/[/IMG]

---

### Post by Mark Phelps on 2013-02-09
> **Solarwin said:**
> I did that, but when i restarted my system it showed me four options (2ubuntu,linux and 2memory tests). What info do u need?
[IMG]http://imageshack.us/photo/my-images/13/screenshotfrom201302091.png/[/IMG]

When update-grub ran, you should have seen messages as the os_prober found things, and one of them should have said something like "Windows 7 Loader ..."

If it didn't show that (and, you can run it again, it won't hurt anything), that means the files os_prober is looking for are gone -- and these are the Windows boot loader files.

To confirm that, look for a folder named "bootmgr" in your Windows partition.  IF Win7 came preloaded on the PC, there will be a small partition containing that, if you installed it, that folder is most likely in the Win 7 OS partition.

Had you not rushed into installing Ubuntu and asked here first, I could have told you how to make your own Win7 Repair CD -- which you could be using now to repair the Win7 boot loader.

You could try using boot-repair (see below) as it has had some success at fixing these kinds of problems:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by Solarwin on 2013-02-09
> **Mark Phelps said:**
> When update-grub ran, you should have seen messages as the os_prober found things, and one of them should have said something like "Windows 7 Loader ..."

If it didn't show that (and, you can run it again, it won't hurt anything), that means the files os_prober is looking for are gone -- and these are the Windows boot loader files.

To confirm that, look for a folder named "bootmgr" in your Windows partition.  IF Win7 came preloaded on the PC, there will be a small partition containing that, if you installed it, that folder is most likely in the Win 7 OS partition.

Had you not rushed into installing Ubuntu and asked here first, I could have told you how to make your own Win7 Repair CD -- which you could be using now to repair the Win7 boot loader.

You could try using boot-repair (see below) as it has had some success at fixing these kinds of problems:

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)


I tried but nothing changed. Here is the paste, hope it could help You:

[http://paste.ubuntu.com/1629976/](http://paste.ubuntu.com/1629976/)

[http://www.filedropper.com/screenshotfrom2013-02-09185555](http://www.filedropper.com/screenshotfrom2013-02-09185555)

---

### Post by bcbc on 2013-02-09
Your windows boot partition has been switched to a linux swap partition. You can't boot windows without those boot files.

Hopefully a Windows Repair disk will fix it.

---

### Post by Solarwin on 2013-02-09
> **bcbc said:**
> Your windows boot partition has been switched to a linux swap partition. You can't boot windows without those boot files.

Hopefully a Windows Repair disk will fix it.
what to do if i dont have windows repair disk,?

---

### Post by bcbc on 2013-02-09
You need either a Windows repair CD or a Windows installation DVD. You can download a windows repair CD ISO from the internet (for about USD10).

I'm not sure it will work though. The repair depends on the detection of Windows and I'm not sure how it does this. If it relies on those boot files that no longer exists you might be out of luck. I'm looking around on the net to see if someone has some instructions.

---

### Post by oldfred on 2013-02-09
I would delete swap from fstab and make sure you are not using it. If you have a fair amount of RAM you may not have used swap and files are still there?

       sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

    
Put a # in front of the swap line to convert to comment.

       sudo mount -a
    If no errors or just warning on no swap then you have removed swap from system.

Then use Disk Utility and change type of sda1 to 07 or NTFS. And add boot flag to sda1.

This also has a link to another site with Windows repair CD.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by bcbc on 2013-02-09
Don't fix just the bootloader and bootsector (that'll be needed too) - you need all the missing boot files as well.

Burn the Windows Repair CD, boot from it and select to repair. If you want to restore the boot partition, you should remove swap as oldfred mentioned, and reformat as NTFS. The boot flag is already set.

This seems to be the closest I can find to your situation: [http://www.sevenforums.com/installation-setup/146403-broken-mbr-boot-system-partition.html](http://www.sevenforums.com/installation-setup/146403-broken-mbr-boot-system-partition.html)

---

