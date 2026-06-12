---
title: "[SOLVED] Wubi Unistall problem"
date: 2008-07-06
forum: General Help
---

### Post by hgergo on 2008-07-06
I go in add remove program and i select ubuntu and unistall and the UAC is asking me to continu ai press to continue and the unistallation is not beginig the same problem is when i try too unistal wit the unistall exe from ubuntu folder.
can sombody help me pls i will unistall wubi

---

### Post by ago on 2008-07-06
Can you sen the wubi log in your user temp folder?
You can uninstall manually [https://wiki.ubuntu.com/WubiGuide#head-6b9eb58ace9884384e5e0d197bcf4159a25ed267](https://wiki.ubuntu.com/WubiGuide#head-6b9eb58ace9884384e5e0d197bcf4159a25ed267)

---

### Post by hgergo on 2008-07-06
where can i find the log?

---

### Post by ago on 2008-07-06
In your user temp folder, type %temp% in windows explorer.

---

### Post by hgergo on 2008-07-06
============ Installer ============
PLUGINSDIR=C:\Users\HeavyD\AppData\Local\Temp\nsyCEC0.tmp
detect_all
Parsing cmdline "D:\Downloads\Wubi-8.04.1.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=989 MB
arch=amd64
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name ; Max #/chars in vol name 3550928; Volume Serial # -868872541; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name ; Max #/chars in vol name 3550932; Volume Serial # 213562637; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 3546856; Volume name ; Max #/chars in vol name 64; Volume Serial # -868872541; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 18663
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=2
Country=HU
Locale=en_AU.UTF-8
TimeZone=Europe/Budapest
Domain=localdomain
HostName=HeavyD-PC
ComputerName=HEAVYD-PC
EnvUsername=HeavyD
UserDomain=HeavyD-PC
UserInfoName=HeavyD
UserProfileFolder=C:\Users\HeavyD
UserProfileName=HeavyD 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 3655360; Volume Serial # -868872541; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 3655364; Volume Serial # 213562637; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 10
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
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 5
============ Installer ============
PLUGINSDIR=C:\Users\HeavyD\AppData\Local\Temp\nsj5981.tmp
detect_all
Parsing cmdline "D:\Downloads\Wubi-8.04.1.exe" --32bit
debug=, 32bit=true, cdboot=
User account type=Admin
Memory=989 MB
arch=i386
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name ; Max #/chars in vol name 3642768; Volume Serial # -868872541; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name ; Max #/chars in vol name 3642772; Volume Serial # 213562637; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 3647736; Volume name ; Max #/chars in vol name 67; Volume Serial # -868872541; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 18663
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=2
Country=HU
Locale=en_AU.UTF-8
TimeZone=Europe/Budapest
Domain=localdomain
HostName=HeavyD-PC
ComputerName=HEAVYD-PC
EnvUsername=HeavyD
UserDomain=HeavyD-PC
UserInfoName=HeavyD
UserProfileFolder=C:\Users\HeavyD
UserProfileName=HeavyD 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 3789768; Volume Serial # -868872541; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 3789772; Volume Serial # 213562637; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 10
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
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 5
LeaveMainPage
Locale=en_AU.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
CreateInstallationFolders
MakeUninstall
Created D:\ubuntu\Uninstall-Ubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
No CD found
DetectIso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink)
get_md5 [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink
      Verifying signature D:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: error loading `iconv.dll': A megadott modul nem található.


gpgv: Signature made 07/04/08 00:36:17 GTB nyári id&#337; using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS-metalink
Found md5 cde82e1566ad8a88e36138853c195b5f
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink md5=cde82e1566ad8a88e36138853c195b5f
Download status=cancel
User cancelled download, quitting.
============ Installer ============
PLUGINSDIR=C:\Users\HeavyD\AppData\Local\Temp\nsjE68F.tmp
detect_all
Parsing cmdline "D:\Downloads\Wubi-8.04.1.exe" --32bit
debug=, 32bit=true, cdboot=
User account type=Admin
Memory=989 MB
arch=i386
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name ; Max #/chars in vol name 3184016; Volume Serial # -868872541; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name ; Max #/chars in vol name 3184020; Volume Serial # 213562637; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 3188984; Volume name ; Max #/chars in vol name 70; Volume Serial # -868872541; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 18385
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=2
Country=HU
Locale=en_AU.UTF-8
TimeZone=Europe/Budapest
Domain=localdomain
HostName=HeavyD-PC
ComputerName=HEAVYD-PC
EnvUsername=HeavyD
UserDomain=HeavyD-PC
UserInfoName=HeavyD
UserProfileFolder=C:\Users\HeavyD
UserProfileName=HeavyD 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 3331016; Volume Serial # -868872541; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 3331020; Volume Serial # 213562637; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 10
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
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 5
LeaveMainPage
Locale=en_AU.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
CreateInstallationFolders
MakeUninstall
Created D:\ubuntu\Uninstall-Ubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
No CD found
DetectIso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink)
get_md5 [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink
      Verifying signature D:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: error loading `iconv.dll': A megadott modul nem található.


gpgv: Signature made 07/04/08 00:36:17 GTB nyári id&#337; using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS-metalink
Found md5 cde82e1566ad8a88e36138853c195b5f
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink md5=cde82e1566ad8a88e36138853c195b5f
Download status=success:D:\ubuntu\install\ubuntu-8.04.1-desktop-i386.iso
ISO file ubuntu-8.04.1-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=D:\ubuntu\install\ubuntu-8.04.1-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from D:\ubuntu\install\ubuntu-8.04.1-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name D:\ubuntu\install\ubuntu-8.04.1-desktop-i386.iso; Volume name ; Max #/chars in vol name ; Volume Serial # 213562637; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive D: has filesystem NTFS
rootSize=4600 homesize=0, swapsize=400, usrsize=0
DoMenuLst D:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive Vista
CopyWubildr
CopyWubildrMbr
editBCD
C:\Users\HeavyD\AppData\Local\Temp\nsjE68F.tmp\wubibcd.exe 
 1:0 
 2:Operation completed successfully. New ID is {e4ead0ca-04ac-11dd-885c-0016d4cecead}
 
 3:HDD 
 4:3
vistaBootDriveCode = {e4ead0ca-04ac-11dd-885c-0016d4cecead} <=> {e4ead0ca-04ac-11dd-885c-0016d4cecead}
vistaBootDriveCode {e4ead0ca-04ac-11dd-885c-0016d4cecead}
Drive & Path name /Users/HeavyD; Volume name ; Max #/chars in vol name D:\ubuntu\install\ubuntu-8.04.1-desktop-i386.iso; Volume Serial # 213562637; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive D: has filesystem NTFS
rootSize=4600 homesize=0, swapsize=400, usrsize=0
AllocFile filename=D:\ubuntu\disks\root.disk size=4600
AllocFile status=success
AllocFile filename=D:\ubuntu\disks\home.disk size=0
AllocFile filename=D:\ubuntu\disks\swap.disk size=400
AllocFile status=success
UncompressFilesAfterInstall
Installation completed successfully!
============ Uninstaller ============
PLUGINSDIR=C:\Users\HeavyD\AppData\Local\Temp\nsiED04.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\HeavyD\AppData\Local\Temp\nsi6BF8.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\HeavyD\AppData\Local\Temp\nsf3BDB.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\HeavyD\AppData\Local\Temp\nsb7E43.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\HeavyD\AppData\Local\Temp\nslE2D9.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\HeavyD\AppData\Local\Temp\nst6855.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\HeavyD\AppData\Local\Temp\nsx8153.tmp
Could not find \ubuntu, quitting...

---

### Post by ago on 2008-07-06
Basically the installer is looking for an \ubuntu directory in the same drive where you execute the uninstaller from, and it fails. So either the directory D:\ubuntu was removed/renamed manually or the installer is launched from another drive.

If you have D:\ubuntu make sure your run the uninstaller from within that folder.

---

### Post by digitalggs on 2008-07-07
Im not sure that is the case with this error. I am having the same problem. the uninstaller is in the same directory as the /ubuntu folder. I even tryed moving it to the root of the drive and still gets that message that it cant find /ubuntu. Even though several lines above it finds it. 

  During the install (post reboot, where you actually boot into LInux) it never completed for me. It got to a point that it asked to import a profile (or something like that) and if there was none or diddnt want to import to select nothing and hit Next. Only there was nothing to select except a line saying there was nothing to select (wich was selectable) but the Next (actually read 'Forward') would not light up. so I closed out of that and it just launched me into 'Live session' (like a Live CD/DVD). I tinkered around with trying to finish the install, rebooting a few times and nada. 

  So here I am trying to uninstall it and try to run the install again but cant uninstall because of the same exact reason as the OP. 

  Im wondering maybe if it is looking for /ubuntu from within the installation itself (Dosent it use some kind of loopback partition or something?). I think since the install itself never actually finished thats why it cant find this '/ubuntu'. As I write this Im starting to sense that this might be a bit obsurd but I am at a loss as to why it cant find this '/ubuntu' when its right there and a few lines before in the log dump it finds the the folder. 

so heres a snippet of my log dump: (logged in as administrator in safe mode w/net)
// trying to use the installer to remove/reinstall...
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsu57.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Administrator\Local Settings\Application Data\Opera\opera\profile\cache4\temporary_download\Wubi-8.04.1.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2046 MB
arch=amd64
DetectCD
      Is Valid CD C:
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
      Is Valid CD I:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive E:\ubuntu
Found InstallationDrive E:\ubuntu
AlreadyInstalled=true OldInstallationDrive=E: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1712; Volume name __XP__; Max #/chars in vol name 1883268; Volume Serial # -400139543; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name G-Files_Prime; Max #/chars in vol name 1883272; Volume Serial # -469680397; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem E:
Drive & Path name 1712; Volume name The_Void; Max #/chars in vol name 1883276; Volume Serial # -334230898; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive E: has valid filesystem NTFS
IsValidFileSystem I:
Drive & Path name 1712; Volume name External; Max #/chars in vol name 1883292; Volume Serial # -1531861388; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive I: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1426576; Volume name __XP__; Max #/chars in vol name 21; Volume Serial # -400139543; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = I:
FreeSpace in I: is 31234
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
IsBackupFolder E:\
IsBackupFolder I:\
GMT=-7
Country=US
Locale=en_US.UTF-8
TimeZone=America/Denver
Domain=localdomain
HostName=vzw_003
ComputerName=VZW_003
EnvUsername=Administrator
UserDomain=VZW_003
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.

// using uninstaller
============ Uninstaller ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsv5C.tmp
Could not find \ubuntu, quitting...

END--

  I will try the manual uninstall. Something kinda caught my eye when I was observing filemon against the uninstaller. I will need to log back into regular Windows to run filemon again and post some of that info too.

---

### Post by digitalggs on 2008-07-07
I just noticed while doing a manual uninstall the the wubildr and wubildr.mbr were in both my C; drive (no ubuntu installed here) and in the E; drive. Maybe this is whats causing the hangup? not sure exactly what these files are (Im guessing boot records). Since I already deleted the folders I cant test a theory that if you remove the ones in the C: (primary drive but no installation) that it will keep looking for this file? Maybe if someone is still having this issue can try if removing those  fixes the uninstaller problem. Unless people are having this problem with ubuntu installed on the primary part (C:).

edit:
the line in the boot.ini reads c:\wubildr.mbr="Ubuntu" (this may have been why my installation diddnt complete properly either). Since the install was actually in E:\.

---

### Post by ago on 2008-07-07
The code seems correct, most likely cause is that the uninstaller does not run from the drive where it was installed (e.g. if it gets unpacked into temp first). In which case the uninstaller would work on C: but not on D: & co. I cannot check that at the moment and unfortunately the log does not contain that info.

---

### Post by ago on 2008-07-07
> **digitalggs said:**
> I just noticed while doing a manual uninstall the the wubildr and wubildr.mbr were in both my C; drive (no ubuntu installed here) and in the E; drive. Maybe this is whats causing the hangup?
No that is normal

> the line in the boot.ini reads c:\wubildr.mbr="Ubuntu" (this may have been why my installation diddnt complete properly either). Since the install was actually in E:\.
That is normal too, it's required by a windows bug in fact...

---

### Post by digitalggs on 2008-07-07
> **ago said:**
> The code seems correct, most likely cause is that the uninstaller does not run from the drive where it was installed (e.g. if it gets unpacked into temp first). In which case the uninstaller would work on C: but not on D: & co. I cannot check that at the moment and unfortunately the log does not contain that info.

  I uninstalled it (manually) and forgot that I was going to run filemon against it again >.< but this might make sence since what I noticed in the filemon was the prefetch being called from the C: drive to some temp file. Any idea on working around this?

---

### Post by ago on 2008-07-07
Yes I can confirm this. The issue is that the uninstaller in 8.04.1 was patched to check the folder on the same drive of the uninstaller. But the uninstaller is self-extracted by NSIS to a temp folder under C:. This in short means that the uninstaller fails when the installation drive is not C:. 

I will have to upload a revised uninstaller until that is fixed. For the time being use the manual instructions:

1. Delete the /ubuntu folder
2. Remove the boot entry from either boot.ini (windows xp) or using EasyBCD (vista) (this takes away Ubuntu from the boot menu)
3. Remove the registry key: HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi using regedit or similar (this takes away "Ubuntu" from the add/remove list)

---

### Post by ago on 2008-07-07
[https://bugs.launchpad.net/wubi/+bug/246201](https://bugs.launchpad.net/wubi/+bug/246201)

---

### Post by digitalggs on 2008-07-07
> **ago said:**
> 
2. Remove the boot entry from either boot.ini (windows xp) or using EasyBCD (vista) (this takes away Ubuntu from the boot menu)



  Good stuff Ago, you're a champ. On step 2 Some WinXP versions do not like you editing c:\boot.ini (also this can be a dangerous place to be). I recomend using MSCONFIG (Start->Run, type in MSCONFIG, then enter or 'OK'), in the GENERAL tab either select Normal startup (if you have no other special startup needs) or under Selective Startup you can select the option for 'Use Original BOOT.INI (instead of 'Use Modified BOOT.INI). You can then varify by going to the BOOT.INI tab to see the line is gone.

---

### Post by ago on 2008-07-07
Please try [https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe)

---

### Post by digitalggs on 2008-07-08
> **ago said:**
> Please try [https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe)
That uninstaller works great. I tryed running it from C:, E: (installed ubuntu here), and I: (External drive over USB). It found the installation from anywhere.

---

### Post by ago on 2008-07-08
I have updated wubi to rev 506 so there is no need for that anymore

---

