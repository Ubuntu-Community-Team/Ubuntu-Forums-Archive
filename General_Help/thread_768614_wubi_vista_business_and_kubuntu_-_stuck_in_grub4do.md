---
title: "wubi vista business and kubuntu - stuck in grub4dos prompt"
date: 2008-04-26
forum: General Help
---

### Post by rb31415926 on 2008-04-26
Hi,

I downloaded the release iso for kubuntu, checked md5 sum, and burnt the cd, ran wubi in windows vista business, installed seemed to work fine, ejected the CD and said it needed to reboot. Upon reboot, I get the menu to select Vista or Kubuntu. If I select Kubuntu, instead of going to the OS, I get stuck in the follow screen, with a command prompt:  

GRUB4DOS 0.4.3 2008-04-22, Memory:639/894M, CodeEnd: 0x41228[ Minimal BASH-like line editing supported. For the..... ...device/filename.]

grub>_

I only have one hard drive (C: under windows vista busines) and that is where I installed from wubi installer. My machine is a Celeron 754 3000 with a A-Rock Vista MB, 1GB DDR ram, 1x250GB HD, my vista has all the latest patches EXCEPT for SP1 that is available in windows updates but I haven't yet installed.

Any ideas?

Thanks

---

### Post by ago on 2008-04-26
I haven't seen this one before. I have asked grub4dos devs.

---

### Post by tinybit on 2008-04-26
wubi have ever used the grub4dos-2008-04-22 version? I am not sure and in doult.

If grub4dos cannot find the menu.lst file, it will show you the grub prompt.

Where is your menu.lst file? Can you access the menu.lst file from the grub commandline, e.g., by using the cat command and the TAB-auto-command-line-completion?

If you cannot, then it is likely the menu.lst file is located exceeding the 137G BIOS limit.

Some buggy BIOSes have no ability to access the sectors outside the 137G limit. So the developers should write a tool to defrag or move the crucial boot files onto the beginning 137G of the disk, so that grub4dos can find them.

---

### Post by ago on 2008-04-26
Tinybit, wubildr (grldr) has an embedded menu that looks for the following config files:

/ubuntu/disks/boot/grub/menu.lst
/ubuntu/install/boot/grub/menu.lst

At the grub prompt please use the "find" command to look for the files above. Could it be that a local menu.lst is overriding?

---

### Post by tinybit on 2008-04-26
> 
Could it be that a local menu.lst is overriding?


this is possible.

grldr firstly will look for /menu.lst, i.e., in  the root dir. if and only if that failed, the embedded pre-set menu gains control.

The string "/menu.lst" should appear in the second sector of the grldr file. If you change this string to an invalid file name such as "/." or "/...." or even "[////]", then the embedded pre-set menu will always gain control.

---

### Post by rb31415926 on 2008-04-26
Thanks for the quick reply!

1)I ran OO-Defrag in Vista to move most of the files (except locked ones) to the beginning of the disk but it did not fix the issue. 

2)Still in Vista, I did a search on menu.lst and found a file by that name in two locations:

c:\ubuntu\winboot\menu.ls
c:\ubuntu\install\boot\grub\menu.ls

Files are different in size, let me know if it helps if I copy their content here.

3)Finally, rebooted, tried to go to kubuntu, got to the grub> prompt, using find was able to find following 2 files:

/ubuntu/install/boot/grub/menu.lst
/ubuntu/winboot/menu.lst

did not find following file:

/ubuntu/disks/boot/grub/menu.lst

ShouldI delete (rename?) one of the menu.lst files?

Thanks

---

### Post by ago on 2008-04-27
You should see either 

c:\ubuntu\winboot\menu.ls

OR

c:\ubuntu\install\boot\grub\menu.ls

But not both together.

Also make sure that there is no menu.lst file in C:\

---

### Post by ago on 2008-04-27
tinybit, here is the embedded menu.lst

```

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 3
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

```

Question: The above will normally run configfile, setting root. When the new configfile is loaded, is the root reset? If it is not, I can simply use:

root ()/realative/path  #without setting the root

In fact keeping the same root when running configfile would make everything easier...

---

