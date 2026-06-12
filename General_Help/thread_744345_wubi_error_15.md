---
title: "wubi error 15"
date: 2008-04-03
forum: General Help
---

### Post by seamustry on 2008-04-03
i installed ubuntu 8.04 beta today using wubi-8.04-beta-rev474

i get this error when i select ubuntu to boot into:

find  --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz

Error 15: file not found

Press any key to continue...

i have uninstalled and reinstalled but i get same exact error.

only have one hard disk and one partition...what to do?

thanks  :mad:

---

### Post by ago on 2008-04-03
can you see /ubuntu/install/boot/vmlinuz?

---

### Post by seamustry on 2008-04-03
hmm...i don't see what you're saying...can i see it where?

thanks for the reply though :)

---

### Post by ago on 2008-04-03
c:\ubuntu\install\boot\vmlinuz

Assuming you installed on C:

---

### Post by seamustry on 2008-04-03
no...my computer has the following:

c:\ubuntu\install\boot and then there is a folder called grub which contains menu.lst

i can't find vmlinuz anywhere either...what could be the problem?

---

### Post by ago on 2008-04-03
Open windows explorer
Type %temp%
There should be a wubi log, pls post it here.

---

### Post by seamustry on 2008-04-03
this is the log:

```

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\admin\LOCALS~1\Temp\nse2.tmp
detect_all
Parsing cmdline "C:\Wubi-8.04-beta-rev474.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
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
Drive & Path name 1702; Volume name ; Max #/chars in vol name 1787832; Volume Serial # 7690455; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # 7690455; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in C: is 14303
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=comp
ComputerName=COMP
EnvUsername=admin
UserDomain=COMP
UserInfoName=admin
UserProfileFolder=C:\Documents and Settings\admin
UserProfileName=admin 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\admin\LOCALS~1\Temp\nsz4.tmp
detect_all
Parsing cmdline "C:\Wubi-8.04-beta-rev474.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
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
Drive & Path name 1702; Volume name ; Max #/chars in vol name 1834328; Volume Serial # 7690455; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # 7690455; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in C: is 14300
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=comp
ComputerName=COMP
EnvUsername=admin
UserDomain=COMP
UserInfoName=admin
UserProfileFolder=C:\Documents and Settings\admin
UserProfileName=admin 
ShowMainPage
Making drive list
Drive & Path name 1742; Volume name ; Max #/chars in vol name 1833288; Volume Serial # 7690455; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 8
PopulateDistroList
DetectIso
      IsValidIso ispoath=\ubuntu-8.04-beta-alternate-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\admin\LOCALS~1\Temp\nsz4.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\admin\LOCALS~1\Temp \ubuntu-8.04-beta-alternate-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 4
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Ubuntu.exe
Created C:\WINDOWS\Uninstall-Ubuntu.exe
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
      IsValidIso ispoath=\ubuntu-8.04-beta-alternate-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\admin\LOCALS~1\Temp\nsz4.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\admin\LOCALS~1\Temp \ubuntu-8.04-beta-alternate-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
Using \ubuntu-8.04-beta-alternate-i386.iso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Checking/Downloading Ubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg md5=
Download status=The requested URL returned error: 404
Error downloading http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg, The req
Trying remote metalink2: http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:C:\ubuntu\install\MD5SUMS
      Verifying signature C:\ubuntu\install\MD5SUMS.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 04/01/08 20:11:33 Eastern Daylight Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst=\ubuntu-8.04-beta-alternate-i386.iso url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=success:C:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\hardy-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name C:\ubuntu\install\hardy-desktop-i386.iso; Volume name ; Max #/chars in vol name ; Volume Serial # 7690455; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size C:
Drive C: has filesystem NTFS
rootSize=3800 homesize=0, swapsize=200, usrsize=0
Drive & Path name C:\ubuntu\install\hardy-desktop-i386.iso; Volume name ; Max #/chars in vol name ; Volume Serial # 7690455; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size C:
Drive C: has filesystem NTFS
rootSize=3800 homesize=0, swapsize=200, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=3800
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=200
UncompressFilesAfterInstall
Installation completed successfully!


```

---

### Post by ago on 2008-04-03
ah you are using an Alternate ISO, you should use a Desktop ISO instead

---

### Post by seamustry on 2008-04-03
ok i'll try that...

---

### Post by seamustry on 2008-04-04
ok it's working now thanks!

---

### Post by plmday on 2008-04-15
Many others said and emphasized that we should use the alternative iso, have they ever test it? They really need to shut up.

---

### Post by ago on 2008-04-15
7.04 requires the alternate ISO but 8.04 and 7.10 require the DESKTOP ISO.

---

### Post by plmday on 2008-04-15
Ah, that accounts for it. Thanks and sorry for my complaints. :)

---

