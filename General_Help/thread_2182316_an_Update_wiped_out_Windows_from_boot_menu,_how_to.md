---
title: "an Update wiped out Windows from boot menu, how to get it back?"
date: 2013-10-20
forum: General Help
---

### Post by azitizz on 2013-10-20
I think it was a recent update of my system (running ubuntu 12.04) along side windows 7. Windows does not appear in the grub boot menu anymore. Ive tried to restore it using the grub costomizer but it doesnt even appear their either. Im not sure exactly when it disappeared and which update did it (or if that was the cause at all) as I dont use Windows 7 too much but still do use it.

Any Ideas on how to get it back?
Thanks in advance

---

### Post by Allavona on 2013-10-21
sudo update-grub

---

### Post by azitizz on 2013-11-03
> **Allavona said:**
> sudo update-grub

Thanks.
I tried it, but nothing. windows does not appear in the list. However I suspect its there by the look on the partition editor, am I right?

Any Ideas on how to restore it?
Thanks in advance
M

---

### Post by Bucky Ball on 2013-11-03
Looks like it's on sda2, but strange 'sudo update-grub' didn't pick it up ...

Do you see that partition in a file manager anywhere in Ubuntu?

PS: Not sure how an update would have wiped it from the grub menu. Has it changed the grub menu so it is now hidden (i.e. 'Other Operating systems' and when you click it takes you to a new window with the Win entry?).

---

### Post by oldfred on 2013-11-03
Just to see lots of details to understand your system.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by azitizz on 2013-11-05
> **Bucky Ball said:**
> Looks like it's on sda2, but strange 'sudo update-grub' didn't pick it up ...

Do you see that partition in a file manager anywhere in Ubuntu?

PS: Not sure how an update would have wiped it from the grub menu. Has it changed the grub menu so it is now hidden (i.e. 'Other Operating systems' and when you click it takes you to a new window with the Win entry?).

Yes I can actually access my windows files from the file manager. Also I'm not sure if its normal but just above the windows partition visible form the file manager, is a partition named System Reserved thats about 100MB in size that Ive never seen before re-installing Ubuntu, and perhaps it didnt appear till later but I cant say. May or may not be related...(see screenshot)

It may not be an update, but it just happened sort of randomly it seems. (I never made any big configuration changes or did an Ubuntu version update etc...) 

And nothing on the boot menu to indicate the lost windows entry. (like "other operating system" etc...)

Thanks for your inputs and Ill be following the suggestions of oldfred very soon. I just lent my live usb to someone and should gte it back tomorrow, plus I need sleep now so back at it tomorrow or the next day.
Thanks again

---

### Post by oldfred on 2013-11-06
Default installs of Windows 7 have a (hidden in Windows) 100MB boot partition. That is so you could encrypt the main install if desired as boot files cannot be encrypted. Normally grub2's os-prober finds the boot files in the 100MB partition and creates a chain load entry to it. Sometimes copies of boot files are in main install so grub finds both and creates 2 entries.

---

### Post by azitizz on 2013-11-16
> **oldfred said:**
> Just to see lots of details to understand your system.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

OK so I finally got everything I needed to do this. Heres the link for the boot info. If anyone can help with a diagnosis it would be very much appreciated.:
[http://paste.ubuntu.com/6429865/](http://paste.ubuntu.com/6429865/)

Thanks for all the help so far.

---

### Post by oldfred on 2013-11-16
Your sda1 is your Windows boot partition and it is missing these two boot files files. Unless for some reason script is not showing them. 

 Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

You need a Windows repairCd or flash drive to fix that.

---

### Post by azitizz on 2013-11-17
> **oldfred said:**
> Your sda1 is your Windows boot partition and it is missing these two boot files files. Unless for some reason script is not showing them. 

 Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

You need a Windows repairCd or flash drive to fix that.

Hmmm, Ok do you think just a regular windows 7 disc work? I also have a Vista to 7 upgrade DVD...

and do you think the disc will simply do the work? (other than changing the boot order in the bios)

---

### Post by oldfred on 2013-11-17
Versions should be the same to fix it. But not sure what difference maybe if different verisons.

One user posted he just copied bootmgr & BCD from  a repair disk and then repaired the BCD to have his install. But probably better to run the repairs from Windows repair console.

       [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

If you run Windows auto repair 3 times like it needs, it will also install the Windows boot loader to the MBR overwriting grub. That would not be bad as grub only boots working Windows and then you can confirm that it works on its own. But then you need to reinstall grub to MBR with Ubuntu live installer and a few commands or with Boot-Repair.

---

### Post by azitizz on 2013-11-17
Great. Its solved! I used teh directions located here: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

As my dvd repair option with win7 wasnt detecting any problem. 

Thanks everyone for your help. Ubuntu Rocks.

---