### Post by tinybit on 2008-04-27
The configfile command WILL set the root device.

```

configfile MENUFILE

```

If the MENUFILE has absolute path, that is, with a leading "(device)", then the root will become (device), that is, the current root will switch to (device).

If the MENUFILE has not a leading "(device)", then this implies the "(device)" is just the current root device. In this case, you may think that the current root will not change across the configfile command.

In fact, the current root device will always switch to the device that the MENUFILE is on.

In the current implementation, the "relative path" will be preserved. This effect might not be what you want it to be. So you need to (re-)define it in the MENUFILE by using "root ()/.../..." or such, or simply reset the relative path by using "root ()".

There is an "fallback" issue with your config above. It is a serious problem. The config should change to this one(certainly the comments added by me should be deleted for a real preset menu):

```

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst # this is entry number 0, the default entry.
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst # this is entry number 1 for "falback 1" to goto
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst # this is entry number 2 for "falback 2" to goto
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst # this is entry number 3 for "falback 3" to goto
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst # this is entry number 4 for "falback 4" to goto
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline # this is entry number 5 for "falback 5" to goto
	commandline

title reboot
	reboot

title halt
	halt

```

The "fallback" actually means "on error goto". So "fallback 1" means "on error goto 1" , "fallback 2" means "on error goto 2", etc.

Both "fallback" without an entry number and "fallback -1" will clear the fallback entries, which means "on error pause and display a message and then return back to main menu".

Because fallback is something like a "goto", endless loop could occur. So be careful.

---

### Post by rb31415926 on 2008-04-27
I tried removing (renaming to .old)

c:\ubuntu\winboot\menu.lst

and it still went to the same grub> prompt.

I then readded the file above and removed (renamed to .old)

c:\ubuntu\install\boot\grub\menu.lst

and I now upon reboot and selecting kubuntu I get:


find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
error 15: file not found
press any key to continue...

Hit enter, and get a menu with several find options, as well as commandline, reboot and halt. All the find options when selected come back with error15 (as expected since I don't have this file).

---

### Post by ago on 2008-04-27
Leave c:\ubuntu\install\boot\grub\menu.lst
At the prompt type 

find --set-root /ubuntu/install/boot/grub/menu.lst
configfile /ubuntu/install/boot/grub/menu.lst

There should be a countdown, hit esc and select the first option

---

### Post by tinybit on 2008-04-27
@ago

should use slash instead of backslash.

---

### Post by rb31415926 on 2008-04-27
Ok, went to grub> promp, typed:

grub>find --set-root /ubuntu/install/boot/grub/menu.lst

got:

(hd0,0)
Filesystem type is ntfs, partition type 0x7
>grub_

Then typed:
grub>configfile /ubuntu/install/boot/grub/menu.lst
Hit enter, something flashes by really fast, can't read it, and I land back at the grub prompt:

GRUB4DOS 04.4.3 2008-04-22 Memory.... ...device/filename]
grub>_

By the way my HD is a SATA HD, not sure if it makes any difference.

I pasted my menu.lst below:

---------------------------------------------------------------------------

#This file is modified at runtime by bootmenu.nsh

debug off
hiddenmenu 
timeout		5
default		0

