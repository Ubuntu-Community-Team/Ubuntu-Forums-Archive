---
title: "Error wubi :("
date: 2007-11-01
forum: General Help
---

### Post by Lex92 on 2007-11-01
Hello

First of all, say that I am Spanish and I am using a translator, so I do not know if something is MEANING: P.

I have a problem with the wubi, after having installed (kubuntu) to select the operating system ubuntu, I get the following error:

Booting 'find / wubi / boot / grub / menu.lst'
Booting 'find / menu.lst'
Find --set-root--ignore-floppies/menu.lst
Error17: File not found


Greetings and thanks

---

### Post by ago on 2007-11-01
You may want to try the 7.10 version
[http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

---

### Post by Lex92 on 2007-11-01
HI! ! !

I download this version, but when I run and when you go by the middle of the installation, I get an error ... 

Please someone help me; (

Screenshot:

[http://img228.imageshack.us/img228/5557/dibujoyl9.jpg](http://img228.imageshack.us/img228/5557/dibujoyl9.jpg)

Greetings and thanks again ^ ^

---

### Post by ago on 2007-11-01
Can you post here %temp%\wubi*.log

---

### Post by Lex92 on 2007-11-01
Forgive, but I can say that the route is? I can not find it on any side ...


Greetings and thank you for helping me

---

### Post by ago on 2007-11-01
type %temp% in your file browser and you should see a wubi log

---

### Post by Lex92 on 2007-11-02
HI!

It is strange but I get only the alpha version, which is not installed ... I Emerging 2 because I had dropped the 2 files that you had, because you did not work, and try the other ... Upload 2

[http://rapidshare.com/files/66902603/logs.rar.html](http://rapidshare.com/files/66902603/logs.rar.html)


Thanks:(

---

### Post by ago on 2007-11-02
Can you try 383 and post the log?

---

### Post by Lex92 on 2007-11-02
I get the error prior to the 383 ... I will update windows. Here I leave log

And once again, many thanks for helping me ^ ^


LOG:

```
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18BC.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\usuario\Escritorio\Wubi-7.10-alpha-rev383.exe" 
DetectProcessorArchitecture
arch=i386
DetectCD
isvalidcd D:\
isvalidcd E:\
isvalidcd F:\
isvalidcd G:\
isvalidcd H:\
isvalidcd I:\
isvalidcd C:\
DetectCD Finished cddrive=
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
CheckFreeSpace C:
DetectBackupFolder
IsBackupFolder C:\
DetectGMT
DetectCountry
DetectLocale
DetectLayoutCode
DetectTimeZone
DetectDomain
DetectHostName
DetectComputerName
DetectUserName
DetectUserDomain
DetectUserInfoName
DetectUserProfileFolder
DetectUserProfileName
UserProfileName=usuario 
ShowMainPage
ChangeInstallationDrive
ChangeInstallationSize
PopulateDistroList
DetectIso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18BC.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18BC.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso


No files to process
 
  
 
isvalid 
nocdinfo
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18BC.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18BC.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso

Extracting  .disk\info

Everything is Ok
 
  
 
isvalid Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531)
 cdinfo=Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531) cdversion=6.06 cddistro=Ubuntu cdarch=i386 cdcodename=Dapper Drake cdsubversion=Release 
GetDistroInfo distro=Ubuntu cdarch=i386 arch=i386
different isoname ubuntu-7.10-desktop-i386.iso != ubuntu-6.06-desktop-i386.iso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18BC.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18BC.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso


No files to process
 
  
 
isvalid 
nocdinfo
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\usuario\CONFIG~1\Temp\nsg18C2.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\usuario\Escritorio\Wubi-7.10-alpha-rev383.exe" 
DetectProcessorArchitecture
arch=i386
DetectCD
isvalidcd D:\
isvalidcd E:\
isvalidcd F:\
isvalidcd G:\
isvalidcd H:\
isvalidcd I:\
isvalidcd C:\
DetectCD Finished cddrive=
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
CheckFreeSpace C:
DetectBackupFolder
IsBackupFolder C:\
DetectGMT
DetectCountry
DetectLocale
DetectLayoutCode
DetectTimeZone
DetectDomain
DetectHostName
DetectComputerName
DetectUserName
DetectUserDomain
DetectUserInfoName
DetectUserProfileFolder
DetectUserProfileName
UserProfileName=usuario 
ShowMainPage
ChangeInstallationDrive
ChangeInstallationSize
PopulateDistroList
DetectIso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsg18C2.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsg18C2.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso


No files to process
 
  
 
isvalid 
nocdinfo
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsg18C2.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsg18C2.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso

Extracting  .disk\info

Everything is Ok
 
  
 
isvalid Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531)
 cdinfo=Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531) cdversion=6.06 cddistro=Ubuntu cdarch=i386 cdcodename=Dapper Drake cdsubversion=Release 
GetDistroInfo distro=Ubuntu cdarch=i386 arch=i386
different isoname ubuntu-7.10-desktop-i386.iso != ubuntu-6.06-desktop-i386.iso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsg18C2.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsg18C2.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso


No files to process
 
  
 
isvalid 
nocdinfo
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\usuario\CONFIG~1\Temp\nsc18C7.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\usuario\Escritorio\Wubi-7.10-alpha-rev383.exe" 
DetectProcessorArchitecture
arch=i386
DetectCD
isvalidcd D:\
isvalidcd E:\
isvalidcd F:\
isvalidcd G:\
isvalidcd H:\
isvalidcd I:\
isvalidcd C:\
DetectCD Finished cddrive=
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
CheckFreeSpace C:
DetectBackupFolder
IsBackupFolder C:\
DetectGMT
DetectCountry
DetectLocale
DetectLayoutCode
DetectTimeZone
DetectDomain
DetectHostName
DetectComputerName
DetectUserName
DetectUserDomain
DetectUserInfoName
DetectUserProfileFolder
DetectUserProfileName
UserProfileName=usuario 
ShowMainPage
ChangeInstallationDrive
ChangeInstallationSize
PopulateDistroList
DetectIso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsc18C7.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsc18C7.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso


No files to process
 
  
 
isvalid 
nocdinfo
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsc18C7.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsc18C7.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso

Extracting  .disk\info

Everything is Ok
 
  
 
isvalid Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531)
 cdinfo=Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531) cdversion=6.06 cddistro=Ubuntu cdarch=i386 cdcodename=Dapper Drake cdsubversion=Release 
GetDistroInfo distro=Ubuntu cdarch=i386 arch=i386
different isoname ubuntu-7.10-desktop-i386.iso != ubuntu-6.06-desktop-i386.iso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsc18C7.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsc18C7.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso


No files to process
 
  
 
isvalid 
nocdinfo
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\usuario\CONFIG~1\Temp\nsp18CC.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\usuario\Escritorio\Wubi-7.10-alpha-rev383.exe" 
DetectProcessorArchitecture
arch=i386
DetectCD
isvalidcd D:\
isvalidcd E:\
isvalidcd F:\
isvalidcd G:\
isvalidcd H:\
isvalidcd I:\
isvalidcd C:\
DetectCD Finished cddrive=
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
CheckFreeSpace C:
DetectBackupFolder
IsBackupFolder C:\
DetectGMT
DetectCountry
DetectLocale
DetectLayoutCode
DetectTimeZone
DetectDomain
DetectHostName
DetectComputerName
DetectUserName
DetectUserDomain
DetectUserInfoName
DetectUserProfileFolder
DetectUserProfileName
UserProfileName=usuario 
ShowMainPage
ChangeInstallationDrive
ChangeInstallationSize
PopulateDistroList
DetectIso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsp18CC.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsp18CC.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso


No files to process
 
  
 
isvalid 
nocdinfo
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsp18CC.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsp18CC.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso

Extracting  .disk\info

Everything is Ok
 
  
 
isvalid Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531)
 cdinfo=Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531) cdversion=6.06 cddistro=Ubuntu cdarch=i386 cdcodename=Dapper Drake cdsubversion=Release 
GetDistroInfo distro=Ubuntu cdarch=i386 arch=i386
different isoname ubuntu-7.10-desktop-i386.iso != ubuntu-6.06-desktop-i386.iso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsp18CC.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsp18CC.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso


No files to process
 
  
 
isvalid 
nocdinfo
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18D1.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\usuario\Escritorio\Wubi-7.10-alpha-rev383.exe" 
DetectProcessorArchitecture
arch=i386
DetectCD
isvalidcd D:\
isvalidcd E:\
isvalidcd F:\
isvalidcd G:\
isvalidcd H:\
isvalidcd I:\
isvalidcd C:\
DetectCD Finished cddrive=
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
CheckFreeSpace C:
DetectBackupFolder
IsBackupFolder C:\
DetectGMT
DetectCountry
DetectLocale
DetectLayoutCode
DetectTimeZone
DetectDomain
DetectHostName
DetectComputerName
DetectUserName
DetectUserDomain
DetectUserInfoName
DetectUserProfileFolder
DetectUserProfileName
UserProfileName=usuario 
ShowMainPage
ChangeInstallationDrive
ChangeInstallationSize
PopulateDistroList
DetectIso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18D1.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18D1.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso


No files to process
 
  
 
isvalid 
nocdinfo
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18D1.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18D1.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso

Extracting  .disk\info

Everything is Ok
 
  
 
isvalid Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531)
 cdinfo=Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531) cdversion=6.06 cddistro=Ubuntu cdarch=i386 cdcodename=Dapper Drake cdsubversion=Release 
GetDistroInfo distro=Ubuntu cdarch=i386 arch=i386
different isoname ubuntu-7.10-desktop-i386.iso != ubuntu-6.06-desktop-i386.iso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18D1.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsr18D1.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso


No files to process
 
  
 
isvalid 
nocdinfo
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\usuario\CONFIG~1\Temp\nsx1A42.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\usuario\Escritorio\Wubi-7.10-alpha-rev383.exe" 
DetectProcessorArchitecture
arch=i386
DetectCD
isvalidcd D:\
isvalidcd E:\
isvalidcd F:\
isvalidcd G:\
isvalidcd H:\
isvalidcd I:\
isvalidcd C:\
DetectCD Finished cddrive=
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
CheckFreeSpace C:
DetectBackupFolder
IsBackupFolder C:\
DetectGMT
DetectCountry
DetectLocale
DetectLayoutCode
DetectTimeZone
DetectDomain
DetectHostName
DetectComputerName
DetectUserName
DetectUserDomain
DetectUserInfoName
DetectUserProfileFolder
DetectUserProfileName
UserProfileName=usuario 
ShowMainPage
ChangeInstallationDrive
ChangeInstallationSize
PopulateDistroList
DetectIso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsx1A42.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsx1A42.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso


No files to process
 
  
 
isvalid 
nocdinfo
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsx1A42.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsx1A42.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso

Extracting  .disk\info

Everything is Ok
 
  
 
isvalid Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531)
 cdinfo=Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531) cdversion=6.06 cddistro=Ubuntu cdarch=i386 cdcodename=Dapper Drake cdsubversion=Release 
GetDistroInfo distro=Ubuntu cdarch=i386 arch=i386
different isoname ubuntu-7.10-desktop-i386.iso != ubuntu-6.06-desktop-i386.iso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsx1A42.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsx1A42.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso


No files to process
 
  
 
isvalid 
nocdinfo
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\usuario\CONFIG~1\Temp\nsi1A47.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\usuario\Escritorio\Wubi-7.10-alpha-rev383.exe" 
DetectProcessorArchitecture
arch=i386
DetectCD
isvalidcd D:\
isvalidcd E:\
isvalidcd F:\
isvalidcd G:\
isvalidcd H:\
isvalidcd I:\
isvalidcd C:\
DetectCD Finished cddrive=
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
CheckFreeSpace C:
DetectBackupFolder
IsBackupFolder C:\
DetectGMT
DetectCountry
DetectLocale
DetectLayoutCode
DetectTimeZone
DetectDomain
DetectHostName
DetectComputerName
DetectUserName
DetectUserDomain
DetectUserInfoName
DetectUserProfileFolder
DetectUserProfileName
UserProfileName=usuario 
ShowMainPage
ChangeInstallationDrive
ChangeInstallationSize
PopulateDistroList
DetectIso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsi1A47.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsi1A47.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Varios\TodoEnUnoV2 By Pentium.iso


No files to process
 
  
 
isvalid 
nocdinfo
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsi1A47.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsi1A47.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\SO\ubuntu\ubuntu-6.06-desktop-i386.iso

Extracting  .disk\info

Everything is Ok
 
  
 
isvalid Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531)
 cdinfo=Ubuntu 6.06 "Dapper Drake" - Release i386 (20060531) cdversion=6.06 cddistro=Ubuntu cdarch=i386 cdcodename=Dapper Drake cdsubversion=Release 
GetDistroInfo distro=Ubuntu cdarch=i386 arch=i386
different isoname ubuntu-7.10-desktop-i386.iso != ubuntu-6.06-desktop-i386.iso
IsValidIso ispoath=C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
ExtractIsoInfo
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsi1A47.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\usuario\CONFIG~1\Temp C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso
C:\DOCUME~1\usuario\CONFIG~1\Temp\nsi1A47.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\Documents and Settings\usuario\Mis documentos\Linux\openSUSE-10.3-GM-GNOME-i386.iso


No files to process
 
  
 
isvalid 
nocdinfo

```

---

