---
title: "Freezes on &quot;Retrieving Installation Files&quot;"
date: 2008-05-22
forum: General Help
---

### Post by Serisium on 2008-05-22
I've been trying to use Wubi to install Ubuntu 8.0.4. The installer always froze on "Retrieving Installation Files", so I manually downloaded the correct Ubuntu 8.0.04 Desktop .iso and put it with Wubi, but It's still freezing.

```
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Garrett\LOCALS~1\Temp\nsb43.tmp
detect_all
Parsing cmdline I:\wubi.exe
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
arch=i386
DetectCD
      Is Valid CD I:
      IsValid Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
Found CD I:
Found CD cddrive=I:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1930420; Volume Serial # 821697659; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1517920; Volume name ; Max #/chars in vol name 58; Volume Serial # 821697659; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 7198
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=D199FX11
ComputerName=D199FX11
EnvUsername=Garrett
UserDomain=D199FX11
UserInfoName=Garrett
UserProfileFolder=C:\Documents and Settings\Garrett
UserProfileName=Garrett 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1774; Volume name ; Max #/chars in vol name 1938388; Volume Serial # 821697659; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 5
PopulateDistroList
DistroList = Ubuntu
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
Locale=en_US.UTF-8
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
      Is Valid CD I:
      IsValid Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
Found CD I:
Found CD cddrive=I:
Installing in automatic mode from CD
CheckCD
check_internet_connection

```

---

### Post by ago on 2008-05-24
Does it freeze, or does it crash?
Can you post the log of when you install from ISO?

---

### Post by Serisium on 2008-05-24
When it gets to that message, it does nothing. According to the task manager it's still responding but I've left it on for days it's still stuck. Anyway, even though the .iso returned a similar error message, I'm running it right now and it seems to be going fine. It's already passed the part that it usually freezes on.

EDIT: Successfully installed. Now I just have to uninstall it before my dad finds out. :(

---

