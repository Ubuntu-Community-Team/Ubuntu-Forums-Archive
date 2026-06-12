---
title: "Dual boot (Ubuntu 12.04 x64 &amp; Win 7 Pro x64) grub menu error: &quot;Invalid EFI file path&quot;"
date: 2013-10-02
forum: General Help
---

### Post by erwin5 on 2013-10-02
Hi all, I'm new to Ubuntu/linux and I'm trying to fix a problem I'm having with the Grub menu.

I have Windows 7 Pro (x64) and Ubuntu 12.04 (x64) installed on separate 120GB SSDs.
I installed Ubuntu first and have its EFI entry listed as first in my boot settings, which loads
Grub properly, but when I choose my Win 7 entry I get the error message: "*Invalid EFI file path*",
and it returns to the menu. Ubuntu and all the other options work properly, and when I change
the Boot order to my Win 7 drive, Windows 7 boots properly by itself.

I ran boot-repair and by using the recommended settings and clicking 'no' for when it
asks whether my 120GB disk is removable (presumably it was referring to my Win 7 drive),
I was met with another error message:

[I]GPT detected. Please create a BIOS-boot partition (> 1 Mb unformatted file system, bios_grub
flag). This can be performed via tools such as GParted. Then try again. Alternatively you can retry
after activating the [Separate/boot/efi partition:] option.

[/I]I do have a pastebin text file that was generated with the boot-repair program, and can post it,
in its entirety, if needed. I scrolled through the file and found a few suspect entries that may be relevant.
Here they are:
[U]
sda1 is where my Windows 7 disk is mapped to[/U]

```
sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD
```

_The menu entry for the Windows 7 loader in Grub_
```

[COLOR=#000000]menuentry [/COLOR][COLOR=#BB4444]"Windows 7 (loader) (on /dev/sda1)"[/COLOR][COLOR=#000000] --class windows --class os [/COLOR][COLOR=#666666]{[/COLOR]
    insmod part_msdos
    insmod ntfs
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root B482F1B682F17CE4
    chainloader +1
[COLOR=#666666]}[/COLOR]
```[COLOR=#222222][FONT=Verdana]

[/FONT]_Another error message_[FONT=Verdana]
[/FONT][/COLOR]```

Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn[COLOR=#BB4444]'t understand GPT[/COLOR]
[COLOR=#BB4444]partition tables.  Or perhaps you deleted the GPT table, and are now using an[/COLOR]
[COLOR=#BB4444]msdos partition table.  Is this a GPT partition table?[/COLOR]
[COLOR=#BB4444]Model: ATA INTEL SSDSC2CW12 (scsi)[/COLOR]
[COLOR=#BB4444]Disk /dev/sda: 120GB[/COLOR]
[COLOR=#BB4444]Sector size (logical/physical): 512B/512B[/COLOR]
[COLOR=#BB4444]Partition Table: gpt
[/COLOR]
```

I'm hesitant to go forward because I already had to wipe out my old install of Windows 7 because I botched 
the first Ubuntu install. Any ideas as to how I can fix it so I can boot into Windows 7 without getting the 
'Invalid EFI file path' message?

---

### Post by oldfred on 2013-10-02
Post link to BootInfo report from Boot-repair, so we can see details.

But with new UEFI systems you can install in either UEFI mode or BIOS/CSM/Legacy mode. And both system then need to be same boot mode. The only way to dual boot if not same boot mode is to go into UEFI/BIOS and turn on or off one mode to boot system installed in that mode. Some will auto switch but you still have to go into UEFI. How hardware info is written for operation system to use is different for UEFI or BIOS, so you cannot start booting one way and switch. 

Ubuntu will boot in BIOS mode or UEFI mode from gpt partitioned drive. 
If you installed Ubuntu in UEFI mode it has a bug and still creates a BIOS type boot entry for Windows that will never work in UEFI mode even if Windows is UEFI or BIOS. But Boot-Repair can convert a UEFI Ubuntu install to BIOS by uninstalling grub-efi and installing grub-pc, but in BIOS mode you need a tiny 1MB unformatted partition with the bios_grub flag. Use gparted to create that if needed anywhere on drive.

After seeing details in BootInfo I can make further suggestions, but above is best guess as of now.

---

### Post by erwin5 on 2013-10-02
Thanks for the answer/insight fred, I'll try boot-repair again and see if I can get some
more info.

Here's the boot repair log:[URL="http://paste.ubuntu.com/6184600/"]

http://paste.ubuntu.com/6184600/[/URL]

Note that I also have two storage drives for media and other program data that I use
with my Windows install (the 250GB and 500GB drives). Not sure if that plays any
role in my problem.

---

### Post by oldfred on 2013-10-02
Since Windows is BIOS, I would create the bios_grub partition and let Boot-Repair booted in BIOS mode convert install to BIOS mode. I might leave efi partition since it is small just in case in the future you want it.

I now format new Linux gpt drives with both an efi partition for future use and a bios_grub for my old system. Then I may move drive to new system and have an efi for it.

Boot-Repair's auto fix install's grub to every MBR, do not run that as you want to keep a Windows boot loader in your Windows drive. Then if grub does not work you can use BIOS or one time boot key to directly boot Windows.

I have had Ubuntu with gpt partitioning since 10.10 and back then had XP with MBR. Data is on another MBR drive with NTFS shared for both XP & Linux. I do not boot XP anymore but still have not converted NTFS partition to LInux. But all new data now goes into a Linux formatted data partition and that is shared with old, new, & test installs.

---

### Post by erwin5 on 2013-10-02
Okay, so if I understand correctly, I'll have to run boot-repair again and create the bios_grub
partition onto the Ubuntu drive, and convert the install to BIOS mode. Then I'd leave the already-existing
EFI partition as it is. Presumably, this, once completed, will allow me to boot into Windows 
via grub because both installs will be running in BIOS mode as opposed to EFI. I thought Ubuntu x64
only ran in EFI mode? Just curious.

I'll give it a shot and see if it works. Thanks fred!

---

### Post by oldfred on 2013-10-02
The 64 bit version of Ubuntu works with BIOS as that is what I have installed in my 6 year old system. I use 12.04, but also have 12.10,13.04 & 13.10 working. I do not have UEFI though.

Create bios_grub before running Boot-Repair. And either change UEFI to only boot in BIOS/CSM mode or be careful to only choose BIOS booting when starting a system.

---

### Post by erwin5 on 2013-10-02
I fixed it!

I ended up not having to go through any BIOS/EFI conversions/boot-repair. All I did was
do a reinstall of Windows, then installed Ubuntu, and fixed some of the partitioning mistakes
I made during the previous install, and now Grub works with both OSes. 

Thanks again fred!

---

### Post by oldfred on 2013-10-02
Sometimes reinstall is quicker and easier. :)

---

