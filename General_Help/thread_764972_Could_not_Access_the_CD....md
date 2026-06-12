---
title: "Could not Access the CD..."
date: 2008-04-24
forum: General Help
---

### Post by se7en.pt on 2008-04-24
Im still having this problem on Ubuntu Final Release!

I tested the Live CD, work fine...
See the checksum, everything fine...
See the %temp% wubi log... everything fine...
Installed with everything closed...windows..etc...

But the problem keep, do all things to 100% and then... 
"Could Not Access The CD, please make sure other applications are not using it and try again"

Im trying to install on:
Windows Xp Sp2 32Bit

If anybody can help me please, I really want and Only want to install Ubuntu over Windows from WUBI...

---

### Post by ago on 2008-04-24
That sometimes happens when a DVD media/drive is used. 
A quick workaround is to use Wubi directly with the ISO. Just place the final desktop ISO and wubi.exe in the same folder and run wubi. Do not leave the CD in the tray.

---

### Post by TuckWat on 2008-04-24
Is this the only workaround?  I downloaded 8.04 on a separate machine and burned a CD of the image.  Does this mean I'll have to re-download the ISO on the machine I want to use wubi on?

Thanks!

---

### Post by ago on 2008-04-24
There are several tools that can create the ISO from the CD

[http://www.google.com/search?q=extract+iso+from+CD](http://www.google.com/search?q=extract+iso+from+CD)

If you have multiple CD drives you can also try insterting the CD in another slot.

---

### Post by joslin on 2008-04-24
I have downloaded the new version of Wubi-8.04-beta-rev501.exe, and the new version of ubuntu (ISO file is ubuntu-8.04-desktop-i386.iso).  However, I can't get wubi to recognize the ISO.  I thought it might be corrupt so I downloaded another from a different mirror - is the latest version of wubi unable to install the newest release of ubuntu?

I have them both in the same directory, and I was able to get it to work with the release candidate version on a different computer yesterday.  

Also, If I have an external hard drive (usb) which I have installed wubi, how do I boot from the device on a new computer?  I assume this involves editing the boot.ini file. Could someone explain this to me?  Thanks!

---

### Post by ago on 2008-04-24
Please post the wubi log in your user temp folder (%temp%)? Also there should be a file called c:\ubuntu\metadl_log.txt. Post that too.

---

### Post by joslin on 2008-04-24
parsing arguments:
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=E:\ubuntu\install\MD5SUMS-metalink.gpg
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg) score:75
Init download: url='http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg)

Download returned: 7 couldn't connect to host

info_code == CURLE_OK
Mirror: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg) score:15
Init download: url='http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg)

Download returned: 7 couldn't connect to host

info_code == CURLE_OK
Mirror: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg) score:-45
Init download: url='http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg)

Download returned: 7 couldn't connect to host

info_code == CURLE_OK
parsing arguments:
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=E:\ubuntu\install\MD5SUMS-metalink.gpg
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg) score:75
Init download: url='http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg)

Download returned: 7 couldn't connect to host

info_code == CURLE_OK
Mirror: [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg) score:15
Init download: url='http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg)

Download returned: 7 couldn't connect to host

parsing arguments:
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=E:\ubuntu\install\MD5SUMS-metalink.gpg
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg) score:75
Init download: url='http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg)

Download returned: 7 couldn't connect to host

parsing arguments:
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=E:\ubuntu\install\MD5SUMS-metalink.gpg
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg) score:75
Init download: url='http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg)

Download returned: 7 couldn't connect to host

parsing arguments:
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=E:\ubuntu\install\MD5SUMS-metalink.gpg
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg) score:75
Init download: url='http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg)

Download returned: 7 couldn't connect to host

parsing arguments:
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=E:\ubuntu\install\MD5SUMS-metalink.gpg
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg) score:75
Init download: url='http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg)

Download returned: 7 couldn't connect to host

info_code == CURLE_OK
Mirror: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg) score:15
Init download: url='http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg)

Download returned: 7 couldn't connect to host

info_code == CURLE_OK
parsing arguments:
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=E:\ubuntu\install\MD5SUMS-metalink.gpg
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg) score:75
Init download: url='http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg)

Download returned: 7 couldn't connect to host

parsing arguments:
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=E:\ubuntu\install\MD5SUMS-metalink.gpg
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg) score:75
Init download: url='http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg)

Download returned: 28 connect() timed out!

info_code == CURLE_OK
Mirror: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg) score:15
Init download: url='http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg)

Download returned: 28 connect() timed out!

---

### Post by ago on 2008-04-24
The server is very busy now and it cannot connect to verify the ISO,

run wubi with the argument: "--skipmd5check"

---

### Post by joslin on 2008-04-24
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\joslin\LOCALS~1\Temp\nsb21.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\joslin\Desktop\Wubi-8.04-beta-rev501.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1015 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
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
Found InstallationDrive E:\ubuntu
AlreadyInstalled=true OldInstallationDrive=E: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1711; Volume name PC COE; Max #/chars in vol name 1866464; Volume Serial # 150657678; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem E:
Drive & Path name 1711; Volume name My Passport; Max #/chars in vol name 1866472; Volume Serial # 412660691; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive E: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1447120; Volume name PC COE; Max #/chars in vol name 48; Volume Serial # 150657678; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 57544
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder E:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=americas.hpqcorp.net
HostName=CCE01-OBW24
ComputerName=CCE01-OBW24
EnvUsername=joslin
UserDomain=AMERICAS
UserInfoName=joslin
UserProfileFolder=C:\Documents and Settings\joslin
UserProfileName=joslin 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1773; Volume name PC COE; Max #/chars in vol name 1883616; Volume Serial # 150657678; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem E:
Drive & Path name 1773; Volume name My Passport; Max #/chars in vol name 1883624; Volume Serial # 412660691; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive E: has valid filesystem NTFS
Adding drive E:
Drive list = C:|E:
ChangeInstallationDrive to E:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=E:\ubuntu\install\ubuntu-8.04-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\joslin\LOCALS~1\Temp\nsb21.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\joslin\LOCALS~1\Temp E:\ubuntu\install\ubuntu-8.04-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
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
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationDrive to E:
ChangeInstallationSize to 15
LeaveMainPage
ChangeInstallationSize to 30
LeaveMainPage
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created E:\ubuntu\Uninstall-Ubuntu.exe
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
      Is Valid CD E:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=E:\ubuntu\install\ubuntu-8.04-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\joslin\LOCALS~1\Temp\nsb21.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\joslin\LOCALS~1\Temp E:\ubuntu\install\ubuntu-8.04-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
Using E:\ubuntu\install\ubuntu-8.04-desktop-i386.iso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Checking/Downloading Ubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink](http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink)
get_md5 [http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink](http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg md5=
Download status=cancel
User cancelled download, quitting.

---

### Post by joslin on 2008-04-24
Now the installation is failing at "execshell compact" - it freezes then asks to debug the error.

---

### Post by se7en.pt on 2008-04-24
> **ago said:**
> That sometimes happens when a DVD media/drive is used. 
A quick workaround is to use Wubi directly with the ISO. Just place the final desktop ISO and wubi.exe in the same folder and run wubi. Do not leave the CD in the tray.

Thanks, that worked for me... really fast post ;)
Im only reply now because im already using Ubuntu.. finally ;) Tks...

Unfortunatly the Wubi from CD dont work but thanks for your good help

---

### Post by ago on 2008-04-24
> **joslin said:**
> Now the installation is failing at "execshell compact" - it freezes then asks to debug the error.

Uninstall and run wubi with and without --skipmd5check

---

