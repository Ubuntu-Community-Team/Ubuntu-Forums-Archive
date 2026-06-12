---
title: "Booting Problems -- See Pic of Screen"
date: 2023-02-22
forum: General Help
---

### Post by Rick St. George on 2023-02-22
Have an SSD drive running Ubuntu-Studio v20.04.

For months ... Receive Error upon booting - "Environment too small, Press any Key to continue".
Pressing Space Bar and it always boots.
Today It won't get that far. It hangs at ...

See attached Pic of Screen.

Any ideas what this means? I'm wondering why I have continuous Boot problems?!?!?

Thanks!
Rick
):P

---

### Post by Bashing-om on 2023-02-22
hey Rick -

A thought - out of space in the boot partition ?

What happens when attempting to boot an older kernel ?

Then look at the usage figures:
```

df -h

```

[INDENT]Maybe no
[INDENT][INDENT]could be Yes[/INDENT][/INDENT][/INDENT]

---

### Post by tea for one on 2023-02-23
> **Rick St. George said:**
> For months ... Receive Error upon booting - "Environment too small, Press any Key to continue".
Is that the full error message?
Do you see "Environment block too small"?

---

### Post by Rick St. George on 2023-02-23
> **tea for one said:**
> Is that the full error message?
Do you see "Environment block too small"?

Yes ... "Evironment Block too small".

After searching ... Someone suggested checking the power connection to the SSD.
Will check after shutdown today!

---

### Post by Rick St. George on 2023-02-23
> **Bashing-om said:**
> hey Rick -

A thought - out of space in the boot partition ?

What happens when attempting to boot an older kernel ?

Then look at the usage figures:
```

df -h

```



Rec'd the following output, but not from different partition, only 1 partition (other than boot) on 150 GB SSD.

```


$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  1.5M  1.6G   1% /run
/dev/sda5       228G  138G   79G  64% /
tmpfs           7.8G     0  7.8G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda1       511M  4.0K  511M   1% /boot/efi
tmpfs           1.6G   12K  1.6G   1% /run/user/1000


```

---

### Post by MAFoElffen on 2023-02-23
Reinstall grub...

"Environment block too small" Error: (listed as an error in RedHat. Will translate for Ubuntu.)
> 
This error occurs when we have a corrupted grub environment file. The expected size of /boot/grub2/grubenv or /boot/efi/EFI/redhat/grubenv should not exceed exactly more than 1024 bytes. In most case, this could happen during some grub customization or during OS Update/Upgrade and reboot. Additionally, we may be required to reinstall the current kernel version.

Do
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls -ltr /boot/grub/grubenv
-rw-r--r-- 1 root root 1024 Feb 22 22:22 /boot/grub/grubenv

```
Note that 1k is 1024 bytes...

The fix listed in RedHat, they use the utility 'grub2-env' to edit that file to restore it... Ubuntu does not normally have this utility (is part of grub-common). But reinstalling Grub2 will replace/renew that file.

---

### Post by Rick St. George on 2023-02-23
That's what I get ... 1024.

FYI ---

```

~$ sudo fdisk -l
Disk /dev/sda: 232.91 GiB, 250059350016 bytes, 488397168 sectors
Disk model: Samsung SSD 840 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf8d469ad

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048   1050623   1048576   512M  b W95 FAT32
/dev/sda2       1052670 488396799 487344130 232.4G  5 Extended
/dev/sda5       1052672 488396799 487344128 232.4G 83 Linux

$ ls -ltr /boot/grub/grubenv
-rw-r--r-- 1 root root 1024 Feb 23 14:05 /boot/grub/grubenv


```

---

### Post by Rick St. George on 2023-02-23
Ran Grup Update;

```

sudo grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.

$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-60-lowlatency
Found initrd image: /boot/initrd.img-5.15.0-60-lowlatency
Found linux image: /boot/vmlinuz-5.15.0-60-lowlatency
Found initrd image: /boot/initrd.img-5.15.0-60-lowlatency
Found linux image: /boot/vmlinuz-5.15.0-56-lowlatency
Found initrd image: /boot/initrd.img-5.15.0-56-lowlatency
Found linux image: /boot/vmlinuz-5.11.0-27-lowlatency
Found initrd image: /boot/initrd.img-5.11.0-27-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```

Rebooting .... will edit when I return and announce results.

System failed to boot;
ERROR: attempt to read or write outside of disk 'hd0'
ERROR: you need to load the kernel first

Back to Grub Menu and chose previous Kernel, then it proceeded to Boot ... fully operational.

What does this mean? Could my SSD drive be going bad? Purchased / installed Dec. 2014.

---

### Post by MAFoElffen on 2023-02-23
'grub-update' will not *reinstall* that file. Needs grub reinstalled... to replace that file. When that file is corrupted, identifying that in it's self-checks during bootup, Grub2 displays that specific error.

---

### Post by Rick St. George on 2023-02-23
> **MAFoElffen said:**
> 'grub-update' will not *reinstall* that file. Needs grub reinstalled... to replace that file. When that file is corrupted, Grub2 displays that error.

Note: the update was after the Install. Wouldn't that Re-Install?

---

### Post by MAFoElffen on 2023-02-23
'grub-update' (after an Install) updates the files used to assemble the grub.cfg (menu file), but not the underlying grub files... That is why, to replace that file, grub would need to be reinstalled.

My best guess, based on my knowledge of Grub.

---

### Post by #&amp;thj^% on 2023-02-23
> **MAFoElffen said:**
> 'grub-update' (after an Install) updates the files used to assemble the grub.cfg (menu file), but not the underlying grub files... That is why, to replace that file, grub would need to be reinstalled.

My best guess, based on my knowledge of Grub.

100% accurate...+1
```
sudo apt install --reinstall grub2
```
reboot
EDIT
@Rick, I noticed your running lowlatency kernels, this will help you if not installed:
```
sudo apt install ubuntustudio-lowlatency-settings
```
```
apt show ubuntustudio-lowlatency-settings
Package: ubuntustudio-lowlatency-settings
Version: 23.04.17
Priority: optional
Section: universe/x11
Source: ubuntustudio-default-settings
Origin: Ubuntu
Maintainer: Ubuntu Studio Developers <ubuntu-studio-devel@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 57.3 kB
Pre-Depends: dpkg (>= 1.15.7.2~)
Homepage: https://launchpad.net/ubuntustudio-default-settings
Task: ubuntustudio-desktop
Download-Size: 13.5 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 Packages
Description: Adds lowlatency kernel as boot default if available
 This package makes the lowlatency kernel the default kernel in GRUB.
 Also adds a second entry for the generic kernel if available.


