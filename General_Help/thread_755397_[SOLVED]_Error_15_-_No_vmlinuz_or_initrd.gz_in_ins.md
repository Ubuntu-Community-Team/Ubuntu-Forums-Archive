---
title: "[SOLVED] Error 15 - No vmlinuz or initrd.gz in /install/boot/"
date: 2008-04-14
forum: General Help
---

### Post by Arabica Bean on 2008-04-14
Hi guys.

I've installed wubi on a secondary partition on my laptop (D:)  

I get the dreaded Error 15 message when I boot ubuntu

from what I can figure, there should be vmlinuz and initrd.gz in the d:\ubuntu\install\boot directory but alas, there is not.

Can I just simply just download these files online and subsidise them into the directory, or will they be unsuitable. I'm not a ubuntu noob but these two files I am not totally familiar with, except that they are crucial in booting.

Thanks for your help in advance.

---

### Post by ago on 2008-04-15
Can you please provide the wubi log file in your user temp directory (%temp%)?

---

### Post by ago on 2008-04-15
Are you using the alternate ISO by any chanche? If so uninstall, delete it the ISO (also from /ubuntu-backup) and let Wubi download the ISO. Which must be a DESKTOP ISO.

---

### Post by Arabica Bean on 2008-04-16
Yes I was using the alternate CD. I'll d/l the desktop cd using wubi, and I'll post back with results.

---

### Post by Arabica Bean on 2008-04-16
Okay, I deleted the Alternate CD, and used wubi to d/l the new Desktop CD.

I uninstalled anything I could see that may affect the new installation of wubi (ubuntu named folders, etc) and ran the installation without errors until I booted up...

After I chose ubuntu, it gave me an error 13 message. Something about unsupported executable methinks.

Another problem arose when I tried to uninstall this installation.  The iso image was saved to the ubuntu-backup folder as planned, but when I ran the installer, it did not recognise the iso in the folder and tried to d/l a new iso! I worked around the new (2nd) installation by dropping the iso into the hardy iso into the /install directory.  This installed ubuntu desktop a second time but alas, the same error 13 message still remains. 

I enclose two wubi logs that I found in my temp folder....

```

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nsi3D.tmp
detect_all
Parsing cmdline "D:\ubuntu-backup\hardy-desktop-i386\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=510 MB
arch=i386
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=&#381;²2à?bs&#8212;Óüð&#339;Xþú
-i386 distro= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=
      ->isoKernel=
      ->distroVersion=
no distroversion
CDInfo cleared
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD Z:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 1814040; Volume Serial # 2090316815; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 1814044; Volume Serial # -663608010; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem I:
Drive & Path name 1711; Volume name MAIN BIG HD; Max #/chars in vol name 1814056; Volume Serial # 401082415; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive I: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 1432960; Volume name ; Max #/chars in vol name 76; Volume Serial # 2090316815; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = I:
FreeSpace in I: is 67065
DetectBackupFolder
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=IE
Locale=en_IE.UTF-8
TimeZone=Europe/Dublin
Domain=localdomain
HostName=bettyblue
ComputerName=BETTYBLUE
EnvUsername=Richey Ward
UserDomain=BETTYBLUE
UserInfoName=Richey Ward
UserProfileFolder=C:\Documents and Settings\Richey Ward
UserProfileName=Richey Ward 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1754; Volume name ; Max #/chars in vol name 1811960; Volume Serial # 2090316815; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Skipping drive C:, not enough free space 4066 <= 5000
IsValidFileSystem D:
Drive & Path name 1754; Volume name ; Max #/chars in vol name 1811964; Volume Serial # -663608010; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
IsValidFileSystem I:
Drive & Path name 1754; Volume name MAIN BIG HD; Max #/chars in vol name 1811976; Volume Serial # 401082415; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive I: has valid filesystem FAT32
Adding drive I:
Drive list = D:|I:
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nsi3D.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\RICHEY~1\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=&#381;²2à?bs&#8212;Óüð&#339;Xþú
-i386 distro= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=
      ->isoKernel=
      ->distroVersion=
no distroversion
CDInfo cleared
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
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nsx42.tmp
detect_all
Parsing cmdline "D:\ubuntu-backup\hardy-desktop-i386\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=510 MB
arch=i386
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD Z:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 1811944; Volume Serial # 2090316815; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 1811948; Volume Serial # -663608010; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem I:
Drive & Path name 1711; Volume name MAIN BIG HD; Max #/chars in vol name 1811960; Volume Serial # 401082415; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive I: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 1432960; Volume name ; Max #/chars in vol name 74; Volume Serial # 2090316815; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = I:
FreeSpace in I: is 67065
DetectBackupFolder
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=IE
Locale=en_IE.UTF-8
TimeZone=Europe/Dublin
Domain=localdomain
HostName=bettyblue
ComputerName=BETTYBLUE
EnvUsername=Richey Ward
UserDomain=BETTYBLUE
UserInfoName=Richey Ward
UserProfileFolder=C:\Documents and Settings\Richey Ward
UserProfileName=Richey Ward 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1754; Volume name ; Max #/chars in vol name 1812496; Volume Serial # 2090316815; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Skipping drive C:, not enough free space 4066 <= 5000
IsValidFileSystem D:
Drive & Path name 1754; Volume name ; Max #/chars in vol name 1812500; Volume Serial # -663608010; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
IsValidFileSystem I:
Drive & Path name 1754; Volume name MAIN BIG HD; Max #/chars in vol name 1812512; Volume Serial # 401082415; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive I: has valid filesystem FAT32
Adding drive I:
Drive list = D:|I:
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nsx42.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\RICHEY~1\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=&#381;²2à?bs&#8212;Óüð&#339;Xþú
-i386 distro= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=
      ->isoKernel=
      ->distroVersion=
no distroversion
CDInfo cleared
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
Locale=en_IE.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
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
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD Z:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nsx42.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\RICHEY~1\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different distro Ubuntu != &#381;²2à?bs&#8212;Óüð&#339;Xþú

CDInfo cleared
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
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
Download status=success:D:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:D:\ubuntu\install\MD5SUMS
      Verifying signature D:\ubuntu\install\MD5SUMS.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 04/15/08 00:26:15 GMT Daylight Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=cancel
User cancelled download, quitting.


```