title Start installer in normal mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in safe graphic mode (only if you have display problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet xforcevesa boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer with ACPI workarounds (only if you have ACPI problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   acpi=off noapic nolapic
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in verbose mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
initrd /ubuntu/install/boot/initrd.gz
boot

title Read-Only Demo (Live CD Desktop)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz iso-scan/filename=/ubuntu/install/installation.iso quiet splash boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
initrd /ubuntu/install/boot/initrd.gz
boot

---

### Post by tinybit on 2008-04-27
Can you type in these commands at the grub prompt and see if it could go?

```

find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz

kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --

initrd /ubuntu/install/boot/initrd.gz

boot

```

This is exactly the content of your first entry shown in floor #13

Note that those are 4 lines:

find ....
kernel ...
initrd ...
boot

The kernel line is very long. don't split it into several lines.

---

### Post by ago on 2008-04-28
You have to type: 
```

find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz

kernel /ubuntu/install/boot/vmlinuz iso-scan/filename=/ubuntu/install/installation.iso boot=casper ro 

initrd /ubuntu/install/boot/initrd.gz

boot

```
I have shortened the kernel line, the above should boot into the Live CD read only demo (to install you need the full line.

---

### Post by rb31415926 on 2008-04-28
OK, I entered the 4 lines in the message #14 (with the long kernel line) and was able to get to the install program.

In step 2 of 6, selected the city and hit ->Forward, after about 60 seconds got error below:

"Partman failed with exit code 10. further information may be found in /var/log/syslog. do you want to try running this step again before continuing? If you do not, your instalation may fail entirely or may be broken."

looking at the file in the message I can see the following line:

Apr 28 23:53:11 ubuntu: ubiquity: cat:
/var/lib/partman/devices/=dev=sda/device: no such file or directory

---

### Post by ago on 2008-04-29
Try with a clean installation. Uninstall, run chkdsk /r, defragment, reinstall, edit preseed, and reboot

---

### Post by kram87 on 2008-04-29
I thought I'd chime in since I have the same problems as the original poster.  I just tried the 4 commands listed earlier at the grub prompt and now I'm sitting at another prompt.  BusyBox v1.1.3 to be exact.  A lot of stuff happened before I got there though.  Loading stuff of some kind, it went too fast for me to read it though.  The prompt looks like so:
         
         (initramfs)

Any ideas?

---

### Post by tinybit on 2008-04-29
> 
Then typed:
grub> configfile /ubuntu/install/boot/grub/menu.lst
Hit enter, something flashes by really fast, can't read it, and I land back at the grub prompt:

GRUB4DOS 04.4.3 2008-04-22 Memory.... ...device/filename]
grub>_


BIOS 137G limit(only for buggy bioses) could cause various problems.

The filename "/ubuntu/install/boot/grub/menu.lst" itself can be accessed normally, but the contents seem to be unaccessible(due to 137G limit or another unknown reason). Can you please print it in this way:

```

cat  /ubuntu/install/boot/grub/menu.lst

```

---

### Post by ago on 2008-04-29
> **kram87 said:**
> I thought I'd chime in since I have the same problems as the original poster.  I just tried the 4 commands listed earlier at the grub prompt and now I'm sitting at another prompt.  BusyBox v1.1.3 to be exact.  A lot of stuff happened before I got there though.  Loading stuff of some kind, it went too fast for me to read it though.  The prompt looks like so:
         
         (initramfs)

Any ideas?

Well it means Linux loads at least. It could be that you did a typo. Try copying c:\ubuntu\winboot\menu.lst to C:\ and booting normally.

See tinybit post as well.

---

### Post by redblue123 on 2008-05-01
I'm having the same issues. Installing out of the box, it boots to grub4dos. I have 2 versions of menu.lst. One is the same as posted in #8.  The other is 0 bytes.

Changing menu.lst to the version in #9 results in a blank screen in which I can barely see what looks like cmain() flashing.

Creating a /menu.lst to with the first 10 or so lines of #13 boots to BusyBox (I cut/pasted, so no typos).

This is ubuntu hardy heron, trying both 386 and 64 versions.  I'm running XP Sp3 on an up to date notebook, so I doubt there would be any buggy bios issues.

---

### Post by ago on 2008-05-01
There should be no menu.lst as #8 and #9 orther than in c:\ubuntu\winboot\menu.lst

You should also have either

c:\ubuntu\install\boot\grub\menu.lst

or

c:\ubuntu\disks\boot\grub\menu.lst

---

### Post by redblue123 on 2008-05-01
c:\ubuntu\winboot\menu.lst is identical to the menu.lst shown in post #8

c:\ubuntu\install\boot\grub\menu.lst is 0 bytes

c:\ubuntu\disks\boot\grub\ is an empty directory

When I boot to ubuntu, I get the grub4dos prompt.

---

### Post by ago on 2008-05-01
c:\ubuntu\install\boot\grub\menu.lst shouldn't be 0 bytes

Maybe try to uninstall and reinstall and please post the log in your user temp folder.

---

### Post by redblue123 on 2008-05-01
```
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\MyName\LOCALS~1\Temp\nsnB.tmp
detect_all
Parsing cmdline Wubi-8.04.exe 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1049 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 1865344; Volume Serial # -57653788; Max 

#/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1415272; Volume name ; Max #/chars in vol name 13; Volume Serial # -57653788; Max 

#/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 

2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 132659
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=MyComputer
ComputerName=MyComputer
EnvUsername=MyName
UserDomain=MyComputer
UserInfoName=MyName
UserProfileFolder=C:\Documents and Settings\MyName
UserProfileName=MyName 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1773; Volume name ; Max #/chars in vol name 1873872; Volume Serial # -57653788; Max 

#/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\temp\ubuntu-8.04-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\MyName\LOCALS~1\Temp\nsnB.tmp\7z.exe e -y -i!.disk\info 

-oC:\DOCUME~1\MyName\LOCALS~1\Temp C:\temp\ubuntu-8.04-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release 

cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Ubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=C:\temp\ubuntu-8.04-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\MyName\LOCALS~1\Temp\nsnB.tmp\7z.exe e -y -i!.disk\info 

-oC:\DOCUME~1\MyName\LOCALS~1\Temp C:\temp\ubuntu-8.04-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release 

cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
Copying C:\temp\ubuntu-8.04-desktop-i386.iso -> C:\ubuntu\install\ubuntu-8.04-desktop-i386.iso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Checking/Downloading Ubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
get_md5 http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.
gpgv: Signature made 04/24/08 03:37:24 Eastern Daylight Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS-metalink
Found md5 22eefa07792160d5b0f398024b397349
Downloading: trymefirst=C:\ubuntu\install\ubuntu-8.04-desktop-i386.iso 

url=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink md5=22eefa07792160d5b0f398024b397349
Download status=success:C:\ubuntu\install\ubuntu-8.04-desktop-i386.iso
ISO file ubuntu-8.04-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\ubuntu-8.04-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\ubuntu-8.04-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name C:\ubuntu\install\ubuntu-8.04-desktop-i386.iso; Volume name ; Max #/chars in vol name ; 

Volume Serial # -57653788; Max #/chars in dir/file names 255; File System Flags 459007; File System Type 

NTFS; File System Name Size 
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
Drive & Path name C:\ubuntu\install\ubuntu-8.04-desktop-i386.iso; Volume name ; Max #/chars in vol name ; 

Volume Serial # -57653788; Max #/chars in dir/file names 255; File System Flags 459007; File System Type 

NTFS; File System Name Size 
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
Installation completed successfully!
```

---

### Post by ago on 2008-05-02
The log looks fine, I will have to add more logging to the next build. 

Please try with a clean installation, uninstalling running chkdsk /r and reinstalling. If c:\ubuntu\install\boot\grub\menu.lst is empty please post a bug in launchpad [https://bugs.launchpad.net/wubi](https://bugs.launchpad.net/wubi) and I will follow up from there.

---

### Post by redblue123 on 2008-05-02
Done

---

### Post by ago on 2008-05-02
thx, keep an eye there I will provide a build this w/e with more logging to try to understand the issue.

---

### Post by redblue123 on 2008-05-02
In the meanwhile, I decided to try running Hardy Heron through wubi, so I used this menu.lst:

```

timeout 10
default 0

title Test
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz iso-scan/filename=/ubuntu/install/ubuntu-8.04-desktop-i386.iso boot=casper console-setup/variantcode= --
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in normal mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.04-desktop-i386.iso automatic-ubiquity noprompt boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --
initrd /ubuntu/install/boot/initrd.gz
boot

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

```

Test worked to boot ubuntu and I had access to my whole HDD through /isodevice (/host did not exist).  However, I could not save any settings.  (adding 'persistent' did not help)

Install failed at the second step with Partman exit code 10, see /var/log/syslog.  zipped syslog is attached.

Any interim suggestions for fixing any these?  

thanks

---

### Post by redblue123 on 2008-05-02
Threatfire, an antivirus program, was interfering with installation.  When I deactivated it, all proceeded normally.

---

