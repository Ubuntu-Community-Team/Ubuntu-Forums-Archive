---
title: "Grub2 can boot Win 7, but not bring it back from hibernation:  error 0xc000009a"
date: 2013-03-13
forum: General Help
---

### Post by Scotsilv on 2013-03-13
Installed Ubuntu 12.04 for dual-boot on HP P7-1222 (a UEFI machine that came with Win 7).

Ubuntu works well.  The 'Grub2 "Windows Boot UEFI loader" selection boots Windows 7 fine, too.

Problem is:  **Win 7 resume from hibernate.**

Pre-Ubuntu I had activated Win 7 hibernation and used it successfully.  I like to hibernate my Windows machines and *then unplug them to protect against voltage spikes* etc., but have a fast restart with retained state.

After Ubuntu was installed, if I hibernate Win 7 (which it seems to do) and then try to reboot it, I get a **"Your computer cannot come out of hibernation 0xc000009a"** error from the Windows loader.  If I try to reboot Win 7 again from Grub2 I am presented with the "delete hibernation file and restart" option, which then does so and reboots Win 7 OK.  Of course, searching on the 0xc000009a error code brings up little of value.  (Thanks, MS, for such informative error messages.)

In effect, I cannot use hibernation in Win 7 anymore.

I've tried the "off the top of my head" attempted fixes - powercfg -h off, then powercfg -h on; defragmenting; etc.  No change.

Here is the grunb.cfg entry for Win 7 boot:

-----------------------------------------------------
[B][I]menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 96AD-5B21
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}
[/I][/B]-----------------------------------------------------

Anyone have a similar issue and found some solution?

---

### Post by Scotsilv on 2013-03-29
No answers to this.

Surely someone else has the same problem?

Cannot bring Win7 back from hibernation if GRUB2 is installed and dual-boot is set up?

---

### Post by coldcritter64 on 2013-03-29
Check out post No. 2 carefully and see if it helps, [http://www.bleepingcomputer.com/forums/t/455135/cannot-hibernate-0xc000009a/](http://www.bleepingcomputer.com/forums/t/455135/cannot-hibernate-0xc000009a/)

Edit: particularly the complete shutdown (not just a restart) and running the chkdsk command etc.

---

### Post by anton-chepurov on 2013-08-12
Hi

The solution from bleepingcomputer.com doesn't help.

So, the problem persists: GRUB2 seems to break hibernation in Win 7 with UEFI. Turning UEFI off in BIOS doesn't help either.

Before installing GRUB2 hibernation worked just fine.

Anybody?

---

### Post by oldfred on 2013-08-12
I do not understand the difference of grub chainloading to the Windows efi file and UEFI loading the same file. When Windows starts it should not see any difference. So it may be something system does either UEFI in loading grub or grub. You can file a bug, one may already exist.
//bugs.launchpad.net/ubuntu/+source/grub2

You really should not use hibernation with Windows as any attempt to write from Ubuntu into the NTFS partition will corrupt it. Best to have a separate shared NTFS data partition even when not hibernating.

Since you have UEFI you may have a work around depending on if your system will boot Ubuntu directly. I see Boot-Repair has done the Windows efi file rename to /EFI/Microsoft/Boot/bkpbootmgfw.efi. This is for those systems that only boot the Windows efi file bootmgfw.efi which they hard code into the UEFI. Ubuntu's shim file which has the Microsoft secure boot key is renamed to bootmgfw.efi to boot Ubuntu and from grub menu you boot bkpbootmgfw.efi which is the original Windows efi file.
But if your system will directly boot ubuntu you do not need rename. Boot-Repair used to automatically rename on second run of Boot-Repair as it was assumed many systems had that issue. It may only be a few, so now the user has to select the rename function. 
So if you can directly boot ubuntu, you can rename Windows efi file back to its correct name, and then when starting up after hibernation can go into UEFI menu and directly boot Windows. If rebooting use UEFI to choose ubuntu entry. Not quite as easy as just dual booting from ubuntu as default and selecting which to boot in grub menu, but should work.

If ubuntu entry in UEFI directly works.
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 


 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

---

