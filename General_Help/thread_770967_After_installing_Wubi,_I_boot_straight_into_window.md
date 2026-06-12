---
title: "After installing Wubi, I boot straight into windows vista as normal."
date: 2008-04-27
forum: General Help
---

### Post by TheOhGodOfHangovers on 2008-04-27
Help,

Completely new to ubuntu, so when a friend told me i didn't need to partition my HD i could just get wubi and try ubuntu out i jumped at it.

First started yesturday by running and downloading everything through wubi.exe but that became unresponsive during dowloading and installatoin and at various other times (i must have tried it 10 times or more)

So today i followed advice and downloaded the ISO and wubi.exe seperately and placed them in the same folder and installed it this way by running wubi.exe. This appears to have worked first time around, although when i was asked to reboot to finish the installation my computer booted as normal straight into windows - without the option of chosing ubuntu. I rebooted a couple more times and the same thing has happened each time. 

What is happening?

Any help would be much appreciated, as i mentoioned though i'm completely new to all this. Thanks.


By the way i'm running Windows VISTA on a relatively new pc with:

Intel Core 2 Quad Q6600
nVidia 8800 GTX
Two seperare 500GB hard drives (at the moment the second one of these is blank (D:)) EVERYTHING is on C:

---

### Post by ago on 2008-04-27
Use easybcd to check the boot menu of Vista.
Attach the log in your user temp folder (%temp%)

---

### Post by TheOhGodOfHangovers on 2008-04-28
Easy BCD says:

There is one entry in the Vista Bootloader.
Bootloader Timeout: 10 seconds.
Default OS: Microsoft Windows Vista

Entry #1

Name:  Microsoft Windows Vista
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

---

### Post by ago on 2008-04-28
We know of a few instances whereby it is not possible to edit the Vista bootloader, but were not able to understand why. Will call in easybcd author.

---

### Post by TheOhGodOfHangovers on 2008-04-28
OK thanks, i really appreciate this.

---

### Post by Computer Guru on 2008-04-28
Ago, those previous errors that some users encountered with bcdedit were more as a result of a broken bootloader than an actual bug - I don't know if this is the issue with TheOhGodOfHandovers or not, but let's find out :D

TOGOH: Can you please do EasyBCD | Diagnostics Center | Copy Debug Data then paste the contents of the clipboard here in a reply?

---

### Post by TheOhGodOfHangovers on 2008-04-28
OK :

There is one entry in the Vista Bootloader.
Bootloader Timeout: 10 seconds.
Default OS: Microsoft Windows Vista

Entry #1

Name:  Microsoft Windows Vista
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

...And That's it

---

### Post by TheOhGodOfHangovers on 2008-04-28
This is copied from View Settings | Detailed (Debug Mode) :

Windows Boot Manager
--------------------
identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
default                 {34a3a529-d5b5-11dc-be4a-001d60b2cf84}
resumeobject            {34a3a52a-d5b5-11dc-be4a-001d60b2cf84}
displayorder            {34a3a529-d5b5-11dc-be4a-001d60b2cf84}
toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout                 10

Windows Boot Loader
-------------------
identifier              {34a3a529-d5b5-11dc-be4a-001d60b2cf84}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  en-US
inherit                 {6efb52bf-1766-41db-a6b3-0ee5eff72bd7}
osdevice                partition=C:
systemroot              \Windows
resumeobject            {34a3a52a-d5b5-11dc-be4a-001d60b2cf84}
nx                      OptIn

Hope that's helpful in some way

thanks again

---

### Post by Computer Guru on 2008-04-28
OK, thanks for that, TOGOH.

Ago, it looks like WubiBCD was never run? Unlike in other cases where the "device" property would be missing, no sign of Wubi is present in the bootloader.

TGOH:
You should be able to add Wubi to the Vista bootloader with EasyBCD.
Just go to EasyBCD | Add/Remove Entries | Linux 
Select "Wubi" from the "Type" drop-down list, give it a nice name, and press "Add Entry"

Confirm that it's appeared in the list of available OSes, then reboot to give it a test.

---

### Post by TheOhGodOfHangovers on 2008-04-28
OK, i did everything you suggested and the Ubuntu appeared in the list of available OSs. 
When i rebooted i saw the widows bootloader screen for the first time! i click on ubuntu and got a black screen with the following on:

*(might have been GRUB4DUS - i can't read my handwriting!)*

GRUB4DOS 0.4.3 2007-06-14, Memory: 636k / 3325M, CodeEnd: 0x3EF2C
[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else Tab lists the possible completions of a divice/filename]

grub>

I pressed TAB and one of the possible commands was boot so i tried entering that and i came back with

grub> Error 8: Kernel must be loaded before booting

At which point ESC was doing nothing so i swithched off and chose vista again.

Really, getting confused now.. is it worth me giving up on Wubi and just partitioning my Hard drive or do you thing this can be sorted?

Again, i really appreciate all your help.

TOGOH

---

### Post by ago on 2008-04-28
Can you please provide the Wubi log in your user temp folder (%temp%)

---

### Post by kram87 on 2008-04-28
I'm having exactly the same problems as the original poster.  I tried using easybcd and adding wubi to my bootloader and got the same prompt with the same errors when trying to use the boot command.  Anyway, heres my log from my temp folder.  I starred out my name fyi.



============ Installer ============
PLUGINSDIR=C:\Users\*****\AppData\Local\Temp\nsw5B8F.tmp
detect_all
Parsing cmdline "C:\Users\*****\Desktop\Wubi-8.04.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2037 MB
arch=i386
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1711; Volume name System; Max #/chars in vol name 3036672; Volume Serial # 211745295; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2544104; Volume name System; Max #/chars in vol name 56; Volume Serial # 211745295; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 32146
DetectBackupFolder
IsBackupFolder C:\
GMT=-7
Country=US
Locale=en_US.UTF-8
TimeZone=America/Denver
Domain=localdomain
HostName=*****
ComputerName=*****
EnvUsername=*****
UserDomain=*****
UserInfoName=*****
UserProfileFolder=C:\Users\*****
UserProfileName=*****
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1773; Volume name System; Max #/chars in vol name 3081272; Volume Serial # 211745295; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
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
      Is Valid CD D:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Checking/Downloading Ubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink](http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink)
