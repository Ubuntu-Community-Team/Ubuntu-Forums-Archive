---
title: "HELP...ERROR 15: file not found !!!!"
date: 2008-04-09
forum: General Help
---

### Post by you.buntu on 2008-04-09
this is my second time using ubuntu... first time was on XP and it worked very well

but now im having problems

there is no menu.lst in ubuntu > disk >boot>grub

its in the install one but there is no where i can change the hd00 to hd01

---

### Post by you.buntu on 2008-04-09
log file

============ Installer ============
PLUGINSDIR=C:\Users\admin\AppData\Local\Temp\nso697D.tmp
detect_all
Parsing cmdline "C:\Users\admin\Music\smack\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2037 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016.1)
      cdversion=7.10 cddistro=Ubuntu cdarch=i386 cdcodename=Gutsy Gibbon cdsubversion=Release 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different version 8.04 != 7.10
CDInfo cleared
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive G:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 2760960; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1709; Volume name RECOVERY; Max #/chars in vol name 2760964; Volume Serial # -1870203592; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
IsValidFileSystem F:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 2760972; Volume Serial # -1775691603; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive F: has valid filesystem FAT32
IsValidFileSystem G:
Drive & Path name 1709; Volume name OTHER; Max #/chars in vol name 2760976; Volume Serial # -1663444685; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive G: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 2724760; Volume name ; Max #/chars in vol name 50; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 7237
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
IsBackupFolder F:\
IsBackupFolder G:\
GMT=10
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=My_PC
ComputerName=MY_PC
EnvUsername=admin
UserDomain=My_PC
UserInfoName=admin
UserProfileFolder=C:\Users\admin
UserProfileName=admin 
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 3375920; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1752; Volume name RECOVERY; Max #/chars in vol name 3375924; Volume Serial # -1870203592; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
Adding drive D:
IsValidFileSystem F:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 3375932; Volume Serial # -1775691603; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive F: has valid filesystem FAT32
Skipping drive F:, not enough free space 2201 <= 5000
IsValidFileSystem G:
Drive & Path name 1752; Volume name OTHER; Max #/chars in vol name 3375936; Volume Serial # -1663444685; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive G: has valid filesystem FAT32
Skipping drive G:, not enough free space 870 <= 5000
Drive list = C:|D:
ChangeInstallationDrive to C:
ChangeInstallationSize to 5
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\Users\admin\Music\smack\ubuntu-8.04-beta-alternate-i386.iso
      ExtractIsoInfo
      C:\Users\admin\AppData\Local\Temp\nso697D.tmp\7z.exe e -y -i!.disk\info -oC:\Users\admin\AppData\Local\Temp C:\Users\admin\Music\smack\ubuntu-8.04-beta-alternate-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=amd64
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationDrive to D:
ChangeInstallationSize to 5
LeaveMainPage
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
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
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=C:\Users\admin\Music\smack\ubuntu-8.04-beta-alternate-i386.iso
      ExtractIsoInfo
      C:\Users\admin\AppData\Local\Temp\nso697D.tmp\7z.exe e -y -i!.disk\info -oC:\Users\admin\AppData\Local\Temp C:\Users\admin\Music\smack\ubuntu-8.04-beta-alternate-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
Copying C:\Users\admin\Music\smack\ubuntu-8.04-beta-alternate-i386.iso -> D:\ubuntu\install\ubuntu-8.04-beta-alternate-i386.iso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Checking/Downloading Ubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink)
get_md5 [http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink)
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg md5=
Download status=The requested URL returned error: 404
Error downloading [http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg](http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg), The req
Trying remote metalink2: [http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink)
get_md5 [http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink)
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:D:\ubuntu\install\MD5SUMS
      Verifying signature D:\ubuntu\install\MD5SUMS.asc
