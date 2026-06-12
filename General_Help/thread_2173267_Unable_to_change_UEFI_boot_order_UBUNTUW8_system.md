---
title: "Unable to change UEFI boot order UBUNTU/W8 system"
date: 2013-09-08
forum: General Help
---

### Post by odror on 2013-09-08
OS: ubuntu 13.10
HW: HP envy 17t j000

Issue #1 On HP laptop I cannot change the default boot OS in the BIOS, But when I used the F9 option at boot I can boot to ubuntu.
Issue #2 When I use efibootmgr -o  command as seen below to change the boot order. During boot the laptop revert back to the the old boot order before the change. interstingly the -n option works (i,e modify boot order for the next boot only). I would like to avoid placing efibootmgr -n ... in my rc.local.

Any ideas how to fix that.

# efibootmgr
> BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 0001,3001,0000,0002,2001,2002,2003
Boot0000* Ubuntu
Boot0001* Windows Boot Manager
Boot0002* ubuntu
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
 
efibootmgr -o 2,1,3001,0,2001,2002 :> BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 0002,0001,3001,0000,2001,2002
Boot0000* Ubuntu
Boot0001* Windows Boot Manager
Boot0002* ubuntu
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk


---

### Post by westie457 on 2013-09-08
Have you tried using yannubuntu.s Boot Repair? See here for more details. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by odror on 2013-09-08
Hi
I am very much familiar with boot repair.  I have used it in the past multiple times. I do not see how it applies in this case. I am able to boot through GRUB, I am able to change the boot order temporary (using efibootmgr ), but not permanently. It is possible that the the HP BIOS preventing changing the boot order.

---

### Post by oldfred on 2013-09-08
I would think your command should work. But vendors do not always implement UEFI as the standard says.
Does UEFI menu show boot order and let you edit it there?

---

### Post by odror on 2013-09-08
> **oldfred said:**
> I would think your command should work. But vendors do not always implement UEFI as the standard says.
Does UEFI menu show boot order and let you edit it there?

On the CMOS I can change the boot order, but only one OS is listed (OS manager), which means windows 8.
If during boot I press F9 I get a list that includes the EFI Operating systems including ubuntu. In fact it also lists a prior failed ubuntu installation. 
I was not able to find a place to edit the UEFI menu. I am not able even to edit within Windows 8.

---

### Post by oldfred on 2013-09-08
Do you have secure boot on, or maybe that is part of the issue. 
UEFI normally only shows secure boot installs with secure boot on. 
Or maybe only secure boot systems can be reordered in your system?

---

### Post by odror on 2013-09-09
> **oldfred said:**
> Do you have secure boot on, or maybe that is part of the issue. 
UEFI normally only shows secure boot installs with secure boot on. 
Or maybe only secure boot systems can be reordered in your system?

I have rechecked it. Secure boot is disabled. I tried when It was enabled. there was no difference.

---

### Post by oldfred on 2013-09-09
Is your UEFI/BIOS the latest version from HP?
Not sure what else to suggest.

---

### Post by odror on 2013-09-09
> **oldfred said:**
> Is your UEFI/BIOS the latest version from HP?
Not sure what else to suggest.

Yes I check. I'll keep checking frequently. I saw this link. I am not sure that I am comfortable doing that. It sounds that it will work.  But it makes w8 boot completely dependent on GRUB.

[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g-Windows-8-and-Software/Changing-Boot-Order-on-Dual-Boot-Windows-8-and-Ubuntu/td-p/2503733]("http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g-Windows-8-and-Software/Changing-Boot-Order-on-Dual-Boot-Windows-8-and-Ubuntu/td-p/2503733")

---

### Post by oldfred on 2013-09-09
the last post in that thread is similar to what Boot-Repair does for some UEFI systems that are hard coded to only boot the Windows efi file. It renames the Windows efi file and makes the default Windows file be really grub2's shim. If your system boots from more than one entry then you still should have two entries in UEFI menu.

UEFI is designed to have an unlimited number of boot loaders in separate folders in efi partition. And it should present all of them and let you change boot order.

       Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
It does this:
Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

    
 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by odror on 2013-09-09
I will try your suggestion Later this week. I need to to do backups etc. I have already install and re install W8/Ubuntu on this computer 3 times. The install disk of ubuntu 13.10 (which is in pre beta stage) is the most compatible with UEFI. This is why I selected it over 13.04.

---

### Post by odror on 2013-09-11
For now I have decided to have the following workaround. 13.10 has other problems that preventing me from committing to ubuntu on my laptop. (The most serious is that the laptop does not wake up properly from sleep. I am waiting for the next nvidia-prime update)

So I placed "/bin/efibootmgr -n 2,1,3001,0,2001,2002" in the rc.local file. This way will guarantee that each next boot will go though grub. This works fine until I boot W8. Then in order to get back to grub I will need to used the CMOS boot menu.

---

