---
title: "Triple Boot XP/8.1/Ubuntu"
date: 2015-01-04
forum: General Help
---

### Post by TechnoDaft on 2015-01-04
k well it  works but not the way i want it to.
I Installed XP then 8.1 the Ubuntu and Grub  has ubuntu/Windows 8 loader for options and the windows 8 loader gives  me an option for XP or Windows 8.1
what I'm wanting is to choose  between 8.1/xp and ubuntu in grub loader instead of using windows 8 loader to choose between 8.1 and xp.
Does anyone know how i can fix that any help will be apreciative.

---

### Post by TechnoDaft on 2015-01-04
[http://paste.ubuntu.com/9673118/](http://paste.ubuntu.com/9673118/)
thats the boot-repair {sda1 has xp but windows 8 boot sector sda2 has 8.1 but it's not detected?}

---

### Post by Mark Phelps on 2015-01-04
> to choose between 8.1/xp and ubuntu in grub loader 

There is no simple way to do that and Boot-Repair is (AFAIK) NOT going to help in that.

Why?

Because all GRUB does, in the case of Windows, is hand over control to the boot loader contained in the partition the GRUB stanza is pointing to.  To have separate GRUB entries, you need not only separate GRUB stanzas, but you need separate boot loaders.

When you install a newer version of Windows, when an older one is already in place, the default is to "upgrade" the existing boot loader information to add the newer OS.  Thus, if you have XP and install Win7, Windows will write the Win7 boot loader files into the XP partition containing the XP boot loader files.  When you then reboot, you will get a Windows OS Selection menu, containing both XP and Win7.

To do what you want, you would need to do the following:
1) Copy the Win8.1 boot loader files from the XP OS partition to the Win8.1 OS partition.
2) Reset the boot loader files in the XP partition back to those used by XP
3) Add a stanza to the GRUB config file fot Win8.1 that points to the Win8.1 boot loader

If your machine is using UEFI, that is whole different situation, one with which I have no experience.

---

### Post by oldfred on 2015-01-05
You probably also have to run chkdsk from XP on the XP partition and chkdsk from a Windows 8 repair flash drive on the Windows 8 install. Move boot flag to the Windows 8 partition before running repairs on it.
Windows boots from MBR to PBR or partition boot sector of partition with boot flag. Inside partition boot sector is reference to the boot loader to use, either ntldr for XP, or bootmgr for Vista or later. So the XP partition now has bootmgr in its PBR. Removing Windows 8 boot files and running chkdsk from XP should reset it to ntldr. You also can use bootsect.exe to install the correct type of PBR.

 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

      
 Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition, but do not have to be)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by TechnoDaft on 2015-01-05
when i repaired XP's boot win8.1 wouldnt boot
I repaired win8.1 and then it went back to windows boot loader for xp/8.1 and grub for linux
But I set grub to auto-boot Ubuntu and used EasyBCD so got 1 menu for all 3 OS's now and no errors so far

thanks for the help tho guys really appreciated and bookmarking those links got a feeling ill be needing em

read the links thanks a lot definatly what I was looking for :D

---

### Post by Mark Phelps on 2015-01-05
> when i repaired XP's boot win8.1 wouldnt boot

That's because Win8 uses a newer generation of boot loaders than XP. When you installed Win8, it copies its newer boot loader files to the XP partition and added XP to the OS selection menu.

---

### Post by oldfred on 2015-01-05
EasyBCD works for some. But can cause issues with grub. It forces grub to use blocklists or hard coded addresses. Grub updates or even a fsck may move file on drive and then it will not boot until you reinstall grub. So have Live installer handy.

Did you move boot flag to Windows 8 before repairing it? Otherwise its repairs just restored Window 8 boot loader to the XP partition.

And splitting Windows boots will not let you boot both systems from Windows. And you have to have fast boot or always on hibernation off or you will have issues, even if only dual booting XP & Windows 8.

---

### Post by TechnoDaft on 2015-01-06
> **oldfred said:**
> EasyBCD works for some. But can cause issues  with grub. It forces grub to use blocklists or hard coded addresses.  Grub updates or even a fsck may move file on drive and then it will not  boot until you reinstall grub. So have Live installer handy. yep  got 1 just incase but no issues so far

> **oldfred said:**
> Did you move boot flag to Windows 8 before  repairing it? Otherwise its repairs just restored Window 8 boot loader  to the XP partition. nope but did that and made a boot partition  and all that and it's working perfectly {got all the boot files backed  up now to XD}

> **oldfred said:**
> And splitting Windows boots will not let you  boot both systems from Windows. And you have to have fast boot or always  on hibernation off or you will have issues, even if only dual booting  XP & Windows 8. fast boot isn't on {I don't think anyways}  and hibernation {in power saving} is disabled

But I got it working and you have answered all my questions/problems and  put me in ther perfect direction to get what i wanted done thank you  very much 
/solved

---

### Post by oldfred on 2015-01-07
Glad it is working. :)

Please change thread to solved.

---