0; gpgv: Signature made 04/04/08 10:22:57 AUS Eastern Daylight Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst=D:\ubuntu\install\ubuntu-8.04-beta-alternate-i386.iso url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=success:D:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=D:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from D:\ubuntu\install\hardy-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name D:\ubuntu\install\hardy-desktop-i386.iso; Volume name RECOVERY; Max #/chars in vol name ; Volume Serial # -1870203592; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size 
Drive D: has filesystem FAT32
rootSize=1500 homesize=0, swapsize=400, usrsize=3100
C:\Users\admin\AppData\Local\Temp\nso697D.tmp\wubibcd.exe 
 1:0 
 2:Operation completed successfully. New ID is {92f38483-0604-11dd-86e1-00e0b8bf21fe}
 
 3:HDD 
 4:3
vistaBootDriveCode = {92f38483-0604-11dd-86e1-00e0b8bf21fe} <=> {92f38483-0604-11dd-86e1-00e0b8bf21fe}
vistaBootDriveCode {92f38483-0604-11dd-86e1-00e0b8bf21fe}
Drive & Path name /Users/admin; Volume name RECOVERY; Max #/chars in vol name D:\ubuntu\install\hardy-desktop-i386.iso; Volume Serial # -1870203592; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size 255
Drive D: has filesystem FAT32
rootSize=1500 homesize=0, swapsize=400, usrsize=3100
AllocFile filename=D:\ubuntu\disks\root.disk size=1500
AllocFile filename=D:\ubuntu\disks\home.disk size=0
AllocFile filename=D:\ubuntu\disks\swap.disk size=400
AllocFile filename=D:\ubuntu\disks\usr.disk size=3100
UncompressFilesAfterInstall
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\admin\AppData\Local\Temp\nsu479B.tmp
detect_all
Parsing cmdline "C:\Users\admin\Music\smack\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2037 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 2474120; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1709; Volume name RECOVERY; Max #/chars in vol name 2474124; Volume Serial # -1870203592; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
IsValidFileSystem F:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 2474132; Volume Serial # -1775691603; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive F: has valid filesystem FAT32
IsValidFileSystem G:
Drive & Path name 1709; Volume name OTHER; Max #/chars in vol name 2474136; Volume Serial # -1663444685; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive G: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 1938176; Volume name ; Max #/chars in vol name 50; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 7050
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
IsBackupFolder F:\
IsBackupFolder G:\
GMT=10
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=My_PC
ComputerName=MY_PC
EnvUsername=admin
UserDomain=My_PC
UserInfoName=admin
UserProfileFolder=C:\Users\admin
UserProfileName=admin 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=C:\Users\admin\AppData\Local\Temp\nse4D07.tmp
un.install
un.BackupIso
Backup D:\ubuntu\install\hardy-desktop-i386.iso
un.CleanBcd
un.RemoveInstallationFolder D:\ubuntu
un.CleanThisDrive C:\
un.CleanConfig.sys C:\
un.CleanThisDrive D:\
un.CleanThisDrive F:\
un.CleanThisDrive G:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Installer ============
PLUGINSDIR=C:\Users\admin\AppData\Local\Temp\nskA499.tmp
detect_all
Parsing cmdline "C:\Users\admin\Music\smack\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2037 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive G:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 3522696; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1709; Volume name RECOVERY; Max #/chars in vol name 3522700; Volume Serial # -1870203592; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
IsValidFileSystem F:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 3522708; Volume Serial # -1775691603; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive F: has valid filesystem FAT32
IsValidFileSystem G:
Drive & Path name 1709; Volume name OTHER; Max #/chars in vol name 3522712; Volume Serial # -1663444685; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive G: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 2986752; Volume name ; Max #/chars in vol name 51; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 6307
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=10
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=My_PC
ComputerName=MY_PC
EnvUsername=admin
UserDomain=My_PC
UserInfoName=admin
UserProfileFolder=C:\Users\admin
UserProfileName=admin 
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 3559624; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1752; Volume name RECOVERY; Max #/chars in vol name 3559628; Volume Serial # -1870203592; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
Adding drive D:
IsValidFileSystem F:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 3559636; Volume Serial # -1775691603; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive F: has valid filesystem FAT32
Skipping drive F:, not enough free space 2201 <= 5000
IsValidFileSystem G:
Drive & Path name 1752; Volume name OTHER; Max #/chars in vol name 3559640; Volume Serial # -1663444685; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive G: has valid filesystem FAT32
Skipping drive G:, not enough free space 870 <= 5000
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 5
PopulateDistroList
DetectIso
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\admin\AppData\Local\Temp\nskA499.tmp\7z.exe e -y -i!.disk\info -oC:\Users\admin\AppData\Local\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=amd64
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
LeaveMainPage
LeaveMainPage
LeaveMainPage
LeaveMainPage
LeaveMainPage
ChangeInstallationDrive to C:
ChangeInstallationSize to 5
============ Installer ============
PLUGINSDIR=C:\Users\admin\AppData\Local\Temp\nsg4A49.tmp
detect_all
Parsing cmdline "C:\Users\admin\Music\smack\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2037 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive G:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 2496568; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1709; Volume name RECOVERY; Max #/chars in vol name 2496572; Volume Serial # -1870203592; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
IsValidFileSystem F:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 2496580; Volume Serial # -1775691603; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive F: has valid filesystem FAT32
IsValidFileSystem G:
Drive & Path name 1709; Volume name OTHER; Max #/chars in vol name 2496584; Volume Serial # -1663444685; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive G: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 1938328; Volume name ; Max #/chars in vol name 53; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 17246
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=10
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=My_PC
ComputerName=MY_PC
EnvUsername=admin
UserDomain=My_PC
UserInfoName=admin
UserProfileFolder=C:\Users\admin
UserProfileName=admin 
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 2596840; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1752; Volume name RECOVERY; Max #/chars in vol name 2596844; Volume Serial # -1870203592; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
Adding drive D:
IsValidFileSystem F:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 2596852; Volume Serial # -1775691603; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive F: has valid filesystem FAT32
Skipping drive F:, not enough free space 2201 <= 5000
IsValidFileSystem G:
Drive & Path name 1752; Volume name OTHER; Max #/chars in vol name 2596856; Volume Serial # -1663444685; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive G: has valid filesystem FAT32
Skipping drive G:, not enough free space 1685 <= 5000
Drive list = C:|D:
ChangeInstallationDrive to C:
ChangeInstallationSize to 10
PopulateDistroList
DetectIso
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\admin\AppData\Local\Temp\nsg4A49.tmp\7z.exe e -y -i!.disk\info -oC:\Users\admin\AppData\Local\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=amd64
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 8
LeaveMainPage
ChangeInstallationSize to 9
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
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
      Is Valid CD E:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\admin\AppData\Local\Temp\nsg4A49.tmp\7z.exe e -y -i!.disk\info -oC:\Users\admin\AppData\Local\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