and the second log...

```

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nst2F.tmp
detect_all
Parsing cmdline "D:\ubuntu-backup\Wubi-8.04-beta-rev487sh.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=510 MB
arch=i386
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD Z:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive I:\ubuntu
Found InstallationDrive I:\ubuntu
AlreadyInstalled=true OldInstallationDrive=I: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1710; Volume name ; Max #/chars in vol name 1806184; Volume Serial # 2090316815; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1710; Volume name ; Max #/chars in vol name 1806188; Volume Serial # -663608010; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem I:
Drive & Path name 1710; Volume name MAIN BIG HD; Max #/chars in vol name 1806196; Volume Serial # 401082415; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive I: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 1434032; Volume name ; Max #/chars in vol name 74; Volume Serial # 2090316815; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = I:
FreeSpace in I: is 67065
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=IE
Locale=en_IE.UTF-8
TimeZone=Europe/Dublin
Domain=localdomain
HostName=bettyblue
ComputerName=BETTYBLUE
EnvUsername=Richey Ward
UserDomain=BETTYBLUE
UserInfoName=Richey Ward
UserProfileFolder=C:\Documents and Settings\Richey Ward
UserProfileName=Richey Ward 
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1772; Volume name ; Max #/chars in vol name 1959776; Volume Serial # 2090316815; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Skipping drive C:, not enough free space 4072 <= 5000
IsValidFileSystem D:
Drive & Path name 1772; Volume name ; Max #/chars in vol name 1959780; Volume Serial # -663608010; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
IsValidFileSystem I:
Drive & Path name 1772; Volume name MAIN BIG HD; Max #/chars in vol name 1959788; Volume Serial # 401082415; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive I: has valid filesystem FAT32
Adding drive I:
Drive list = D:|I:
ChangeInstallationDrive to I:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nst2F.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\RICHEY~1\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=&#381;²2à?bs&#8212;Óüð&#339;Xþú
-i386 distro= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=
      ->isoKernel=
      ->distroVersion=
no distroversion
CDInfo cleared
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nst2F.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\RICHEY~1\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=&#381;²2à?bs&#8212;Óüð&#339;Xþú
-i386 distro= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=
      ->isoKernel=
      ->distroVersion=
no distroversion
CDInfo cleared
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
============ Installer ============
Ubuntu is already running, quitting
LeaveMainPage
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_IE.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
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
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different distro Ubuntu != &#381;²2à?bs&#8212;Óüð&#339;Xþú

CDInfo cleared
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD Z:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nst2F.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\RICHEY~1\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different distro Ubuntu != &#381;²2à?bs&#8212;Óüð&#339;Xþú

CDInfo cleared
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nst2F.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\RICHEY~1\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different distro Ubuntu != &#381;²2à?bs&#8212;Óüð&#339;Xþú

CDInfo cleared
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
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
Download status=success:D:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:D:\ubuntu\install\MD5SUMS
      Verifying signature D:\ubuntu\install\MD5SUMS.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 04/15/08 00:26:15 GMT Daylight Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=cancel
User cancelled download, quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nsv4A.tmp
detect_all
Parsing cmdline "D:\ubuntu-backup\Wubi-8.04-beta-rev487sh.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=510 MB
arch=i386
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD Z:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1710; Volume name ; Max #/chars in vol name 1813384; Volume Serial # 2090316815; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1710; Volume name ; Max #/chars in vol name 1813388; Volume Serial # -663608010; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem I:
Drive & Path name 1710; Volume name MAIN BIG HD; Max #/chars in vol name 1813400; Volume Serial # 401082415; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive I: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 1434032; Volume name ; Max #/chars in vol name 75; Volume Serial # 2090316815; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = I:
FreeSpace in I: is 67065
DetectBackupFolder
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=IE
Locale=en_IE.UTF-8
TimeZone=Europe/Dublin
Domain=localdomain
HostName=bettyblue
ComputerName=BETTYBLUE
EnvUsername=Richey Ward
UserDomain=BETTYBLUE
UserInfoName=Richey Ward
UserProfileFolder=C:\Documents and Settings\Richey Ward
UserProfileName=Richey Ward 
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
Can't open registry key! ()
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1772; Volume name ; Max #/chars in vol name 1963192; Volume Serial # 2090316815; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Skipping drive C:, not enough free space 4065 <= 5000
IsValidFileSystem D:
Drive & Path name 1772; Volume name ; Max #/chars in vol name 1963196; Volume Serial # -663608010; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
IsValidFileSystem I:
Drive & Path name 1772; Volume name MAIN BIG HD; Max #/chars in vol name 1963208; Volume Serial # 401082415; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive I: has valid filesystem FAT32
Adding drive I:
Drive list = D:|I:
ChangeInstallationDrive to D:
ChangeInstallationSize to 10
PopulateDistroList
DetectIso
      IsValidIso ispoath=D:\ubuntu\install\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nsv4A.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\RICHEY~1\LOCALS~1\Temp D:\ubuntu\install\hardy-desktop-i386.iso
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=&#381;²2à?bs&#8212;Óüð&#339;Xþú
-i386 distro= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=
      ->isoKernel=
      ->distroVersion=
no distroversion
CDInfo cleared
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nsv4A.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\RICHEY~1\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=&#381;²2à?bs&#8212;Óüð&#339;Xþú
-i386 distro= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=
      ->isoKernel=
      ->distroVersion=
no distroversion
CDInfo cleared
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nsv4A.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\RICHEY~1\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=&#381;²2à?bs&#8212;Óüð&#339;Xþú
-i386 distro= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=
      ->isoKernel=
      ->distroVersion=
no distroversion
CDInfo cleared
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
Locale=en_IE.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
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
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD Z:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=D:\ubuntu\install\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nsv4A.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\RICHEY~1\LOCALS~1\Temp D:\ubuntu\install\hardy-desktop-i386.iso
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different distro Ubuntu != &#381;²2à?bs&#8212;Óüð&#339;Xþú

CDInfo cleared
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nsv4A.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\RICHEY~1\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different distro Ubuntu != &#381;²2à?bs&#8212;Óüð&#339;Xþú

CDInfo cleared
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\RICHEY~1\LOCALS~1\Temp\nsv4A.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\RICHEY~1\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid  &#381;²2à?bs&#8212;Óüð&#339;Xþú

      cdversion= cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= cdcodename= cdsubversion= cdbuild= 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=&#381;²2à?bs&#8212;Óüð&#339;Xþú
 cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different distro Ubuntu != &#381;²2à?bs&#8212;Óüð&#339;Xþú

CDInfo cleared
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
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
Download status=success:D:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:D:\ubuntu\install\MD5SUMS
      Verifying signature D:\ubuntu\install\MD5SUMS.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 04/15/08 00:26:15 GMT Daylight Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=success:D:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=D:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from D:\ubuntu\install\hardy-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name D:\ubuntu\install\hardy-desktop-i386.iso; Volume name ; Max #/chars in vol name ; Volume Serial # -663608010; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive D: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
Drive & Path name D:\ubuntu\install\hardy-desktop-i386.iso; Volume name ; Max #/chars in vol name ; Volume Serial # -663608010; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive D: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=D:\ubuntu\disks\root.disk size=9000
AllocFile filename=D:\ubuntu\disks\home.disk size=0
AllocFile filename=D:\ubuntu\disks\swap.disk size=1000
UncompressFilesAfterInstall
Installation completed successfully!

```

