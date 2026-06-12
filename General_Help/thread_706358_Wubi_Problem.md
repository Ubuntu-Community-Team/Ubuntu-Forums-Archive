---
title: "Wubi Problem"
date: 2008-02-24
forum: General Help
---

### Post by skezza on 2008-02-24
I would normally use a proper installation, but I need it to work on the NT Bootloader sadly. I know its possible, but I have not looked into it, but i assumed Wubi would be a good alternative. Not one version of Wubi works. 7.04 one gets block device error, 7.10 flash restarts and 8.04 flash restarts. Looks like its not going to work huh?

---

### Post by ago on 2008-02-24
Skezza I will need more details to be able to help (I am more interested in 8.04 at this point...).

There is a log in the user temp file (type %temp% in windows explorer) which is relevant for any issue on the windows side.

---

### Post by skezza on 2008-02-28
sorry it took so long to reply heres my log:

ill say this now, arch=amd64????????
its an Intel Quad Core my friend. certainly not an amd, with no disrespect to them because ive had them and they are very good!

> ============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Joe\LOCALS~1\Temp\nsu343.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Joe\Local Settings\Temporary Internet Files\Content.IE5\T0ZDUOA1\Wubi-8.04-alpha-rev429[1].exe" 
debug=, 32bit=, cdboot=
arch=amd64
DetectCD
      Is Valid CD D:\
CDInfo cleared
      Is Valid CD C:\
CDInfo cleared
      Is Valid CD E:\
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive E:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in c: is 921032
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder E:\
GMT=0
Country=GB
Locale=en_GB
TimeZone=Europe/London
Domain=localdomain
HostName=home-50b7384f45
ComputerName=HOME-50B7384F45
EnvUsername=Joe
UserDomain=HOME-50B7384F45
UserInfoName=Joe
UserProfileFolder=C:\Documents and Settings\Joe
UserProfileName=Joe 
ShowMainPage
Making drive list
Drive & Path name 1244; Volume name ; Max #/chars in vol name 1697064; Volume Serial # -991892807; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Adding drive C:
Drive & Path name 1244; Volume name MAC; Max #/chars in vol name 1697072; Volume Serial # -1008610788; Max #/chars in dir/file names 255; File System Flags 6; File System Type HFSJ; File System Name Size HDD
Skipping drive E:, unknown filesystem HFSJ
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
AddDistroToList Ubuntu-i386
AddDistroToList Ubuntu-amd64
AddDistroToList Kubuntu-i386
AddDistroToList Kubuntu-amd64
AddDistroToList Xubuntu-i386
AddDistroToList Xubuntu-amd64
AddDistroToList Edubuntu-i386
AddDistroToList Edubuntu-amd64
DistroList = Ubuntu|Kubuntu|Xubuntu|Edubuntu
PopulateLanguageListBox
      GetDistroInfo distrfullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-amd64.iso.metalink
      ->isoKernel=casper/vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
      GetDistroInfo distrfullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-amd64.iso.metalink
      ->isoKernel=casper/vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
LeaveMainPage
Locale=en_GB
      GetDistroInfo distrfullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-amd64.iso.metalink
      ->isoKernel=casper/vmlinuz
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
      Is Valid CD D:\
CDInfo cleared
      Is Valid CD C:\
CDInfo cleared
      Is Valid CD E:\
CDInfo cleared
No CD found
DetectIso
Checking/Downloading ubuntu-desktop-amd64.iso.metalink
retrieve_partial_files
check_internet_connection
connected
Trying remote metalink: [http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-amd64.iso.metalink](http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-amd64.iso.metalink)
Downloading: isopath= remote_metalink=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-amd64.iso.metalink
Download status=success:C:\ubuntu\install\hardy-desktop-amd64.iso
ISO file hardy-desktop-amd64.iso retrieved!!!
CopyKernel isokernel=casper/vmlinuz, iso=C:\ubuntu\install\hardy-desktop-amd64.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\hardy-desktop-amd64.iso
UncompressFilesPriorInstall
Drive & Path name 1789872; Volume name ; Max #/chars in vol name 34; Volume Serial # -991892807; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
rootSize=13000 homesize=0, swapsize=2000, usrsize=0
Drive & Path name 1962264; Volume name ; Max #/chars in vol name 34; Volume Serial # -991892807; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
rootSize=13000 homesize=0, swapsize=2000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=13000
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=2000
UncompressFilesAfterInstall
============ Uninstaller ============
PLUGINSDIR=C:\DOCUME~1\Joe\LOCALS~1\Temp\nse35.tmp
un.install
un.BackupIso
Backup C:\ubuntu\install\hardy-desktop-amd64.iso
un.CleanBcd
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanConfig.sys C:\
un.CleanThisDrive E:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
un.RemoveUninstallers C:\WINDOWS\Uninstall.exe

