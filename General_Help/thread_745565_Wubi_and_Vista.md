---
title: "Wubi and Vista"
date: 2008-04-04
forum: General Help
---

### Post by seamustry on 2008-04-04
I was wondering about  your opinions about running wubi in vista...are there any installation or uninstallation issues??

i read somewhere that wubi doesn't completely uninstall on vista...is that true?

thanks!

---

### Post by ago on 2008-04-05
Wubi should work well on vista

---

### Post by seamustry on 2008-04-05
ok so i tried installing in vista and i get this error:

could not retreive some essential files.

both desktop iso and wubi are in same directory...have tried a couple times and am getting same error. worked fine in xp but my other laptop has vista on it...

thanks

---

### Post by ago on 2008-04-05
If you type %temp% in windows explorer you should see a wubi log, pls post it here

---

### Post by seamustry on 2008-04-05
ok here is the log...i appreciate your help!!!

```

============ Installer ============
PLUGINSDIR=C:\Users\User~1\AppData\Local\Temp\nsp54BE.tmp
detect_all
Parsing cmdline "C:\Users\user\Desktop\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2046 MB
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
Drive & Path name 1709; Volume name ; Max #/chars in vol name 2700040; Volume Serial # 1344857337; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2686264; Volume name ; Max #/chars in vol name 28; Volume Serial # 1344857337; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 41955
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=laptop
ComputerName=LAPTOP
EnvUsername=User
UserDomain=laptop
UserInfoName=User
UserProfileFolder=C:\Users\User
UserProfileName=User 
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 3170672; Volume Serial # 1344857337; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\Users\User\Desktop\ubuntu-8.04-beta-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\UserA~1\AppData\Local\Temp\nsp54BE.tmp\7z.exe e -y -i!.disk\info -oC:\Users\UserA~1\AppData\Local\Temp C:\Users\User\Desktop\ubuntu-8.04-beta-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
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
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 4
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
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=C:\Users\User\Desktop\ubuntu-8.04-beta-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\UserA~1\AppData\Local\Temp\nsp54BE.tmp\7z.exe e -y -i!.disk\info -oC:\Users\UserA~1\AppData\Local\Temp C:\Users\User\Desktop\ubuntu-8.04-beta-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
Copying C:\Users\User\Desktop\ubuntu-8.04-beta-desktop-i386.iso -> C:\ubuntu\install\ubuntu-8.04-beta-desktop-i386.iso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
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
Download status=success:C:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:C:\ubuntu\install\MD5SUMS
      Verifying signature C:\ubuntu\install\MD5SUMS.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 04/03/08 19:22:57 Eastern Daylight Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst=C:\ubuntu\install\ubuntu-8.04-beta-desktop-i386.iso url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=success:C:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\hardy-desktop-i386.iso
7z error: error
Could not retrieve some essential files

```

---

### Post by ago on 2008-04-05
Last line I see reads 'isvalidfilesystem c:' 
Are you sure this is all the log?

---

### Post by seamustry on 2008-04-05
uh yeah i think so...i can see the full thing here at my end...the last couple of lines go like this:

```

Parsing C:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst=C:\ubuntu\install\ubuntu-8.04-beta-desktop-i386.iso url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=success:C:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\hardy-desktop-i386.iso
7z error: error
Could not retrieve some essential files

```

---

### Post by nutz on 2008-04-05
I tested Wubi on a laptop running Vista and it worked just fine.

---

### Post by seamustry on 2008-04-06
ok so here's what i did to get it to work:

i installed winrar and got the wubi that comes with the .iso file. that worked and now i have a problem during installation.

after doing something for a few seconds, it give me an option at step 6 of 7 about importing settings from previous user. then it says no user found to import from and doesn't let me go forward. what's going on there?

---

### Post by nutz on 2008-04-06
You can also download Wubi directly from this site...

