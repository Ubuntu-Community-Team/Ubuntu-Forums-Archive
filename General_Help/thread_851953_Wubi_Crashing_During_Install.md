---
title: "Wubi Crashing During Install"
date: 2008-07-07
forum: General Help
---

### Post by Sun_Paladin on 2008-07-07
Hi. I an American student in Japan using a Toshiba Dynabook laptop with an Intel Celeron M CPU 430 @ 1.73 GHz, 1.0GB of ram, Mobile Intel 945GM/GU Express Chipset, Windows Vista Basic, and plenty of hard drive space at this moment. I have downloaded the ubuntu-8.04.1-desktop-i386 iso and the Wubi-8.04.1 installer exe. I have placed both of these files in a folder on my desktop and when I try to run the installer I get a nasty little error mostly in Japanese, but enough English to tell me that Wubi crashed during the beginning of install. What I want to know is first of all why is Wubi crashing at the very beginning of the install and second what can I do to fix this? This school I am at has a very fast internet connection so downloading another copy of the iso would not be a problem. I will post the error code beneath this. I apologize that most of the error marker id's or whatever they are called are in Japanese, but the errors themselves are in English. I thought maybe someone might have encountered this before and would might know what the Japanese is actually saying. Thank you for any help in assisting me with this confusing problem.

&#21839;&#38988;&#12398;&#32626;&#21517;:
  &#21839;&#38988;&#12452;&#12505;&#12531;&#12488;&#21517;:	APPCRASH
  &#12450;&#12503;&#12522;&#12465;&#12540;&#12471;&#12519;&#12531;&#21517;:	Wubi-8.04.1.exe
  &#12450;&#12503;&#12522;&#12465;&#12540;&#12471;&#12519;&#12531;&#12398;&#12496;&#12540;&#12472;&#12519;&#12531;:	8.4.1.0
  &#12450;&#12503;&#12522;&#12465;&#12540;&#12471;&#12519;&#12531;&#12398;&#12479;&#12452;&#12512;&#12473;&#12479;&#12531;&#12503;:	47eebf2f
  &#38556;&#23475;&#12514;&#12472;&#12517;&#12540;&#12523;&#12398;&#21517;&#21069;:	StackHash_c5f0
  &#38556;&#23475;&#12514;&#12472;&#12517;&#12540;&#12523;&#12398;&#12496;&#12540;&#12472;&#12519;&#12531;:	6.0.6000.16386
  &#38556;&#23475;&#12514;&#12472;&#12517;&#12540;&#12523;&#12398;&#12479;&#12452;&#12512;&#12473;&#12479;&#12531;&#12503;:	4549bdc9
  &#20363;&#22806;&#12467;&#12540;&#12489;:	c0000374
  &#20363;&#22806;&#12458;&#12501;&#12475;&#12483;&#12488;:	000af1c9
  OS &#12496;&#12540;&#12472;&#12519;&#12531;:	6.0.6000.2.0.0.768.2
  &#12525;&#12465;&#12540;&#12523; ID:	2057
  &#36861;&#21152;&#24773;&#22577; 1:	c5f0
  &#36861;&#21152;&#24773;&#22577; 2:	35fbee54db7fc9e4d6df8ff4a52cf0c3
  &#36861;&#21152;&#24773;&#22577; 3:	e863
  &#36861;&#21152;&#24773;&#22577; 4:	f25ae3cc267e86eaea55f3893b367b8b

