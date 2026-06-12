---
title: "Computer doesn't boot into rEFInd after updating"
date: 2014-07-09
forum: General Help
---

### Post by DiscoDave95 on 2014-07-09
Hello, I have been running Xubuntu 12.04 and Windows 7 on a computer that came with UEFI, therefore i had to use rEFInd to dual boot it. I had it working fine until recently after I updating ubuntu.  The computer now boots straight into windows without asking. I able to get to rEFInd by pressing going to the boot options at startup and selecting rEFInd. So my question is, how can I get rEFInd to boot when I turn on my computer?

if i run ```
efibootmgr
``` i get

```
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0001,3001,0002,0004,2001,2002,2003
Boot0000* Notebook Hard Drive
Boot0001* Windows Boot Manager
Boot0002* rEFInd
Boot0004* Ubuntu
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot3005* Internal Hard Disk or Solid State Disk

```

---

### Post by oldfred on 2014-07-09
This is what you ran, but you can use efibootmgr to change boot order.
sudo efibootmgr -v

[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)


-o | --bootorder XXXX,YYYY,ZZZZ,...     explicitly set BootOrder (hex)
See example for details on what 3 and 4 are:
> 3) A system administrator wants to change the boot order.  She would
   call 'efibootmgr -o 3,4' to specify PXE boot first, then Linux
   boot.
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by DiscoDave95 on 2014-07-10
I tried using the efibootmgr to set refind as the first one, but that did not work.

---

### Post by oldfred on 2014-07-10
What brand computer? 
Sony & HP only boot the entry with Windows description in UEFI. But I thought rEFInd was a work around that would even boot those systems?

---

### Post by DiscoDave95 on 2014-07-10
HP, but rEFInd works, it just won't start at startup anymore. I have to hit esc then go to the boot options and select rEFInd to get to it.

and just to be clear if i run ```
efibootmgr -v
``` in root, i recieve:
```
root@David-lap:/home/david# efibootmgr -v
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0001,3001,0002,0004,2001,2002,2003
Boot0000* Notebook Hard Drive    BIOS(2,500,00)................-.Z.......Z.A.Z........................................
Boot0001* Windows Boot Manager    HD(1,800,32000,2d676fa2-e49a-4bf3-bb31-fcbfa075f939)File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0002* rEFInd    HD(1,800,32000,2d676fa2-e49a-4bf3-bb31-fcbfa075f939)File(\EFI\refind\refind_x64.efi)
Boot0004* Ubuntu    HD(1,800,32000,2d676fa2-e49a-4bf3-bb31-fcbfa075f939)File(\EFI\ubuntu\grubx64.efi)RC
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC
Boot3001* Internal Hard Disk or Solid State Disk    RC
Boot3002* Internal Hard Disk or Solid State Disk    RC
Boot3003* Internal Hard Disk or Solid State Disk    RC
Boot3005* Internal Hard Disk or Solid State Disk    RC

```

Therefore i'll enter ```
efibootmgr -o 0002, 0004, 0001
``` as root and reboot with no success

---

### Post by oldfred on 2014-07-10
Try without spaces between numbers & comma. Example does not show any. But I do not know for sure.
And it does look like leading zeros are optional or not required? You can try without zeros if without spaces does not work.

---

### Post by DiscoDave95 on 2014-07-10
I tried without spaces and without leading 0s. When I checked the efibootmgr before rebooting, it was correct and had rEFInd first. After restarting the pc, the computer booted up into the windows bootloader instead of refind.  Then when i checked the efibootmgr again, it had the windows bootloader first. Do I have to do something else after i run the command?

---

### Post by oldfred on 2014-07-10
No Windows & your UEFI are one that just resets every time to only Windows and either UEFI or Windows resets it. It wants to make sure you default to Windows. 

This is another work around. Instead of shim or grub change to whatever rEFInd uses as its file. Perhaps:
 \EFI\refind\refind_x64.efi


 **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

Or:

 **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)




 [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

