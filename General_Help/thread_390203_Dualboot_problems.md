---
title: "Dualboot problems"
date: 2007-03-21
forum: General Help
---

### Post by dobbeltseng on 2007-03-21
Hi.

I have some problems with dualbooting Ubuntu and XP on a laptop, using the Windows bootmanager.
First I install Ubuntu 6.10. I split my disk in 3 partitions.

Hda1 - NTFS
Hda2 - Ext3
Hda3 - Swap

When Ubuntu is finished I copy the bootloader from MBR with the command:
dd if=/dev/hda of=/tmp/ubuntu.bin bs=512 count=1
Then I copy the ubuntu.bin file to an usb-stick.

Now I install XP to the NTFS partition. 
When XP is installed, I copy the ubuntu.bin file to c:\ in XP.
Then I edit boot.ini in XP and add the line:
c:\ubuntu.bin="Ubuntu"
Save the file and reboot the computer. I can now boot booth Ubuntu and XP from the Windows bootmanager.
So far so good. 

My problems begin when I install a program called "Safeboot" in XP.
It's a program that encrypts the Windows partition and installs a bootprotection.
When I boot the computer I first get a logon screen for safeboot.
I login on the safeboot loginprompt, and then I come to the Windows bootmanager.
When I choose Ubuntu, grub starts and I get to the place where it says:
Starting up...
Then nothing more happends. Can anyone please help me with this?
Any help would be very much appreciated.

---

### Post by Kamikaze Wardriver on 2007-03-21
I don't have much experience with safeboot. I can offer a guess as to what is happening. If the windows partition is encrypted then you maybe having trouble accessing the ubuntu.bin file after you enter the grub phase. If having the drive encrypted is causing problems you may need to contact the vendor for a work around.

---

### Post by dobbeltseng on 2007-03-22
> **Kamikaze Wardriver said:**
> I don't have much experience with safeboot. I can offer a guess as to what is happening. If the windows partition is encrypted then you maybe having trouble accessing the ubuntu.bin file after you enter the grub phase. If having the drive encrypted is causing problems you may need to contact the vendor for a work around.

I also thought that that might be the problem. But if I remove the Grub bootloader and install Lilo instead, it works fine. 
But isn't it so that when you update the kernel, you have to reconfigure Lilo each time?
That's why I would like to use Grub as the bootloader for Ubuntu.

---

### Post by Kamikaze Wardriver on 2007-03-22
> **dobbeltseng said:**
> I also thought that that might be the problem. But if I remove the Grub bootloader and install Lilo instead, it works fine. 
But isn't it so that when you update the kernel, you have to reconfigure Lilo each time?
That's why I would like to use Grub as the bootloader for Ubuntu.


Have you tried to install Linux first and then install XP? Maybe if Grub comes up before the windows bootloader that might work.

---

### Post by Kamikaze Wardriver on 2007-03-22
> **dobbeltseng said:**
> I also thought that that might be the problem. But if I remove the Grub bootloader and install Lilo instead, it works fine. 
But isn't it so that when you update the kernel, you have to reconfigure Lilo each time?
That's why I would like to use Grub as the bootloader for Ubuntu.

Actually my last post was backwards. If you want to move Grub ahead of Windows then you would first install XP. Then install linux. After that boot to windows and load Safeboot. If safeboot only encrypts the windows partition and not the entire drive that should work.

---

### Post by dannyboy79 on 2007-03-22
I think the last post is saying that you should try to use grub as your bootloader. BUt the question would be how do you get grub to use the safe boot booting method??? You would really need to understand what safeboot does?

You could always try to create a small boot partition and instead of storing ubuntu.bin on your c drive, store on this little unencrypted boot partition, that should work. then your boot.ini would be something like
d:\ubuntu.bin="Ubuntu"


I found this on a college website and suggestions for protecting laptops:

Does Safeboot support the Linux operating system?  It does support some flavors of Linux.  Please contact IT Services for additional help in this regard.

So you best bet would be to call them if you want to stick with it and not use a boot partition..

---

