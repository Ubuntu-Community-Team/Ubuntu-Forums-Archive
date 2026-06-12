---
title: "Intallation Errors - Seeking Advice"
date: 2008-04-09
forum: General Help
---

### Post by jkiesel on 2008-04-09
I just installed Wubi and ran it - after rebooting and loading Ubuntu I encountered some errors during the install. I forget the specifics of what the message stated but it refused to continue after it began checking the installation. 

I exited and uninstalled Ubuntu. Now every time I try to redownload the intaller it gives me an illegal operation message when the intaller is run. Does anyone have any ideas? I had thought to reformat but I'm not sure I'd like to take that much of my time - I also don't have means of backing up my files.

---

### Post by ago on 2008-04-09
if you type %temp% in the bar of windows explorer there should be a wubi log, pls post it here

---

### Post by jkiesel on 2008-04-09
I use Opera = /

---

### Post by ago on 2008-04-09
I assume you have a file browser...

---

### Post by jkiesel on 2008-04-09
Do you mean what I use to unzip files? If so I use powerarchiver for that.

---

### Post by ago on 2008-04-09
I simply mean that all windows versions come with a file explorer/file manager/explorer that lets you navigate files and directories. Just type %temp% to go to your temp folder, the wubi log is in there.

---

### Post by jkiesel on 2008-04-09
Ah, gotcha - the temp folder. I've attached it here = )

---

### Post by jkiesel on 2008-04-09
...or maybe I didn't. It says its an invalid file when I try to upload it?

---

### Post by gali98 on 2008-04-09
> **jkiesel said:**
> ...or maybe I didn't. It says its an invalid file when I try to upload it?

You probably tried to upload the folder.... either zip the folder and upload it or find the specific file you need and upload it or just paste the text from the file you need.
Kory

---

### Post by ago on 2008-04-09
No need to upload all the temp folder, only paste the content of the wubi log file

---

### Post by jkiesel on 2008-04-10
Agh, I see what it was. I didn't know there was such thing as a .log file. Anyhow, here's the readout:

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Logos\LOCALS~1\Temp\nse18.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Logos\Desktop\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
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
Drive & Path name 1709; Volume name ; Max #/chars in vol name 1846780; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1417248; Volume name ; Max #/chars in vol name 38; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 7075
DetectBackupFolder
IsBackupFolder C:\
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=seraphic-origin
ComputerName=SERAPHIC-ORIGIN
EnvUsername=Logos
UserDomain=SERAPHIC-ORIGIN
UserInfoName=Logos
UserProfileFolder=C:\Documents and Settings\Logos
UserProfileName=Logos 
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 1850004; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 5
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
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/xubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Xubuntu
Changing icon to Xubuntu.ico
LeaveMainPage
      GetDistroInfo distrofullname=Kubuntu-KDE4-i386 distro=Kubuntu-KDE4 cddistro= cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/kubuntu-kde4-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Kubuntu-KDE4