```

---

### Post by tea for one on 2023-02-23
> **Rick St. George said:**
> Yes ... "Evironment Block too small".

Eons ago, these were the commands I used to fix this.
Unfortunately, I can't remember if this was via a live session or after I had managed to boot into a regular session?
```
sudo rm /boot/grub/grubenv
sudo grub-editenv /boot/grub/grubenv create
```

---

### Post by MAFoElffen on 2023-02-23
RE: [https://www.linuxsysadmins.com/grub2-editenv-block-too-small/](https://www.linuxsysadmins.com/grub2-editenv-block-too-small/)

On mine,
```

mafoelffen@Mikes-ThinkPad-T520:~$ grub2-editenv list
Command 'grub2-editenv' not found, did you mean:
  command 'grub-editenv' from deb grub-common (2.06-2ubuntu7.1)

```

---

### Post by Rick St. George on 2023-02-23
> **1fallen said:**
> 100% accurate...+1
```
sudo apt install --reinstall grub2
```
reboot
[/code]

This is what I got;

```

$ sudo apt install --reinstall grub2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  grub-efi-amd64 grub-efi-amd64-bin:i386 grub-efi-amd64:i386 grub-pc-bin grub-pc grub-ieee1275-bin
  grub-ieee1275 grub-efi-ia32-bin grub-efi-ia32 grub-efi-amd64-bin

E: Package 'grub2' has no installation candidate

```

also; 

```

$ sudo apt install ubuntustudio-lowlatency-settings

Reading package lists... 0%                                                                            
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntustudio-lowlatency-settings is already the newest version (20.04.2.2).
ubuntustudio-lowlatency-settings set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

---

### Post by MAFoElffen on 2023-02-24
Please post the result of
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"

```
From the Ubuntu Wiki: (Re: [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing))
> 
When using the grub-install command, the boot information is updated and written to the designated drive, missing - but not corrupted or intentionally deleted - files are restored. Specifically the core.img, [COLOR=#ff0000]grubenv[/COLOR], and device.map are updated and missing modules restored. If missing, the grub folder will be recreated. The grub-install command does not generate a new GRUB 2 menu (grub.cfg)

If it says UEFI mode then
```

sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy

```
If Legacy, then
```

sudo grub-install /dev/sdX

```
...where "X" is the disk that your system boots from...

---

### Post by Rick St. George on 2023-02-24
Upon ReBoot, I get the Grub prompt ... No Bootup! Trying to find solution. I do show;

```

ls
(hd0) (hd0,msdos5) (hd0,msdos1) 

```

msdos1 is the small boot partition
msdos5 is the main partition with Ubuntu

I followed instructions at [https://linuxhint.com/grub_rescue_ubuntu/]("https://linuxhint.com/grub_rescue_ubuntu/") ; boot proceeds, 
but get the same same screen as I posted in post 1.

Any ideas?

---

### Post by Rick St. George on 2023-02-24
Have Grub2 Boot Repair disk, booted from disk, password need, mine failed, boot repair menu up, chose Boot Repair - Boot Repair susscessful;
Upon shutdown, and booted compute, booted to Grub Prompt!

What gives???

---

### Post by oldfred on 2023-02-24
If running Boot-Repair, follow its instructions to post link to summary report when asking for help in the forum.

are you booting consistently in UEFI boot mode or BIOS/Legacy/CSM boot mode? Both for live installer to make repairs and setting in UEFI/BIOS to boot installed system.
Most systems now are both UEFI or BIOS if less than 10 years old.
Some very new systems now are UEFI only. But then you should have gpt partitioning for UEFI.

---

### Post by Rick St. George on 2023-02-24
Boot Repair disk ONLY shows;
```

pastebin.ubuntu.com/

```

Don't know if booting UEFI or BIOS, as upon boot up can't get into BIOS. I suspect EFI / UEFI, but don't remember anyplace to select or designate such. 
In GRUB (after prompt) it shows (hd0,msdos1) and (hd0,msdos5) as mentioned above. 
I tried;

```

set boot=(hd0,msdos1)
set root=(hd0,msdos5)

linux /boot/vmlinuz-5.15.0-60-lowlatency root=/dev/sda1

```

But as stated above, after command "boot" it comes right back to the screenpic posted in post #1.
Will try using Live-CD, using command prompt to install Grub.

---

### Post by Rick St. George on 2023-02-24
Managed to get into BIOS, there is a UEFI Boot Drive BBS Priorities / 1st Boot / 
Options are;
UEFI: Built-in EFI Shell
Disabled.

Selected is UEFI: Built-in EFI Shell.

MOBO shows MSI brand, V E7640AMS v20.3; with AMD FX-8320 Eight Core Processor; DRAM Freq. 1600 Mhz.

---

### Post by Rick St. George on 2023-02-24
Used Live-Disk for same version UbuntuStudio v20.04.5 and followed instructions here --> [https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/]("https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/")

Upon ReStart .. selecting first option produced Errro -- "need to load kernel first", so selected 2nd option for previous version 5.15.0.56 lowlatency
and Booted up OK. Probably still did not fix the problem. Any final suggestions before I shutdown at end of day?
Thanks!

---

### Post by Rick St. George on 2023-02-24
Used Live-Disk for same version UbuntuStudio v20.04.5 and followed instructions here --> [https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/]("https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/")

Upon ReStart .. selecting first option produced Error -- "need to load kernel first", so selected 2nd option for previous version 5.15.0.56 lowlatency (instead of 60)
and Booted up OK. Probably still did not fix the problem. Any final suggestions before I shutdown at end of day?
Thanks!

---

### Post by MAFoElffen on 2023-02-24
I still do not see that you uploaded a boot-info report to a pastebin so we can review it... That would be so useful to see what is going on (instead of guessing).

Even in Post #16, when asked for the output of
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"

```
Nothing returned from that... No output posted back from you... That would have told us what your system booted as and what your BIOS setting were set as. Instead, you just went on with other things.

Please help us to be able to help you. We really do want you to be able to resolve this.

---

### Post by Rick St. George on 2023-02-24
> **MAFoElffen said:**
> I still do not see that you uploaded a boot-info report to a pastebin so we can review it... That would be so useful to see what is going on (instead of guessing).
Please help us to be able to help you. We really do want you to be able to resolve this.

