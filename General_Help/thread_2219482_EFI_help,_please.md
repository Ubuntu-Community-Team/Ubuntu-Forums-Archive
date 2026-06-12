---
title: "EFI help, please"
date: 2014-04-24
forum: General Help
---

### Post by drfox on 2014-04-24
I reinstalled Xubuntu 14.04 on an HP Envy 7 notebook after upgrading Win8 to Win8.1, I left secure boot on and legacy boot off. It installed OK, but wouldn't boot to Xubuntu automatically.
I ran Boot-Repair 2 times with live CD. First time Boot-Repair told me to turn off secure boot, second time it told me there was an error.
Here are my boot urls before repair, after repair 1 and after repair 2:
[http://paste.ubuntu.com/7319786](http://paste.ubuntu.com/7319786), 
[http://paste.ubuntu.com/7319819](http://paste.ubuntu.com/7319819), 
[http://paste.ubuntu.com/7321432](http://paste.ubuntu.com/7321432)
I should tell you that there are 2 ubuntu entries. The first, with a small "u" doesn't boot ubuntu. The one with the capital "U" does. The first is from a previous attempt to get Xubuntu running. 
I would like to boot to grub with the ability to choose Windows.
Thanks for your help

---

### Post by oldfred on 2014-04-24
I do not know how you got grub legacy installed to MBR. That will not work.

It does look like a standard UEFI install with signed kernels, so should boot with secure boot on.

Do not normally see this from Boot-Repair. Not sure what causes it to say this. Line 504.

> 
 line 504
Unusual EFI:

line 9182
 Wrong GRUB version detected.



But it shows grub installed without error.

If you have secure boot on, the other entry may be grub which may work without secure boot. Only shim or the signed version of grub will work with secure boot on.

In UEFI menu can you change to make ubuntu entry first in boot order.

```
 BootOrder: 0000,3004,3000,3001,2002,2001,2003
Boot0002* Internal CD/DVD ROM Drive (UEFI)
Boot0004* Windows Boot Manager
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3004* Internal Hard Disk or Solid State Disk
Boot0000* ubuntu,BootCurrent: 0002


```

Some UEFI menu's have both hardware devices like hard drives, & DVD mixed with UEFI entries. Others have two separate choices for hard ware boot order and UEFI boot order.
       MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)

Many of the older issues have been solved with 14.04, so not sure if these may help or not:

 [SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

### Post by drfox on 2014-04-24
Thanks OldFred, but still heed help.
I restored the Windows 8 mbr (THAT was a pain!), edited out some of the options with efibootmgr, and reran Boot-Repair.
Again, it exited saying there was an error, and the machine default boots into Windows.
[http://paste.ubuntu.com/7326813](http://paste.ubuntu.com/7326813)
Is next step just biting the bullet and reinstalling without EFI?

---

### Post by oldfred on 2014-04-24
There was no reason to install a Windows boot loader to the protective MBR. That is only for booting with BIOS mode and your Windows will only boot in UEFI mode.

Can you choose Ubuntu entry in UEFI menu? Or what happens?
Or do you have one time boot key and does it show Ubuntu.
Have you tried with both secure boot on and secure boot off?

Some have found this works to boot also.
       Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

Some also manually copy shim or grub efi file to /Boot/bootx64.efi

      
 UEFI - in efi partition Manual copy grubx64.efi to bootx64.efi to make it work.
[http://ubuntuforums.org/showthread.php?t=2101840&p=12440378#post12440378](http://ubuntuforums.org/showthread.php?t=2101840&p=12440378#post12440378)

---

### Post by drfox on 2014-04-24
> **oldfred said:**
> There was no reason to install a Windows boot loader to the protective MBR. That is only for booting with BIOS mode and your Windows will only boot in UEFI mode.

I only did that to overwrite the old grub that you said had been put there originally.

> **oldfred said:**
> Can you choose Ubuntu entry in UEFI menu? Or what happens?  Have you tried with both secure boot on and secure boot off?

The machine automatically boots to Windows. There is no UEFI menu unless I press Escape, wait awhile for another menu to come up, press F9 for boot options. Then I get the boot menu.  I have tried with secure boot both off and on. I'll try your suggestions on the windows side of things.

Thanks OldFred, 
Larry

---

### Post by Joao Lacerda on 2014-04-25
Hi Drfox

" OldFred have helped me on the same issue.
What I am telling you hier is what I have learned from him.
Check also his info about uefi. This was for me very useful." 

When you boot the pc you can enter the uefi menu using using F1 of F2 etc check wich one is for your computer.
Inside your UEFI it must be possible to choose from there, the boot order. If Ubuntu is there and you set it to boot first, it will bring you to the grub menu.

With this code you can check if your hdd boots in uefi mode.```
[COLOR=#333333][FONT=monospace][ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" [/FONT][/COLOR]
```

and with this one you can check if Ubuntu has been installed if UEFI mode.

copy and paste this code on your terminal. if you can boot ubuntu using the boot key.

```
[COLOR=#333333][FONT=Ubuntu][ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode"[/FONT][/COLOR]
```

If Ubuntu is in the uefi menu you can choose from there de order to boot.

"boot repair have made a mess on my UEFI, fortunately I have restored it to it's original " 

Good luck.

---

### Post by drfox on 2014-04-29
Thank you OldFred and Obrigado Joao.
I have tried everything.
Xubuntu is installed in EFI mode. Secure boot is off. I actually reinstalled with a boot partition and turned off the boot flag on the Windows EFI boot partition
I've edited the the boot order with efibootmgr -o, but on reboot Windows boots and on rechecking efibootmgr, the order goes back to the original
I have used the bcdedit command in Windows
I have copied and pasted the grubx64.efi file as bootx64.efi as suggested.
I just keep booting Windows, I can't tell whether Windows 8.1 or the particular HP bios is the culprit, but they sure are making it hard for us to dual boot.
I guess I'll just have to live with pressing Esc and then F9 whenever I have to reboot the computer. Not what I'm used to, and not ideal, but better than having to fight with this any longer.

I'm going to leave this thread unsolved, because I never could figure out a workaround, but again, thanks for your help everyone.
Larry

---

### Post by oldfred on 2014-04-29
I believe there are several alternatives. I mentioned some above, but have put together what i know all in one list.

 **Sysytems that only boot Windows from UEFI. Often Sony & HP**
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Some install rEFInd which seems to be another workaround.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

Any rename of files, may require it to be done again after Windows updates as it will overwrite the Windows files. So be sure to copy shim or grub files not just rename them as you may need them again.

---