[http://wubi-installer.org/](http://wubi-installer.org/)

That is the method I used and it worked very well.

---

### Post by seamustry on 2008-04-06
I tried installing again and now i'm getting the "could not retrieve some essential files" error again....when i look in the log (posted above), i see this line:

7z error: error.

what is that and how to fix it. i have the latest .iso and latest wubi available.

---

### Post by ago on 2008-04-06
Can you attach the full log?

---

### Post by seamustry on 2008-04-06
ok here's the log again:

```

============ Installer ============
PLUGINSDIR=C:\Users\User~1\AppData\Local\Temp\nsp54BE.tmp
detect_all
Parsing cmdline "C:\Users\user\Desktop\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2046 MB
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
Drive & Path name 1709; Volume name ; Max #/chars in vol name 2700040; Volume Serial # 1344857337; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2686264; Volume name ; Max #/chars in vol name 28; Volume Serial # 1344857337; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 41955
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=laptop
ComputerName=LAPTOP
EnvUsername=User
UserDomain=laptop
UserInfoName=User
UserProfileFolder=C:\Users\User
UserProfileName=User 
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 3170672; Volume Serial # 1344857337; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\Users\User\Desktop\ubuntu-8.04-beta-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\UserA~1\AppData\Local\Temp\nsp54BE.tmp\7z.exe e -y -i!.disk\info -oC:\Users\UserA~1\AppData\Local\Temp C:\Users\User\Desktop\ubuntu-8.04-beta-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
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
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 4
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
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=C:\Users\User\Desktop\ubuntu-8.04-beta-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\UserA~1\AppData\Local\Temp\nsp54BE.tmp\7z.exe e -y -i!.disk\info -oC:\Users\UserA~1\AppData\Local\Temp C:\Users\User\Desktop\ubuntu-8.04-beta-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
Copying C:\Users\User\Desktop\ubuntu-8.04-beta-desktop-i386.iso -> C:\ubuntu\install\ubuntu-8.04-beta-desktop-i386.iso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
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
Download status=success:C:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:C:\ubuntu\install\MD5SUMS
      Verifying signature C:\ubuntu\install\MD5SUMS.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 04/03/08 19:22:57 Eastern Daylight Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst=C:\ubuntu\install\ubuntu-8.04-beta-desktop-i386.iso url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=success:C:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\hardy-desktop-i386.iso
7z error: error
Could not retrieve some essential files

```

---

### Post by ago on 2008-04-06
It might be that the ISO downloaded was corrupted. You might check the md5 of the iso in c:\ubuntu\install\ with the one in [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS)

---

### Post by seamustry on 2008-04-06
yeah i thought that too but i re-downloaded the .iso and it still doesn't work...what does 7z: error mean anyways?

---

### Post by seamustry on 2008-04-06
also...does it matter what mirror i download from? i always use the same mirror so they might have the bad version??

---

### Post by ago on 2008-04-06
> **seamustry said:**
> yeah i thought that too but i re-downloaded the .iso and it still doesn't work...what does 7z: error mean anyways?

7z is used to extract a file (the kernel) from the ISO, and it fails.

---

### Post by seamustry on 2008-04-07
ok i took a different approach and decided to let wubi do the downloading and everything...

i started up the installer, etc and i made sure that there aren't any .iso's that it might mistake as ubuntu cd so that it will download a new one by itself.

here's the error log that i'm getting:

```

============ Installer ============
PLUGINSDIR=C:\Users\user~1\AppData\Local\Temp\nswD403.tmp
detect_all
Parsing cmdline "C:\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2046 MB
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
Drive & Path name 1709; Volume name ; Max #/chars in vol name 3297512; Volume Serial # 1344857337; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 3284712; Volume name ; Max #/chars in vol name 28; Volume Serial # 1344857337; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 42652
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=laptop
ComputerName=LAPTOP
EnvUsername=user
UserDomain=laptop
UserInfoName=user
UserProfileFolder=C:\Users\user
UserProfileName=user 
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 3367904; Volume Serial # 1344857337; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 4
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
Trying remote metalink: http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg md5=
Download status=The requested URL returned error: 404
Error downloading http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg, The req
Trying remote metalink2: http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:C:\ubuntu\install\MD5SUMS
      Verifying signature C:\ubuntu\install\MD5SUMS.asc
error; ; ; ; 
Error verifying signature: error
The download was interrupted with the error: 
============ Uninstaller ============
PLUGINSDIR=C:\Users\user~1\AppData\Local\Temp\nsr77CF.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanConfig.sys C:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Installer ============
PLUGINSDIR=C:\Users\user~1\AppData\Local\Temp\nsv5DC0.tmp
detect_all
Parsing cmdline "C:\Users\user\Desktop\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=2046 MB
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
Drive & Path name 1709; Volume name ; Max #/chars in vol name 2695848; Volume Serial # 1344857337; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2679808; Volume name ; Max #/chars in vol name 31; Volume Serial # 1344857337; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 42626
DetectBackupFolder
IsBackupFolder C:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=laptop
ComputerName=LAPTOP
EnvUsername=user
UserDomain=laptop
UserInfoName=user
UserProfileFolder=C:\Users\user
UserProfileName=user 
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1752; Volume name ; Max #/chars in vol name 2789232; Volume Serial # 1344857337; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 4
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
Trying remote metalink: http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg md5=
Download status=The requested URL returned error: 404
Error downloading http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg, The req
Trying remote metalink2: http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:C:\ubuntu\install\MD5SUMS
      Verifying signature C:\ubuntu\install\MD5SUMS.asc
error; ; ; ; 
Error verifying signature: error
The download was interrupted with the error: 


```

---

### Post by ago on 2008-04-07
remove c:\ubuntu
then install again

---

### Post by seamustry on 2008-04-07
yep i've already done that...this log comes after i've done the removing and trying again stuff...don't know what's going on :(

---

### Post by ago on 2008-04-07
can you post C:\ubuntu\install\MD5SUMS*

---

### Post by seamustry on 2008-04-07
ok here's the text file for that:

```

1501ac593fb7afbdbb5efd25b32868e8  edubuntu-desktop-amd64.iso.metalink
6d3fd087a8d43c4fb8449bfcf635274b  edubuntu-desktop-i386.iso.metalink
9a1f46e6267cb2758850de27281c94d5  kubuntu-desktop-amd64.iso.metalink
ccd23082d03a1aa0119d6fcab329c166  kubuntu-desktop-i386.iso.metalink
3a19bf5f72179779a7431b86edbf5b8b  kubuntu-kde4-desktop-amd64.iso.metalink
71246645235529fd783751ff2e7c4c1b  kubuntu-kde4-desktop-i386.iso.metalink
e9225c74532ce3c68cbeacee8b16a85c  ubuntu-desktop-amd64.iso.metalink
7623756fc4bf51c1512d807ea195b671  ubuntu-desktop-i386.iso.metalink
126a18d9cd80cebead069e227ec79e13  xubuntu-desktop-amd64.iso.metalink
e5c41840e6c977dfdc9f26769cff81ac  xubuntu-desktop-i386.iso.metalink

```

and there's also an MD5SUMS.asc file which i don't know how to open.

---

### Post by ago on 2008-04-07
it's better if you remove any iso and partial file in the folder and any subfolder then zip c:\ubuntu\install and post it here

---

### Post by seamustry on 2008-04-07
how do i post a zip file to the forums??

---

### Post by ago on 2008-04-07
Post Reply > Manage Attachments

---

### Post by seamustry on 2008-04-08
ok so i got it to finally work by burning the iso to a cd and running wubi from there.

works fine now...

---

