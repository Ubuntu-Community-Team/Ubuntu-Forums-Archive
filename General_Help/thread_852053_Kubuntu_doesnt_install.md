---
title: "Kubuntu doesnt install"
date: 2008-07-07
forum: General Help
---

### Post by spivjwp on 2008-07-07
Hello,

I'm new here, and went to install Wubi and Kubuntu. So i tryed, and then it gave a error:

The download was ended with the following error:

But there is no error!!

He is every time trying to connect to something, but dont get a connection. Maybe wrong URL's in the program ?

I'm Dutch..

---

### Post by ago on 2008-07-07
Might be that the mirror you used was momentarily down

You can send the wubi log in your user temp folder to confirm this.

---

### Post by spivjwp on 2008-07-07
```

============ Installer ============
PLUGINSDIR=C:\Users\Marvin\AppData\Local\Temp\nsu2D50.tmp
detect_all
Parsing cmdline "C:\Users\Marvin\Downloads\Wubi-8.04.1(2).exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2045 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD K:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name HP; Max #/chars in vol name 3519632; Volume Serial # -1065439869; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name FACTORY_IMAGE; Max #/chars in vol name 3519636; Volume Serial # -2005661924; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 3131488; Volume name HP; Max #/chars in vol name 46; Volume Serial # -1065439869; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 192675
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=1
Country=NL
Locale=nl_NL.UTF-8
TimeZone=Europe/Amsterdam
Domain=localdomain
HostName=MarvinPC
ComputerName=MARVINPC
EnvUsername=Marvin
UserDomain=MarvinPC
UserInfoName=Marvin
UserProfileFolder=C:\Users\Marvin
UserProfileName=Marvin 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name HP; Max #/chars in vol name 35753000; Volume Serial # -1065439869; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name FACTORY_IMAGE; Max #/chars in vol name 35753004; Volume Serial # -2005661924; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Skipping drive D:, not enough free space 1587 <= 5000
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\Users\Marvin\Downloads\ubuntu-8.04.1-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\Marvin\AppData\Local\Temp\nsu2D50.tmp\7z.exe e -y -i!.disk\info -oC:\Users\Marvin\AppData\Local\Temp C:\Users\Marvin\Downloads\ubuntu-8.04.1-desktop-i386.iso
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release i386 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=amd64
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.04.1/kubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Kubuntu
Changing icon to Kubuntu.ico
LeaveMainPage
Locale=nl_NL.UTF-8
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.04.1/kubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Kubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD K:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=C:\Users\Marvin\Downloads\ubuntu-8.04.1-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\Marvin\AppData\Local\Temp\nsu2D50.tmp\7z.exe e -y -i!.disk\info -oC:\Users\Marvin\AppData\Local\Temp C:\Users\Marvin\Downloads\ubuntu-8.04.1-desktop-i386.iso
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release i386 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.04.1/kubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
different distro Kubuntu != Ubuntu
CDInfo cleared
      GetDistroInfo distrofullname=Kubuntu-amd64 distro=Kubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.04.1/kubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Kubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: http://releases.ubuntu.com/kubuntu/8.04.1/kubuntu-8.04.1-desktop-amd64.metalink
get_md5 http://releases.ubuntu.com/kubuntu/8.04.1/kubuntu-8.04.1-desktop-amd64.metalink
Downloading: trymefirst= url=http://releases.ubuntu.com/kubuntu/8.04.1/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/kubuntu/8.04.1/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: error loading `iconv.dll': Kan opgegeven module niet vinden.