Using D:\ubuntu-backup\hardy-desktop-i386.iso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Checking/Downloading Ubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink)
get_md5 [http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink)
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg md5=
Download status=The requested URL returned error: 404
Error downloading [http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg](http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg), The req
Trying remote metalink2: [http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink)
get_md5 [http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink)
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:C:\ubuntu\install\MD5SUMS
      Verifying signature C:\ubuntu\install\MD5SUMS.asc
0; gpgv: Signature made 04/04/08 10:22:57 AUS Eastern Daylight Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst=D:\ubuntu-backup\hardy-desktop-i386.iso url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=success:C:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\hardy-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name C:\ubuntu\install\hardy-desktop-i386.iso; Volume name ; Max #/chars in vol name ; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 
Drive C: has filesystem NTFS
rootSize=8000 homesize=0, swapsize=1000, usrsize=0
C:\Users\admin\AppData\Local\Temp\nsg4A49.tmp\wubibcd.exe 
 1:0 
 2:Operation completed successfully. New ID is {92f38484-0604-11dd-86e1-00e0b8bf21fe}
 
 3:HDD 
 4:3
vistaBootDriveCode = {92f38484-0604-11dd-86e1-00e0b8bf21fe} <=> {92f38484-0604-11dd-86e1-00e0b8bf21fe}
vistaBootDriveCode {92f38484-0604-11dd-86e1-00e0b8bf21fe}
Drive & Path name /Users/admin; Volume name ; Max #/chars in vol name C:\ubuntu\install\hardy-desktop-i386.iso; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=8000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=8000
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
UncompressFilesAfterInstall
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\admin\AppData\Local\Temp\nsiAF81.tmp
detect_all
Parsing cmdline "C:\Users\admin\Music\smack\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2037 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 3414072; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1709; Volume name RECOVERY; Max #/chars in vol name 3414076; Volume Serial # -1870203592; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
IsValidFileSystem F:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 3414084; Volume Serial # -1775691603; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive F: has valid filesystem FAT32
IsValidFileSystem G:
Drive & Path name 1709; Volume name OTHER; Max #/chars in vol name 3414088; Volume Serial # -1663444685; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive G: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 2855832; Volume name ; Max #/chars in vol name 42; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 8003
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=10
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=My_PC
ComputerName=MY_PC
EnvUsername=admin
UserDomain=My_PC
UserInfoName=admin
UserProfileFolder=C:\Users\admin
UserProfileName=admin 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=C:\Users\admin\AppData\Local\Temp\nsiB2DB.tmp
un.install
un.BackupIso
Backup C:\ubuntu\install\hardy-desktop-i386.iso
un.CleanBcd
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanConfig.sys C:\
un.CleanThisDrive D:\
un.CleanThisDrive F:\
un.CleanThisDrive G:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Installer ============
PLUGINSDIR=C:\Users\admin\AppData\Local\Temp\nsj5986.tmp
detect_all
Parsing cmdline "C:\Users\admin\Music\smack\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2037 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 7346232; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1709; Volume name RECOVERY; Max #/chars in vol name 7346236; Volume Serial # -1870203592; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
IsValidFileSystem F:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 7346244; Volume Serial # -1775691603; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive F: has valid filesystem FAT32
IsValidFileSystem G:
Drive & Path name 1709; Volume name OTHER; Max #/chars in vol name 7346248; Volume Serial # -1663444685; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive G: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 6787992; Volume name ; Max #/chars in vol name 42; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 16587
DetectBackupFolder
Found BackupFolder C:\ubuntu-backup
GMT=10
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=My_PC
ComputerName=MY_PC
EnvUsername=admin
UserDomain=My_PC
UserInfoName=admin
UserProfileFolder=C:\Users\admin
UserProfileName=admin 
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 7446504; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1752; Volume name RECOVERY; Max #/chars in vol name 7446508; Volume Serial # -1870203592; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
Adding drive D:
IsValidFileSystem F:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 7446516; Volume Serial # -1775691603; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive F: has valid filesystem FAT32
Skipping drive F:, not enough free space 2201 <= 5000
IsValidFileSystem G:
Drive & Path name 1752; Volume name OTHER; Max #/chars in vol name 7446520; Volume Serial # -1663444685; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive G: has valid filesystem FAT32
Skipping drive G:, not enough free space 1685 <= 5000
Drive list = C:|D:
ChangeInstallationDrive to C:
ChangeInstallationSize to 10
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\admin\AppData\Local\Temp\nsj5986.tmp\7z.exe e -y -i!.disk\info -oC:\Users\admin\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=amd64
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
LeaveMainPage
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
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
      Is Valid CD E:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\admin\AppData\Local\Temp\nsj5986.tmp\7z.exe e -y -i!.disk\info -oC:\Users\admin\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080318.1)
