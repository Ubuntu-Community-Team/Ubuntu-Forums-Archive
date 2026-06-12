---
title: "Wubi Crashes on startup"
date: 2008-04-10
forum: General Help
---

### Post by Noremacam on 2008-04-10
I downloaded the latest version of wubi off their website(wubi-installer.org/). It crashes instantly upon launching. I redownloaded it to verify it wasn't a bad download and I got the same result.

Its the typical windows error message:

 "Windows based UBuntu Installer has encountered a problem and needs to close. We are sorry for the invonvenience."

It then asks me if I want to send a windows error report. What gives?

---

### Post by ago on 2008-04-10
There should be a wubi log file in %temp% please post it here. Also make sure you are using wubi rev 482

---

### Post by novaa on 2008-04-11
Both rev 479 and rev 482 crashes here as well.

The installer, 1.2MB, crashes everytime i double click on it. No way to install Wubi...

---

### Post by novaa on 2008-04-11
This is my logfile

> 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\yyyy\LOCALS~1\Temp\nsq1CF.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\yyyy\Application Data\Opera\Opera 9.5 beta\profile\cache4\temporary_download\Wubi-8.04-beta-rev482.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1022 MB
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
Drive & Path name 1711; Volume name ; Max #/chars in vol name 1805600; Volume Serial # -119904579; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1415840; Volume name ; Max #/chars in vol name 59; Volume Serial # -119904579; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 50381
DetectBackupFolder
IsBackupFolder C:\
GMT=2
Country=NO
Locale=en_AU.UTF-8
TimeZone=Europe/Oslo
Domain=localdomain
HostName=denial
ComputerName=DENIAL
EnvUsername=yyyy
UserDomain=DENIAL
UserInfoName=yyyy
UserProfileFolder=C:\Documents and Settings\yyyy
UserProfileName=yyyy 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\yyyy\LOCALS~1\Temp\nsz1D1.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\yyyy\Application Data\Opera\Opera 9.5 beta\profile\cache4\temporary_download\Wubi-8.04-beta-rev482.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1022 MB
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
Drive & Path name 1711; Volume name ; Max #/chars in vol name 1805600; Volume Serial # -119904579; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1415840; Volume name ; Max #/chars in vol name 59; Volume Serial # -119904579; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 50379
DetectBackupFolder
IsBackupFolder C:\
GMT=2
Country=NO
Locale=en_AU.UTF-8
TimeZone=Europe/Oslo
Domain=localdomain
HostName=denial
ComputerName=DENIAL
EnvUsername=yyyy
UserDomain=DENIAL
UserInfoName=yyyy
UserProfileFolder=C:\Documents and Settings\yyyy
UserProfileName=yyyy 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\yyyy\LOCALS~1\Temp\nsa1DA.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\yyyy\Desktop\Wubi-8.04-beta-rev482.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1022 MB
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
Drive & Path name 1711; Volume name ; Max #/chars in vol name 1805576; Volume Serial # -119904579; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1415584; Volume name ; Max #/chars in vol name 59; Volume Serial # -119904579; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 50375
DetectBackupFolder
IsBackupFolder C:\
GMT=2
Country=NO
Locale=en_AU.UTF-8
TimeZone=Europe/Oslo
Domain=localdomain
HostName=denial
ComputerName=DENIAL
EnvUsername=yyyy
UserDomain=DENIAL
UserInfoName=yyyy
UserProfileFolder=C:\Documents and Settings\yyyy
UserProfileName=yyyy 


---

### Post by ago on 2008-04-11
I will provide a build with more debugging info tonight for you to try

---

