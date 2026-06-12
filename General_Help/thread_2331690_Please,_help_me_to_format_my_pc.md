---
title: "Please, help me to format my pc"
date: 2016-07-24
forum: General Help
---

### Post by elpalomolelouch on 2016-07-24
Hi. I have a problem with the BIOS America Megatrends 2.15.1226 and I hope you can help me :')
Ok, I'm going to explain the problem: I want to format my pc and install linux ubuntu, the problem is when I enter to the BIOS, in the boot tab, I just have these options:


Boot option priorities 
Boot option #1 [Windows Boot Manager] 




OS Select 


So I can't select a boot option with a hard drive like an usb or a cd/dvd, this is the problem. I've investigated a lot of this problem, and I couldn't find anything, so I wait your help, please help me.


Thank you for your attention.
If someone have any doubt just ask and I'll try to solve it as fastest as possible

PD: Sorry for my terrible English, I'm from Argentina so I don't speak English very good.

---

### Post by mastablasta on 2016-07-25
what happens if you select boot option priorities?

---

### Post by yancek on 2016-07-25
If you purchased this machine from a major manufacturer (HP, Dell, Asus, etc.) you should have a manual.  If you don't it would be a good idea to do an online search for whatever computer you have and append the word manual to it as most manufacturer have online manuals available.  You can then search for a way to access the boot priority settings if the above suggestion fails.

---

### Post by oldfred on 2016-07-25
If you have UEFI Secure Boot on, it may not let you boot anything other than the Secure Boot options and it may also not let you boot external devices as they by default may be assumed as not Secure.
Turn off UEFI Secure Boot. It may also just be called "Windows" or "Other" in UEFI. You want other.
And you may have to turn on allow USB or DVD boot.

You also have to have made the flash drive or DVD correctly as bootable devices, otherwise the UEFI boot manager will not see a standard data flash drive.

       Ubuntu UEFI install ISO
Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Easy way to create UEFI only bootable flash drive
[URL="http://ubuntuforums.org/showthread.php?t=2299040"]http://ubuntuforums.org/showthread.php?t=2299040

      [/URL]
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

Even more info in link in my signature.
 

    [URL="http://ubuntuforums.org/showthread.php?t=2299040"]
[/URL]

---

### Post by elpalomolelouch on 2016-07-25
[mastablasta]("https://ubuntuforums.org/member.php?u=964486") 
You can't select it, you just can select Boot option #1 and OS.
If you select boot option #1 you can select [Windows Boot Manager] or nothing.
If you select OS, a new tab will open and you can select the OS, but the unique OS avaiable is Windows 8 (the default OS) :/mastablasta[mastablasta]("https://ubuntuforums.org/member.php?u=964486") 

[yancek]("https://ubuntuforums.org/member.php?u=1928724")
The problem is that I have no idea which is my computer, I just know the patent (Bangho) but I don't know which is my serial number, or my motherboard's name. I've searched it before so don't worry about that, and I've search a manual too and I couldn't find anything, If I start searching something like that, it will be a waste of time, thanks anyways.

[oldfred]("https://ubuntuforums.org/member.php?u=852711") 
I will try it, I think it would be a solution, the unique problem is that If I want to enter the BIOS I can't enter in the boot, for example, when you turn on your pc appears the computer's patent and in some place of the screen a message saying that if you want to enter the BIOS you must press "x" key (x would be any key),  but in my computer the message doesn't appears, so if I want to enter the BIOS in Windows 8 I have to go to the right side of the screen, then the tab of windows 8 will appear, I have to select change pc's configuration, and in this tab I have to select, general, and in that tab (yes I know there're a lot of tabs xD) I have to go to the lower part and select the option that says reboot now. You reboot, select repair, then advanced options and configuration of UEFI, you reboot again and then you enter to the BIOS, yes, It's very complicated.

---

### Post by oui on 2016-07-25
usually Ubuntu does all things needing themself during the installation... you only, if it continue to be so, only to install ubuntu completely fresh from the actual ISO on your harddisk and give it completely free to install on all the complete disk. I suppose Ubuntu make less error as human operator doing that. after the installation is finish, you can shrink, if you need, the partition to create more partitions.

manipulate in the BIOS is probably not a good idea so long other ways are really possible. an other way is to do it themself using "gparted". you create a new partition table and this will formate your harddisk very efficiently. but what will create a new partition table? have you the knowledge in that matter? if yes, gparted can be used as adequate tool...

---

### Post by oldfred on 2016-07-25
Found an older thread looks like user had same BIOS and same issue, but did not post if Solved or not, nor any explanation.
User posted a variety of screen shots also:
[https://ubuntuforums.org/showthread.php?t=2166009](https://ubuntuforums.org/showthread.php?t=2166009)

This user had same issue. But it was an Asus.
He had to update UEFI/BIOS to get it to work. Can you download new UEFI/BIOS from vendor?
[http://www.techsupportforum.com/forums/f108/solved-how-do-i-add-usb-cd-rom-in-bios-842049.html](http://www.techsupportforum.com/forums/f108/solved-how-do-i-add-usb-cd-rom-in-bios-842049.html)

---

### Post by elpalomolelouch on 2016-07-25
[[COLOR=#000000]oui[/COLOR]]("https://ubuntuforums.org/member.php?u=22410")[COLOR=#000000] [/COLOR]
That's a good idea, i think I'll use vmware to do it, anyways, I'm feeling useless because I can't format my pc throught the BIOS :(

[[COLOR=#C61919]oldfred[/COLOR]]("https://ubuntuforums.org/member.php?u=852711")[COLOR=#000000] [/COLOR]
I know it..... but I'm really scared, because if i make a mistake, or my internet connection fails I wouldn't be able to use my computer anymore :(

[[COLOR=#C61919]oldfred[/COLOR]]("https://ubuntuforums.org/member.php?u=852711")
If you can find an upgrade of my BIOS i will be very grateful

---

### Post by oldfred on 2016-07-25
Need exact brand/model of system. And version of UEFI/BIOS. You cannot use any other source reliably than the vendor.

You normally then go to the vendor's web site and look for section on support. The often have copies of manuals, driver updates(for Windows) and BIOS/UEFI updates with instructions on how to do the update. 

I have desktops with motherboard, so I go to motherboard vendor and search for support for my model motherboard. Then compare latest version with the version I have.

---

