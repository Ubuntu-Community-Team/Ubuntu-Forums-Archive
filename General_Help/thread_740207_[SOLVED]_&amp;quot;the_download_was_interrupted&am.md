---
title: "[SOLVED] &amp;quot;the download was interrupted&amp;quot; but no error message"
date: 2008-03-30
forum: General Help
---

### Post by orengolan on 2008-03-30
I try to install wubi (wubi-8.04-beta-rev457.exe) on a vaio vista.
after entering the basic ubuntu details (user, password etc)
i get this error message:
the download was interrupted with the error:


but there is no error message so i don't know what to search for.

the log file say Download status=couldn't connect to host
here it is:
```
PLUGINSDIR=C:\Users\Yuka\AppData\Local\Temp\nse64EB.tmp
detect_all
Parsing cmdline "C:\Users\Yuka\Desktop\Wubi-8.04-beta-rev457.exe"
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
FreeSpace in c: is 47493
DetectBackupFolder
IsBackupFolder C:\
GMT=-7
Country=US
Locale=en_US.UTF-8
TimeZone=America/Denver
Domain=localdomain
HostName=Yuka-PC
ComputerName=YUKA-PC
EnvUsername=Yuka
UserDomain=Yuka-PC
UserInfoName=Yuka
UserProfileFolder=C:\Users\Yuka
UserProfileName=Yuka
ShowMainPage
Making drive list
Drive & Path name 1734; Volume name ; Max #/chars in vol name 7100224; Volume Serial # 642767501; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall.exe
Created C:\Windows\Uninstall.exe
Created reg key 1
Created reg key 2
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
Checking/Downloading Ubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg md5=
Download status=couldn't connect to host
Error downloading http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg, couldn'
Trying remote metalink2: http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=couldn't connect to host
Error downloading http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg, couldn'
The download was interrupted with the error: 
```

any ideas?
i really want to run ubuntu side by side with vista.

thanks

---

### Post by ago on 2008-03-30
Either your connection was down or the sourceforge server was down. If you retry it should work.

---

### Post by Termy58 on 2008-03-30
That is a pretty old revision, try it with a newer version

[http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)

---

### Post by wingmanjd on 2008-04-01
I receive this error as well on the latest version (Wubi-8.04-beta-rev469.exe) on two different machines.  One is a home built (Win XP Pro, SP3) and the other is a Dell Inspiron 1100 (Win XP Pro, SP3).

---

### Post by ago on 2008-04-01
Can you pls attach the wubi log in %temp%?

---

### Post by wingmanjd on 2008-04-01
I hope these are what you're looking for.

Logs attached

---

### Post by ago on 2008-04-01
There should be another log in your temp folder, you can access such folder by typing %temp% in windows explorer

---

### Post by wingmanjd on 2008-04-01
My bad.

Temp log attached from version rev472

---

### Post by ago on 2008-04-01
Confirmed I am on it

---

### Post by disabled_mastershake16 on 2008-04-01
Hey, this is weird, it just happened to me, and i just registered to tell you that, im with you on this problem and its funny how recent these posts are lol great timing but, i have no clue about linux lol i just wanna try it very badly!!!

---

### Post by ago on 2008-04-01
rev 474 should be good

---

### Post by disabled_mastershake16 on 2008-04-01
No, it doesn't work, i JUST tried, literally seconds ago

Same thing

also if this helps, for some reason my computer, after i put it on a wireless network doesnt allow programs like Limewire and some programs to even install or access internet, for instance Limewire and Google Earth wont work!!! It's weird

---

### Post by ago on 2008-04-01
hmm 474 works here...

---

### Post by disabled_mastershake16 on 2008-04-01
Is there a manual way? that i can still have XP and Ubuntu though?

Please help me

My computer is gay
The program wont connect to the internet is the problem.....
I have no firewall either..... any help?

---

### Post by ago on 2008-04-01
Try to delete the ubuntu folder manually. Then run 474 again.
That assumes that you can download files  from the internet
If you can't download the ubuntu-daily iso from another machine and copy it over

---

### Post by disabled_mastershake16 on 2008-04-01
Same things..... damnit!!!!

Any other ways?

Do you know if using Virtual Box works?

Any i can download files but for some reaosn some programs cant use internet...

---

### Post by ago on 2008-04-01
Do you have internet connection?
If yes then please post the wubi log (type %temp% in windows explorer)

---

