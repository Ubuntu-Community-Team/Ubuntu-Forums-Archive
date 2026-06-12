---
title: "how to install ubuntu on second disk alongside Windows 10(with grub on separate disk)"
date: 2020-02-15
forum: General Help
---

### Post by empleat on 2020-02-15
[COLOR=#000000]I need to ubuntu be installed on second disk ! Both my disks are GPT and i am using UEFI boot. Also i need bootloader on second disk, if linux would crap out, so i can save Windows. This is non negotiable !!![/COLOR]
[COLOR=#000000]I installed it , but i didn't see entry in bios and i didn't see grub, but computer booted straight into Ubuntu. I tried boot-repair, but it was bugged, it didn't even work and various solutions... Nothing worked ![/COLOR]
[COLOR=#000000]How do i install ubuntu this way, so i can select my system at start using grub ? And i don't have much time as well, i need to set this up asap. I uninstalled it, but i need to install it again.

How did i post new thread from editing ??... Can't delete it sry...[/COLOR]

---

### Post by oldfred on 2020-02-15
Its a bug in Ubiquity installer. Other distributions will install to drive selected. Ubuntu only installs to first drive.

Often easiest solution is in UEFI turn off/disable Windows drive. Then drive you install into will be first drive. Or physically disconnect Windows drive.

If not able to hide or disconnect Windows drive, you can unmount wrong ESP and mount correct ESP. But you have to do it in the middle of the install during password creation screen & after install update fstab with correct ESP (somehow it still finds the first unmounted drive). 
Used this to install 20.04 to sdb & put boot files in sdb, as it wanted to keep 18.04 as main working install on sda. Still had to reset boot order in UEFI.

       Posted work around to manually unmount & mount correct ESP during install #23 & #26
[URL="https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379"]https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379
      [/URL]
 Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457) 
    
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488)

---

### Post by empleat on 2020-02-16
So i did that and it worked, ubuntu is now working. Problem is grub is not showing when i start computer, it boots straight into linux. And boot-repair from live usb is bugged as well, it says: boot to live usb and than run it again. But i am already in live-usb. How do i bring back grub menu please ???? I tried already couple random solution from internet and nothing seems to work...

---

### Post by oldfred on 2020-02-16
Are you able to boot your install?
If installed in UEFI boot mode, you can press escape right after UEFI/BIOS screen and before grub loads.
Have you run this?
sudo update-grub from within install.

Have seen several others with the message from Boot-Repair on live installer when in live installer. Not sure what it checks?

---

### Post by empleat on 2020-02-17
So for order: i disconnected all disks - so disk i want install to is only one. I chose something else, made one / partition, one swap 5000MB. One efi 2800 mb. Choose efi partition for bootloader and installed ubuntu. Than switched on disks and boot straight into ubuntu, which gave already error when i get to the desktop. Just some generic message, don't remember it. But i verified sha256 sum of iso. And made bootable usb using rufus fat 32, gpt, uefi. And rest was on default and used dd mode.

I can boot into ubuntu by manually choosing boot record, which is annoying, i used to have grub, when i could choose and system boot automatically to system of last choosing... I tried command sudo update-grub and it still doesn't work. Pressing escape, after post screen brings me to command line not to the grub ! 

> [COLOR=#000000]Have seen several others with the message from Boot-Repair on live installer when in live installer. Not sure what it checks?[/COLOR][COLOR=#000000] 
No i get only message that i need to be in live usb, when i tried to run recommended repair within boot-repair utility. [/COLOR]

---

### Post by oldfred on 2020-02-17
When you say is boots when manually choosing, are you not choosing in grub?
Or is it UEFI boot menu?

Then it may be that you have wrong default in UEFI boot choice?
In UEFI you have various settings to change boot order. Most allow deleting entries also. That often is f2. Then the order you set is what you see in f10 or f12 UEFI boot menu.

In Ubuntu you can see UEFI boot options:
sudo efibootmgr -v

Can you run the Boot-Repair Summary Report and post that link?

---

### Post by empleat on 2020-02-17
No grub shows, i am choosing boot record from BIOS. I have only 2 entries ubuntu and my windows bootloader.  I just completed summary-info and gonna try that command from ubuntu install: [https://paste.ubuntu.com/p/bwhfcMQn5c/](https://paste.ubuntu.com/p/bwhfcMQn5c/)   Command showed only 2 boots , same  as in bios boot selection menu. How to show grub at boot than ? Because it boots straight into ubuntu. And have that command line when i press escape after post screen.

---

### Post by oldfred on 2020-02-17
You are not showing the Windows UEFI boot entry.
You can add on with efibootmgr. 
see 
man efibootmgr
New Windows entry 
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/sda -p 2 if sda2
To see entry:
sudo efibootmgr -v

You also show LDM on sde which is proprietary to Microsoft and will not work with Linux.
[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Shown as SFS, Dynamic also on gpt as LDM
[https://docs.microsoft.com/en-us/windows/win32/api/winioctl/ns-winioctl-partition_information_gpt?redirectedfrom=MSDN](https://docs.microsoft.com/en-us/windows/win32/api/winioctl/ns-winioctl-partition_information_gpt?redirectedfrom=MSDN)

After adding UEFI entry, and making sure Windows fast start up is off:
sudo update-grub
Grub can only boot working Windows or Windows that is not hibernated nor needs chkdsk. So then you may need either to directly boot from UEFI or use your Windows repair/recovery disk to make repairs.

---

### Post by C.S.Cameron on 2020-02-18
I installed Windows on one disk and Ubuntu on another.
When I boot I press F12 and select either the Windows Boot Manager or the Ubuntu Disk.
If I select the Ubuntu disk the Grub menu opens. I can not select Windows from the grub menu.
In my opinion UEFI sucks.

---

### Post by empleat on 2020-02-18
You wanted me to post summary from boot-repair, so i did.
Thats strange, line 1043: [COLOR=#000000]Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootmgfw.efi
Also command "[/COLOR][COLOR=#000000]sudo efibootmgr -v" showed windows boot entry.
LDM is dynamic disk ? I have windows on sda so it shouldn't be relevant.

You know what i don't use linux that often, i think i forget about grub. I just glad i can even boot to linux now. Thanks for your help ![/COLOR]

---

### Post by oldfred on 2020-02-18
If Windows fast start up off, this then should add Windows to grub menu.
sudo update-grub

But if mostly using Windows and booting from UEFI boot menu, you really do not have to add Windows to grub menu and can leave Windows fast start up on.

---

### Post by C.S.Cameron on 2020-02-18
> **oldfred said:**
> If Windows fast start up off, this then should add Windows to grub menu.
sudo update-grub.

Is this true if Windows is UEFI and Ubuntu is BIOS? I have tried "sudo update-grub" and every menuentry I can find, even chainloading.

I have also tried doing "sudo update-grub" with Full install UEFI pendrive, (with mkusb boot partition).

---

### Post by yancek on 2020-02-19
> Is this true if Windows is UEFI and Ubuntu is BIOS? I have tried "sudo  update-grub" and every menuentry I can find, even chainloading. 

Grub installed in Legacy mode will not boot an EFI install of windows.  Spent many hours reading/researching and testing and have never come across anything that works.  Legacy Grub will boot an EFI install of another Linux.

---

### Post by C.S.Cameron on 2020-02-19
> **yancek said:**
> Grub installed in Legacy mode will not boot an EFI install of windows.  Spent many hours reading/researching and testing and have never come across anything that works.  Legacy Grub will boot an EFI install of another Linux.

Can we take this a step further and say that an UEFI install of Ubuntu will will not boot an EFI install of Windows? (If on separate disks).

Edit:
Or say that any install of grub on one disk will will not boot an EFI install of Windows on another disk?

---

### Post by oldfred on 2020-02-20
Grub will boot Windows on another drive, if UEFI Secure Boot is off. If Secure Boot is on, it will not boot Windows as something the the chain of trust is lost.
I have seen the output of efibootmgr -v that shows a different GUID & partition number in details between Windows & Ubuntu UEFI entries.

It just is Windows must have fast start up off and not otherwise need repairs. Grub only boots working Windows.

---