Please see Post #20, after OldFred's advice in #19. The option wasn't available, but showed the URL ONLY with no upload.
Don't know why!?!? 

Thanks for everyone's help. I will find out in the morning if Boots back up Ok.

---

### Post by MAFoElffen on 2023-02-25
You say in another thread, that this system now boots. If this is now "Solved". If so, please explain for others what was wrong and what resolved your issue. I, for one am curious about what you found.Then, please mark it as solved, so that others may find your solution..

---

### Post by Rick St. George on 2023-02-26
After Restart this Sunday morning (Sat. my day off) its back to the same screen "Unable to mount root fs on unknown block (0,0)". 
Grub does come up, 1st Option failed with above screen. Used previous kernel ... same problem.
Really am beside myself ! ? ! ?
Any ideas?

---

### Post by Rick St. George on 2023-02-26
Hope the following Computer Info helps. The System-info.txt file was blank. No URL provided. Managed to copy the following to mousepad to save.

```



---------- Other Details from 'Various':
The current kernel version is:       5.15.0-56-lowlatency 
    --- Operating System Release Description --- 
The current release description is:  Ubuntu 20.04.5 LTS 

Original Installation Date:          2021-07-24+10:58:30 
Original Installation Media: Ubuntu-Studio 20.04.2.0 LTS "Focal Fossa" - Release amd64 (20210210)

The Linux Kernel Command Line use to boot was: 
BOOT_IMAGE=/boot/vmlinuz-5.15.0-56-lowlatency root=UUID=7426e742-ddf2-4ade-98a8-ad444dda2e5b ro



   --- Hardware Enablement Stack (HWE) Informationt:
These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.15.0.60.66
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.4.0.26.32

   --- HWE Package Status from 'dpkg':
HWE package linux-generic-hwe-20.04 was not detected. Please check kernel version to verify range
Ubuntu Certified Hardware Platform. Safe to install the Hardware Enablement Stack (HWE).


Current boot mode:   Legacy mode (alias CSM alias BIOS mode)
   --- SecureBoot Status from 'mokutil':
        This would check / have checked if SecureBoot was enabled or not, 
        and checks if the system BIOS was UEFI or Lagacy only BIOS, 
        but package mokutil was not installed. If you would like to check
        this information, please install 'mokutil' and rerun script.



---------- Mount Details of '/etc/fstab':
UUID=7426e742-ddf2-4ade-98a8-ad444dda2e5b /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
/dev/disk/by-id/usb-Kingston_DataTraveler_2.0_C86000BDB9E9EE702A3400EC-0:0-part1 /mnt/usb-Kingston_DataTraveler_2.0_C86000BDB9E9EE702A3400EC-0:0-part1 auto noauto,x-gvfs-show 0 0
/dev/disk/by-uuid/A00D-96E4 /mnt/A00D-96E4 vfat umask=0077 0 1

---------- Current Mount Details of 'mount':
/dev/sda1 on /mnt/A00D-96E4 type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)
/dev/sdb1 on /media/stephen/Data type ext4 (rw,nosuid,nodev,relatime,uhelper=udisks2)


*** End Of Report ***


```

---

### Post by MAFoElffen on 2023-02-26
Sidenote: Since I am the author of and head of the project that created that report... I am curious why there was problems with that (We tested it extensively.) Please help the community by posting the output of:
```

ls -lh ~/system-info.txt

```

Back to business: Please post some of the missing info from that:
```

grep 'model name' /proc/cpuinfo | head -n1
lsblk -f | grep -v 'loop'

```
And the output of
```

sudo grub-install -v --recheck /dev/sda

```

---

### Post by Rick St. George on 2023-02-26
Here you go;