Using C:\ubuntu-backup\hardy-desktop-i386.iso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Checking/Downloading Ubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink)
get_md5 [http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink)
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg md5=
Download status=The requested URL returned error: 404
Error downloading [http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg](http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg), The req
Trying remote metalink2: [http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink)
get_md5 [http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink)
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:C:\ubuntu\install\MD5SUMS
      Verifying signature C:\ubuntu\install\MD5SUMS.asc
0; gpgv: Signature made 04/04/08 10:22:57 AUS Eastern Daylight Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst=C:\ubuntu-backup\hardy-desktop-i386.iso url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=success:C:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\hardy-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name C:\ubuntu\install\hardy-desktop-i386.iso; Volume name ; Max #/chars in vol name ; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
C:\Users\admin\AppData\Local\Temp\nsj5986.tmp\wubibcd.exe 
 1:0 
 2:Operation completed successfully. New ID is {92f38485-0604-11dd-86e1-00e0b8bf21fe}
 
 3:HDD 
 4:3
vistaBootDriveCode = {92f38485-0604-11dd-86e1-00e0b8bf21fe} <=> {92f38485-0604-11dd-86e1-00e0b8bf21fe}
vistaBootDriveCode {92f38485-0604-11dd-86e1-00e0b8bf21fe}
Drive & Path name /Users/admin; Volume name ; Max #/chars in vol name C:\ubuntu\install\hardy-desktop-i386.iso; Volume Serial # 943750654; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=9000
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
UncompressFilesAfterInstall
Installation completed successfully!

