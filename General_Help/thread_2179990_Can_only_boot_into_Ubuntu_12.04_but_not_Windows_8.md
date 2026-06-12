---
title: "Can only boot into Ubuntu 12.04 but not Windows 8"
date: 2013-10-10
forum: General Help
---

### Post by nurulnad on 2013-10-10
Hello,

After installing Ubuntu 12.04, I cannot boot into Windows 8.
I am not sure if Ubuntu installed in UEFI mode or legacy mode. All I did was pop in the installation disk, and it said something like "This computer already has Windows 8. Choose your installation type:" for which I chose to "install Ubuntu 12.04 alongside Windows 8".

Upon restarting after the install, my grub2 shows a Windows 8 option but previously when I chose it, it said: 
error, unknown: "drivemap"
error, invalid efi file path

I then ran boot repair which told me "GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted  filesystem, bios_grub flag). This can be performed via tools such as  Gparted. Then try again."
So I created the filesystem, and ran boot repair again. It completely reinstalled my grub2.

Now when I choose the Windows 8 option on grub2, it says:
error: invalid arch independent ELF magic.
error: no such device: C246D7CE46D7C0F9.
error: invalid arch independent ELF magic.
error: invalid EFI file path.

I've been googling for a long time but I'm not getting anywhere, so I really hope someone can help or give me a lead on this. It is of extreme importance for me to be able to boot into Windows 8.

Here is my boot info:
[http://paste.ubuntu.com/6220308/](http://paste.ubuntu.com/6220308/)

Thank you so much.

---

### Post by oldfred on 2013-10-10
You have a mess. (Sorry)

It looks like your Windows was installed in BIOS mode with MBR(msdos) partitioning as you have none of the UEFI required Windows partitions.
But then it looks like you converted to UEFI with gpt partitions. 
But Windows only boots from gpt with UEFI and it needs its partition configuration like this:
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

I would suggest converting back to MBR with gdisk. You can use Boot-Repair to convert Ubuntu install to BIOS as it uninstalls grub-efi(UEFI) and installs grub-pc (BIOS) or just reinstall.

How you boot install media from UEFI/BIOS menu is how the system is installed for both Windows & Ubuntu.


 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

       
 GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

 Windows convert to MBR
[http://blog.paulgu.com/2008/01/06/how-to-delete-gpt-protective-partition/](http://blog.paulgu.com/2008/01/06/how-to-delete-gpt-protective-partition/)

---

