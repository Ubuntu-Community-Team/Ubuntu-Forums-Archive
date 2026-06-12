---
title: "error msg: &quot;Could not access the CD&quot;"
date: 2008-03-24
forum: General Help
---

### Post by tanguy_k on 2008-03-24
Hello

I tried wubi that comes with Kubuntu 8.04 - KDE4 (kubuntu-kde4-8.04-beta-desktop-i386.iso) and I get stuck at the end of the step:
"Creating image"
It reads the CD until 100% (or almost)
and I always get the message:
"Could not access the CD, please make sure other applications blabla"

Of course Wubi is the only application accessing the CD. I tried to download different .iso files and burn them. It does not come from this a bad CD/.iso either.

I tried to find other posts/bugs reports with the same problem with no luck :/

I can reproduce the bug everytime

Any idea?

---

### Post by ago on 2008-03-24
There is a wubi log in %temp% please post it here.
Also check the md5 of the CD with the one you find on the website you downloaded it from.

---

### Post by tanguy_k on 2008-03-24
thx for the info

I tried with kubuntu 8.04 AMD/i386/KDE4 and now I'm trying with beta 1 ubuntu-8.04-desktop-i386 so the one that should have been tested the most.

Here is the log of one of the fealure:

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\tanguy_k\LOCALS~1\Temp\nsk5.tmp
detect_all
Parsing cmdline D:\wubi.exe
debug=, 32bit=, cdboot=
arch=amd64
DetectCD
      Is Valid CD D:
      IsValid Kubuntu-KDE4 8.04 "Hardy Heron" - Beta i386 (20080318.2)
      cdversion=8.04 cddistro=Kubuntu-KDE4 cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrfullname=Kubuntu-KDE4-i386 distro= cddistro=Kubuntu-KDE4 cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/kubuntu-kde4-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Kubuntu-KDE4 8.04 "Hardy Heron" - Beta i386 (20080318.2)
Found CD D:
Found CD cddrive=D:
Changing icon to Kubuntu-KDE4.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in C: is 5319
DetectBackupFolder
IsBackupFolder C:\
GMT=1
Country=FR
Locale=en_US.UTF-8
LayoutCode=fr
TimeZone=Europe/Paris
Domain=localdomain
HostName=lenovo
ComputerName=LENOVO
EnvUsername=tanguy_k
UserDomain=LENOVO
UserInfoName=tanguy_k
UserProfileFolder=C:\Documents and Settings\tanguy_k
UserProfileName=tanguy_k 
ShowMainPage
Making drive list
Drive & Path name 1736; Volume name ; Max #/chars in vol name 1809408; Volume Serial # 1825803810; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 4
PopulateDistroList
DistroList = Kubuntu-KDE4
PopulateLanguageListBox
      GetDistroInfo distrfullname=Kubuntu-KDE4-i386 distro=Kubuntu-KDE4 cddistro=Kubuntu-KDE4 cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/kubuntu-kde4-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Kubuntu-KDE4
Changing icon to Kubuntu-KDE4.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrfullname=Kubuntu-KDE4-i386 distro=Kubuntu-KDE4 cddistro=Kubuntu-KDE4 cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/kubuntu-kde4-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall.exe
Created C:\WINDOWS\Uninstall.exe
Created reg key 1
Created reg key 2
CopyDistFolders
GetIso
DetectCD
      Is Valid CD D:
      IsValid Kubuntu-KDE4 8.04 "Hardy Heron" - Beta i386 (20080318.2)
      cdversion=8.04 cddistro=Kubuntu-KDE4 cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrfullname=Kubuntu-KDE4-i386 distro=Kubuntu-KDE4 cddistro=Kubuntu-KDE4 cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/kubuntu-kde4-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Kubuntu-KDE4 8.04 "Hardy Heron" - Beta i386 (20080318.2)
Found CD D:
Found CD cddrive=D:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
We are connected and can get the ISO md5, skipping CheckCD
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: LastError = 1 Incorrect function.

Asking user to retry CD2ISO
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO was cancelled, quitting

---

### Post by tanguy_k on 2008-03-24
OK it works with ubuntu-8.04-beta1-i386
So there is definitely a bug with Kubuntu-8.04.

I guess it should be a stupid bug....

---

### Post by evdjj3j on 2008-03-26
I am receiving the same error msg, but i am using ubuntu-8.04-beta-desktop-i386.  Below is the Wubi install log.

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\user\LOCALS~1\Temp\nsl5.tmp
detect_all
Parsing cmdline E:\wubi.exe
debug=, 32bit=, cdboot=
arch=amd64
DetectCD
      Is Valid CD E:
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrfullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in c: is 167680
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=user-desktop
ComputerName=USER-DESKTOP
EnvUsername=user
UserDomain=USER-DESKTOP
UserInfoName=user
UserProfileFolder=C:\Documents and Settings\user
UserProfileName=user 
ShowMainPage
Making drive list
Drive & Path name 1736; Volume name ; Max #/chars in vol name 1734052; Volume Serial # 1752487373; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Adding drive C:
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
ShowMainPage
Making drive list
Drive & Path name 1736; Volume name ; Max #/chars in vol name 1840140; Volume Serial # 1752487373; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Adding drive C:
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall.exe
Created C:\WINDOWS\Uninstall.exe
Created reg key 1
Created reg key 2
CopyDistFolders
GetIso
DetectCD
      Is Valid CD E:
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
We are connected and can get the ISO md5, skipping CheckCD
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: LastError = 23 Data error (cyclic redundancy check).

