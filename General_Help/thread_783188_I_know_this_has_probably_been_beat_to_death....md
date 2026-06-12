---
title: "I know this has probably been beat to death..."
date: 2008-05-05
forum: General Help
---

### Post by Rackham on 2008-05-05
but I can't find a simple, straight forward answer. I've installed Wubi / Ubuntu 8.04 on a second hard drive (slave) on my XP Pro machine to test it out. Unfortunately, regardless of how I install it, from the Live CD, the Wubi installer, etc - it gives me an error 15 on boot. It looks like it installs fine, and even gives me the multiboot option on startup, but then it goes to an error 15 screen, from which there is no escape other than to reboot, try again, and finally, boot into windows to type what you all may find to be inane, and possibly redundant questions. I just need a simple, straight answer on how to fix it, without all the seemingly requisite Linux mumbo jumbo. :) 

Any assistance you can provide would be appreciated. Thanks.

---

### Post by Catalyst2Death on 2008-05-05
Have you checked the cd for errors?

When you boot the live cd, there should be an option to check the cd for errors, run this and it will verify that the everything is in order.  If its not, then the answer is fairly simple.  You need to reburn the cd and run the install again.  If the disk checks out, then it sounds like there is a corrupted file somewhere, in which case you may want to reinstall using a different cd-drive.  This may not be the most appropriate thing, but these are the steps I would take before doing anything terribly serious.

---

### Post by Rackham on 2008-05-05
Actually - I've burned the CD twice with 2 fresh downloads, in addition to downloading via the Wubi app about 3 times. I've tried it with the CD ISO for 386, and for AMD64, just for kicks. Reformatted the slave drive 2x, and I still do not like green eggs and ham. Since the instructions say not to use an alternate or DVD ISO, I have not tried those options, however.

---

### Post by ago on 2008-05-05
If you press ESC after "Ubuntu" at boot, what is your first item you see?

---

### Post by Rackham on 2008-05-05
After attempting to boot, and pushing Esc, I get this:

UBUNTU 8.04, KERNEL 2.6.24-16-GENERIC
UBUNTU 8.04, KERNEL 2.6.24-16-GENERIC (RECOVERY MODE)
UBUNTU 8.04, MEMTEST 86+

OTHER OPERATING SYSTEMS
WINDOWS NT/2000/XP
WINDOWS XP MEDIA CENTER EDITION

After I choose any of the Linux boot options, I get the following error 15 message:

FIND --SET ROOT /UBUNTU/DISKS/BOOT/VMLINUZ
ERROR 15: FILE NOT FOUND

---

### Post by Xerp on 2008-05-05
!! how do I delete duplicates :/

---

### Post by Xerp on 2008-05-05
If you're looking for a testing drive, then one possible way forward would be to use Virtual Box. You can then install Ubuntu as a virtual machine to play with :) No chance of an "error 15" there, as you'll be using a virtual drive...

---

### Post by tinybit on 2008-05-05
@ago

WUBILDR can be found&#65288;because it is booted&#65289;but /UBUNTU/DISKS/BOOT/VMLINUZ cannot be found. Possible reasons:

1. /UBUNTU/DISKS/BOOT/VMLINUZ is on a different drive than the one wubildr is on. A buggy BIOS might be able to read wubildr on one drive but not /UBUNTU/DISKS/BOOT/VMLINUZ on another drive.

2. /UBUNTU/DISKS/BOOT/VMLINUZ is on the same drive as wubildr is, but /UBUNTU/DISKS/BOOT/VMLINUZ is occupying disk sectors exceeding the 137G buggy BIOS limit.

So for maximum compatibility we need to place vmlinuz and initrd on the first drive(usually C:, the Windows "boot drive"), and not beyond 137G physically.

---

### Post by MetalMusicAddict on 2008-05-05
I'm betting that GRUB is on the other drive (not the one you installed to) and it's not pointing to where you installed it.

I get the error because I have installed GRUB to another drive than my OS drive before.

