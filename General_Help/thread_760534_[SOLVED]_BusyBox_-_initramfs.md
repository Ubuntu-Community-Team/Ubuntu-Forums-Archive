---
title: "[SOLVED] BusyBox - initramfs"
date: 2008-04-20
forum: General Help
---

### Post by airjer on 2008-04-20
When trying in verbose mode right before the busybox console I get:

ata4.01: qc timeout

Then this continues to scroll over and over again after the console appears:

ata4.00: status: {DRDY}
ata4: soft resetting link
ata4.00: configured for UDMA/33
ata4: EH complete
ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0pio 36 in
cdb 12 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00
res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

Within my casper.log I get a few "Unable to find a medium containing a live filesystem"'s.

At the bottom of my initramfs.debug file I get
+return
+mountroot
+exec
+exec
+exec
+exec

Wubi-8.04-beter-rev491.log
```
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nst3360.tmp
detect_all
Parsing cmdline "C:\ubuntu-backup\Wubi-8.04-beta-rev491.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-2 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive H:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 9983184; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 9983196; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 9983204; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 9404056; Volume name ; Max #/chars in vol name 42; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 55772
DetectBackupFolder
IsBackupFolder C:\
Found BackupFolder C:\ubuntu-backup
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=dam4nn-PC
ComputerName=DAM4NN-PC
EnvUsername=da.m4nn
UserDomain=dam4nn-PC
UserInfoName=da.m4nn
UserProfileFolder=C:\Users\da.m4nn
UserProfileName=da.m4nn 
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
Drive & Path name 1773; Volume name ; Max #/chars in vol name 10107856; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem F:
Drive & Path name 1773; Volume name Data; Max #/chars in vol name 10107868; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Adding drive F:
IsValidFileSystem H:
Drive & Path name 1773; Volume name Games; Max #/chars in vol name 10107876; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
Adding drive H:
Drive list = C:|F:|H:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\hardy-desktop-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nst3360.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-amd64.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Release Candidate amd64 (20080417)
      cdversion=8.04 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release Candidate cdbuild=20080417 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release Candidate amd64 (20080417)
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
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
instfiles_pre
instfiles_show
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
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
      Is Valid CD E:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\hardy-desktop-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nst3360.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-amd64.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Release Candidate amd64 (20080417)
      cdversion=8.04 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release Candidate cdbuild=20080417 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release Candidate amd64 (20080417)
Using C:\ubuntu-backup\hardy-desktop-amd64.iso
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Checking/Downloading Ubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
get_md5 http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg md5=
Download status=The requested URL returned error: 404
Error downloading http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg, The req
Trying remote metalink2: http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-amd64.metalink
get_md5 http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-amd64.metalink
Downloading: trymefirst= url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=The requested URL returned error: 404
Error downloading http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg, The req
Using C:\ubuntu-backup\hardy-desktop-amd64.iso but skipping checksum since no metalink file could be found
ISO file hardy-desktop-amd64.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\hardy-desktop-amd64.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\hardy-desktop-amd64.iso
UncompressFilesPriorInstall
Drive & Path name d; Volume name ; Max #/chars in vol name ; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
C:\Users\DAE508~1.M4N\AppData\Local\Temp\nst3360.tmp\wubibcd.exe 
 1:0 
 2:Employing Vista x64 sysnative workaround.
Operation completed successfully. New ID is {dc0245cb-0ac9-11dd-b663-00508db55b7b}
 
 3:HDD 
 4:3
vistaBootDriveCode = {dc0245cb-0ac9-11dd-b663-00508db55b7b} <=> peration completed successfully. New I
vistaBootDriveCode {dc0245cb-0ac9-11dd-b663-00508db55b7b}
Drive & Path name /Users/da.m4nn; Volume name ; Max #/chars in vol name d; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
UncompressFilesAfterInstall
Installation completed successfully!
instfiles_leave
finish_pre
finish_show
finish_leave

```

I've been trying over and over again since Wubi-8.04-alpha-rev449 and with multiple iso downloads with no luck... I can't find information on a fix anywhere. I'm downloading the release candidate now and grabbed rev492. Will try as soon as the RC finishes. I assume I'll be getting the same result though as that's been the case :/. Any help is HIGHLY appreciated!

---

### Post by airjer on 2008-04-20
Well rev492 deleted the release candidate iso, lol... re-downloading it and I'll run the built in Wubi.

---

### Post by airjer on 2008-04-20
Turns out all I had to do was input the "irqpoll" option and it went right into the install... such a simple step fr all this trouble I've been going through... I kept reading about it, but no one really stated where to input it so I just guessed and input it towards the end of the second boot line.

---

### Post by ago on 2008-04-20
Can you please add your recipe to the WubiGuide?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