Asking user to retry CD2ISO
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: LastError = 23 Data error (cyclic redundancy check).

Asking user to retry CD2ISO
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO was cancelled, quitting
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\user\LOCALS~1\Temp\nsdF.tmp
detect_all
Parsing cmdline E:\wubi.exe
debug=, 32bit=, cdboot=
arch=amd64
DetectCD
      Is Valid CD E:
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrfullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
FreeSpace in c: is 167678
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=user-desktop
ComputerName=USER-DESKTOP
EnvUsername=user
UserDomain=USER-DESKTOP
UserInfoName=user
UserProfileFolder=C:\Documents and Settings\user
UserProfileName=user 
ShowMainPage
Making drive list
Drive & Path name 1736; Volume name ; Max #/chars in vol name 1734052; Volume Serial # 1752487373; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall.exe
Created C:\WINDOWS\Uninstall.exe
Created reg key 1
Created reg key 2
CopyDistFolders
GetIso
DetectCD
      Is Valid CD E:
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
We are connected and can get the ISO md5, skipping CheckCD
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: LastError = 23 Data error (cyclic redundancy check).

Asking user to retry CD2ISO
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: LastError = 23 Data error (cyclic redundancy check).

Asking user to retry CD2ISO

---

### Post by evdjj3j on 2008-03-26
I also checked the MD5 of the ISO, checked out ok.  I noticed looking at the log file the error is a CRC error reading from the hard drive.  I have an Nvidia RAID 0 array, could this possibly be causing the problem.  I have not had any such errors in Windows so I don't think I have a defective drive.

---

### Post by juanluisslp on 2008-03-30
i have the same problem with Kubuntu

---