I would fix the MBR of the windows drive then pull it. Install to the drive you want and make sure GRUB goes to that drive. (If its the only drive it's a safe bet it will) Add back in the windows drive. Boot into linux and edit GRUB to point to the XP drive also.

Otherwise, I would just put a small partition on your windows drive and install to that.

---

### Post by Rackham on 2008-05-05
OK, I was under the impression that the Wubi app didn't require a new partition to install it.... in any event, I tried installing it to my C drive, even though that is absolutely not where I want it to be, and it still gave me error 15. I'll try the other suggestions in the morning. Thanks for the input though, I'll get back with an update.

---

### Post by Rackham on 2008-05-06
all the stuff mentioned above is on the proper drive, the wubildr, and the vmlinuz are all on the same disk.

I think, that it may be time to abandon this until the bugs are worked out. Thanks for all the help so far though,

---

### Post by ago on 2008-05-06
Try this [https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230](https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230)

---

### Post by ago on 2008-05-06
What version of Wubi did you use?

We do not use FIND --SET ROOT /UBUNTU/DISKS/BOOT/VMLINUZ in wubi 8.04
Also there is no /UBUNTU/DISKS/BOOT/VMLINUZ because the kernel is probably called vmlinuz-2.6.24-16-generic

Do you have some left overs from previous installations? Such as C:\menu.lst or C:\wubildr* or C:\grldr*? (that is in ANY drive).

---

### Post by Leonick on 2008-05-06
Instead of making an new thread ill post in here.

I tried the latest ubuntu beta on a virtual machine, now when the real release came i wanted to do a wubi install to be able to boot into ubuntu and use all my hardware which is a thing i have never done before.

So i downloaded the iso file and mounted it with Daemon Tools and ran wubi. Everything worked out fine in windows and i rebooted the machine. I booted in to ubuntu and it installed everything fine and rebooted now after completed installation i get the same arror already mentioned here.

Its installed on my C drive and i gave it 15gb.
Pressing esc after selecting ubuntu give the same as said on page one except i have two Windows XP Pro (wonder why??).

I have tried installing twice now, everything working fine untill its time for a real boot up.

---

### Post by ago on 2008-05-06
All of you with multiple harddisks: 

try this [https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230](https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230)

---

### Post by Leonick on 2008-05-06
And if i say i cant even find "root (" or "#groot" in that file?
(c:\ubuntu\disks\boot\grub\menu.lst)

---

### Post by ago on 2008-05-06
pls post c:\ubuntu\disks\boot\grub\menu.lst

---

### Post by Leonick on 2008-05-06
Though maybe it could be the "# root		(hd0,0)" and "# groot=(hd2,0)" parts?

---

### Post by ago on 2008-05-06
replace it with the following

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
# kopt=root=UUID=30AC7052AC701496 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=30AC7052AC701496 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=30AC7052AC701496 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Home Edition
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


```

---

### Post by Leonick on 2008-05-06
Thanks!
It works great now!

---

### Post by candtalan on 2008-05-06
One problem I have had with older PCs into which I had put larger modern hard drives into has been that the hard drive I had called for loading or booting was too large to be properly recognised by the older bios in the PC. 
I am not sure how this might impact into a wubi install.

good luck

---

### Post by Rackham on 2008-05-06
> **ago said:**
> What version of Wubi did you use?

We do not use FIND --SET ROOT /UBUNTU/DISKS/BOOT/VMLINUZ in wubi 8.04
Also there is no /UBUNTU/DISKS/BOOT/VMLINUZ because the kernel is probably called vmlinuz-2.6.24-16-generic

Do you have some left overs from previous installations? Such as C:\menu.lst or C:\wubildr* or C:\grldr*? (that is in ANY drive).

The most recent version. 8.04 - I've never run any other Linux installer on this machine, this was the first. So, if those files are not part of the installation package, or are not supposed to be created by the install, then there are other issues that need to be addressed.

---

### Post by ago on 2008-05-06
In 8.04 we use find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz

find --set-root /ubuntu/disks/boot/vmlinuz 

was used in 7.10...

Are you sure you have no left overs? 
Try to uninstall, delete any wubildr* file and menu.lst file from any drive and reinstall again. If it happens again please post /ubuntu/disks/boot/grub/menu.lst

---

### Post by tinybit on 2008-05-06
> **candtalan said:**
> One problem I have had with older PCs into which I had put larger modern hard drives into has been that the hard drive I had called for loading or booting was too large to be properly recognised by the older bios in the PC. 
I am not sure how this might impact into a wubi install.

good luck

The BIOS problem will have influence on the booting of all OSes including Windows.

Consider why Windows must be BOOTed on a primary partition(and even must on the first drive, the hd0) though it can be INSTALLed on a logical partition with its system in. The Windows installer will guarantee all sensitive boot files such as NTLDR/BOOTMGR be placed in a way that BIOS can easily access.

GRUB4DOS relies heavily on BIOS to access files. So the boot files that grub4dos needs to read should all be arranged properly beforehand.

---

### Post by digitalggs on 2008-07-08
I am also getting this error:

```

find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz

error: 15 file not found

```

installing Kubuntu KDE4
I downloaded the ISO directly since wubi could not download it. 
kubuntu-kde4-8.04.1-alternate-amd64.iso (705MB)

Using wubi installer Wubi-8.04.1-rev506.exe (958KB)

info at [https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230](https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230)
does not apply to me (except the last part but I do not have the option of installing to another part and chkdsk returns no errors)

I uninstalled adn tryed reinstalling, no joy..

I look in the ubuntu folder and I do not see e:/ubuntu/install/boot/vmlinuz (not sure if the file is supposed to be there or if it extracted fromt he ISO ?
```
CopyKernel isokernel=casper\vmlinuz, iso=E:\ubuntu\install\kubuntu-kde4-8.04.1-alternate-amd64.iso, cddrive=
```

I am not seeing anything wierd except some failed MD5 checks in teh wubi.log
Wubi-8.04.1-rev506.log:
```

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\!8420~1.@#&\LOCALS~1\Temp\nsx2F.tmp
detect_all
Parsing cmdline "E:\Wubi-8.04.1-rev506.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2046 MB
arch=amd64
DetectCD
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive E:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name __XP__; Max #/chars in vol name 1866764; Volume Serial # -400139543; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name G-Files_Prime; Max #/chars in vol name 1866768; Volume Serial # -469680397; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem E:
Drive & Path name 1712; Volume name The_Void; Max #/chars in vol name 1866772; Volume Serial # -334230898; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive E: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1427328; Volume name __XP__; Max #/chars in vol name 28; Volume Serial # -400139543; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = E:
FreeSpace in E: is 39934
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
IsBackupFolder E:\
Found BackupFolder E:\ubuntu-backup
GMT=-7
Country=US
Locale=en_US.UTF-8
TimeZone=America/Denver
Domain=localdomain
HostName=vzw_003
ComputerName=VZW_003
EnvUsername=!..@#&!
UserDomain=VZW_003
UserInfoName=!..@#&!
UserProfileFolder=C:\Documents and Settings\!..@#&!
UserProfileName=!..@#&! 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name __XP__; Max #/chars in vol name 1871860; Volume Serial # -400139543; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name G-Files_Prime; Max #/chars in vol name 1871864; Volume Serial # -469680397; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
IsValidFileSystem E:
Drive & Path name 1778; Volume name The_Void; Max #/chars in vol name 1871868; Volume Serial # -334230898; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive E: has valid filesystem NTFS
Adding drive E:
Drive list = C:|D:|E:
ChangeInstallationDrive to E:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=E:\ubuntu-backup\kubuntu-kde4-8.04.1-alternate-amd64.iso
      ExtractIsoInfo
      C:\DOCUME~1\!8420~1.@#&\LOCALS~1\Temp\nsx2F.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\!8420~1.@#&\LOCALS~1\Temp E:\ubuntu-backup\kubuntu-kde4-8.04.1-alternate-amd64.iso
      IsValid Kubuntu-KDE4 8.04.1 "Hardy Heron" - Release amd64 (20080701.2)
      cdversion=8.04.1 cddistro=Kubuntu-KDE4 cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080701.2 
      GetDistroInfo distrofullname=Kubuntu-KDE4-amd64 distro= cddistro=Kubuntu-KDE4 cdarch=amd64 arch=amd64
      ->metalinkURL=http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/kubuntu-kde4-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Kubuntu-KDE4 8.04.1 "Hardy Heron" - Release amd64 (20080701.2)
AddDistroToList Ubuntu-i386
AddDistroToList Ubuntu-amd64
AddDistroToList Kubuntu-i386
AddDistroToList Kubuntu-amd64
AddDistroToList Kubuntu-KDE4-i386
AddDistroToList Kubuntu-KDE4-amd64
AddDistroToList Xubuntu-i386
AddDistroToList Xubuntu-amd64
DistroList = Ubuntu|Kubuntu|Kubuntu-KDE4|Xubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Kubuntu-KDE4-amd64 distro=Kubuntu-KDE4 cddistro=Kubuntu-KDE4 cdarch=amd64 arch=amd64
      ->metalinkURL=http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/kubuntu-kde4-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Kubuntu-KDE4
Changing icon to Kubuntu-KDE4.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Kubuntu-KDE4-amd64 distro=Kubuntu-KDE4 cddistro=Kubuntu-KDE4 cdarch=amd64 arch=amd64
      ->metalinkURL=http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/kubuntu-kde4-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
CreateInstallationFolders
MakeUninstall
Created E:\ubuntu\Uninstall-Kubuntu-KDE4.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=E:\ubuntu-backup\kubuntu-kde4-8.04.1-alternate-amd64.iso
      ExtractIsoInfo
      C:\DOCUME~1\!8420~1.@#&\LOCALS~1\Temp\nsx2F.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\!8420~1.@#&\LOCALS~1\Temp E:\ubuntu-backup\kubuntu-kde4-8.04.1-alternate-amd64.iso
      IsValid Kubuntu-KDE4 8.04.1 "Hardy Heron" - Release amd64 (20080701.2)
      cdversion=8.04.1 cddistro=Kubuntu-KDE4 cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080701.2 
      GetDistroInfo distrofullname=Kubuntu-KDE4-amd64 distro=Kubuntu-KDE4 cddistro=Kubuntu-KDE4 cdarch=amd64 arch=amd64
      ->metalinkURL=http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/kubuntu-kde4-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Kubuntu-KDE4 8.04.1 "Hardy Heron" - Release amd64 (20080701.2)
Using E:\ubuntu-backup\kubuntu-kde4-8.04.1-alternate-amd64.iso
      GetDistroInfo distrofullname=Kubuntu-KDE4-amd64 distro=Kubuntu-KDE4 cddistro=Kubuntu-KDE4 cdarch=amd64 arch=amd64
      ->metalinkURL=http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/kubuntu-kde4-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Kubuntu-KDE4-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/kubuntu-kde4-8.04.1-desktop-amd64.metalink
get_md5 http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/kubuntu-kde4-8.04.1-desktop-amd64.metalink
Downloading: trymefirst= url=http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/MD5SUMS-metalink.gpg md5=
Download status=success:E:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/MD5SUMS-metalink md5=
Download status=success:E:\ubuntu\install\MD5SUMS-metalink
      Verifying signature E:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: Signature made 07/03/08 12:46:47 US Mountain Standard Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing E:\ubuntu\install\MD5SUMS-metalink
Could not find any md5
Trying remote metalink2: http://cdimage.ubuntu.com/kubuntu-kde4/hardy/daily-live/current/hardy-desktop-amd64.metalink
get_md5 http://cdimage.ubuntu.com/kubuntu-kde4/hardy/daily-live/current/hardy-desktop-amd64.metalink
Downloading: trymefirst= url=http://cdimage.ubuntu.com/kubuntu-kde4/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=The requested URL returned error: 404
Error downloading http://cdimage.ubuntu.com/kubuntu-kde4/hardy/daily-live/current/MD5SUMS-metalink.gpg, The req
Using E:\ubuntu-backup\kubuntu-kde4-8.04.1-alternate-amd64.iso but skipping checksum since no metalink file could be found
ISO file kubuntu-kde4-8.04.1-alternate-amd64.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=E:\ubuntu\install\kubuntu-kde4-8.04.1-alternate-amd64.iso, cddrive=
Extracting with 7z kernel/initrd from E:\ubuntu\install\kubuntu-kde4-8.04.1-alternate-amd64.iso
UncompressFilesPriorInstall
Drive & Path name gpgv: Signature made 07/03/08 12:46:47 US Mountain Standard Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; Volume name The_Void; Max #/chars in vol name ; Volume Serial # -334230898; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive E: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst E:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
EditBootIni C:\boot.ini
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
Drive & Path name gpgv: Signature made 07/03/08 12:46:47 US Mountain Standard Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; Volume name The_Void; Max #/chars in vol name ; Volume Serial # -334230898; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive E: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=E:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=E:\ubuntu\disks\home.disk size=0
AllocFile filename=E:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
Installation completed successfully!


```

I tryed installing Kubuntu (KDE3.5) using manually downloaded ISO
kubuntu-8.04.1-dvd-amd64.iso
and get the same thing..

am I missing something?:popcorn:

---

### Post by digitalggs on 2008-07-08
here is the contents of the /ubuntu folder. I removed teh .disk and .iso files for obvious reasons.

---

### Post by ago on 2008-07-08
Hmm the metalink for amd64 is missing for Kubuntu... That is a server issue

But seems ok now [http://releases.ubuntu.com/kubuntu/8.04.1/MD5SUMS-metalink](http://releases.ubuntu.com/kubuntu/8.04.1/MD5SUMS-metalink)

You might have hit the server while they were updating the metalinks

Be aware that the URLs for the KDE mirrors are incorrect at the moment.

---