### Post by disabled_mastershake16 on 2008-04-01
Here it is[PHP]

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\MANCHI~1\LOCALS~1\Temp\nse57.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Manchinton\Desktop\Wubi-8.04-beta-rev474.exe" 
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
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
Drive & Path name 1702; Volume name ; Max #/chars in vol name 1847844; Volume Serial # 685530138; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # 685530138; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in C: is 18775
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=manchint-iqxuj7
ComputerName=MANCHINT-IQXUJ7
EnvUsername=Manchinton
UserDomain=MANCHINT-IQXUJ7
UserInfoName=Manchinton
UserProfileFolder=C:\Documents and Settings\Manchinton
UserProfileName=Manchinton 
ShowMainPage
Making drive list
Drive & Path name 1742; Volume name ; Max #/chars in vol name 1851732; Volume Serial # 685530138; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 15
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
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
Download status=Failed to connect to 66.35.250.210: Bad access
Error downloading http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg, Failed 
Trying remote metalink2: http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=Failed to connect to 66.35.250.210: Bad access
Error downloading http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg, Failed 
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\MANCHI~1\LOCALS~1\Temp\nse115.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Manchinton\Desktop\Wubi-8.04-beta-rev474.exe" 
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
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
Drive & Path name 1702; Volume name ; Max #/chars in vol name 1847844; Volume Serial # 685530138; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # 685530138; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in C: is 18717
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=manchint-iqxuj7
ComputerName=MANCHINT-IQXUJ7
EnvUsername=Manchinton
UserDomain=MANCHINT-IQXUJ7
UserInfoName=Manchinton
UserProfileFolder=C:\Documents and Settings\Manchinton
UserProfileName=Manchinton 
ShowMainPage
Making drive list
Drive & Path name 1742; Volume name ; Max #/chars in vol name 1851724; Volume Serial # 685530138; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
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
Download status=Failed to connect to 66.35.250.210: Bad access
Error downloading http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg, Failed 
Trying remote metalink2: http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=Failed to connect to 66.35.250.210: Bad access
Error downloading http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg, Failed 
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\MANCHI~1\LOCALS~1\Temp\nsi11C.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Manchinton\Desktop\Wubi-8.04-beta-rev474.exe" 
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
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
Drive & Path name 1702; Volume name ; Max #/chars in vol name 1847844; Volume Serial # 685530138; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # 685530138; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in C: is 18717
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=manchint-iqxuj7
ComputerName=MANCHINT-IQXUJ7
EnvUsername=Manchinton
UserDomain=MANCHINT-IQXUJ7
UserInfoName=Manchinton
UserProfileFolder=C:\Documents and Settings\Manchinton
UserProfileName=Manchinton 
ShowMainPage
Making drive list
Drive & Path name 1742; Volume name ; Max #/chars in vol name 1851724; Volume Serial # 685530138; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
ShowMainPage
Making drive list
Drive & Path name 1742; Volume name ; Max #/chars in vol name 1890332; Volume Serial # 685530138; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 10
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
Download status=Failed to connect to 66.35.250.210: Bad access
Error downloading http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg, Failed 
Trying remote metalink2: http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=Failed to connect to 66.35.250.210: Bad access
Error downloading http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg, Failed 
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\MANCHI~1\LOCALS~1\Temp\nsh125.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Manchinton\Desktop\Wubi-8.04-beta-rev474.exe" 
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
Drive & Path name 1702; Volume name ; Max #/chars in vol name 1847844; Volume Serial # 685530138; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # 685530138; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in C: is 18719
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=manchint-iqxuj7
ComputerName=MANCHINT-IQXUJ7
EnvUsername=Manchinton
UserDomain=MANCHINT-IQXUJ7
UserInfoName=Manchinton
UserProfileFolder=C:\Documents and Settings\Manchinton
UserProfileName=Manchinton 
ShowMainPage
Making drive list
Drive & Path name 1742; Volume name ; Max #/chars in vol name 1851172; Volume Serial # 685530138; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 15
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
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
Download status=Failed to connect to 66.35.250.210: Bad access
Error downloading http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg, Failed 
Trying remote metalink2: http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=Failed to connect to 66.35.250.210: Bad access
Error downloading http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg, Failed 
The download was interrupted with the error: [/PHP]

---

### Post by ago on 2008-04-01
That looks more like an connection problem on your side.
Maybe you can still download files manually, in such case grab the iso from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) and place it in the same folder as wubi.exe

---

### Post by TehDuke on 2008-04-19
I just had the same message.

---

### Post by ago on 2008-04-19
can you attach the logs please? they are in the user temp folder(%temp%)

consider though that servers are a bit busy at release days

---

### Post by The Exquisite on 2008-04-19
Same problem here.

---

### Post by ago on 2008-04-19
Please download the ISO manually ([http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)) and place it in the same folder as Wubi exe
There is an issue with the server will be fixed later on today

---

### Post by sd25 on 2008-05-26
hi..i also have the same problem..how do i fix it? ..i really want to try wubi out but the error "download was interrupted" keeps showing up.thnx

---

### Post by full_hyperion on 2008-05-30
I also got this problem, and with me, the computer time was wrong (somewhere in 2002). 

After setting this right the problem was solved.

---

### Post by americanknight on 2008-12-23
Yeah, for me the problem was also fixed by changing my date (which was 2003) to today...my anniversary. Must be a sign to go out by my wife some flowers.

---

### Post by jamesspratt on 2009-02-24
Same prob, suspected it miught error as my work network was a little busy today giving it some stop/startiness.
Rebooted my machine then ran the uninstall and all ubuntu files deleted ok this time. Then ran WUBI again.

---

