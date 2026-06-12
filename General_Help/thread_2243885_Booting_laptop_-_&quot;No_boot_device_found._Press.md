---
title: "Booting laptop - &quot;No boot device found. Press any key to reboot the machine?&quot;"
date: 2014-09-11
forum: General Help
---

### Post by Little Blue on 2014-09-11
Hi,

Dell inspiron laptop with win8 / ubuntu 12.04 dual boot.

This evening I decided to reboot have spent a few weeks just suspending the machine. When it came back on, after the bios screen it gave me:

```

Checking media [fail]
No boot device found. Press any key to reboot the machine.

```

The bios lists the drive's existence (though not in any boot order), and the drive passes dell's diagnostic ePSA tool. As it also can be seen when I boot a liveboot usb I'm confident the drive's ok, but something's happened to the system's boot capability.

I found a very similar post here [http://ubuntuforums.org/showthread.php?t=2190394&](http://ubuntuforums.org/showthread.php?t=2190394&) and attempted to repair via boot-repair. It did not work, the paste bin is here: [http://paste2.org/IcV59shk](http://paste2.org/IcV59shk)

Any thoughts?

EDIT: I noticed in the bootinfo that it had no loader installed to the MBR. Boot-repair didn't give any options for MBR restoration and [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) implies I would need to repair the MBR with a windows disk anyway.

Fortunately I do have a windows recover stick to hand and tried to boot that up, to see if it gave me the same options they refer to in that link. Unfortunately its a hybrid windows/dell recovery so it didn't quite do that. Instead it allowed me to reboot to get to the windows recovery partition, in the process of which it dumped me back into grub!

I can now get into my linux install, but cannot restart the machine without having to go through the windows usb stick... Putting it to sleep works ok though so its functional for me, (famous last words...) This is a heck of a workaround, but it is a workaround, and might help folks here understand what's going on, because I sure don't!

---

### Post by oldfred on 2014-09-12
You have UEFI, so you should not have a boot loader in MBR as that would be for BIOS boot.

        /EFI/Microsoft/Boot/bkpbootmgfw.efi 

That tells me you ran Boot-Repair's "buggy" UEFI fix. Most Dells did not really need that and it was a early fix for HP, Sony and others that only booted Windows from UEFI menu.
With that rename the UEFI boots the Windows entry which really is grub, and then from grub you boot the bkpbootmgfw.efi file to boot Windows.
Older versions of Ubuntu also needed Boot-Repair to add a correct UEFI boot entry as the os-prober was still only creating BIOS type boot entries that did not work with UEFI. That has since been fixed, but if you have a newer grub it will try to boot the bootmgfw.efi entry will really is grub from the Boot-Repair rename.

First lets undo rename:

 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

Post this from your install.
      
 modprobe efivars
sudo efibootmgr -v

You may also want to houseclean some of the older kernels.
       Determine your current kernel:
uname -a
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

If synaptic not installed:
sudo apt-get install synaptic

---

### Post by Little Blue on 2014-11-03
Firstly, I'm terribly sorry for not replying sooner. This did not time itself well with finishing my phd thesis and other parts of my life, so once I had a working-ish machine, I just ran with it, which feels like really bad practice! So sorry!

So, to update this issue:

Boot repair, this is the pastebin I get following boot-repair [http://paste.ubuntu.com/8805258/](http://paste.ubuntu.com/8805258/) with ticking the restore efi backups and saying "no" to activate WinEFI which it offers to do (answering yes keeps /EFI/Microsoft/Boot/bkpbootmgfw.efi in the output).

Following this, I still can't boot into ubuntu normally, and have to go through a windows recovery stick as mentioned in my original edit to get the system to recognise the boot loaders. At this point, the grub screen looks corrupted (I can get a camera if it help, not sure how best to describe it), but I can load ubuntu from there. Restarting from ubuntu appears to cause the system to completely forget where the boot loaders are, sending me back to the original message. There's no sign of either the windows or ubuntu bootloader in the F12 boot options on startup, unless I've rebooted from windows/the windows recovery stick.

Following the modprobe
[http://paste.ubuntu.com/8805470/](http://paste.ubuntu.com/8805470/)

Thanks for the suggestion to tidy out some of the old kernals. Turns out I had quite a few hanging around...

---

### Post by oldfred on 2014-11-03
What model Dell?

I thought Dell would dual boot without special work arounds like HP & Sony.

But both UEFI boot menu & f12 one time boot key should show both Windows and Ubuntu. 
Do you have secure boot still on? Grub will not boot Windows from its menu with it on, due to a bug. 
With secure boot off, you should have 3 ways to boot Windows, UEFI, f12, or grub menu.

I do not really see anything wrong with summary report and your configuration.

Some other Dell threads, usually the newer version of Ubuntu works better. Dell did have sputnik for 12.04 to fix misc issues. And supposedly 14.04 has all those included.

 Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

This may apply to all Dell Intel based models:

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

      
 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
[http://ubuntuforums.org/showthread.php?t=2204287](http://ubuntuforums.org/showthread.php?t=2204287)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)

---