gpgv: Signature made 07/03/08 23:30:39 West-Europa (zomertijd) using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS-metalink
Found md5 fb884f9d901ed2cc8babf3fcb173dbc2
Downloading: trymefirst= url=http://releases.ubuntu.com/kubuntu/8.04.1/kubuntu-8.04.1-desktop-amd64.metalink md5=fb884f9d901ed2cc8babf3fcb173dbc2
Download status=The requested URL returned error: 404
Trying remote metalink2: http://cdimage.ubuntu.com/kubuntu/hardy/daily-live/current/hardy-desktop-amd64.metalink
get_md5 http://cdimage.ubuntu.com/kubuntu/hardy/daily-live/current/hardy-desktop-amd64.metalink
Downloading: trymefirst= url=http://cdimage.ubuntu.com/kubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=The requested URL returned error: 404
Error downloading http://cdimage.ubuntu.com/kubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg, The req
De download werd onderbroken met error: 

```


Its sometimes dutch.

---

### Post by ago on 2008-07-07
The metalink URL is correct. There should be another log in C:\ubuntu\*metadl*

---

### Post by spivjwp on 2008-07-07
> **ago said:**
> The metalink URL is correct. There should be another log in C:\ubuntu\*metadl*

I just checked the Metalink, but the downloadlinks for NL in the metalink are having 404-pages. So the downloadlinks are offline..

The metadl-log:

```

parsing arguments:
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=C:\ubuntu\install\MD5SUMS-metalink.gpg
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/MD5SUMS-metalink.gpg score:75
Init download: url='http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/MD5SUMS-metalink.gpg

Download returned: 0 

info_code == CURLE_OK
Checking file C:\ubuntu\install\MD5SUMS-metalink.gpg.partial
File check successful!

parsing arguments:
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=C:\ubuntu\install\MD5SUMS-metalink
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/MD5SUMS-metalink score:75
Init download: url='http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/MD5SUMS-metalink', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04.1/release/MD5SUMS-metalink

Download returned: 0 

info_code == CURLE_OK
Checking file C:\ubuntu\install\MD5SUMS-metalink.partial
File check successful!

parsing arguments:
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=C:\ubuntu\install\MD5SUMS-metalink.gpg
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: http://cdimage.ubuntu.com/kubuntu-kde4/hardy/daily-live/current/MD5SUMS-metalink.gpg score:75
Init download: url='http://cdimage.ubuntu.com/kubuntu-kde4/hardy/daily-live/current/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: http://cdimage.ubuntu.com/kubuntu-kde4/hardy/daily-live/current/MD5SUMS-metalink.gpg

Download returned: 22 The requested URL returned error: 404

info_code == CURLE_OK
Response code: 404 truncating to 0

Mirror: http://cdimage.ubuntu.com/kubuntu-kde4/hardy/daily-live/current/MD5SUMS-metalink.gpg score:15
Init download: url='http://cdimage.ubuntu.com/kubuntu-kde4/hardy/daily-live/current/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: http://cdimage.ubuntu.com/kubuntu-kde4/hardy/daily-live/current/MD5SUMS-metalink.gpg

Download returned: 22 The requested URL returned error: 404

info_code == CURLE_OK
Response code: 404 truncating to 0

Mirror: http://cdimage.ubuntu.com/kubuntu-kde4/hardy/daily-live/current/MD5SUMS-metalink.gpg score:-45
Init download: url='http://cdimage.ubuntu.com/kubuntu-kde4/hardy/daily-live/current/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: http://cdimage.ubuntu.com/kubuntu-kde4/hardy/daily-live/current/MD5SUMS-metalink.gpg

Download returned: 22 The requested URL returned error: 404

info_code == CURLE_OK
Response code: 404 truncating to 0

```

---

### Post by ago on 2008-07-07
The log above refers to the second attempt, and it is irrelevant.

What country are you in? Check the mirror in [http://releases.ubuntu.com/kubuntu/8.04.1/kubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/kubuntu/8.04.1/kubuntu-8.04.1-desktop-amd64.metalink)

Country mirrors have preference, otherwise a random mirror is selected.

Otherwise download manually from one of the mirrors listed in the link above and save the ISO in the same folder as wubi.exe

---

### Post by spivjwp on 2008-07-07
All the links in the metalink aren't working.  So maybe the metalink needs to be updated.

---

