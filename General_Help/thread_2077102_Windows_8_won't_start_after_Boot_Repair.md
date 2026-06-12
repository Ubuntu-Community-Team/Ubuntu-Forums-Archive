---
title: "Windows 8 won't start after Boot Repair"
date: 2012-10-27
forum: General Help
---

### Post by Nudi on 2012-10-27
Yesterday I upgraded my Windows 7/Ubuntu 12.04 machine to Windows 8. Everything worked just fine, except the upgrade killed the OS selection. No problem, load Ubuntu from a USB stick and run Boot Repair.

Now I can boot Ubuntu again, but when I select "Windows UEFI loader" in GRUB, it looks like it wants to boot Windows 7. At least the "Windows is loading files" message looks a lot like Windows 7 and not 8. And then the machine reboots.

I can still select "Windows UEFI recovery", but that just starts the Vaio (it's a sony laptop) recovery partition, obviously.

Here's my Boot Repair report: [http://paste.ubuntu.com/1308117/](http://paste.ubuntu.com/1308117/)

Any idea how I can get Windows 8 to work again?

**Edit:** I already tried update-grub. Didn't work.

---

### Post by oldfred on 2012-10-27
Your sda3 efi partition has several Windows efi files.

                       /EFI/microsoft/boot/bootmgfw.efi 
                       /EFI/microsoft/boot/bootmgfw.efi.bkp 

You are booting the second which has the .bkp. Since most users only have had the one install that has also worked. But since you have Windows 7 before perhaps that is the Windows 7 boot file and bootmgrw.efi is the new one??

I might try editing your 25_custom and see if that makes a difference. Just a guess.

---

### Post by Nudi on 2012-10-28
That definitely seems like the right direction. I changed the /etc/grub.d/25_custom from

```
menuentry "Windows UEFI loader" {
search --fs-uuid --no-floppy --set=root E248-8D15
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi**.bkp**
}
```

to

```
menuentry "Windows UEFI loader" {
search --fs-uuid --no-floppy --set=root E248-8D15
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}
```

Then I ran update-grub and rebootet the machine. When I selected Windows UEFI loader, the screen turned black for a moment and then went back to the OS selection.

I also tried the same thing with a couple of other files in that folder (bootmgr.efi and bootx64.efi). No luck either.

Any other suggestions? Do I need to change anything else in that 25_custom file?

---

### Post by oldfred on 2012-10-28
It seems like some sort of Windows issue as once grub has passed booting to Windows it is not really involved.

Boot-Repair will not fix Windows issues but may show us if some major is out of place. Otherwise you may need a Windows repairCD or USB. And as I understand it the standard Windows repairCD have to be changed to work with UEFI.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by Nudi on 2012-10-28
It actually *is* a Boot Repair issue..

I've also got an open [question over at Superuser]("http://superuser.com/questions/494601/windows-8-fails-to-load-after-boot-repair") where I just posted the following update:

> I managed to get back into Windows again. I changed the line

```
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi.bkp
```

in /etc/grub.d/25_custom (if you're reading this looking for help for the same problem: your file might be called something different) to

```
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
```

and copied the file bootmgfw.efi from [Windows partition]/Windows/Boot/EFI to /boot/efi/EFI/Microsoft/Boot. (The file already existed, so I renamed it to bootmgfw.efi.old to back it up.) Lastly, I ran a sudo update-grub.

When I restarted the computer, Windows 8 was booting up again, but without a GRUB screen. So guess what.. I could not boot into Ubuntu now.

In Windows, I installed EasyBCD and added an Ubuntu boot option. When I tried to selected that after another reboot, it failed because it couldn't find some file. I tried this with the EasyBCD option to find my Linux installation automatically and I also tried manually selecting the partition. Both had the same result.

So I once again tried booting from my Ubuntu USB stick and running Boot Repair. This time I got Windows' OS selection screen (the one I set up in EasyBCD). When I selected Windows 8 there, it rebooted the computer.

I feel like I'm getting more constructive answers here, so.. any ideas? :)

---

### Post by oldfred on 2012-10-28
I think you have to select the default from your UEFI menu, so it knows which efi file to load.

Did they finally update easyBCD as it did not work with UEFI before. It was only for BIOS/MBR booting.

---