---

### Post by ago on 2008-04-09
> **you.buntu said:**
> this is my second time using ubuntu... first time was on XP and it worked very well

but now im having problems

there is no menu.lst in ubuntu > disk >boot>grub

its in the install one but there is no where i can change the hd00 to hd01

ubuntu/disks/boot is filled after linux-side installation after rebooting from windows

if you had it already installed sometime a filesystem corruption will hide files/folders which will appear as hidden files (found0000*)

The log seems fine.

---

### Post by you.buntu on 2008-04-09
i forgot to mention...im now on a vista machine...

anyway i can resolve this?

---

### Post by ago on 2008-04-09
Well you have now uninstalled, so you will have to install again.
Doesn't the installer work? If it should look for c:\ubuntu\install\boot\grub\menu.lst

---

### Post by you.buntu on 2008-04-09
tried the uninstall and reinstall a few time

 here is the menu.lst from install


> #This file is modified at runtime by bootmenu.nsh

debug off
hiddenmenu 
timeout		5
default		0

title Start installer in normal mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz boot=casper debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/hardy-desktop-i386.iso quiet splash ro automatic-ubiquity locale=en_US.UTF-8 noprompt --  
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in safe graphic mode (only if you have display problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz xforcevesa boot=casper debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/hardy-desktop-i386.iso quiet splash ro automatic-ubiquity locale=en_US.UTF-8 noprompt --  
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer with ACPI workarounds (only if you have ACPI problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz quiet boot=casper debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/hardy-desktop-i386.iso ro automatic-ubiquity locale=en_US.UTF-8 noprompt -- acpi=off noapic nolapic  
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in verbose mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debug boot=casper debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/hardy-desktop-i386.iso ro debug-ubiquity automatic-ubiquity locale=en_US.UTF-8 noprompt --  
initrd /ubuntu/install/boot/initrd.gz
boot


---

### Post by ago on 2008-04-09
Yeah that looks good.

If the installer does not start it might be that your hard disk cannot be "seen" during boot by grub4dos.

To confirm try to press "insert" immediately after selecting ubuntu, then if you can go into a command line mode for grub4dos type

find \ubuntu\install\boot\grub\menu.lst

---

### Post by you.buntu on 2008-04-11
Thanx for the help...

I ran wubi from a CD i burnt and it works great

---

### Post by kmittal on 2008-11-05
I have the similar problem with my ubuntu 8.04 and the same menu.lst file. But I am unable to understand the solution.Will someone clarify?:confused:

---

