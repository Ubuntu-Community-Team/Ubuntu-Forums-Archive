---
title: "[SOLVED] hal.dll missing or corrupt."
date: 2008-05-16
forum: General Help
---

### Post by tamoneya on 2008-05-16
Recently I got the windows: "hal.dll missing or corrupt" error.  I have searched the forums a fair amount and found one nice thread:[http://ubuntuforums.org/showthread.php?t=327386](http://ubuntuforums.org/showthread.php?t=327386).  I have looked at all of the threads referenced by this thread but it seems like my problem is slightly different.  Most of the users seemed to have the problem the first time that they ran windows after setting up a dual boot.  I have had a dual boot running with no problems for a couple months now and I see no reason why my boot.ini and everything should have changed.  I also even tried some of the windows solutions like actually replacing the hal.dll file through repair console. (I have a XP SP1 disk on hand).  Here are a bunch of files and outputs that may be helpful.

menu.lst
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
splashimage = (hd0,2)/boot/grub/grubuntu.xpm.gz
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a17b81fe-af9c-4f5a-841f-93bc83aaaa98 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##spls

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a17b81fe-af9c-4f5a-841f-93bc83aaaa98 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a17b81fe-af9c-4f5a-841f-93bc83aaaa98 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

c:/boot.ini:```
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

sudo fdisk -l:```
tamoneya@ubuntu1:~/.FAH$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19eae19c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           18718       19457     5944050    5  Extended
/dev/sda2   *       14802       18717    31442040    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3               1        1824    14651248+  83  Linux
/dev/sda4            1825       14801   104237752+  83  Linux
/dev/sda5           18718       19457     5944018+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Let me know if there are any other files that I should be looking at.

---

### Post by ibuclaw on 2008-05-16
Your menu.lst and boot.ini files seem in order (They are practically identical to mine minus the partition number).

As for your fdisk list:
[QUOTE=tamoneya]
/dev/sda2   *       14802       18717    31442040    7  HPFS/NTFS
**Partition 2 does not end on cylinder boundary.**
[/QUOTE]
That is the only irregularity I see.

Have you ran a disk check for any erroneous sectors on that partition?

Regards
Iain

---

### Post by tamoneya on 2008-05-16
i think that shouldnt be a problem, that was there when I first installed windows.  Anyways, how do you suggest I go about checking it.
```
tamoneya@ubuntu1:/$ sudo fsck /dev/sda2
fsck 1.40.8 (13-Mar-2008)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2

```

Also I found this in c:\ntldr:```
@Windows could not start because of an error in the software.
Please report this problem as :
^@\^@^@^@Windows could not start because the following file was not found
and is required :
^@^@^@P^@^@^@Windows could not start because of a bad copy of the
following file :
^@^@^@T^@^@^@Windows could not start because the following file is missing
or corrupt:
^@^@^@T^@^@^@Windows could not start because of a hardware memory
configuration problem.
^@\^@^@^@Windows could not start because of a computer disk hardware
configuration problem.
^@^@^@`^@^@^@Windows could not start because of a general computer hardware
configuration problem.
^@^@^@^@d^@^@^@Windows could not start because of the following ARC firmware
boot configuration problem :
^@^@^@@^@^@^@Check hardware memory configuration and amount of RAM.
^@^@^@^@(^@^@^@Too many configuration entries.
^@^@^@0^@^@^@Could not access disk partition tables
^@^@^@^@<^@^@^@The 'osloadpartition' parameter setting is invalid.
^@^@^@X^@^@^@Could not read from the selected boot disk.  Check boot path
and disk hardware.
^@^@<^@^@^@The 'systempartition' parameter setting is invalid.
^@^@^@X^@^@^@Could not read from the selected system boot disk.
Check 'systempartition' path.
^@H^@^@^@The 'osloadfilename' parameter does not point to a valid file.
^@^@^@^@,^@^@^@<Windows root>\system32\ntoskrnl.exe.
^@@^@^@^@The 'osloader' parameter does not point to a valid file.
^@^@(^@^@^@<Windows root>\system32\hal.dll.
^@^@^\^@^@^@'osloader'\hal.dll
^@^@^@^@^X^@^@^@Loader error 1.
^@^@^@^X^@^@^@Loader error 2.
^@^@^@$^@^@^@load needed DLLs for kernel.
^@^@ ^@^@^@load needed DLLs for HAL.
^@^\^@^@^@find system drivers.
^@^@^\^@^@^@read system drivers.
^@^@0^@^@^@did not load system boot device driver.
^@^@^@0^@^@^@load system hardware configuration file.
^@^@0^@^@^@find system partition name device name.
^@^@^@ ^@^@^@find boot partition name.
^@D^@^@^@did not properly generate ARC name for HAL and system paths.
^@^@^X^@^@^@Loader error 3.
^@^@^@,^@^@^@<Windows root>\system32\ntoskrnl.exe
^@^@D^@^@^@Please contact your support person to report this problem.
^@^@^@^@&#65533;^@^@^@You can attempt to repair this file by starting Windows Setup
using the original Setup CD-ROM.
Select 'r' at the first screen to start repair.
^@^@4^@^@^@Please re-install a copy of the above file.
^@^@^@&#65533;^@^@^@Please check the Windows documentation about hardware memory
requirements and your hardware reference manuals for
additional information.
^@^@^@&#65533;^@^@^@Please check the Windows documentation about hardware disk
configuration and your hardware reference manuals for
additional information.
^@^@^@^@&#65533;^@^@^@Please check the Windows documentation about hardware
configuration and your hardware reference manuals for additional
information.
^@&#65533;^@^@^@Please check the Windows documentation about ARC configuration
options and your hardware reference manuals for additional
information.
^@^@&#65533;^A^@^@     Hardware Profile/Configuration Recovery Menu

This menu allows you to select a hardware profile
to be used when Windows is started.

If your system is not starting correctly, then you may switch to a
previous system configuration, which may overcome startup problems.
IMPORTANT: System configuration changes made since the last successful
startup will be discarded.
^@^@^@l^@^@^@Use the up and down arrow keys to move the highlight
to the selection you want. Then press ENTER.
^@^@^@^@&#65533;^@^@^@No hardware profiles are currently defined. Hardware profiles
can be created from the System applet of the control panel.
^@^@^@^@|^@^@^@To switch to the Last Known Good configuration, press 'L'.
To Exit this menu and restart your computer, press F3.
^@^@^@^@t^@^@^@To switch to the default configuration, press 'D'.
To Exit this menu and restart your computer, press F3.
^@^@^@^@^H^@^@^@L
^@^H^@^@^@D
^@L^@^@^@Seconds until highlighted choice will be started automatically: %d
^@^@^@^@L^@^@^@
Press spacebar NOW to invoke Hardware Profile/Last Known Good menu
^@^@,^@^@^@Boot default hardware configuration
^@^@^@d^@^@^@The system is being restarted from its previous location.
Press the spacebar to interrupt.
^@^@^@D^@^@^@The system could not be restarted from its previous location
^@^@^X^@^@^@due to no memory.
^@0^@^@^@because the restoration image is corrupt.
^@X^@^@^@because the restoration image is not compatible with the current
configuration.
^@^@ ^@^@^@due to an internal error.
^@ ^@^@^@due to an internal error.
^@ ^@^@^@due to a read failure.
^@^@^@^@(^@^@^@System restart has been paused:
^@^@^@@^@^@^@Delete restoration data and proceed to system boot menu
^@^@^@$^@^@^@Continue with system restart
^@^@l^@^@^@The last attempt to restart the system from its previous location
failed.  Attempt to restart again?
^@4^@^@^@Continue with debug breakpoint on system wake
^@x^@^@^@Windows could not start because the specified kernel does
not exist or is not compatible with this processor.
^@^@^@^\^@^@^@Starting Windows...
^@^@^@^\^@^@^@Resuming Windows...
^@^@^@&#65533;^@^@^@Windows could not start because there was an error reading
the boot settings from NVRAM.

Please check your firmware settings.  You may need to restore your
NVRAM settings from a backup.
^@^@^@^@^\^@^@^@ [debugger enabled]
^@^@^@^X^@^@^@Windows (default)
^@(^@^@^@NTLDR: BOOT.INI file not found.
^@^@^@<^@^@^@NTLDR: no [operating systems] section in boot.txt.
^@^@^@^@(^@^@^@Booting default kernel from %s.
^@^@^@4^@^@^@Please select the operating system to start:
^@^@h^@^@^@

Use the up and down arrow keys to move the highlight to your choice.
Press ENTER to choose.
^@^@H^@^@^@Seconds until highlighted choice will be started automatically:
^@^@^@0^@^@^@Invalid BOOT.INI file
Booting from %s
^@^@^@^@<^@^@^@I/O Error accessing boot sector file
%s\BOOTSECT.DOS
^@$^@^@^@NTLDR: Couldn't open drive %s
^@0^@^@^@NTLDR: Fatal Error %d reading BOOT.INI
^@^@^@^@0^@^@^@
NTDETECT V5.0 Checking Hardware ...

^@^@^@^X^@^@^@NTDETECT failed
^@^@^@H^@^@^@Current Selection:
  Title..: %s
  Path...: %s
  Options: %s
^@^@^@ ^@^@^@Enter new load options:
^@^@^@^X^@^@^@ [EMS enabled]
^@^@^@^@^\^@^@^@Invalid BOOT.INI file
^@@^@^@^@Windows Advanced Options Menu
Please select an option:
^@^@^@^P^@^@^@Safe Mode
^@ ^@^@^@Safe Mode with Networking
^@(^@^@^@Step-by-Step Confirmation Mode
^@^@^@^@$^@^@^@Safe Mode with Command Prompt
^@^P^@^@^@VGA Mode
^@^@H^@^@^@Directory Services Restore Mode (Windows domain controllers only)
^@L^@^@^@Last Known Good Configuration (your most recent settings that worked)
^@^X^@^@^@Debugging Mode
^@^@^@^@4^@^@^@Disable automatic restart on system failure
^@^@^@^\^@^@^@Enable Boot Logging
^@^@^@P^@^@^@For troubleshooting and advanced startup options for Windows, pres$
^@^@^@^X^@^@^@Enable VGA Mode
^@^@^@<^@^@^@
Press ESCAPE to disable safeboot and boot normally.
^@ ^@^@^@Start Windows Normally
^@^@^@^@ ^@^@^@Return to OS Choices Menu
^@^P^@^@^@Reboot
^@^@^@^@<^B^@^@We apologize for the inconvenience, but Windows did not start su$
recent hardware or software change might have caused this.

If your computer stopped responding, restarted unexpectedly, or was
automatically shut down to protect your files and folders, choose Last Known
Good Configuration to revert to the most recent settings that worked.

If a previous startup attempt was interrupted due to a power failure or because
the Power or Reset button was pressed, or if you aren't sure what caused the
problem, choose Start Windows Normally.
^@&#65533;^@^@^@Windows was not shutdown successfully.  If this was due to the system $
responding, or if the system shutdown to protect data, you might be able to
recover by choosing one of the Safe Mode configurations from the menu below:
^@^@^@^@$^@^@^@Seconds until Windows starts:
^@^H^@^@^@&#65533;
^@^H^@^@^@&#65533;
^@L^@^@^@Windows could not start due to an error while booting from a RAMDISK.
^@0^@^@^@Windows failed to open the RAMDISK image.
^@ ^@^@^@Loading RAMDISK image...

```

I guess I have to go about fixing up ntldr but I have no clue why it go corrupted.

---

### Post by ibuclaw on 2008-05-16
No, that should look like that. ntldr is a windows executable file.

Although, to check that we have (somewhat) the same file.
[PHP]/$ du -h ntldr
248K	ntldr
/$ md5sum ntldr
9ec920f4179d45af3a6638a083d39c85  ntldr
[/PHP]

[PHP]
/WINDOWS/system32$ du -h hal.dll
132K	hal.dll
/WINDOWS/system32$ md5sum hal.dll
f9a0f579fc18036ffdd9e26e0d268ccd  hal.dll
[/PHP]
I have XP Home Edition by the way, so don't freak out that they are different.
Although they shouldn't be (but then again... you can't trust proprietary vendors to ship the exact same binaries ;) ).

Regards
Iain

---

### Post by tamoneya on 2008-05-16
after reading ntldr more closely it seems that there are not error logs but the messages that ntldr throws when errors occur.  So I stopped looking into ntldr.  Do you think doing a fixmbr and then reinstalling grub would have any effect on this problem?

---

### Post by tamoneya on 2008-05-16
> **tinivole said:**
> No, that should look like that. ntldr is a windows executable file.

Although, to check that we have (somewhat) the same file.
[PHP]/$ du -h ntldr
248K	ntldr
/$ md5sum ntldr
9ec920f4179d45af3a6638a083d39c85  ntldr
[/PHP]

[PHP]
/WINDOWS/system32$ du -h hal.dll
132K	hal.dll
/WINDOWS/system32$ md5sum hal.dll
f9a0f579fc18036ffdd9e26e0d268ccd  hal.dll
[/PHP]
I have XP Home Edition by the way, so don't freak out that they are different.
Although they shouldn't be (but then again... you can't trust proprietary vendors to ship the exact same binaries ;) ).

Regards
Iain

ntldr is identical```
tamoneya@ubuntu1:/windows$ du -h ntldr
248K	ntldr
tamoneya@ubuntu1:/windows$ md5sum ntldr
9ec920f4179d45af3a6638a083d39c85  ntldr

```

hal.dll however is not:```
tamoneya@ubuntu1:/windows/WINDOWS/system32$ du -h hal.dll 
100K	hal.dll
tamoneya@ubuntu1:/windows/WINDOWS/system32$ md5sum hal.dll
14899fb16e1263bdc6e17aec0a69bb97  hal.dll

```
I tried replacing hal.dll from the install cd: d:/i386/hal.dl_

---

### Post by ibuclaw on 2008-05-16
That seems feasible.

If you have made sure that your hal.dll file is correctly put and your partition tables haven't changed numbers (so the windows boot file is pointing at the wrong location, ie: from 2 to 3 in the boot.ini file).

Then give a shot. The worst that can happen is that the problem will still be there, right? But that is easily overcome.

Regards
Iain

---

### Post by tamoneya on 2008-05-16
> **tinivole said:**
> That seems feasible.

If you have made sure that your hal.dll file is correctly put and your partition tables haven't changed numbers (so the windows boot file is pointing at the wrong location, ie: from 2 to 3 in the boot.ini file).

Then give a shot. The worst that can happen is that the problem will still be there, right? But that is easily overcome.

Regards
Iain

Im going to give it a try.  It will take me a while and then I will post back here.

---

### Post by ibuclaw on 2008-05-16
When you come back.

I've uploaded my hal.dll file here:
[http://img.ui-portal.de/gmxcom/filestorage/en/application/guestaccess.html?path=Share%20from%20iainbuclaw@gmx.co.uk&token=CC6760E91A34256D#](http://img.ui-portal.de/gmxcom/filestorage/en/application/guestaccess.html?path=Share%20from%20iainbuclaw@gmx.co.uk&token=CC6760E91A34256D#)

Regards
Iain

---

### Post by tamoneya on 2008-05-17
Thanks for you help but the whole thing got broken.  I did fixmbr and that obviously removed GRUB but didnt allow me to get boot.ini working any better.  bootcfg /rebuild was complaining that the disk had errors and that i should run chkdsk and chkdsk kept telling me there were no problems.  To make a long story short I backed up everything and did a full dual OS reinstall.

---