Changing icon to Kubuntu-KDE4.ico
LeaveMainPage
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/kubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Kubuntu
Changing icon to Kubuntu.ico
LeaveMainPage
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
LeaveMainPage
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/xubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Xubuntu
Changing icon to Xubuntu.ico
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/xubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Xubuntu.exe
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
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/xubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Checking/Downloading Xubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://wubi-installer.org/metalinks/8.04-final/xubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04-final/xubuntu-desktop-i386.iso.metalink)
get_md5 [http://wubi-installer.org/metalinks/8.04-final/xubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04-final/xubuntu-desktop-i386.iso.metalink)
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg md5=
Download status=The requested URL returned error: 404
Error downloading [http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg](http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg), The req
Trying remote metalink2: [http://wubi-installer.org/metalinks/8.04/xubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04/xubuntu-desktop-i386.iso.metalink)
get_md5 [http://wubi-installer.org/metalinks/8.04/xubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04/xubuntu-desktop-i386.iso.metalink)
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:C:\ubuntu\install\MD5SUMS
      Verifying signature C:\ubuntu\install\MD5SUMS.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 04/03/08 17:22:57 Central America Standard Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS
Found md5 e5c41840e6c977dfdc9f26769cff81ac
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/xubuntu-desktop-i386.iso.metalink md5=e5c41840e6c977dfdc9f26769cff81ac
Download status=The requested URL returned error: 404
The download was interrupted with the error: The requested URL returned error: 404
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Logos\LOCALS~1\Temp\nsl24.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Logos\Desktop\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
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
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 1890052; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1428112; Volume name ; Max #/chars in vol name 34; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 7041
DetectBackupFolder
IsBackupFolder C:\
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=seraphic-origin
ComputerName=SERAPHIC-ORIGIN
EnvUsername=Logos
UserDomain=SERAPHIC-ORIGIN
UserInfoName=Logos
UserProfileFolder=C:\Documents and Settings\Logos
UserProfileName=Logos 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Logos\LOCALS~1\Temp\nsa26.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Logos\Desktop\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
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
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 1890052; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1428112; Volume name ; Max #/chars in vol name 34; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 7039
DetectBackupFolder
IsBackupFolder C:\
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=seraphic-origin
ComputerName=SERAPHIC-ORIGIN
EnvUsername=Logos
UserDomain=SERAPHIC-ORIGIN
UserInfoName=Logos
UserProfileFolder=C:\Documents and Settings\Logos
UserProfileName=Logos 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Logos\LOCALS~1\Temp\nsi28.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Logos\Desktop\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
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
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1709; Volume name ; Max #/chars in vol name 1843660; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1417248; Volume name ; Max #/chars in vol name 39; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 7148
DetectBackupFolder
IsBackupFolder C:\
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=seraphic-origin
ComputerName=SERAPHIC-ORIGIN
EnvUsername=Logos
UserDomain=SERAPHIC-ORIGIN
UserInfoName=Logos
UserProfileFolder=C:\Documents and Settings\Logos
UserProfileName=Logos 
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 1848764; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 5
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
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
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
      Is Valid CD D:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
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
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 04/03/08 17:22:57 Central America Standard Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=success:C:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\hardy-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name C:\ubuntu\install\hardy-desktop-i386.iso; Volume name ; Max #/chars in vol name ; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=4600 homesize=0, swapsize=400, usrsize=0
Drive & Path name C:\ubuntu\install\hardy-desktop-i386.iso; Volume name ; Max #/chars in vol name ; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=4600 homesize=0, swapsize=400, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=4600
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=400
UncompressFilesAfterInstall
Installation completed successfully!
============ Uninstaller ============
PLUGINSDIR=C:\DOCUME~1\Logos\LOCALS~1\Temp\nsv14.tmp
un.install
un.BackupIso
Backup C:\ubuntu\install\hardy-desktop-i386.iso
un.CleanBcd
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanConfig.sys C:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Logos\LOCALS~1\Temp\nsv17.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Logos\Desktop\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
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
Drive & Path name 1709; Volume name ; Max #/chars in vol name 1890052; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1428112; Volume name ; Max #/chars in vol name 31; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 6350
DetectBackupFolder
IsBackupFolder C:\
Found BackupFolder C:\ubuntu-backup
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=seraphic-origin
ComputerName=SERAPHIC-ORIGIN
EnvUsername=Logos
UserDomain=SERAPHIC-ORIGIN
UserInfoName=Logos
UserProfileFolder=C:\Documents and Settings\Logos
UserProfileName=Logos 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Logos\LOCALS~1\Temp\nse25.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Logos\Application Data\Opera\Opera\profile\cache4\temporary_download\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
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
Drive & Path name 1709; Volume name ; Max #/chars in vol name 1787660; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1417320; Volume name ; Max #/chars in vol name 35; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 6346
DetectBackupFolder
IsBackupFolder C:\
Found BackupFolder C:\ubuntu-backup
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=seraphic-origin
ComputerName=SERAPHIC-ORIGIN
EnvUsername=Logos
UserDomain=SERAPHIC-ORIGIN
UserInfoName=Logos
UserProfileFolder=C:\Documents and Settings\Logos
UserProfileName=Logos 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Logos\LOCALS~1\Temp\nsx2B.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Logos\Application Data\Opera\Opera\profile\cache4\temporary_download\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
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
Drive & Path name 1709; Volume name ; Max #/chars in vol name 1787660; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1417320; Volume name ; Max #/chars in vol name 35; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 6344
DetectBackupFolder
IsBackupFolder C:\
Found BackupFolder C:\ubuntu-backup
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=seraphic-origin
ComputerName=SERAPHIC-ORIGIN
EnvUsername=Logos
UserDomain=SERAPHIC-ORIGIN
UserInfoName=Logos
UserProfileFolder=C:\Documents and Settings\Logos
UserProfileName=Logos 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Logos\LOCALS~1\Temp\nsc35.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Logos\Desktop\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
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
Drive & Path name 1709; Volume name ; Max #/chars in vol name 1890052; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1428112; Volume name ; Max #/chars in vol name 35; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 6341
DetectBackupFolder
IsBackupFolder C:\
Found BackupFolder C:\ubuntu-backup
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=seraphic-origin
ComputerName=SERAPHIC-ORIGIN
EnvUsername=Logos
UserDomain=SERAPHIC-ORIGIN
UserInfoName=Logos
UserProfileFolder=C:\Documents and Settings\Logos
UserProfileName=Logos 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Logos\LOCALS~1\Temp\nso5.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Logos\Application Data\Opera\Opera\profile\cache4\temporary_download\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
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
Drive & Path name 1709; Volume name ; Max #/chars in vol name 1787660; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1417320; Volume name ; Max #/chars in vol name 31; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 6338
DetectBackupFolder
IsBackupFolder C:\
Found BackupFolder C:\ubuntu-backup
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=seraphic-origin
ComputerName=SERAPHIC-ORIGIN
EnvUsername=Logos
UserDomain=SERAPHIC-ORIGIN
UserInfoName=Logos
UserProfileFolder=C:\Documents and Settings\Logos
UserProfileName=Logos 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Logos\LOCALS~1\Temp\nst92.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Logos\Application Data\Opera\Opera\profile\cache4\temporary_download\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
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
Drive & Path name 1709; Volume name ; Max #/chars in vol name 1787652; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1417320; Volume name ; Max #/chars in vol name 40; Volume Serial # -1932802544; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 6321
DetectBackupFolder
IsBackupFolder C:\
Found BackupFolder C:\ubuntu-backup
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=seraphic-origin
ComputerName=SERAPHIC-ORIGIN
EnvUsername=Logos
UserDomain=SERAPHIC-ORIGIN
UserInfoName=Logos
UserProfileFolder=C:\Documents and Settings\Logos
UserProfileName=Logos

---

### Post by ago on 2008-04-10
Can you try rev 482?

---

### Post by jkiesel on 2008-04-11
Are you referring to Ubuntu 482 or Wubi 482?

---

### Post by ago on 2008-04-12
wubi  rev 482 with latest daily ISO of ubuntu

---

