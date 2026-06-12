---
title: "[SOLVED] XP won't boot!"
date: 2008-06-05
forum: General Help
---

### Post by Andross707 on 2008-06-05
If anyone could help....

XP hard froze on me while I was using it and I had to shutdown holding down the power button. Now, I can only boot into Ubuntu (Installed through Wubi) and when I try to select any option for XP (Safe, Normal, last known good config, etc) the computer just reboots and brings me back to the select the OS menu...

This is the computer at work and I need to use it for today so if anyone could help extremely quickly it would be very appreciated!

---

### Post by Gannon8 on 2008-06-05
> **Andross707 said:**
> the computer just reboots and brings me back to the select the OS menu...
Looks like a virus. Good thing you had a boot menu!
Try installing an Ubuntu virus scanner and scan windows.

---

### Post by Andross707 on 2008-06-05
OK I am installing the first result that comes up after searching Virus Scan in the Add/Remove Programs and will try to run it but if anyone has a faster fix I need to be able to get back into XP in about an hour

---

### Post by jualin on 2008-06-05
well if you are that desperate for Windows XP, you might want to install Windows in a virtual machine in Ubuntu so at least you can access it in an hour. Can you access your windows files from Ubuntu? And for the antivirus try ClamAV, it's very user-friendly. Good luck!

---

### Post by Andross707 on 2008-06-05
It asks me to update my virus definitions but when I try it says I must be root...I know the password but how can I enter it?

I tried to scan /host/ which is the windows directory in Wubi but it only scans 18 files and says no virus was found (Note I don't know how to authenticate myself as root in order to update the definitions for this...)

I've also read in other threads that you can run a chkdsk /r in Windows...is there something like this in Ubuntu? 45 min till the doctor arrives...

---

### Post by msidhard on 2008-06-05
just put the bootable Xp cd in drive and try to boot it from cd. then it will ask for repair of xp which was already installed . then u can fix the booting problem of xp. i havent installed ubuntu  using wubi so i cant tell further info about the consequences. if u get grub replaced by xp boot loader then u can download super grub disk and fix the os menu

---

### Post by jualin on 2008-06-05
To authenticate yourself as root you need to open the Run screen by pressing Alt + F2, and then writing > sudo (program that you want to initiate) To know what is the specific command name of your program go to System, Administration, System Monitor and look for the process name, which is usually something similar to the name of your program, for instance to open Nautilus as root you would type > sudo nautilus and that should make the trick. Now I think that msidhard's idea is better, since XP is really bad at getting back from Virus destruction.

---

### Post by Andross707 on 2008-06-05
For some reason I can't seem to boot from the diagnostics CD I have... I've tried to press F12 on startup and select to boot from the CD ROM but it just reboots me again and I'm back at the OS selection screen...

---

### Post by jualin on 2008-06-05
try other options instead Cdrom, sometimes is DVD or something like that. Plus that has to your first choice for booting if Hard Drive is your first choice then you will get the same problem again.

---

### Post by Andross707 on 2008-06-05
There is a Utility Partition I managed to boot to and it offered me a diagnostic scan option which I tried (the 10-20 minute long version) but no results came from it... Now though sometimes when I try to boot to Windows it looks like I might get the Windows loading screen but nothing happens and the monitor goes into suspend mode and just hangs...I probably shouldn't have but I held down the power button again to turn the computer off (I waited for about 2 minutes before doing this)

---

### Post by jualin on 2008-06-05
I dont know why your CDROM is not booting up your Windows XP CD. Do you have an original Windows XP CD?

---

### Post by Andross707 on 2008-06-05
Its a Dell Dimension and XPS Resource CD that contains Device drivers, Diagnostics and utilities, and computer documentation...it says on the CD label that I can boot from it.

---

### Post by jualin on 2008-06-05
then you should go back to the BIOS and try other boot options with the boot order. Sorry I cant be of too much help.

---

### Post by Andross707 on 2008-06-05
Well I'm still at it...ran a disk checking utility that ran off the service disk but no errors were found...I also ran a video card check from that same disk and that test also found no errors. I'm stuck, every time I select to boot from Windows XP in the boot menu it just restarts the computer and brings me back to the boot menu.....Does anyone have any idea of how to fix this computer?

Edit: Some semi-good news is that the recovery disk works and I've found that if I simply choose not to run the diagnostics utilities it will drop me to a dos prompt. The problem is that when I try to run chkdsk it just gives my some information about a drive (a drive that is referred to as a RAMdisk and that is listed as being smaller than my Hard Drive). chkdsk with the /r doesn't even run at all.

News 2: Now when I try to boot into windows and do a special boot of 'boot into safe mode with command prompt' I can reproduce the 'looks like I'm going to see the windows loading screen but then the monitor power light goes orange for a little bit and then the computer restarts' error. With trying to start windows normally it just reboots without a pause and it used to do this on 'boot into safe mode with command prompt'.

---

### Post by rogerdpenguin on 2008-06-05
Surprisingly enough this same situation happened to me, except a lot worse O_o. I was doing a video card update in ubuntu. I didn't know what I was doing and I accidentally got the WRONG video card update :mad:. I got a black screen and did a hard reboot. My computer would go through the menu right BEFORE the boot menu, then would restart >___>. I had to get a whole new hard drive. Lost 200 gigs of data ](*,)](*,)](*,)

EDIT: try booting a windows xp cd if you have one?

---

### Post by alzie on 2008-06-05
You may want to try supergrubdisk here:  
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Download and burn to cd,  hopefully you should be able to repair the MBR for windows.

I hope this helps

fdisk /mbr at the dos prompt MIGHT repair it.

---

### Post by ago on 2008-06-06
> **Andross707 said:**
> Its a Dell Dimension and XPS Resource CD that contains Device drivers, Diagnostics and utilities, and computer documentation...it says on the CD label that I can boot from it.

That is not a Windows CD. You can borrow one, boot into recovery console, and run chkdsk /r

---

### Post by Andross707 on 2008-06-08
Ok, I finally got XP to boot and not just go to a auto reboot after selecting it in the bootup menu after I found the XP Re installation CD and ran ChkDsk /r in the console.... It took me a little while because I didn't have the admin password that the recovery console asks for and had to download a bootable CD to reset the computer's password (shady). Another problem I encountered was that while I was in the process of trying to manually see if I could guess the admin's password I had tried to 'repair the Windows installation' with the option the XP re installation CD gave me. For future users, I must advise not to do this as this caused a whole other series of headaches (such as deleting all accounts but the administrators (data saved but desktop setup and whatnot lost))and I found that the reason XP crashed in the first place was due to a bad video card driver that caused the initial hard freeze that forced me to hold down the power button to turn off the computer. I would like to thank you guys for the help and the responses.

---