```

$ ls -lh ~/system-info.txt
-rw-rw-r-- 1 stephen stephen 0 Feb 26 13:41 /home/stephen/system-info.txt

$ grep 'model name' /proc/cpuinfo | head -n1
model name	: AMD FX(tm)-8320 Eight-Core Processor

$ lsblk -f | grep -v 'loop'
NAME   FSTYPE LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINT
sda                                                                     
&#9500;&#9472;sda1 vfat         A00D-96E4                             506.2M     1% /mnt/A00D-96E4
&#9500;&#9472;sda2                                                                  
&#9492;&#9472;sda5 ext4         7426e742-ddf2-4ade-98a8-ad444dda2e5b   78.4G    60% /
sdb                                                                     
&#9492;&#9472;sdb1 ext4   Data  857e518c-ccf1-4380-b76c-1d320df366d0   75.6G    38% /media/stephen/Data

$ sudo grub-install -v --recheck /dev/sda
grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ... not found.
grub-install: info: Looking for /proc/device-tree ...
grub-install: info: ... not found.
Installing for i386-pc platform.
grub-install: info: cannot open `/boot/grub/device.map': No such file or directory.
grub-install: info: copying `/usr/lib/grub/i386-pc/ufs1_be.mod' -> `/boot/grub/i386-pc/ufs1_be.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/aout.mod' -> `/boot/grub/i386-pc/aout.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/part_plan.mod' -> `/boot/grub/i386-pc/part_plan.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gfxterm.mod' -> `/boot/grub/i386-pc/gfxterm.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/video_bochs.mod' -> `/boot/grub/i386-pc/video_bochs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/zstd.mod' -> `/boot/grub/i386-pc/zstd.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/ufs1.mod' -> `/boot/grub/i386-pc/ufs1.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/lvm.mod' -> `/boot/grub/i386-pc/lvm.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/setjmp_test.mod' -> `/boot/grub/i386-pc/setjmp_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/minix3_be.mod' -> `/boot/grub/i386-pc/minix3_be.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/crc64.mod' -> `/boot/grub/i386-pc/crc64.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/romfs.mod' -> `/boot/grub/i386-pc/romfs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/testspeed.mod' -> `/boot/grub/i386-pc/testspeed.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/videotest.mod' -> `/boot/grub/i386-pc/videotest.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_twofish.mod' -> `/boot/grub/i386-pc/gcry_twofish.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/terminfo.mod' -> `/boot/grub/i386-pc/terminfo.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/video.mod' -> `/boot/grub/i386-pc/video.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/part_amiga.mod' -> `/boot/grub/i386-pc/part_amiga.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cpio.mod' -> `/boot/grub/i386-pc/cpio.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_rmd160.mod' -> `/boot/grub/i386-pc/gcry_rmd160.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/acpi.mod' -> `/boot/grub/i386-pc/acpi.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_serpent.mod' -> `/boot/grub/i386-pc/gcry_serpent.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gdb.mod' -> `/boot/grub/i386-pc/gdb.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cpio_be.mod' -> `/boot/grub/i386-pc/cpio_be.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/signature_test.mod' -> `/boot/grub/i386-pc/signature_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/testload.mod' -> `/boot/grub/i386-pc/testload.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/serial.mod' -> `/boot/grub/i386-pc/serial.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/video_cirrus.mod' -> `/boot/grub/i386-pc/video_cirrus.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_md5.mod' -> `/boot/grub/i386-pc/gcry_md5.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/terminal.mod' -> `/boot/grub/i386-pc/terminal.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/file.mod' -> `/boot/grub/i386-pc/file.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/play.mod' -> `/boot/grub/i386-pc/play.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/morse.mod' -> `/boot/grub/i386-pc/morse.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_rfc2268.mod' -> `/boot/grub/i386-pc/gcry_rfc2268.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_crc.mod' -> `/boot/grub/i386-pc/gcry_crc.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/usbms.mod' -> `/boot/grub/i386-pc/usbms.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/crypto.mod' -> `/boot/grub/i386-pc/crypto.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/afs.mod' -> `/boot/grub/i386-pc/afs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/verifiers.mod' -> `/boot/grub/i386-pc/verifiers.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/keystatus.mod' -> `/boot/grub/i386-pc/keystatus.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/random.mod' -> `/boot/grub/i386-pc/random.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cs5536.mod' -> `/boot/grub/i386-pc/cs5536.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/fshelp.mod' -> `/boot/grub/i386-pc/fshelp.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/keylayouts.mod' -> `/boot/grub/i386-pc/keylayouts.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/udf.mod' -> `/boot/grub/i386-pc/udf.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_arcfour.mod' -> `/boot/grub/i386-pc/gcry_arcfour.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/lzopio.mod' -> `/boot/grub/i386-pc/lzopio.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/xnu_uuid.mod' -> `/boot/grub/i386-pc/xnu_uuid.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/wrmsr.mod' -> `/boot/grub/i386-pc/wrmsr.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/memrw.mod' -> `/boot/grub/i386-pc/memrw.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/pxe.mod' -> `/boot/grub/i386-pc/pxe.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/font.mod' -> `/boot/grub/i386-pc/font.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/test.mod' -> `/boot/grub/i386-pc/test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/minix3.mod' -> `/boot/grub/i386-pc/minix3.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cbmemc.mod' -> `/boot/grub/i386-pc/cbmemc.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/hwmatch.mod' -> `/boot/grub/i386-pc/hwmatch.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/efiemu.mod' -> `/boot/grub/i386-pc/efiemu.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/trig.mod' -> `/boot/grub/i386-pc/trig.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gzio.mod' -> `/boot/grub/i386-pc/gzio.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/password_pbkdf2.mod' -> `/boot/grub/i386-pc/password_pbkdf2.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/lsacpi.mod' -> `/boot/grub/i386-pc/lsacpi.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/raid5rec.mod' -> `/boot/grub/i386-pc/raid5rec.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/usbtest.mod' -> `/boot/grub/i386-pc/usbtest.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/mpi.mod' -> `/boot/grub/i386-pc/mpi.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/minix_be.mod' -> `/boot/grub/i386-pc/minix_be.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/ntfscomp.mod' -> `/boot/grub/i386-pc/ntfscomp.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_cast5.mod' -> `/boot/grub/i386-pc/gcry_cast5.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/test_blockarg.mod' -> `/boot/grub/i386-pc/test_blockarg.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/newc.mod' -> `/boot/grub/i386-pc/newc.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/uhci.mod' -> `/boot/grub/i386-pc/uhci.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/sleep.mod' -> `/boot/grub/i386-pc/sleep.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/ahci.mod' -> `/boot/grub/i386-pc/ahci.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/mdraid09_be.mod' -> `/boot/grub/i386-pc/mdraid09_be.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/hdparm.mod' -> `/boot/grub/i386-pc/hdparm.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/dm_nv.mod' -> `/boot/grub/i386-pc/dm_nv.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/part_sun.mod' -> `/boot/grub/i386-pc/part_sun.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/exfat.mod' -> `/boot/grub/i386-pc/exfat.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/jpeg.mod' -> `/boot/grub/i386-pc/jpeg.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/bfs.mod' -> `/boot/grub/i386-pc/bfs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/vbe.mod' -> `/boot/grub/i386-pc/vbe.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/functional_test.mod' -> `/boot/grub/i386-pc/functional_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/linux16.mod' -> `/boot/grub/i386-pc/linux16.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gettext.mod' -> `/boot/grub/i386-pc/gettext.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/nilfs2.mod' -> `/boot/grub/i386-pc/nilfs2.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_camellia.mod' -> `/boot/grub/i386-pc/gcry_camellia.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/chain.mod' -> `/boot/grub/i386-pc/chain.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/probe.mod' -> `/boot/grub/i386-pc/probe.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cbtable.mod' -> `/boot/grub/i386-pc/cbtable.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/ldm.mod' -> `/boot/grub/i386-pc/ldm.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/ctz_test.mod' -> `/boot/grub/i386-pc/ctz_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/tar.mod' -> `/boot/grub/i386-pc/tar.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/video_fb.mod' -> `/boot/grub/i386-pc/video_fb.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/hexdump.mod' -> `/boot/grub/i386-pc/hexdump.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/ext2.mod' -> `/boot/grub/i386-pc/ext2.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/part_msdos.mod' -> `/boot/grub/i386-pc/part_msdos.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/ehci.mod' -> `/boot/grub/i386-pc/ehci.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/sendkey.mod' -> `/boot/grub/i386-pc/sendkey.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/minicmd.mod' -> `/boot/grub/i386-pc/minicmd.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/iso9660.mod' -> `/boot/grub/i386-pc/iso9660.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cryptodisk.mod' -> `/boot/grub/i386-pc/cryptodisk.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_idea.mod' -> `/boot/grub/i386-pc/gcry_idea.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/legacycfg.mod' -> `/boot/grub/i386-pc/legacycfg.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/ohci.mod' -> `/boot/grub/i386-pc/ohci.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/regexp.mod' -> `/boot/grub/i386-pc/regexp.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/minix.mod' -> `/boot/grub/i386-pc/minix.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/minix2_be.mod' -> `/boot/grub/i386-pc/minix2_be.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/hfs.mod' -> `/boot/grub/i386-pc/hfs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/bitmap_scale.mod' -> `/boot/grub/i386-pc/bitmap_scale.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/loadenv.mod' -> `/boot/grub/i386-pc/loadenv.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/ls.mod' -> `/boot/grub/i386-pc/ls.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/usb_keyboard.mod' -> `/boot/grub/i386-pc/usb_keyboard.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/iorw.mod' -> `/boot/grub/i386-pc/iorw.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/configfile.mod' -> `/boot/grub/i386-pc/configfile.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/priority_queue.mod' -> `/boot/grub/i386-pc/priority_queue.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_dsa.mod' -> `/boot/grub/i386-pc/gcry_dsa.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/datehook.mod' -> `/boot/grub/i386-pc/datehook.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gfxterm_background.mod' -> `/boot/grub/i386-pc/gfxterm_background.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/xfs.mod' -> `/boot/grub/i386-pc/xfs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/offsetio.mod' -> `/boot/grub/i386-pc/offsetio.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/usbserial_common.mod' -> `/boot/grub/i386-pc/usbserial_common.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cbls.mod' -> `/boot/grub/i386-pc/cbls.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/pci.mod' -> `/boot/grub/i386-pc/pci.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/macbless.mod' -> `/boot/grub/i386-pc/macbless.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/luks.mod' -> `/boot/grub/i386-pc/luks.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cmdline_cat_test.mod' -> `/boot/grub/i386-pc/cmdline_cat_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/div_test.mod' -> `/boot/grub/i386-pc/div_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/hashsum.mod' -> `/boot/grub/i386-pc/hashsum.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/lsapm.mod' -> `/boot/grub/i386-pc/lsapm.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/archelp.mod' -> `/boot/grub/i386-pc/archelp.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/exfctest.mod' -> `/boot/grub/i386-pc/exfctest.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_rsa.mod' -> `/boot/grub/i386-pc/gcry_rsa.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/ntfs.mod' -> `/boot/grub/i386-pc/ntfs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/linux.mod' -> `/boot/grub/i386-pc/linux.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cmp.mod' -> `/boot/grub/i386-pc/cmp.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cat.mod' -> `/boot/grub/i386-pc/cat.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/multiboot.mod' -> `/boot/grub/i386-pc/multiboot.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/time.mod' -> `/boot/grub/i386-pc/time.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/part_bsd.mod' -> `/boot/grub/i386-pc/part_bsd.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/odc.mod' -> `/boot/grub/i386-pc/odc.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/freedos.mod' -> `/boot/grub/i386-pc/freedos.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_sha512.mod' -> `/boot/grub/i386-pc/gcry_sha512.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/vga_text.mod' -> `/boot/grub/i386-pc/vga_text.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/part_dvh.mod' -> `/boot/grub/i386-pc/part_dvh.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/msdospart.mod' -> `/boot/grub/i386-pc/msdospart.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/part_gpt.mod' -> `/boot/grub/i386-pc/part_gpt.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cpuid.mod' -> `/boot/grub/i386-pc/cpuid.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/relocator.mod' -> `/boot/grub/i386-pc/relocator.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/plan9.mod' -> `/boot/grub/i386-pc/plan9.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/usbserial_pl2303.mod' -> `/boot/grub/i386-pc/usbserial_pl2303.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/search_label.mod' -> `/boot/grub/i386-pc/search_label.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/read.mod' -> `/boot/grub/i386-pc/read.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/datetime.mod' -> `/boot/grub/i386-pc/datetime.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/loopback.mod' -> `/boot/grub/i386-pc/loopback.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/raid6rec.mod' -> `/boot/grub/i386-pc/raid6rec.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/date.mod' -> `/boot/grub/i386-pc/date.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_blowfish.mod' -> `/boot/grub/i386-pc/gcry_blowfish.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/tga.mod' -> `/boot/grub/i386-pc/tga.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gfxmenu.mod' -> `/boot/grub/i386-pc/gfxmenu.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/vga.mod' -> `/boot/grub/i386-pc/vga.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/ufs2.mod' -> `/boot/grub/i386-pc/ufs2.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/f2fs.mod' -> `/boot/grub/i386-pc/f2fs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/bufio.mod' -> `/boot/grub/i386-pc/bufio.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/videotest_checksum.mod' -> `/boot/grub/i386-pc/videotest_checksum.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/sfs.mod' -> `/boot/grub/i386-pc/sfs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/xzio.mod' -> `/boot/grub/i386-pc/xzio.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/bswap_test.mod' -> `/boot/grub/i386-pc/bswap_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/pbkdf2.mod' -> `/boot/grub/i386-pc/pbkdf2.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/squash4.mod' -> `/boot/grub/i386-pc/squash4.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/progress.mod' -> `/boot/grub/i386-pc/progress.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/password.mod' -> `/boot/grub/i386-pc/password.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/sleep_test.mod' -> `/boot/grub/i386-pc/sleep_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/png.mod' -> `/boot/grub/i386-pc/png.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/true.mod' -> `/boot/grub/i386-pc/true.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/bitmap.mod' -> `/boot/grub/i386-pc/bitmap.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/zfscrypt.mod' -> `/boot/grub/i386-pc/zfscrypt.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/div.mod' -> `/boot/grub/i386-pc/div.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/syslinuxcfg.mod' -> `/boot/grub/i386-pc/syslinuxcfg.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/geli.mod' -> `/boot/grub/i386-pc/geli.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gptsync.mod' -> `/boot/grub/i386-pc/gptsync.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/eval.mod' -> `/boot/grub/i386-pc/eval.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/tftp.mod' -> `/boot/grub/i386-pc/tftp.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/part_dfly.mod' -> `/boot/grub/i386-pc/part_dfly.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/legacy_password_test.mod' -> `/boot/grub/i386-pc/legacy_password_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/macho.mod' -> `/boot/grub/i386-pc/macho.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/adler32.mod' -> `/boot/grub/i386-pc/adler32.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/jfs.mod' -> `/boot/grub/i386-pc/jfs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/disk.mod' -> `/boot/grub/i386-pc/disk.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/usbserial_ftdi.mod' -> `/boot/grub/i386-pc/usbserial_ftdi.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/reboot.mod' -> `/boot/grub/i386-pc/reboot.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/truecrypt.mod' -> `/boot/grub/i386-pc/truecrypt.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/nativedisk.mod' -> `/boot/grub/i386-pc/nativedisk.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/biosdisk.mod' -> `/boot/grub/i386-pc/biosdisk.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/part_sunpc.mod' -> `/boot/grub/i386-pc/part_sunpc.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/memdisk.mod' -> `/boot/grub/i386-pc/memdisk.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/mdraid09.mod' -> `/boot/grub/i386-pc/mdraid09.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cmp_test.mod' -> `/boot/grub/i386-pc/cmp_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/btrfs.mod' -> `/boot/grub/i386-pc/btrfs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/mdraid1x.mod' -> `/boot/grub/i386-pc/mdraid1x.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/extcmd.mod' -> `/boot/grub/i386-pc/extcmd.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/lspci.mod' -> `/boot/grub/i386-pc/lspci.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_sha256.mod' -> `/boot/grub/i386-pc/gcry_sha256.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/diskfilter.mod' -> `/boot/grub/i386-pc/diskfilter.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/smbios.mod' -> `/boot/grub/i386-pc/smbios.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/help.mod' -> `/boot/grub/i386-pc/help.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/zfs.mod' -> `/boot/grub/i386-pc/zfs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/zfsinfo.mod' -> `/boot/grub/i386-pc/zfsinfo.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/usb.mod' -> `/boot/grub/i386-pc/usb.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/mmap.mod' -> `/boot/grub/i386-pc/mmap.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/fat.mod' -> `/boot/grub/i386-pc/fat.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/strtoull_test.mod' -> `/boot/grub/i386-pc/strtoull_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_des.mod' -> `/boot/grub/i386-pc/gcry_des.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/mda_text.mod' -> `/boot/grub/i386-pc/mda_text.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/part_apple.mod' -> `/boot/grub/i386-pc/part_apple.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/parttool.mod' -> `/boot/grub/i386-pc/parttool.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/all_video.mod' -> `/boot/grub/i386-pc/all_video.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/hfspluscomp.mod' -> `/boot/grub/i386-pc/hfspluscomp.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/pgp.mod' -> `/boot/grub/i386-pc/pgp.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/pxechain.mod' -> `/boot/grub/i386-pc/pxechain.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/shift_test.mod' -> `/boot/grub/i386-pc/shift_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cmosdump.mod' -> `/boot/grub/i386-pc/cmosdump.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_tiger.mod' -> `/boot/grub/i386-pc/gcry_tiger.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/setpci.mod' -> `/boot/grub/i386-pc/setpci.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/minix2.mod' -> `/boot/grub/i386-pc/minix2.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/elf.mod' -> `/boot/grub/i386-pc/elf.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_rijndael.mod' -> `/boot/grub/i386-pc/gcry_rijndael.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/pcidump.mod' -> `/boot/grub/i386-pc/pcidump.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/rdmsr.mod' -> `/boot/grub/i386-pc/rdmsr.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/mul_test.mod' -> `/boot/grub/i386-pc/mul_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/hello.mod' -> `/boot/grub/i386-pc/hello.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/net.mod' -> `/boot/grub/i386-pc/net.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/halt.mod' -> `/boot/grub/i386-pc/halt.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/tr.mod' -> `/boot/grub/i386-pc/tr.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_md4.mod' -> `/boot/grub/i386-pc/gcry_md4.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/xnu_uuid_test.mod' -> `/boot/grub/i386-pc/xnu_uuid_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_seed.mod' -> `/boot/grub/i386-pc/gcry_seed.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/video_colors.mod' -> `/boot/grub/i386-pc/video_colors.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/search_fs_uuid.mod' -> `/boot/grub/i386-pc/search_fs_uuid.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/search_fs_file.mod' -> `/boot/grub/i386-pc/search_fs_file.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gfxterm_menu.mod' -> `/boot/grub/i386-pc/gfxterm_menu.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/hfsplus.mod' -> `/boot/grub/i386-pc/hfsplus.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_whirlpool.mod' -> `/boot/grub/i386-pc/gcry_whirlpool.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/at_keyboard.mod' -> `/boot/grub/i386-pc/at_keyboard.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/normal.mod' -> `/boot/grub/i386-pc/normal.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/pbkdf2_test.mod' -> `/boot/grub/i386-pc/pbkdf2_test.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/scsi.mod' -> `/boot/grub/i386-pc/scsi.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/xnu.mod' -> `/boot/grub/i386-pc/xnu.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cbfs.mod' -> `/boot/grub/i386-pc/cbfs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/ata.mod' -> `/boot/grub/i386-pc/ata.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/multiboot2.mod' -> `/boot/grub/i386-pc/multiboot2.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/bsd.mod' -> `/boot/grub/i386-pc/bsd.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/reiserfs.mod' -> `/boot/grub/i386-pc/reiserfs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/backtrace.mod' -> `/boot/grub/i386-pc/backtrace.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/videoinfo.mod' -> `/boot/grub/i386-pc/videoinfo.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/915resolution.mod' -> `/boot/grub/i386-pc/915resolution.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/part_acorn.mod' -> `/boot/grub/i386-pc/part_acorn.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cmostest.mod' -> `/boot/grub/i386-pc/cmostest.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/drivemap.mod' -> `/boot/grub/i386-pc/drivemap.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/http.mod' -> `/boot/grub/i386-pc/http.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/affs.mod' -> `/boot/grub/i386-pc/affs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/boot.mod' -> `/boot/grub/i386-pc/boot.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/echo.mod' -> `/boot/grub/i386-pc/echo.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/procfs.mod' -> `/boot/grub/i386-pc/procfs.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/search.mod' -> `/boot/grub/i386-pc/search.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/pata.mod' -> `/boot/grub/i386-pc/pata.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/cbtime.mod' -> `/boot/grub/i386-pc/cbtime.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/setjmp.mod' -> `/boot/grub/i386-pc/setjmp.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/blocklist.mod' -> `/boot/grub/i386-pc/blocklist.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/usbserial_usbdebug.mod' -> `/boot/grub/i386-pc/usbserial_usbdebug.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/ntldr.mod' -> `/boot/grub/i386-pc/ntldr.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/gcry_sha1.mod' -> `/boot/grub/i386-pc/gcry_sha1.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/spkmodem.mod' -> `/boot/grub/i386-pc/spkmodem.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/lsmmap.mod' -> `/boot/grub/i386-pc/lsmmap.mod'.
grub-install: info: copying `/usr/lib/grub/i386-pc/efiemu32.o' -> `/boot/grub/i386-pc/efiemu32.o'.
grub-install: info: copying `/usr/lib/grub/i386-pc/efiemu64.o' -> `/boot/grub/i386-pc/efiemu64.o'.
grub-install: info: copying `/usr/lib/grub/i386-pc/moddep.lst' -> `/boot/grub/i386-pc/moddep.lst'.
grub-install: info: copying `/usr/lib/grub/i386-pc/command.lst' -> `/boot/grub/i386-pc/command.lst'.
grub-install: info: copying `/usr/lib/grub/i386-pc/fs.lst' -> `/boot/grub/i386-pc/fs.lst'.
grub-install: info: copying `/usr/lib/grub/i386-pc/partmap.lst' -> `/boot/grub/i386-pc/partmap.lst'.
grub-install: info: copying `/usr/lib/grub/i386-pc/parttool.lst' -> `/boot/grub/i386-pc/parttool.lst'.
grub-install: info: copying `/usr/lib/grub/i386-pc/video.lst' -> `/boot/grub/i386-pc/video.lst'.
grub-install: info: copying `/usr/lib/grub/i386-pc/crypto.lst' -> `/boot/grub/i386-pc/crypto.lst'.
grub-install: info: copying `/usr/lib/grub/i386-pc/terminal.lst' -> `/boot/grub/i386-pc/terminal.lst'.
grub-install: info: copying `/usr/lib/grub/i386-pc/modinfo.sh' -> `/boot/grub/i386-pc/modinfo.sh'.
grub-install: info: copying `/usr/share/grub/unicode.pf2' -> `/boot/grub/fonts/unicode.pf2'.
grub-install: info: /dev/sda5 is not present.
grub-install: info: Looking for /dev/sda5.
grub-install: info: /dev/sda is a parent of /dev/sda5.
grub-install: info: /dev/sda5 starts from 1052672.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 488397168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 488397168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 4 starts from 1052672.
grub-install: info: /dev/sda5 is present.
grub-install: info: Looking for /dev/sda5.
grub-install: info: /dev/sda is a parent of /dev/sda5.
grub-install: info: /dev/sda5 starts from 1052672.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 488397168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 488397168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 4 starts from 1052672.
grub-install: info: /dev/sda5 is present.
grub-install: info: Looking for /dev/sda5.
grub-install: info: /dev/sda is a parent of /dev/sda5.
grub-install: info: /dev/sda5 starts from 1052672.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 488397168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 488397168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 4 starts from 1052672.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 488397168.
grub-install: info: /dev/sda is present.
grub-install: info: Looking for /dev/sda.
grub-install: info: /dev/sda is a parent of /dev/sda.
grub-install: info: /dev/sda is present.
grub-install: info: Looking for /dev/sda.
grub-install: info: /dev/sda is a parent of /dev/sda.
grub-install: info: /dev/sda is present.
grub-install: info: Looking for /dev/sda.
grub-install: info: /dev/sda is a parent of /dev/sda.
grub-install: info: grub-mkimage --directory '/usr/lib/grub/i386-pc' --prefix '(,msdos5)/boot/grub' --output '/boot/grub/i386-pc/core.img'  --dtb '' --format 'i386-pc' --compression 'auto'  'ext2' 'part_msdos' 'biosdisk' 
.
grub-install: info: the total module size is 0x41f0.
grub-install: info: reading /usr/lib/grub/i386-pc/kernel.img.
grub-install: info: locating the section .text at 0x0.
grub-install: info: locating the section .rodata at 0x5864.
grub-install: info: locating the section .data at 0x6820.
grub-install: info: locating the section .bss at 0x7020.
grub-install: info: reading /usr/lib/grub/i386-pc/fshelp.mod.
grub-install: info: reading /usr/lib/grub/i386-pc/ext2.mod.
grub-install: info: reading /usr/lib/grub/i386-pc/part_msdos.mod.
grub-install: info: reading /usr/lib/grub/i386-pc/biosdisk.mod.
grub-install: info: kernel_img=0x557fc6e3ad70, kernel_size=0x700c.
grub-install: info: the core size is 0x595d.
grub-install: info: reading /usr/lib/grub/i386-pc/lzma_decompress.img.
grub-install: info: reading /usr/lib/grub/i386-pc/diskboot.img.
grub-install: info: writing 0x200 bytes.
grub-install: info: writing 0x648d bytes.
grub-install: info: copying `/usr/lib/grub/i386-pc/boot.img' -> `/boot/grub/i386-pc/boot.img'.
grub-install: info: grub-bios-setup  --verbose     --directory='/boot/grub/i386-pc' --device-map='/boot/grub/device.map' '/dev/sda'.
grub-install: info: reading /boot/grub/i386-pc/boot.img.
grub-install: info: reading /boot/grub/i386-pc/core.img.
grub-install: info: Opening dest `hostdisk//dev/sda'.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 488397168.
grub-install: info: /dev/sda5 is present.
grub-install: info: Looking for /dev/sda5.
grub-install: info: /dev/sda is a parent of /dev/sda5.
grub-install: info: /dev/sda5 starts from 1052672.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 488397168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 488397168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 4 starts from 1052672.
grub-install: info: /dev/sda5 is present.
grub-install: info: Looking for /dev/sda5.
grub-install: info: /dev/sda is a parent of /dev/sda5.
grub-install: info: /dev/sda5 starts from 1052672.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 488397168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 488397168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 4 starts from 1052672.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 488397168.
grub-install: info: guessed root_dev `hostdisk//dev/sda' from dir `/boot/grub/i386-pc'.
grub-install: info: setting the root device to `hostdisk//dev/sda,msdos5'.
grub-install: info: saving <1,0,512>.
grub-install: info: saving <2,0,512>.
grub-install: info: saving <3,0,512>.
grub-install: info: saving <4,0,512>.
grub-install: info: saving <5,0,512>.
grub-install: info: saving <6,0,512>.
grub-install: info: saving <7,0,512>.
grub-install: info: saving <8,0,512>.
grub-install: info: saving <9,0,512>.
grub-install: info: saving <10,0,512>.
grub-install: info: saving <11,0,512>.
grub-install: info: saving <12,0,512>.
grub-install: info: saving <13,0,512>.
grub-install: info: saving <14,0,512>.
grub-install: info: saving <15,0,512>.
grub-install: info: saving <16,0,512>.
grub-install: info: saving <17,0,512>.
grub-install: info: saving <18,0,512>.
grub-install: info: saving <19,0,512>.
grub-install: info: saving <20,0,512>.
grub-install: info: saving <21,0,512>.
grub-install: info: saving <22,0,512>.
grub-install: info: saving <23,0,512>.
grub-install: info: saving <24,0,512>.
grub-install: info: saving <25,0,512>.
grub-install: info: saving <26,0,512>.
grub-install: info: saving <27,0,512>.
grub-install: info: saving <28,0,512>.
grub-install: info: saving <29,0,512>.
grub-install: info: saving <30,0,512>.
grub-install: info: saving <31,0,512>.
grub-install: info: saving <32,0,512>.
grub-install: info: saving <33,0,512>.
grub-install: info: saving <34,0,512>.
grub-install: info: saving <35,0,512>.
grub-install: info: saving <36,0,512>.
grub-install: info: saving <37,0,512>.
grub-install: info: saving <38,0,512>.
grub-install: info: saving <39,0,512>.
grub-install: info: saving <40,0,512>.
grub-install: info: saving <41,0,512>.
grub-install: info: saving <42,0,512>.
grub-install: info: saving <43,0,512>.
grub-install: info: saving <44,0,512>.
grub-install: info: saving <45,0,512>.
grub-install: info: saving <46,0,512>.
grub-install: info: saving <47,0,512>.
grub-install: info: saving <48,0,512>.
grub-install: info: saving <49,0,512>.
grub-install: info: saving <50,0,512>.
grub-install: info: saving <51,0,512>.
grub-install: info: saving <52,0,512>.
grub-install: info: saving <53,0,512>.
grub-install: info: saving <54,0,512>.
grub-install: info: saving <55,0,512>.
grub-install: info: saving <56,0,512>.
grub-install: info: saving <57,0,512>.
grub-install: info: saving <58,0,512>.
grub-install: info: saving <59,0,512>.
grub-install: info: saving <60,0,512>.
grub-install: info: saving <61,0,512>.
grub-install: info: saving <62,0,512>.
grub-install: info: saving <63,0,512>.
grub-install: info: saving <64,0,512>.
grub-install: info: saving <65,0,512>.
grub-install: info: saving <66,0,512>.
grub-install: info: saving <67,0,512>.
grub-install: info: saving <68,0,512>.
grub-install: info: saving <69,0,512>.
grub-install: info: saving <70,0,512>.
grub-install: info: saving <71,0,512>.
grub-install: info: saving <72,0,512>.
grub-install: info: saving <73,0,512>.
grub-install: info: saving <74,0,512>.
grub-install: info: saving <75,0,512>.
grub-install: info: saving <76,0,512>.
grub-install: info: saving <77,0,512>.
grub-install: info: saving <78,0,512>.
grub-install: info: saving <79,0,512>.
grub-install: info: saving <80,0,512>.
grub-install: info: saving <81,0,512>.
grub-install: info: saving <82,0,512>.
grub-install: info: saving <83,0,512>.
grub-install: info: saving <84,0,512>.
grub-install: info: saving <85,0,512>.
grub-install: info: saving <86,0,512>.
grub-install: info: saving <87,0,512>.
grub-install: info: saving <88,0,512>.
grub-install: info: saving <89,0,512>.
grub-install: info: saving <90,0,512>.
grub-install: info: saving <91,0,512>.
grub-install: info: saving <92,0,512>.
grub-install: info: saving <93,0,512>.
grub-install: info: saving <94,0,512>.
grub-install: info: saving <95,0,512>.
grub-install: info: saving <96,0,512>.
grub-install: info: saving <97,0,512>.
grub-install: info: saving <98,0,512>.
grub-install: info: saving <99,0,512>.
grub-install: info: saving <100,0,512>.
grub-install: info: saving <101,0,512>.
grub-install: info: saving <102,0,512>.
grub-install: info: saving <103,0,512>.
grub-install: info: saving <104,0,512>.
Installation finished. No error reported.


```

