---
title: "upgrading Win 7 to 10 in a dual boot system?"
date: 2020-02-04
forum: General Help
---

### Post by garyed on 2020-02-04
I'm currently dual booting Windows 7 with Ubuntu 18.04. I've heard that there is still a way to do an online upgrade to Windows 10 but I've read that it will cause problems a a dual boot system.  One other note is that Win7 & Ubuntu are on the same drive using a gpt partition. I assume I would need to reinstall grub afterwards but was wondering if there is really anything else I need to worry about? Also if someone could post instructions or a good link or for reinstalling grub in my situation I would appreciate it.
Thanks for any help,

---

### Post by CelticWarrior on 2020-02-04
> **garyed said:**
> (...I)  One other note is that Win7 & Ubuntu are on the same drive using a gpt partition. I assume I would need to reinstall grub afterwards but was wondering if there is really anything else I need to worry about

Windows in GPT is necessarily UEFI mode. So, no worries.

---

### Post by garyed on 2020-02-04
So am I correct that if i can upgrade Win 7 to 10 than all I should need to do is reinstall grub to get my Ubuntu back working? I'm just wondering if I have to worry about Windows 10 erasing any of my Ubuntu partitions that are on the same drive.

---

### Post by dragonfly41 on 2020-02-04
[COLOR=#000000]> was wondering if there is really anything else I need to worry about? 

I would add to the "worry list" not having a backup in (as a minimum) a second drive.[/COLOR]

---

### Post by yancek on 2020-02-04
I'm not familiar with the process but according to the link below, you need to first buy a license as apparently the time to get a free upgrade is past.  It does describe method to upgrade/install.  The 2nd link below seems to indicate it is still possible so you'll have to research and try it yourself.

[https://www.digitaltrends.com/computing/how-to-upgrade-windows-7-to-windows-10/](https://www.digitaltrends.com/computing/how-to-upgrade-windows-7-to-windows-10/)

[https://www.cnet.com/how-to/you-can-still-download-windows-10-free-you-should-because-windows-7-dead/](https://www.cnet.com/how-to/you-can-still-download-windows-10-free-you-should-because-windows-7-dead/)

If you do a backup and decide on a full install of windows 10, it has a 'Custom' install option where you can select the partition on which to install windows.

If you do in fact have windows 7 on a GPT drive which requires EFI for microsoft systems, it should create a folder for the windows EFI file and should not overwrite the Ubuntu files there.

---

### Post by garyed on 2020-02-04
I do have all my data backed up but I don't want to have to reinstall everything if I can help it. Here's a screen shot of my gparted for my OS drive. I have two other TB drives for backups & stuff.

---

### Post by CelticWarrior on 2020-02-04
Yes, it's in UEFI mode. Good.
But because you're asking the way you did and probably have no idea about BIOS (or Legacy or CSM) vs. UEFI modes... Not good.

---

### Post by dragonfly41 on 2020-02-04
Recently I added an external SSD and I now follow the practice of creating (through GParted in a LiveUSB) an ESP partition for each Ubuntu system which coexists with Windows 10.  

[This helpful article]("https://www.zdnet.com/article/hands-on-linux-uefi-multi-boot-my-way/") I found in searching around confirms that multiple ESP partitions can be installed.

This means in effect that in troubleshooting I can disable the ESP partition (/dev/sda1) which Windows uses and boot up Ubuntu OS from its ESP partition. For example in your dual boot layout you have unallocated space before /dev/sda5 and if I were setting up I would take 500 MB of that unallocated space to create a second ESP in that single drive. My external USB SSD also has an ESP partition.

Another practice I now follow is to install rEFInd which gives an alternative means of booting.

[Another helpful article]("https://forums.linuxmint.com/viewtopic.php?t=287353") is found here.

---

### Post by garyed on 2020-02-05
> **dragonfly41 said:**
> Recently I added an external SSD and I now follow the practice of creating (through GParted in a LiveUSB) an ESP partition for each Ubuntu system which coexists with Windows 10.  

[This helpful article]("https://www.zdnet.com/article/hands-on-linux-uefi-multi-boot-my-way/") I found in searching around confirms that multiple ESP partitions can be installed.

This means in effect that in troubleshooting I can disable the ESP partition (/dev/sda1) which Windows uses and boot up Ubuntu OS from its ESP partition. For example in your dual boot layout you have unallocated space before /dev/sda5 and if I were setting up I would take 500 MB of that unallocated space to create a second ESP in that single drive. My external USB SSD also has an ESP partition.

Another practice I now follow is to install rEFInd which gives an alternative means of booting.

[Another helpful article]("https://forums.linuxmint.com/viewtopic.php?t=287353") is found here.

Thanks , 
I'll check them out,
I don't even know what an ESP partition is but I'm sure i'll find out.
Thanks for the help

---

### Post by garyed on 2020-02-05
> **CelticWarrior said:**
> Yes, it's in UEFI mode. Good.
But because you're asking the way you did and probably have no idea about BIOS (or Legacy or CSM) vs. UEFI modes... Not good.

I do have an idea but it's been a while since I've messed with them & I'm mostly concerned about the Windows 10 upgrade messing with my Ubuntu partitions.  I remember having a time with GPT partitioning when I built this system I 'm planning on upgrading Windows on but everything worked out OK in the end.
Here's the link from about five years ago when I originally set this system up:  [https://ubuntuforums.org/showthread.php?t=2258934&highlight=dual+boot+uefi](https://ubuntuforums.org/showthread.php?t=2258934&highlight=dual+boot+uefi)

---

### Post by CelticWarrior on 2020-02-05
OK, here's the elaborated version of my original "no worries" statement.

Thanks to GPT and UEFI the Windows version upgrade won't mess with the other partitions, as long as you know your way around the Windows installer.

In the old times with BIOS the typical recommendation was to install Windows first but now with UEFI the order of installations is irrelevant because, unlike before, multiple OSes can have their bootloaders coexisting in the ESP (EFI System Partition) and, from UEFI settings > Boot (or equivalent menu) select each one to boot independently. And this can and should be used to your advantage in your upgrade project. I suggest temporarily changing the boot order to boot Windows directly. The upgrade process requires multiple reboots and it's easier to just let Windows do its thing. Then, once finished, you can change it back to "Ubuntu" which is actually Grub, boot Ubuntu and run 'sudo update-grub' to assure Grub has the up to date information on how to chainload with the Windows bootloader.

Your concern about Windows messing up partitions is valid but not applicable to GPT. That happened a few times after some Windows feature upgrades in MBR/BIOS installations only. I'm not sure why it happened but I don't believe it was a deliberate move from Microsoft like some said at the time. I think it was a side effect of some file system optimizations introduced in those feature upgrades that had an impact in the partition table. There are no reports of anything bad happening in GPT/UEFI.

---

### Post by garyed on 2020-02-05
Update,
Everything went as smooth as clock work & all my worrying was for nothing. Upgrading from Windows 7 pro to Windows 10 didn't even effect grub on my dual boot system.  
So for anyone running Windows 7 or 8 who wants update to Windows 10 for free it looks like it's still available at Microsoft's site & at least for me it worked perfectly.
My only advice if you're dual booting Windows & Ubuntu is I would change /etc/default/grub to default to booting into Windows for the update. The system has to reboot quite a few times while updating to Windows 10 so it kept booting back into Ubuntu every time I walked away from the computer & I had to reboot & manually go into Windows each time to finish updating. 
Thanks again to everyone for the advice.

---

### Post by CelticWarrior on 2020-02-06
> **garyed said:**
> My only advice if you're dual booting Windows & Ubuntu is I would change /etc/default/grub to default to booting into Windows for the update.

No need, really.

Quoting myself in the previous post (and highlighting the part you didn't understand):

> multiple OSes can have their bootloaders coexisting in the ESP (EFI  System Partition) and, **from UEFI settings > Boot (or equivalent menu)  select each one to boot independently.** And this can and should be used  to your advantage in your upgrade project. **I suggest temporarily  changing the boot order to boot Windows directly. **The upgrade process  requires multiple reboots and it's easier to just let Windows do its  thing. Then, once finished, you can change it back to "Ubuntu" which is  actually Grub, boot Ubuntu and run 'sudo update-grub' to assure Grub has  the up to date information on how to chainload with the Windows  bootloader. 

This is obviously applicable to UEFI installation only. If you were to do the same in a MBR/BIOS dual-boot you'd need to reinstall Grub after the Windows version upgrade. If Windows and Ubuntu were installed in different drives and the Windows drive already has a Windows bootloader in its MBR then one can change the drive boot order prior to installing Ubuntu so Grub is installed in the same drive where Ubuntu will be. It would then be quite easy to change the boot order to the other drive temporarily to upgrade Windows smoothly.

---

### Post by garyed on 2020-02-07
> **CelticWarrior said:**
> No need, really.

Quoting myself in the previous post (and highlighting the part you didn't understand):

 

This is obviously applicable to UEFI installation only. If you were to do the same in a MBR/BIOS dual-boot you'd need to reinstall Grub after the Windows version upgrade. If Windows and Ubuntu were installed in different drives and the Windows drive already has a Windows bootloader in its MBR then one can change the drive boot order prior to installing Ubuntu so Grub is installed in the same drive where Ubuntu will be. It would then be quite easy to change the boot order to the other drive temporarily to upgrade Windows smoothly.

I see what you mean now. I tried changing the boot order in the BIOS just to see how it would work & it did boot right up to Windows & bypass grub. Windows did boot up a little different though because it makes me enter my password if I boot up through the BIOS but if I boot to Windows through grub then it does not.  I do also have both Windows, Ubuntu & Grub on the same drive. Anyways that's good info to know. I'm so paranoid when I mess with Windows that I was thinking about completely disconnecting my other two drives before upgrading.

---

### Post by dragonfly41 on 2020-02-07
In post #5 I suggested the option of rEFInd.  Even with rEFInd I have had problems with Ubuntu 18.04 not being always found in an external SSD in docking station. Always the internal Ubuntu was found but not always the external Ubuntu.

In an experiment today I found that I can modify refind.conf (in /boot/efi/EFI/refind/) to force order of searching.

Default configuration is  [B]scanfor internal,external optical,manual
[/B]
I set it to **scanfor external,internal,optical,manual**

That is, scan **externa**l drives first.

And this forced an entry to boot up SSD first.

I rather suspect that there is some delay in booting up drives in a docking station and I have read other posts confirming this.

Just another nugget of information.

---