---

### Post by ago on 2008-02-28
The name "amd64" is extremely unfortunate since it creates a lot of confusion. It simply means "64bit" architectures, such as yours, whether Intel or AMD.
The above logs are fine by the way.

---

### Post by skezza on 2008-02-28
right, so why the reset?

It simply flash resets everytime i try to install? Any tricks in store? Ive thought maybe downloading the 8.04 Alpha Desktop CD and installing a proper install but im going to end up messing up my bootloader set up :(

---

### Post by ago on 2008-02-28
I do not understand what you mean by "flash reset" can you pls rephrase?
Do you mean that wubi crashes?

---

### Post by skezza on 2008-02-29
basically. i load wubi from the bootloader (Ubuntu Linux) and it immediately resets. It just goes in a loop. It will reset everytime i try. some call it flash resetting some call it hard resetting

---

### Post by ago on 2008-03-01
So you select wubi from the bootloader and the system reboots.
Is that correct?
Try pressing "INS" rapidly as soon as you select Ubuntu
You should see a bit more messages

---

### Post by skezza on 2008-03-01
INS? What do you mean INS? not heard that phraze before. Because its from windows bootloader obviously standard options are a bit restricted. There used to be a debug mode but i cant seem to work out where that is.

---

### Post by lond on 2008-03-01
> **skezza said:**
> INS? What do you mean INS? not heard that phraze before. Because its from windows bootloader obviously standard options are a bit restricted. There used to be a debug mode but i cant seem to work out where that is.

He referring to the "Insert" button on your keyboard.

// lond

---

### Post by FrostiEE on 2008-03-01
> **lond said:**
> He referring to the "Insert" button on your keyboard.

// lond

And you press insert rapidly *after* you choose Ubuntu from the  Windows bootloader.

---

### Post by skezza on 2008-03-11
sorry i took so long to reply. here is what i have, i took a picture and ill type in what happens after i press on the bootloader. btw, ive also inserted an IDE hard drive and will install on that tonight to see if it makes any difference :)

Kernel alive
kernel direct mapping tables up to........ (cant distinguish it but anyway) then it normally restarts or just goes black screen mode :( ill try the insert key

---

### Post by skezza on 2008-03-20
That is just 8.04 by the way, 7 gives a different error, but thats with both of them, Wubi and the live disk. Is there any way round this?

---

### Post by skezza on 2008-04-17
> **FrostiEE said:**
> And you press insert rapidly *after* you choose Ubuntu from the  Windows bootloader.tried that, same symptoms. just checking if theres an update for it now.

---

### Post by skezza on 2008-04-20
would it be worth downloading an old version and trying that. because i got further with those ones, you know? at least i got an error rather than just a blank screen. :(

---

### Post by remard on 2008-04-20
ok yesterday i download wubi 8.04 to install on my brand new machine   acer whit vista home basic , the thing install and reboot then a got the option of ubuntu or vista when I chosse ubuntu i get a error message , cant boot ubuntu , can annyone help me ...i use ubuntu on my hold machine and love it ...i would like to run it on my new vista ...i whanna use both ...

---

### Post by ago on 2008-04-20
See [https://wiki.ubuntu.com/WubiGuide#head-a2f73efbce9a94cf460a095713c599594c3a05d1](https://wiki.ubuntu.com/WubiGuide#head-a2f73efbce9a94cf460a095713c599594c3a05d1)

---