### Post by ago on 2008-04-11
Can you please try with [http://people.ubuntu.com/~evand/tmp/Wubi-8.04-beta-rev482.exe](http://people.ubuntu.com/~evand/tmp/Wubi-8.04-beta-rev482.exe)
and provide log if it fails?

---

### Post by Noremacam on 2008-04-11
Okay... trying it now

---

### Post by Noremacam on 2008-04-11
> **ago said:**
> Can you please try with [http://people.ubuntu.com/~evand/tmp/Wubi-8.04-beta-rev482.exe](http://people.ubuntu.com/~evand/tmp/Wubi-8.04-beta-rev482.exe)
and provide log if it fails?

OK, this time the file you posted works fine(I only tested it to the point it brought up the window, which is farther than I got before) but the original rev482 doesn't at all.

Here's the log file using the **ORIGINAL** wubi executable:

P.S. I replaced every instance in the log of my real name with my ubuntu name for obvious reasons

> ============ Installer ============
PLUGINSDIR=C:\DOCUME~1\CAMERO~1\LOCALS~1\Temp\nsl8D.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Noremacam\Desktop\Wubi-8.04-beta-rev482.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive E:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 1803736; Volume Serial # -600015256; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem E:
Drive & Path name 1711; Volume name Backup; Max #/chars in vol name 1803744; Volume Serial # 2015193938; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive E: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1427360; Volume name ; Max #/chars in vol name 35; Volume Serial # -600015256; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 79715
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder E:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=noremacam
ComputerName=NOREMACAM
EnvUsername=######
UserDomain=NOREMACAM
UserInfoName=Noremacam
UserProfileFolder=C:\Documents and Settings\Noremacam
UserProfileName=Noremacam 

And here's the log from the wubi executable you posted:

> ============ Installer ============
PLUGINSDIR=C:\DOCUME~1\CAMERO~1\LOCALS~1\Temp\nsq8F.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Noremacam\Desktop\Wubi-8.04-beta-rev482(2).exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive E:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 1803648; Volume Serial # -600015256; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem E:
Drive & Path name 1711; Volume name Backup; Max #/chars in vol name 1803656; Volume Serial # 2015193938; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive E: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1427160; Volume name ; Max #/chars in vol name 34; Volume Serial # -600015256; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 79713
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder E:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=noremacam
ComputerName=NOREMACAM
EnvUsername=Noremacam
UserDomain=Noremacam
UserInfoName=Noremacam
UserProfileFolder=C:\Documents and Settings\Noremacam
UserProfileName=Noremacam
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1754; Volume name ; Max #/chars in vol name 1806552; Volume Serial # -600015256; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem E:
Drive & Path name 1754; Volume name Backup; Max #/chars in vol name 1806560; Volume Serial # 2015193938; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive E: has valid filesystem NTFS
Adding drive E:
Drive list = C:|E:
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
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-amd64.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips

---

### Post by bmfgeorgin2 on 2008-04-11
I have the same problem what wrong?

---

### Post by ago on 2008-04-11
Sorry,

can you please redownload [http://people.ubuntu.com/~evand/tmp/Wubi-8.04-beta-rev482.exe](http://people.ubuntu.com/~evand/tmp/Wubi-8.04-beta-rev482.exe) 

run it again and submit the logo?

---

### Post by Noremacam on 2008-04-11
no problem. Here's another log from the last one you posted:

> ============ Installer ============
PLUGINSDIR=C:\DOCUME~1\NOREMA~1\LOCALS~1\Temp\nspFE.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\**(omited)**\Desktop\Wubi-8.04-beta-rev482(3).exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1023 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive E:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 1801456; Volume Serial # -600015256; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem E:
Drive & Path name 1711; Volume name Backup; Max #/chars in vol name 1801464; Volume Serial # 2015193938; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive E: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1427160; Volume name ; Max #/chars in vol name 30; Volume Serial # -600015256; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 79740
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder E:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=Noremacam
ComputerName=NOREMACAM
EnvUsername=**(omited)**
UserDomain=NOREMACAM
UserInfoName=**(omited)**
UserProfileFolder=C:\Documents and Settings\Noremacam
UserProfileName=**(omited)**
DetectNetworkSettings
NicNumber=1
NicNumber=2
ReadReg
ReadReg_Multi_SZ 1
ReadReg_Multi_SZ 2
ReadReg_Multi_SZ 3
ReadReg_Multi_SZ finish
NicNumber=3
NicNumber=4
NicNumber=5
NicNumber=6
NicNumber=7
NicNumber=8
NicNumber=9
NicNumber=10
NicNumber=11
ReadReg
ReadReg_Multi_SZ 1
ReadReg_Multi_SZ 2
ReadReg_Multi_SZ 3
ReadReg_Multi_SZ finish
NicNumber=12
NicNumber=13
NicNumber=14
NicNumber=15
NicNumber=16
NicNumber=17
NicNumber=18
NicNumber=19
DefaultGateway=192.168.1.1, IPAddress=192.168.1.9 SubnetMask=255.255.255.0 NameServer=208.67.222.222
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1754; Volume name ; Max #/chars in vol name 1797296; Volume Serial # -600015256; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem E:
Drive & Path name 1754; Volume name Backup; Max #/chars in vol name 1797304; Volume Serial # 2015193938; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive E: has valid filesystem NTFS
Adding drive E:
Drive list = C:|E:
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
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-amd64.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips

---

### Post by bmfgeorgin2 on 2008-04-11
ok it works

---

### Post by ago on 2008-04-12
that might be a random result. I will upload a special build later on today

---

### Post by ago on 2008-04-12
Can you please try [http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev484sh.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev484sh.exe) and let me know whether it crashes or not (+log)?

Thanks

---

### Post by w3stfa11 on 2008-04-12
I'm getting a similar error.

Wubi says:

Wubi has generated errors and will be closed by Windows. You will need to restart the program.

I'm using Win2000. The first time I ran the wubi, it worked fine but I interrupted it while it was downloading Xubuntu. 

Using Wubi-8.04-beta-rev482.exe. 

Log is here:
[http://pastebin.com/m6d40d102](http://pastebin.com/m6d40d102)

Edit: Ok, rev486sh is working.

---