---

### Post by MAFoElffen on 2023-02-26
I see where it found your system installed in /dev/sda5 and successfully installed Legacy boot to the root of /dev/sda...

Does it still not boot?

---

### Post by Rick St. George on 2023-02-26
This morning, I looked inside the box. Vacummed, cleaned, reversed the SATA cables on #1 and #2 to see if it made a difference. 
It booted up and I believe I chose the 2nd / previous Kernel. I am on it now, thats how I got above info.

Did your instructions have me Re-Install Grub?

---

### Post by MAFoElffen on 2023-02-26
> **Rick St. George said:**
> Did your instructions have me Re-Install Grub?
Yes it did. It included output to see if it did install, and if it didn't where the problem "was." Happy that it is going for you now!

---

### Post by Rick St. George on 2023-02-26
Did you see any problems? I just did a Shutdown / Restart, and Grub came up, but also showed "Environment Block too small", but pressing any key and it came up OK.
Still concerned something is wrong. I noticed in my partial SysInfo a couple posts ago, Current Boot Mode shows "Legacy Mode (alias BIOS Mode). 
As you say, it put Boot at front of SDA (which is sda1) a small partition 537 MB FAT with mount pt. /dev/disk/by-uuid/A00D-96E4 /mnt/A00D-96E4. 
Main = sda5, ext4, 249 GB UbuntuStudio OS.
DISKs shows Drive OK using Smart Data. 
So, Don't understand this "Environment Block too Small" message !!?!?  Does the HWE have any significance as it shows ;

> 

   --- Hardware Enablement Stack (HWE) Informationt:
These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.15.0.60.66
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.4.0.26.32

   --- HWE Package Status from 'dpkg':
HWE package linux-generic-hwe-20.04 was not detected. Please check 
kernel version to verify range
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).


Maybe that's why it is booting with 5.15.0.56 and not 5.15.0.60 
Should I install it HWE? Just logically curious.

---

### Post by MAFoElffen on 2023-02-26
The HWE package is not going to affect the error of /boot/grub2/grubenv file being reported as corrupted.

What I would do if it were me (since you are Grub2 Legacy boot)... Is
```

which grub-editenv
grub-editenv --help

```
If there, then
```

sudo rm /boot/grub/grubenv
sudo grub-editenv /boot/grub/grubenv create

```

---

### Post by Rick St. George on 2023-02-26
Afterward, contents of grubenv is a series of ###############
Is that correct? Didn't the install do this? Why do it again?
Time to ReStart and see what happens!

......................  

ReStart Successful and using 1st Option. No Environment Message. Thanks a MILLION !!!

Case closed! Somehow it got corrupted. Probably due to all the Updates every other day. But rather be safe than sorry!

---