I'm stumped but your program is a true asset to the ubuntu community. I wish you the very best of success with it, and any other projects you may have. :)

Edit:something I just noticed is that the name of the CD distro seems to be corrupted.... :s

---

### Post by ago on 2008-04-16
Error 13 is usually due to a corrupt ISO, you can verify that by comparing the MD5 of c:\ubuntu\install\boot\vmlinuz with the value in md5sums.txt within the ISO.
Which also explains the second issue.

---

### Post by Arabica Bean on 2008-04-17
Yep, the iso was corrupt when I downloaded it with wubi. I torrented a new iso, and that solved the problem. Many thanks

---

### Post by dasche on 2008-04-30
plz advise why cannot use the alternate iso? i cannot download the desktop iso again because having a slow connection....plz tell me some way of using the alt iso with wubi.........many thanks...:confused:

---

### Post by ago on 2008-04-30
> **dasche said:**
> plz advise why cannot use the alternate iso? i cannot download the desktop iso again because having a slow connection....plz tell me some way of using the alt iso with wubi.........many thanks...:confused:

The alternate ISO works very differently from the Live CD and at the moment the alternate ISO is not supported. Support is planned for 8.10.

---

### Post by Arabica Bean on 2008-04-30
I tried a whole load of workarounds with the alternate CD when I had the problem, and nothing worked.   My personal advice is to download the desktop iso file via torrent. You say that you have a slow connection.  I do too but trust me, it's worth the download!

---