get_md5 [http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink](http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg md5=
Download status=couldn't connect to host
Error downloading [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg), couldn'
Trying remote metalink2: [http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: Signature made 04/22/08 18:03:44 Pacific Daylight Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS-metalink
Found md5 54e601083de40180b539f9e24c613de9
Downloading: trymefirst= url=http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.metalink md5=54e601083de40180b539f9e24c613de9
Download status=success:C:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\hardy-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name C:\ubuntu\install\hardy-desktop-i386.iso; Volume name System; Max #/chars in vol name ; Volume Serial # 211745295; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
C:\Users\*****\AppData\Local\Temp\nsw5B8F.tmp\wubibcd.exe 
 1:0 
 2:Operation completed successfully. New ID is {1dbe8c2d-0b39-11dd-81dd-b2149d665bd9}
 
 3:HDD 
 4:3
vistaBootDriveCode = {1dbe8c2d-0b39-11dd-81dd-b2149d665bd9} <=> {1dbe8c2d-0b39-11dd-81dd-b2149d665bd9}
vistaBootDriveCode {1dbe8c2d-0b39-11dd-81dd-b2149d665bd9}
Drive & Path name /Users/*****; Volume name System; Max #/chars in vol name C:\ubuntu\install\hardy-desktop-i386.iso; Volume Serial # 211745295; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
Installation completed successfully!

---

### Post by ago on 2008-04-29
Strange the vista code is there as far as I can see

---

### Post by kram87 on 2008-04-29
So I just reinstalled it and now it works fine as far as I can tell.  Weird.

---

### Post by TheOhGodOfHangovers on 2008-04-29
I decided to do as the previous poster and reinstall everything, and it all seems to be working fine now

I have no idea what was wrong but it seems to be OK now

In easyBCD and on windows bootloader there is still an entry for the previous install, how do i get rid of this?

thanks

---

### Post by ago on 2008-04-29
Can't you change that with EasyBCD?

---

### Post by Computer Guru on 2008-05-03
He should be able to, from the "Add/Remove Entries" page.

---

### Post by afroxav on 2008-11-27
When I reinstall, I get the same error over and over... here is my log ```
============ Installer ============
PLUGINSDIR=C:\Users\****\AppData\Local\Temp\nssEB88.tmp
detect_all
Parsing cmdline "C:\Users\****\AppData\Local\Temp\7zSE87A.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=766 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.10 "Intrepid Ibex" - Release i386 (20081029.5)
      cdversion=8.10 cddistro=Ubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release cdbuild=20081029.5 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Ubuntu 8.10 "Intrepid Ibex" - Release i386 (20081029.5)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive F:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1720; Volume name ****; Max #/chars in vol name 3134184; Volume Serial # -722175485; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1720; Volume name ****; Max #/chars in vol name 3134188; Volume Serial # -1004281819; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1720; Volume name ****; Max #/chars in vol name 3134196; Volume Serial # 1178277023; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2760680; Volume name ****; Max #/chars in vol name 68; Volume Serial # -722175485; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 98228
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
IsBackupFolder F:\
GMT=-****
Country=****
Locale=****
TimeZone=****
Domain=****
HostName=****
ComputerName=****
EnvUsername=****
UserDomain=****
UserInfoName=****
UserProfileFolder=C:\Users\****
UserProfileName=**** 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1786; Volume name ****; Max #/chars in vol name 2912984; Volume Serial # -722175485; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1786; Volume name ****; Max #/chars in vol name 2912988; Volume Serial # -1004281819; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
IsValidFileSystem F:
Drive & Path name 1786; Volume name ****; Max #/chars in vol name 2912996; Volume Serial # 1178277023; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Adding drive F:
Drive list = C:|D:|F:
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_CA.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
CreateInstallationFolders
MakeUninstall
Created D:\ubuntu\Uninstall-Ubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.10 "Intrepid Ibex" - Release i386 (20081029.5)
      cdversion=8.10 cddistro=Ubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release cdbuild=20081029.5 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Ubuntu 8.10 "Intrepid Ibex" - Release i386 (20081029.5)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=c451e4a0b734d483e35d47df928d5f0a
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO D:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Checking/Downloading Ubuntu-8.10
Skipmd5 is true, using D:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=D:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from D:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name ****; Max #/chars in vol name ****; Volume Serial # -1004281819; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive D: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst D:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
Drive & Path name success; Volume name ****; Max #/chars in vol name ****; Volume Serial # -1004281819; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive D: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=D:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=D:\ubuntu\disks\home.disk size=0
AllocFile filename=D:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=640 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!

```

Here is my bootloader before manual changes : ```
There is a total of 1 entry listed in the Vista Bootloader.
Bootloader Timeout: 30 seconds.
Default OS: 

Entry #1

Name:  Microsoft Windows Vista
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows
```
Here is after:```
There are a total of 2 entries listed in the Vista Bootloader.
Bootloader Timeout: 30 seconds.
Default OS: 

Entry #1

Name:  Microsoft Windows Vista
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #2

Name:  Ubuntu 8.10 Intrepid Ibex
BCD ID:  {5ef284a4-bcb5-11dd-b534-00192151ad1c}
Drive:  C:\
Bootloader Path:  \NST\NeoGrub.mbr
```

---

### Post by Swagman on 2008-11-28
This  query is just for my own knowledge.

It would appear from the above posts that people are downloading wubi seperately and trying to install from that ?

Why ? Is there a particular reason ?

Why are they not simply booting into windows and then inserting the Ubuntu Cd (previously burnt ISO image) ?

The popup asks how they would like to install it. If The user chooses "install into Windows" (cant remember actual wordage) then **THAT** is wubi. No need to go get anything different.


Am I missing something here. Please enlighten me as I only want to look a muppet once if I can help it !!

---

### Post by slmouradian on 2008-11-28
WUbI can use a CD or an ISO.

have a look at [http://wubi-installer.org/faq.php]("http://wubi-installer.org/faq.php") for more.

---

### Post by Swagman on 2008-11-28
> **slmouradian said:**
> WUbI can use a CD or an ISO.

have a look at [http://wubi-installer.org/faq.php]("http://wubi-installer.org/faq.php") for more.

Ok .. So basically it means you don't have to burn an ISO to disk.

Personally I'd still prefer the disk.

Thanks for clearing that up.

---

### Post by ago on 2008-12-01
Put /ubuntu/winboot/menu.lst in the root directory and make sure that grub4dos uses that menu.lst

---