&#12503;&#12521;&#12452;&#12496;&#12471;&#12540;&#12395;&#38306;&#12377;&#12427;&#22768;&#26126;&#12434;&#12362;&#35501;&#12415;&#12367;&#12384;&#12373;&#12356;:
  [http://go.microsoft.com/fwlink/?linkid=50163&clcid=0x0411](http://go.microsoft.com/fwlink/?linkid=50163&clcid=0x0411)

---

### Post by ago on 2008-07-07
There is a log in your user temp folder (type %temp% in windows explorer), please post it here.

---

### Post by Sun_Paladin on 2008-07-07
This was the most recent entry I could find in that folder. I can run the program again to check to see if this information is correct.

I had to run the program again to get this log.

CORRECTION:

============ Installer ============
PLUGINSDIR=C:\Users\Owner\AppData\Local\Temp\nsy95CE.tmp
detect_all
Parsing cmdline "C:\Users\Owner\Desktop\Ubuntu\Wubi-8.04.1.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1013 MB
arch=i386
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release i386 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release i386 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name S3A6065D001; Max #/chars in vol name 2245120; Volume Serial # 1044177234; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1754592; Volume name S3A6065D001; Max #/chars in vol name 59; Volume Serial # 1044177234; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 42075
DetectBackupFolder
IsBackupFolder C:\
GMT=9
Country=GB
Locale=ja_JP.UTF-8
TimeZone=Europe/London
Domain=localdomain
HostName=x9806184
ComputerName=X9806184
EnvUsername=Owner
UserDomain=X9806184
UserInfoName=Owner
UserProfileFolder=C:\Users\Owner
UserProfileName=Owner 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name S3A6065D001; Max #/chars in vol name 2403896; Volume Serial # 1044177234; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico

---

### Post by ago on 2008-07-07
There should be a Wubi*.log in your user temp folder, that is the one needed

---

### Post by ago on 2008-07-07
Seems like a segfault, try to mount the ISO using daemontools or similar and run wubi within the mounted ISO.

---

### Post by Sun_Paladin on 2008-07-07
The iso file has been mounted the entire time with DAEMON Tools Lite (4.12.3).

Also do you mean when you write run within the mounted iso that I should run Wubi from within its folder or place it someplace else and run it?

---

### Post by ago on 2008-07-07
Then try _without_ daemon tools. Simply place wubi 8.04.1 and the ISO in the same directory and run wubi.exe from there. Segfaults are difficult to track down, but usually changing your setup addresses the issue.

---

### Post by Sun_Paladin on 2008-07-07
New temp file without DAEMON Tools running and the iso file and the Wubi file sitting in a folder named Ubuntu sitting on my Desktop.


============ Installer ============
PLUGINSDIR=C:\Users\Owner\AppData\Local\Temp\nsy95CE.tmp
detect_all
Parsing cmdline "C:\Users\Owner\Desktop\Ubuntu\Wubi-8.04.1.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1013 MB
arch=i386
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release i386 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release i386 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name S3A6065D001; Max #/chars in vol name 2245120; Volume Serial # 1044177234; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1754592; Volume name S3A6065D001; Max #/chars in vol name 59; Volume Serial # 1044177234; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 42075
DetectBackupFolder
IsBackupFolder C:\
GMT=9
Country=GB
Locale=ja_JP.UTF-8
TimeZone=Europe/London
Domain=localdomain
HostName=x9806184
ComputerName=X9806184
EnvUsername=Owner
UserDomain=X9806184
UserInfoName=Owner
UserProfileFolder=C:\Users\Owner
UserProfileName=Owner 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name S3A6065D001; Max #/chars in vol name 2403896; Volume Serial # 1044177234; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
============ Installer ============
PLUGINSDIR=C:\Users\Owner\AppData\Local\Temp\nshA2C9.tmp
detect_all
Parsing cmdline "C:\Users\Owner\Desktop\Ubuntu\Wubi-8.04.1.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1013 MB
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
Drive & Path name 1712; Volume name S3A6065D001; Max #/chars in vol name 7094776; Volume Serial # 1044177234; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6604256; Volume name S3A6065D001; Max #/chars in vol name 51; Volume Serial # 1044177234; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 42073
DetectBackupFolder
IsBackupFolder C:\
GMT=9
Country=GB
Locale=ja_JP.UTF-8
TimeZone=Europe/London
Domain=localdomain
HostName=x9806184
ComputerName=X9806184
EnvUsername=Owner
UserDomain=X9806184
UserInfoName=Owner
UserProfileFolder=C:\Users\Owner
UserProfileName=Owner 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name S3A6065D001; Max #/chars in vol name 7252088; Volume Serial # 1044177234; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\Users\Owner\Desktop\Ubuntu\ubuntu-8.04.1-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\Owner\AppData\Local\Temp\nshA2C9.tmp\7z.exe e -y -i!.disk\info -oC:\Users\Owner\AppData\Local\Temp C:\Users\Owner\Desktop\Ubuntu\ubuntu-8.04.1-desktop-i386.iso
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release i386 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release i386 (20080702.1)
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
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico


Ugly I know.

---

### Post by ago on 2008-07-07
Try to run wubi with "--debug" argument, it will show loads and loads of message boxes, but it might go through at the end.

---

### Post by Sun_Paladin on 2008-07-07
Would you be able to tell me the syntax for running a program in Windows from within the cmd? I do not know how to navigate within cmd to a folder on my desktop. Thanks.

---

### Post by Sun_Paladin on 2008-07-07
Nevermind figured out the previous part. More code from the temp file. Again the iso is not mounted with DAEMON Tools.

============ Installer ============
PLUGINSDIR=C:\Users\Owner\AppData\Local\Temp\nsq2004.tmp
detect_all
Parsing cmdline "C:\Users\Owner\Desktop\Ubuntu\Wubi-8.04.1.exe" --debug
debug=true, 32bit=, cdboot=
User account type=Admin
Memory=1013 MB
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
Drive & Path name 1712; Volume name S3A6065D001; Max #/chars in vol name 3301352; Volume Serial # 1044177234; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2541592; Volume name S3A6065D001; Max #/chars in vol name 54; Volume Serial # 1044177234; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 42061
DetectBackupFolder
IsBackupFolder C:\
GMT=9
Country=GB
Locale=ja_JP.UTF-8
TimeZone=Europe/London
Domain=localdomain
HostName=x9806184
ComputerName=X9806184
EnvUsername=Owner
UserDomain=X9806184
UserInfoName=Owner
UserProfileFolder=C:\Users\Owner
UserProfileName=Owner 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name S3A6065D001; Max #/chars in vol name 3071480; Volume Serial # 1044177234; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\Users\Owner\Desktop\Ubuntu\ubuntu-8.04.1-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\Owner\AppData\Local\Temp\nsq2004.tmp\7z.exe e -y -i!.disk\info -oC:\Users\Owner\AppData\Local\Temp C:\Users\Owner\Desktop\Ubuntu\ubuntu-8.04.1-desktop-i386.iso
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release i386 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release i386 (20080702.1)
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
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico

---

### Post by ago on 2008-07-07
I am out of ideas at the moment, I will need to create a custom build with more logs/switches, but cannot do it now. If you open a bug in http:launchpad.net/wubi it will be easier for me (and for you) to follow it up.

---

### Post by Sun_Paladin on 2008-07-08
This topic has now been posted as a bug on the Wubi Launchpad.

Here's the link to the bug report.

[https://bugs.launchpad.net/wubi/+bug/246605](https://bugs.launchpad.net/wubi/+bug/246605)

---

