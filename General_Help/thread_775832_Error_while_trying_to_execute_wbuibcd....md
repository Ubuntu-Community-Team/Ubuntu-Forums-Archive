---
title: "Error while trying to execute wbuibcd..."
date: 2008-04-30
forum: General Help
---

### Post by LouisLam on 2008-04-30
I don't know how to fix this problem.

I am using Vista SP1.

It seems that Ubuntu have been installed sccessfully, but when I reboot my computer, I can't see Ubuntu in the boot list.

What should I do? Thanks!

[IMG]http://x6f.xanga.com/1aec731614033186568126/w143204129.png[/IMG]
[IMG]http://xd2.xanga.com/69bc601605732186568149/t143204145.png[/IMG]

---

### Post by ago on 2008-04-30
Can you pls post the wubi log in your user temp folder?

---

### Post by LouisLam on 2008-04-30
> **ago said:**
> ============ Installer ============
PLUGINSDIR=C:\Temp\nsy2E87.tmp
detect_all
Parsing cmdline "C:\ubuntu-backup\Wubi-8.04(1).exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=766 MB
arch=i386
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 3178976; Volume Serial # 1479339033; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 3167416; Volume name ; Max #/chars in vol name 76; Volume Serial # 1479339033; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 51448
DetectBackupFolder
IsBackupFolder C:\
Found BackupFolder C:\ubuntu-backup
GMT=8
Country=CN
Locale=zh_CN.UTF-8
LayoutCode=cn
TimeZone=Asia/Shanghai
Domain=localdomain
HostName=LouisLam-Vista
ComputerName=LOUISLAM-VISTA
EnvUsername=Louis Lam
UserDomain=LOUISLAM-VISTA
UserInfoName=Louis Lam
UserProfileFolder=C:\Users\Louis Lam
UserProfileName=Louis Lam 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1773; Volume name ; Max #/chars in vol name 3287656; Volume Serial # 1479339033; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\ubuntu-8.04-desktop-i386.iso
      ExtractIsoInfo
      C:\Temp\nsy2E87.tmp\7z.exe e -y -i!.disk\info -oC:\Temp C:\ubuntu-backup\ubuntu-8.04-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 6
LeaveMainPage
Locale=zh_CN.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
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
      Is Valid CD E:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\ubuntu-8.04-desktop-i386.iso
      ExtractIsoInfo
      C:\Temp\nsy2E87.tmp\7z.exe e -y -i!.disk\info -oC:\Temp C:\ubuntu-backup\ubuntu-8.04-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
Using C:\ubuntu-backup\ubuntu-8.04-desktop-i386.iso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
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
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: error loading `iconv.dll': &#25214;&#19981;&#21040;&#25351;&#23450;&#30340;&#27169;&#32068;&#12290;


gpgv: Signature made 04/24/08 15:37:24 &#20013;&#22283;&#27161;&#28310;&#26178;&#38291; using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS-metalink
Found md5 22eefa07792160d5b0f398024b397349
Downloading: trymefirst=C:\ubuntu-backup\ubuntu-8.04-desktop-i386.iso url=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink md5=22eefa07792160d5b0f398024b397349
Download status=success:C:\ubuntu\install\ubuntu-8.04-desktop-i386.iso
ISO file ubuntu-8.04-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\ubuntu-8.04-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\ubuntu-8.04-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name C:\ubuntu\install\ubuntu-8.04-desktop-i386.iso; Volume name ; Max #/chars in vol name ; Volume Serial # 1479339033; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 
Drive C: has filesystem NTFS
rootSize=5500 homesize=0, swapsize=500, usrsize=0
C:\Temp\nsy2E87.tmp\wubibcd.exe 
 1:-2146232576 
 2: 
 3:HDD 
 4:3
Error while trying to execute wubibcd:: 
vistaBootDriveCode = {} <=> 
vistaBootDriveCode {}
Drive & Path name /Users/Louis Lam; Volume name ; Max #/chars in vol name C:\ubuntu\install\ubuntu-8.04-desktop-i386.iso; Volume Serial # 1479339033; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=5500 homesize=0, swapsize=500, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=5500
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=500
AllocFile status=success
UncompressFilesAfterInstall
Installation completed successfully!


"&#25214;&#19981;&#21040;&#25351;&#23450;&#30340;&#27169;&#32068;" Means "The module cannot be found"

---

### Post by LouisLam on 2008-04-30
I feel that the ubuntu installer can not write data to my boot menu...
Have any methods can I add Ubuntu to boot list manually?

---

### Post by ago on 2008-05-01
You can use EasyBCD, it does have a boot option for wubi.

---