### Post by ago on 2008-03-31
[https://bugs.launchpad.net/wubi/+bug/207137](https://bugs.launchpad.net/wubi/+bug/207137)

I will work on that today/tomorrow, but it is an annoying bug because I cannot reproduce it myself and hence will need your help to test. Please subscribe to the bug to be notified when a fix is available.

To test you will need to use a new version of wubi (when it will be available) with the CD/CDDRIVE that did NOT work.

---

### Post by evdjj3j on 2008-03-31
I did some more testing and used Nero Image Drive to mount the ISO as a cd.  I then tried to install and had no problems until it asked to reboot.  After the reboot Ubuntu started boot and hung.  I booted back into Windows and uninstalled Ubuntu.  This leads me to believe the RAID controller is not the problem.

---

### Post by ago on 2008-04-01
Yes raid is not supported and there is not much I can do there.
But at least the CD ISO extraction should be fixed in latest builds (468+)

---

### Post by bmwracer0 on 2008-04-02
I am having the same problem, no raid at all. XP MCE2005

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Michael\LOCALS~1\Temp\nsm37.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Michael\Desktop\Wubi-8.04-beta-rev474.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=i386
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
      IsValid Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Alpha 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
Found CD D:
Found CD cddrive=D:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
Drive & Path name 1702; Volume name SQ004033P03; Max #/chars in vol name 1838072; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name Admin; Volume name SQ004033P03; Max #/chars in vol name ; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in C: is 9486
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=toshiba-user
ComputerName=TOSHIBA-USER
EnvUsername=Michael
UserDomain=TOSHIBA-USER
UserInfoName=Michael
UserProfileFolder=C:\Documents and Settings\Michael
UserProfileName=Michael 
ShowMainPage
Making drive list
Drive & Path name 1742; Volume name SQ004033P03; Max #/chars in vol name 1839112; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 6
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
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
      IsValid Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Alpha 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
Found CD D:
Found CD cddrive=D:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
We are connected and can get the ISO md5, skipping CheckCD
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: LastError = 1 Incorrect function.

Asking user to retry CD2ISO
CD2ISO C:\ubuntu\install\installation.iso

I tried using the .exe and an .iso, burning the .iso, and mounting the iso with daemon tools. I also tried the same three methods with alpha 5, and it gives the same result. HELP!

---

### Post by ago on 2008-04-02
At what stage is the progressbar of "creating image"? Finished/almost finished or at the beginning? Also can you please run an md5 check on the CD comparing with the md5 available on the website you downloaded it from?

---

### Post by bmwracer0 on 2008-04-02
It hits 100% when it fails. What method should I be looking to use? Using the CD I burned? Mounting the image? The MD5 checks correctly too.

---

### Post by ago on 2008-04-02
Can you please try [http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev475.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev475.exe)
If it still does not work please provide the log

---

### Post by bmwracer0 on 2008-04-02
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Michael\LOCALS~1\Temp\nsiEE.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Michael\Desktop\Wubi-8.04-beta-rev475.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=i386
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
      IsValid Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Alpha 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
Found CD D:
Found CD cddrive=D:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
Drive & Path name 1702; Volume name SQ004033P03; Max #/chars in vol name 1837848; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1702; Volume name My Book 250; Max #/chars in vol name 1837856; Volume Serial # 1746946680; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1702; Volume name My Book 320; Max #/chars in vol name 1837864; Volume Serial # -599912659; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive I: has valid filesystem NTFS
Drive & Path name Admin; Volume name SQ004033P03; Max #/chars in vol name ; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in I: is 109817
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder I:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=toshiba-user
ComputerName=TOSHIBA-USER
EnvUsername=Michael
UserDomain=TOSHIBA-USER
UserInfoName=Michael
UserProfileFolder=C:\Documents and Settings\Michael
UserProfileName=Michael 
ShowMainPage
Making drive list
Drive & Path name 1742; Volume name SQ004033P03; Max #/chars in vol name 1841520; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive & Path name 1742; Volume name My Book 250; Max #/chars in vol name 1841528; Volume Serial # 1746946680; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Adding drive F:
Drive & Path name 1742; Volume name My Book 320; Max #/chars in vol name 1841536; Volume Serial # -599912659; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive I: has valid filesystem NTFS
Adding drive I:
Drive list = C:|F:|I:
ChangeInstallationDrive to C:
ChangeInstallationSize to 6
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
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
      IsValid Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Alpha 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
Found CD D:
Found CD cddrive=D:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
We are connected and can get the ISO md5, skipping CheckCD
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: The number of bytes written doesn't equal the disk size!
Asking user to retry CD2ISO
User did not select to retry CD2ISO, quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Michael\LOCALS~1\Temp\nsgF7.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Michael\Desktop\Wubi-8.04-beta-rev475.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=i386
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
      IsValid Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Alpha 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
Found CD D:
Found CD cddrive=D:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
Drive & Path name 1702; Volume name SQ004033P03; Max #/chars in vol name 1868224; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1702; Volume name My Book 250; Max #/chars in vol name 1868232; Volume Serial # 1746946680; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1702; Volume name My Book 500; Max #/chars in vol name 1868236; Volume Serial # 278846377; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive G: has valid filesystem NTFS
Drive & Path name Admin; Volume name SQ004033P03; Max #/chars in vol name ; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in G: is 66763
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder G:\
IsBackupFolder I:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=toshiba-user
ComputerName=TOSHIBA-USER
EnvUsername=Michael
UserDomain=TOSHIBA-USER
UserInfoName=Michael
UserProfileFolder=C:\Documents and Settings\Michael
UserProfileName=Michael 
ShowMainPage
Making drive list
Drive & Path name 1742; Volume name SQ004033P03; Max #/chars in vol name 1786456; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive & Path name 1742; Volume name My Book 250; Max #/chars in vol name 1786464; Volume Serial # 1746946680; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Adding drive F:
Drive & Path name 1742; Volume name My Book 500; Max #/chars in vol name 1786468; Volume Serial # 278846377; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive G: has valid filesystem NTFS
Adding drive G:
Drive & Path name 1742; Volume name My Book 320; Max #/chars in vol name 1786476; Volume Serial # -599912659; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive I: has valid filesystem NTFS
Adding drive I:
Drive list = C:|F:|G:|I:
ChangeInstallationDrive to C:
ChangeInstallationSize to 6
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Michael\LOCALS~1\Temp\nsvFA.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Michael\Desktop\Wubi-8.04-beta-rev475.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=i386
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
      IsValid Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Alpha 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
Found CD D:
Found CD cddrive=D:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
Drive & Path name 1702; Volume name SQ004033P03; Max #/chars in vol name 1859536; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name Admin; Volume name SQ004033P03; Max #/chars in vol name ; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in C: is 9424
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=toshiba-user
ComputerName=TOSHIBA-USER
EnvUsername=Michael
UserDomain=TOSHIBA-USER
UserInfoName=Michael
UserProfileFolder=C:\Documents and Settings\Michael
UserProfileName=Michael 
ShowMainPage
Making drive list
Drive & Path name 1742; Volume name SQ004033P03; Max #/chars in vol name 1839984; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 6
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
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
      IsValid Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Alpha 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
Found CD D:
Found CD cddrive=D:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
We are connected and can get the ISO md5, skipping CheckCD
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: The number of bytes written doesn't equal the disk size!
Asking user to retry CD2ISO
User did not select to retry CD2ISO, quitting.

---

### Post by ago on 2008-04-02
can you pls redownload and try again?
also let me know if the cd extraction is much slower.

---

### Post by bmwracer0 on 2008-04-02
i redownloaded using the torrent, and it did take longer, but it failed. now i am retrying the download straight from the site.

---

### Post by ago on 2008-04-02
I meant wubi rev 475 (476 has been reverted to 474 code)

---

### Post by bmwracer0 on 2008-04-02
thats with a new cd download, and a new 475 download

wouldnt let me post the txt file cause it was too big, and couldnt be posted. sorry

and yes, it was very slow this time

---

