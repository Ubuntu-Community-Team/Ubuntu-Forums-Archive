---
title: "Install problem: Partman failed with exit code 10"
date: 2008-04-24
forum: General Help
---

### Post by scythe000 on 2008-04-24
I've tried both the regular and alternate cd for 8.04 Wubi, installs ok, then after I set my timezone, I get the follwoing message: Partman failed with exit code 10.

c2d x6800, Vista, 2x500gb in hardware raid 0, 4 gigs of ram.

Any ideas? I can choose to continue anyway, but it will either crash, or just dump me to the live cd.

---

### Post by scythe000 on 2008-04-24
Here's the wubi-8.04-beta-rev495.log:

============ Installer ============
PLUGINSDIR=C:\Users\SCYTHE~1.SEP\AppData\Local\Temp\nsb9298.tmp
detect_all
Parsing cmdline I:\wubi.exe
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-2 MB
arch=amd64
DetectCD
      Is Valid CD I:
      IsValid Ubuntu 8.04 "Hardy Heron" - Release amd64 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release amd64 (20080423)
Found CD I:
Found CD cddrive=I:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive H:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name ; Max #/chars in vol name 7036400; Volume Serial # 1815001567; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name 750gig; Max #/chars in vol name 7036404; Volume Serial # -1193568107; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1712; Volume name 1TB; Max #/chars in vol name 7036420; Volume Serial # 873511614; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6476856; Volume name ; Max #/chars in vol name 27; Volume Serial # 1815001567; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 647522
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
IsBackupFolder H:\
GMT=-7
Country=US
Locale=en_US.UTF-8
TimeZone=America/Denver
Domain=localdomain
HostName=Sepulchre
ComputerName=SEPULCHRE
EnvUsername=Scythe
UserDomain=Sepulchre
UserInfoName=Scythe
UserProfileFolder=C:\Users\Scythe.Sepulchre
UserProfileName=Scythe 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1774; Volume name ; Max #/chars in vol name 7053912; Volume Serial # 1815001567; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1774; Volume name 750gig; Max #/chars in vol name 7053916; Volume Serial # -1193568107; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
IsValidFileSystem H:
Drive & Path name 1774; Volume name 1TB; Max #/chars in vol name 7053932; Volume Serial # 873511614; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
Adding drive H:
Drive list = C:|D:|H:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
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
      Is Valid CD I:
      IsValid Ubuntu 8.04 "Hardy Heron" - Release amd64 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release amd64 (20080423)
Found CD I:
Found CD cddrive=I:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=2e48c322d74a2291b6e0cfce6c7883cb
Checking md5 of I:\casper\filesystem.squashfs
CheckCD raw status = success:I:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Checking/Downloading Ubuntu-8.04
Skipmd5 is true, using C:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\installation.iso, cddrive=I:
Extracting with 7z kernel/initrd from C:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name ; Max #/chars in vol name scythe; Volume Serial # 1815001567; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
C:\Users\SCYTHE~1.SEP\AppData\Local\Temp\nsb9298.tmp\wubibcd.exe 
 1:0 
 2:Employing Vista x64 sysnative workaround.
Operation completed successfully. New ID is {7ee638ff-f871-11dc-b326-00044b14afc6}
 
 3:HDD 
 4:3
vistaBootDriveCode = {7ee638ff-f871-11dc-b326-00044b14afc6} <=> peration completed successfully. New I
vistaBootDriveCode {7ee638ff-f871-11dc-b326-00044b14afc6}
Drive & Path name /Users/Scythe.Sepulchre; Volume name ; Max #/chars in vol name success; Volume Serial # 1815001567; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=528 for drive=I:
EjectCD DeviceIoControl exited with code 0 (1==success)
Installation completed successfully!
============ Uninstaller ============
PLUGINSDIR=C:\Users\SCYTHE~1.SEP\AppData\Local\Temp\nsr128A.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive D:\
un.CleanConfig.sys D:\
un.CleanThisDrive H:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Installer ============
PLUGINSDIR=C:\Users\SCYTHE~1.SEP\AppData\Local\Temp\nso97DF.tmp
detect_all
Parsing cmdline E:\wubi.exe
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-2 MB
arch=amd64
DetectCD
      Is Valid CD E:
      IsValid Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive H:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name ; Max #/chars in vol name 9254096; Volume Serial # 1815001567; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name 750gig; Max #/chars in vol name 9254100; Volume Serial # -1193568107; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1712; Volume name 1TB; Max #/chars in vol name 9254116; Volume Serial # 873511614; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 9164712; Volume name ; Max #/chars in vol name 30; Volume Serial # 1815001567; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 647023
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
IsBackupFolder H:\
GMT=-7
Country=US
Locale=en_US.UTF-8
TimeZone=America/Denver
Domain=localdomain
HostName=Sepulchre
ComputerName=SEPULCHRE
EnvUsername=Scythe
UserDomain=Sepulchre
UserInfoName=Scythe
UserProfileFolder=C:\Users\Scythe.Sepulchre
UserProfileName=Scythe 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1774; Volume name ; Max #/chars in vol name 9489208; Volume Serial # 1815001567; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1774; Volume name 750gig; Max #/chars in vol name 9489212; Volume Serial # -1193568107; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
IsValidFileSystem H:
Drive & Path name 1774; Volume name 1TB; Max #/chars in vol name 9489228; Volume Serial # 873511614; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
Adding drive H:
Drive list = C:|D:|H:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Ubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD E:
      IsValid Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=3879aa51ef0b4b1b7bf9472744208417
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Checking/Downloading Ubuntu-8.04
Skipmd5 is true, using C:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from C:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name ; Max #/chars in vol name scythe; Volume Serial # 1815001567; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
C:\Users\SCYTHE~1.SEP\AppData\Local\Temp\nso97DF.tmp\wubibcd.exe 
 1:0 
 2:Employing Vista x64 sysnative workaround.
Operation completed successfully. New ID is {7ee63900-f871-11dc-b326-00044b14afc6}
 
 3:HDD 
 4:3
vistaBootDriveCode = {7ee63900-f871-11dc-b326-00044b14afc6} <=> peration completed successfully. New I
vistaBootDriveCode {7ee63900-f871-11dc-b326-00044b14afc6}
Drive & Path name /Users/Scythe.Sepulchre; Volume name ; Max #/chars in vol name success; Volume Serial # 1815001567; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=488 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!

---

### Post by scythe000 on 2008-04-24
And here's the metadl_log.txt:

parsing arguments:
     MD5
     TRANSLATE:
     /CHECK
Source
Source is a local file
Checking file E:\casper\filesystem.squashfs
MD5: 3879aa51ef0b4b1b7bf9472744208417 3879aa51ef0b4b1b7bf9472744208417
File check successful!

---

### Post by ago on 2008-04-25
Most "hardware" raid are in fact software raids that are not supported.
In any case, uninstall, run wubi again, at boot after ubuntu press "esc" and select "verbose mode"

You should have a C:\ubuntu\installation-logs.zip. Please attach it here.

---

### Post by sloggerkhan on 2008-04-25
don't know if this applies to you, but on my computer very similar thing happened unless I installed with external HDs unplugged.

---

### Post by ago on 2008-04-25
> **sloggerkhan said:**
> don't know if this applies to you, but on my computer very similar thing happened unless I installed with external HDs unplugged.

It would be interessing to have full logs (verbose mode) with the extarnal HD plugged in!

---

### Post by scythe000 on 2008-04-25
No external HDDs, except for a thumbdrive used for Vista's ReadyBoost.
Raid 0 is set up in my BIOS, so I'm releatively sure that's hardware, not software.
There is no c:\ubuntu\installation-logs.zip file.

As soon as I can, I'll try the verbose mode. Thanks!

---

### Post by ago on 2008-04-25
When the installation stops, press CTRL + ALT + F2 then run

sudo sh /custom-installation/hooks/failure-command.sh

the command will generate the log files above.

Also what is the make and model of your raid controller? Runnincg lspci -vvv might also provide some useful info

---

### Post by scythe000 on 2008-04-26
Ok, gave the above a try. Nothing happens when I CTRL-ALT-F2 or F-anything. If I cancel install, it then dumps me to a live cd  ubuntu, which is what I'm writing this from.

I did do the verbose mode, and saw a lot of "attempt to access beyond end of device" errors and "buffer I/O error on Device SD1".

I apologize for total n00bness, but I'm not sure what these mean. They look like memory errors to me. Any Ideas? Shoot away, I'm in a live CD as it is.

I did find a file called .xsession-errors:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinpu$
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/16402
** Message: another SSH agent is running at: /tmp/ssh-eTWvb16402/agent.16402
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
Window manager warning: Failed to read saved session file /home/ubuntu/.metacit$
seahorse nautilus module initialized
Initializing nautilus-share extension
11

** (nautilus:18139): WARNING **: Unable to add monitor: Not supported
evolution-alarm-notify-Message: Setting timeout for 64662 1209254400 1209189738
evolution-alarm-notify-Message:  Sun Apr 27 00:00:00 2008

evolution-alarm-notify-Message:  Sat Apr 26 06:02:18 2008

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usersha$
Please ask your system administrator to enable user sharing.

  PID TTY          TIME CMD
17685 ?        00:00:00 pulseaudio
WARNING: modinfo for module fglrx failed: modinfo: could not open /lib/modules/$

WARNING: modinfo for module nvidia_new failed: modinfo: could not open /lib/mod$

WARNING: modinfo for module nvidia failed: modinfo: could not open /lib/modules$

WARNING: modinfo for module nvidia_new failed: modinfo: could not open /lib/mod$

---

### Post by ago on 2008-04-26
Try to run chkdsk /r on windows (same partition where you have wubi).

---

### Post by scythe000 on 2008-04-27
Ok, just finished chkdsk /r. Took 4 hours or so. No errors.

---

### Post by ago on 2008-04-27
Now uninstall wubi
And install again
Please let me know if it works or not

---

### Post by scythe000 on 2008-04-27
Ok, progress!

It fully installed this time. I booted into Ubuntu, installed the nVidia driver, rebooted and now am faced with an error 15, and Ubuntu will not load. Ugh.

1. So, were there errors on my HDD that the CHKDSK /R fixed?

2. I'll search around, I think I saw some threads about the error 15.

3. How do I mount my windows partition?

TIA!

---

### Post by ago on 2008-04-27
try to get the exact error message

---

### Post by scythe000 on 2008-04-28
Ok, it was telling me it (grub?) couldn't find the root.dsk file. I took a little initiative and edited the boot file, and it turns out grub was trying to boot from the wrong partition. Don't know how or why it changed, although it seems others have had the same issues. I guess I just need to figure out how to mount my C:\ drive, and find myself a cool GUI theme.

---

### Post by ago on 2008-04-28
If you have multiple disks see [https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230](https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230)

---

### Post by Ravioli817 on 2008-05-01
I just installed Ubuntu with the Wubi installer, it told me to reboot and i got the same error message "Partman failed with exit code 10." I tried installing it in verbose mode and then I reinstalled it but i still got the same message...

---

### Post by ago on 2008-05-01
Do you have logs in C:\ubuntu\installation-logs.zip?
If so post them here

---

### Post by Ravioli817 on 2008-05-02
I have the folder but the installation-logs.zip doesnt exist but i have a curl_log and a metadll_log

---

### Post by Gripp on 2008-05-02
> **scythe000 said:**
> 
...Raid 0 is set up in my BIOS, so I'm releatively sure that's hardware, not software.
...

i have my raid 0 set up in the bios too, windows runs from the raid set up, only see the one disk, etc. and i thought the same. but it turned out linux saw it as a software raid.  it was good fun trying to mount in linux.. if it is the using intel raid then i think it is always a softraid.

---

### Post by Ravioli817 on 2008-05-02
I only have one hard drive so raid doesnt apply to me, is raid your problem or is it because of something else? The error message told me to look at /var/log/syslog for more information. It wont let me attach it so i have to copy, i dont know if it will help but just in case...

here it is:

May  3 00:35:43 ubuntu avahi-daemon[7968]: Registering new address record for fe80::211:11ff:fe3e:532a on eth0.*.
May  3 00:35:44 ubuntu ubiquity[8481]: Ubiquity 1.8.7
May  3 00:35:48 ubuntu ubiquity[8481]: log-output -t ubiquity laptop-detect
May  3 00:35:50 ubuntu ubiquity[8481]: log-output -t ubiquity fontconfig-voodoo --auto --force --quiet
May  3 00:35:52 ubuntu ubiquity[8481]: switched to page stepLanguage
May  3 00:35:52 ubuntu kernel: [   67.322971] eth0: no IPv6 routers present
May  3 00:35:53 ubuntu localechooser: info: Locale has been preseeded to en_US.UTF-8
May  3 00:35:53 ubuntu localechooser: info: Set languagechooser/language-name = 'English'
May  3 00:35:53 ubuntu localechooser: info: Set countrychooser/shortlist-en = 'US'
May  3 00:35:53 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May  3 00:35:53 ubuntu localechooser: info: LANGNAME=English
May  3 00:35:53 ubuntu localechooser: info: line=English;0;en;US;en_US.UTF-8;UTF-8;;kbd=lat0-sun16(utf8)
May  3 00:35:53 ubuntu localechooser: info: Set debian-installer/language = 'en'
May  3 00:35:53 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May  3 00:35:53 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
May  3 00:35:53 ubuntu localechooser: info: Set debian-installer/country = 'US'
May  3 00:35:53 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'kbd=lat0-sun16(utf8)'
May  3 00:35:53 ubuntu localechooser: info: Set debconf/language = 'en'
May  3 00:35:53 ubuntu localechooser: info: Set debian-installer/country = 'US'
May  3 00:35:53 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May  3 00:35:53 ubuntu ubiquity[8481]: debconffilter_done: Language (current: Language)
May  3 00:35:53 ubuntu ubiquity[8481]: Step_before = stepLanguage
May  3 00:35:55 ubuntu ubiquity[8481]: switched to page stepLocation
May  3 00:36:06 ubuntu localechooser: info: Locale has been preseeded to en_US.UTF-8
May  3 00:36:06 ubuntu localechooser: info: Set languagechooser/language-name-fb = 'English'
May  3 00:36:06 ubuntu localechooser: info: Set countrychooser/shortlist-en = 'US'
May  3 00:36:06 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May  3 00:36:06 ubuntu localechooser: info: Set debconf/language = ''
May  3 00:36:06 ubuntu localechooser: info: Set countrychooser/country-name = 'United States'
May  3 00:36:06 ubuntu localechooser: info: Set debian-installer/country = 'US'
May  3 00:36:06 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May  3 00:36:06 ubuntu ubiquity[8481]: debconffilter_done: Timezone (current: Timezone)
May  3 00:36:06 ubuntu ubiquity[8481]: Step_before = stepLocation
May  3 00:36:07 ubuntu ubiquity[8481]: log-output -t ubiquity setxkbmap -model pc105 -layout us
May  3 00:36:08 ubuntu ubiquity: Your console font configuration will be updated the next time your system
May  3 00:36:08 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
May  3 00:36:08 ubuntu ubiquity[8481]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
May  3 00:36:08 ubuntu ubiquity[8481]: debconffilter_done: ConsoleSetup (current: ConsoleSetup)
May  3 00:36:08 ubuntu ubiquity[8481]: Step_before = stepLocation
May  3 00:36:09 ubuntu kernel: [   83.661062] end_request: I/O error, dev fd0, sector 0
May  3 00:36:09 ubuntu kernel: [   83.685048] end_request: I/O error, dev fd0, sector 0
May  3 00:36:22 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May  3 00:36:22 ubuntu ntfsresize: Device name        : /dev/sda2
May  3 00:36:22 ubuntu ntfsresize: NTFS volume version: 3.1
May  3 00:36:22 ubuntu ntfsresize: Cluster size       : 4096 bytes
May  3 00:36:22 ubuntu ntfsresize: Current volume size: 76174316032 bytes (76175 MB)
May  3 00:36:22 ubuntu ntfsresize: Current device size: 76174318080 bytes (76175 MB)
May  3 00:36:22 ubuntu ntfsresize: Checking filesystem consistency ...
May  3 00:36:22 ubuntu ntfsresize: Accounting clusters ...
May  3 00:36:22 ubuntu ntfsresize: Space in use       : 58887 MB (77.3%)
May  3 00:36:22 ubuntu ntfsresize: Collecting resizing constraints ...
May  3 00:36:22 ubuntu ntfsresize: You might resize at 58886766592 bytes or 58887 MB (freeing 17288 MB).
May  3 00:36:22 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May  3 00:36:24 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May  3 00:36:24 ubuntu ntfsresize: Device name        : /dev/sda2
May  3 00:36:24 ubuntu ntfsresize: NTFS volume version: 3.1
May  3 00:36:24 ubuntu ntfsresize: Cluster size       : 4096 bytes
May  3 00:36:24 ubuntu ntfsresize: Current volume size: 76174316032 bytes (76175 MB)
May  3 00:36:24 ubuntu ntfsresize: Current device size: 76174318080 bytes (76175 MB)
May  3 00:36:24 ubuntu ntfsresize: Checking filesystem consistency ...
May  3 00:36:24 ubuntu ntfsresize: Accounting clusters ...
May  3 00:36:24 ubuntu ntfsresize: Space in use       : 58887 MB (77.3%)
May  3 00:36:24 ubuntu ntfsresize: Collecting resizing constraints ...
May  3 00:36:24 ubuntu ntfsresize: You might resize at 58886766592 bytes or 58887 MB (freeing 17288 MB).
May  3 00:36:24 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May  3 00:36:25 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May  3 00:36:25 ubuntu ntfsresize: Device name        : /dev/sda2
May  3 00:36:25 ubuntu ntfsresize: NTFS volume version: 3.1
May  3 00:36:25 ubuntu ntfsresize: Cluster size       : 4096 bytes
May  3 00:36:25 ubuntu ntfsresize: Current volume size: 76174316032 bytes (76175 MB)
May  3 00:36:25 ubuntu ntfsresize: Current device size: 76174318080 bytes (76175 MB)
May  3 00:36:25 ubuntu ntfsresize: Checking filesystem consistency ...
May  3 00:36:25 ubuntu ntfsresize: Accounting clusters ...
May  3 00:36:25 ubuntu ntfsresize: Space in use       : 58887 MB (77.3%)
May  3 00:36:25 ubuntu ntfsresize: Collecting resizing constraints ...
May  3 00:36:25 ubuntu ntfsresize: You might resize at 58886766592 bytes or 58887 MB (freeing 17288 MB).
May  3 00:36:25 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May  3 00:36:25 ubuntu ubiquity[8481]: debconffilter_done: Partman (current: Partman)
May  3 00:36:25 ubuntu ubiquity[8481]: dbfilter_handle_status: ('Partman', 10)
May  3 00:36:33 ubuntu ubiquity[8481]: dbfilter_handle_status: response -7
May  3 00:36:33 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
May  3 00:36:33 ubuntu ubiquity[8481]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
May  3 00:36:33 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
May  3 00:36:33 ubuntu ubiquity[8481]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^xserver-xorg/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
May  3 00:36:35 ubuntu /usr/sbin/cron[9571]: (CRON) INFO (pidfile fd = 3)
May  3 00:36:35 ubuntu /usr/sbin/cron[9572]: (CRON) STARTUP (fork ok)
May  3 00:36:35 ubuntu /usr/sbin/cron[9572]: (CRON) INFO (Running @reboot jobs)
May  3 00:36:35 ubuntu kernel: [  110.391385] [drm] Setting GART location based on new memory map
May  3 00:36:35 ubuntu kernel: [  110.391858] [drm] Loading R300 Microcode
May  3 00:36:35 ubuntu kernel: [  110.391910] [drm] writeback test succeeded in 1 usecs
May  3 00:36:38 ubuntu gdm[9526]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
May  3 00:36:38 ubuntu gdm[9526]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
May  3 00:36:38 ubuntu gdm[9526]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
May  3 00:36:41 ubuntu pulseaudio[9788]: pid.c: Stale PID file, overwriting.
May  3 00:36:42 ubuntu hcid[8242]: Default passkey agent (:1.26, /org/bluez/passkey) registered
May  3 00:36:42 ubuntu hcid[8242]: Default authorization agent (:1.26, /org/bluez/auth) registered
May  3 00:36:46 ubuntu NetworkManager: <info>  Updating allowed wireless network lists. 
May  3 00:36:46 ubuntu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

---

### Post by ago on 2008-05-03
ntfsresize should not run at all.
Uninstall, renstall, check that you have virtual disks in c:\ubuntu\disks\*.disk

Then at boot press ESC and select verbose mode. If it fails please attach the log.

---

### Post by Ravioli817 on 2008-05-03
Thanks Ago, reinstalling in verbose worked

---

### Post by JonTheJester1337 on 2008-05-09
I have run into the same problem but have been unable to overcome. First off, I know I have a RAID-0 array via Promise Technology: FastTrak 378/SATA 378. If this is futile because of this, please let me know.
I cleaned up a bunch of space on my hard disk, ran chkdsk /r on the main drive, defragged, then installed Wubi. Installation runs fine until the partitioner comes in, where I get the error. I installed via verbose mode, so attached is var/log/syslog. I am unfamiliar with working on Ubuntu just yet, but do I need to do something special to get it to see the RAID array as a single drive as opposed to 2 drives? My array claims to be hardware based...

May  9 13:02:54 ubuntu syslogd 1.5.0#1ubuntu1: restart.
May  9 13:02:55 ubuntu kernel: Inspecting /boot/System.map-2.6.24-16-generic
May  9 13:02:55 ubuntu kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
May  9 13:02:55 ubuntu kernel: Symbols match kernel version 2.6.24.
May  9 13:02:55 ubuntu kernel: Loaded 23088 symbols from 99 modules.
May  9 13:02:55 ubuntu kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
May  9 13:02:55 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
May  9 13:02:55 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
May  9 13:02:55 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
May  9 13:02:55 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
May  9 13:02:55 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fea0000 (usable)
May  9 13:02:55 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fea0000 - 000000007feaf000 (ACPI data)
May  9 13:02:55 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007feaf000 - 000000007ff00000 (ACPI NVS)
May  9 13:02:55 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
May  9 13:02:55 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
May  9 13:02:55 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  9 13:02:55 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
May  9 13:02:55 ubuntu kernel: [    0.000000] 1150MB HIGHMEM available.
May  9 13:02:55 ubuntu kernel: [    0.000000] 896MB LOWMEM available.
May  9 13:02:55 ubuntu kernel: [    0.000000] found SMP MP-table at 000f6bf0
May  9 13:02:55 ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 523936) 0 entries of 256 used
May  9 13:02:55 ubuntu kernel: [    0.000000] Zone PFN ranges:
May  9 13:02:55 ubuntu kernel: [    0.000000]   DMA             0 ->     4096
May  9 13:02:55 ubuntu kernel: [    0.000000]   Normal       4096 ->   229376
May  9 13:02:55 ubuntu kernel: [    0.000000]   HighMem    229376 ->   523936
May  9 13:02:55 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
May  9 13:02:55 ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
May  9 13:02:55 ubuntu kernel: [    0.000000]     0:        0 ->   523936
May  9 13:02:55 ubuntu kernel: [    0.000000] On node 0 totalpages: 523936
May  9 13:02:55 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May  9 13:02:55 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
May  9 13:02:55 ubuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
May  9 13:02:55 ubuntu kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
May  9 13:02:55 ubuntu kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
May  9 13:02:55 ubuntu kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
May  9 13:02:55 ubuntu kernel: [    0.000000]   HighMem zone: 292259 pages, LIFO batch:31
May  9 13:02:55 ubuntu kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May  9 13:02:55 ubuntu kernel: [    0.000000] DMI present.
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6C50 checksum 0
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: RSDP 000F6C50, 0014 (r0 PTLTD )
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: RSDT 7FEA9389, 003C (r1 PTLTD    RSDT    6040000  LTP        0)
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: FACP 7FEAEE21, 0074 (r1 Clevo            6040000 PTL         3)
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: DSDT 7FEA93C5, 5A5C (r1  INTEL GRANTSDL  6040000 MSFT  100000E)
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: FACS 7FEAFFC0, 0040
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: APIC 7FEAEE95, 0068 (r1 PTLTD  ^I APIC    6040000  LTP        0)
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: APIC 7FEAEEFD, 0068 (r1 PTLTD  ^I APIC    6040000  LTP        0)
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: BOOT 7FEAEF65, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: MCFG 7FEAEF8D, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: SSDT 7FEAEFC9, 0037 (r1 PTLTD  ACPIHT    6040000  LTP        1)
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  9 13:02:55 ubuntu kernel: [    0.000000] Processor #0 15:3 APIC version 20
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
May  9 13:02:55 ubuntu kernel: [    0.000000] Processor #1 15:3 APIC version 20
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  9 13:02:55 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
May  9 13:02:55 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
May  9 13:02:55 ubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  9 13:02:55 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  9 13:02:55 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
May  9 13:02:55 ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009c000 - 000000000009d000
May  9 13:02:55 ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 00000000000a0000
May  9 13:02:55 ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
May  9 13:02:55 ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
May  9 13:02:55 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519843
May  9 13:02:55 ubuntu kernel: [    0.000000] Kernel command line: debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
May  9 13:02:55 ubuntu kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
May  9 13:02:55 ubuntu kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
May  9 13:02:55 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  9 13:02:55 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  9 13:02:55 ubuntu kernel: [    0.000000] Initializing CPU#0
May  9 13:02:55 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  9 13:02:55 ubuntu kernel: [    0.000000] Detected 3400.380 MHz processor.
May  9 13:02:55 ubuntu kernel: [   28.513949] Console: colour VGA+ 80x25
May  9 13:02:55 ubuntu kernel: [   28.513953] console [tty0] enabled
May  9 13:02:55 ubuntu kernel: [   28.517335] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  9 13:02:55 ubuntu kernel: [   28.517685] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  9 13:02:55 ubuntu kernel: [   28.619619] Memory: 2065336k/2095744k available (2157k kernel code, 29016k reserved, 998k data, 364k init, 1178240k highmem)
May  9 13:02:55 ubuntu kernel: [   28.619680] virtual kernel memory layout:
May  9 13:02:55 ubuntu kernel: [   28.619681]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
May  9 13:02:55 ubuntu kernel: [   28.619682]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May  9 13:02:55 ubuntu kernel: [   28.619683]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
May  9 13:02:55 ubuntu kernel: [   28.619683]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
May  9 13:02:55 ubuntu kernel: [   28.619684]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
May  9 13:02:55 ubuntu kernel: [   28.619685]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
May  9 13:02:55 ubuntu kernel: [   28.619686]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
May  9 13:02:55 ubuntu kernel: [   28.620001] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May  9 13:02:55 ubuntu kernel: [   28.620115] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
May  9 13:02:55 ubuntu kernel: [   28.700141] Calibrating delay using timer specific routine.. 6806.63 BogoMIPS (lpj=13613277)
May  9 13:02:55 ubuntu kernel: [   28.700242] Security Framework initialized
May  9 13:02:55 ubuntu kernel: [   28.700286] SELinux:  Disabled at boot.
May  9 13:02:55 ubuntu kernel: [   28.700336] AppArmor: AppArmor initialized
May  9 13:02:55 ubuntu kernel: [   28.700378] Failure registering capabilities with primary security module.
May  9 13:02:55 ubuntu kernel: [   28.700426] Mount-cache hash table entries: 512
May  9 13:02:55 ubuntu kernel: [   28.700586] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
May  9 13:02:55 ubuntu kernel: [   28.700909] monitor/mwait feature present.
May  9 13:02:55 ubuntu kernel: [   28.700950] using mwait in idle threads.
May  9 13:02:55 ubuntu kernel: [   28.700993] CPU: Trace cache: 12K uops, L1 D cache: 16K
May  9 13:02:55 ubuntu kernel: [   28.701063] CPU: L2 cache: 1024K
May  9 13:02:55 ubuntu kernel: [   28.701103] CPU: Physical Processor ID: 0
May  9 13:02:55 ubuntu kernel: [   28.701143] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
May  9 13:02:55 ubuntu kernel: [   28.701467] Compat vDSO mapped to ffffe000.
May  9 13:02:55 ubuntu kernel: [   28.701520] Checking 'hlt' instruction... OK.
May  9 13:02:55 ubuntu kernel: [   28.716579] SMP alternatives: switching to UP code
May  9 13:02:55 ubuntu kernel: [   28.718319] Early unpacking initramfs... done
May  9 13:02:55 ubuntu kernel: [   28.991142] ACPI: Core revision 20070126
May  9 13:02:55 ubuntu kernel: [   28.991231] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May  9 13:02:55 ubuntu kernel: [   28.995098] CPU0: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 04
May  9 13:02:55 ubuntu kernel: [   28.995214] SMP alternatives: switching to SMP code
May  9 13:02:55 ubuntu kernel: [   28.995973] Booting processor 1/1 eip 3000
May  9 13:02:55 ubuntu kernel: [   29.006204] Initializing CPU#1
May  9 13:02:55 ubuntu kernel: [   29.083950] Calibrating delay using timer specific routine.. 6800.75 BogoMIPS (lpj=13601517)
May  9 13:02:55 ubuntu kernel: [   29.083959] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
May  9 13:02:55 ubuntu kernel: [   29.083966] monitor/mwait feature present.
May  9 13:02:55 ubuntu kernel: [   29.083971] CPU: Trace cache: 12K uops, L1 D cache: 16K
May  9 13:02:55 ubuntu kernel: [   29.083974] CPU: L2 cache: 1024K
May  9 13:02:55 ubuntu kernel: [   29.083976] CPU: Physical Processor ID: 0
May  9 13:02:55 ubuntu kernel: [   29.083978] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
May  9 13:02:55 ubuntu kernel: [   29.084336] CPU1: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 04
May  9 13:02:55 ubuntu kernel: [   29.084818] Total of 2 processors activated (13607.39 BogoMIPS).
May  9 13:02:55 ubuntu kernel: [   29.085005] ENABLING IO-APIC IRQs
May  9 13:02:55 ubuntu kernel: [   29.085214] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
May  9 13:02:55 ubuntu kernel: [   29.363815] APIC calibration not consistent with PM Timer: 232ms instead of 100ms
May  9 13:02:55 ubuntu kernel: [   29.363867] APIC delta adjusted to PM-Timer: 1250042 (2900268)
May  9 13:02:55 ubuntu kernel: [   29.364037] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
May  9 13:02:55 ubuntu kernel: [   29.384114] Brought up 2 CPUs
May  9 13:02:55 ubuntu kernel: [   29.384177] CPU0 attaching sched-domain:
May  9 13:02:55 ubuntu kernel: [   29.384218]  domain 0: span 03
May  9 13:02:55 ubuntu kernel: [   29.384287]   groups: 01 02
May  9 13:02:55 ubuntu kernel: [   29.384416]   domain 1: span 03
May  9 13:02:55 ubuntu kernel: [   29.384484]    groups: 03
May  9 13:02:55 ubuntu kernel: [   29.384582] CPU1 attaching sched-domain:
May  9 13:02:55 ubuntu kernel: [   29.384621]  domain 0: span 03
May  9 13:02:55 ubuntu kernel: [   29.384689]   groups: 02 01
May  9 13:02:55 ubuntu kernel: [   29.384817]   domain 1: span 03
May  9 13:02:55 ubuntu kernel: [   29.384886]    groups: 03
May  9 13:02:55 ubuntu kernel: [   29.385226] net_namespace: 64 bytes
May  9 13:02:55 ubuntu kernel: [   29.385273] Booting paravirtualized kernel on bare hardware
May  9 13:02:55 ubuntu kernel: [   29.385839] Time: 13:01:16  Date: 05/09/08
May  9 13:02:55 ubuntu kernel: [   29.385901] NET: Registered protocol family 16
May  9 13:02:55 ubuntu kernel: [   29.386174] EISA bus registered
May  9 13:02:55 ubuntu kernel: [   29.386218] ACPI: bus type pci registered
May  9 13:02:55 ubuntu kernel: [   29.386382] PCI: PCI BIOS revision 2.10 entry at 0xfd951, last bus=10
May  9 13:02:55 ubuntu kernel: [   29.386424] PCI: Using configuration type 1
May  9 13:02:55 ubuntu kernel: [   29.386464] Setting up standard PCI resources
May  9 13:02:55 ubuntu kernel: [   29.399600] ACPI: EC: Look up EC in DSDT
May  9 13:02:55 ubuntu kernel: [   29.403028] ACPI: Interpreter enabled
May  9 13:02:55 ubuntu kernel: [   29.403069] ACPI: (supports S0 S3 S4 S5)
May  9 13:02:55 ubuntu kernel: [   29.403238] ACPI: Using IOAPIC for interrupt routing
May  9 13:02:55 ubuntu kernel: [   29.403518] ACPI: EC: non-query interrupt received, switching to interrupt mode
May  9 13:02:55 ubuntu kernel: [   29.410340] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
May  9 13:02:55 ubuntu kernel: [   29.410385] ACPI: EC: driver started in interrupt mode
May  9 13:02:55 ubuntu kernel: [   29.410474] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  9 13:02:55 ubuntu kernel: [   29.411028] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
May  9 13:02:55 ubuntu kernel: [   29.411073] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
May  9 13:02:55 ubuntu kernel: [   29.411693] PCI: Transparent bridge - 0000:00:1e.0
May  9 13:02:55 ubuntu kernel: [   29.411805] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  9 13:02:55 ubuntu kernel: [   29.412035] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG_._PRT]
May  9 13:02:55 ubuntu kernel: [   29.412190] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
May  9 13:02:55 ubuntu kernel: [   29.417133] ACPI: PCI Interrupt Link [LNKA] (IRQs 10) *11
May  9 13:02:55 ubuntu kernel: [   29.417375] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
May  9 13:02:55 ubuntu kernel: [   29.417583] ACPI: PCI Interrupt Link [LNKC] (IRQs 10) *5
May  9 13:02:55 ubuntu kernel: [   29.417820] ACPI: PCI Interrupt Link [LNKD] (IRQs 11) *10
May  9 13:02:55 ubuntu kernel: [   29.418061] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
May  9 13:02:55 ubuntu kernel: [   29.418271] ACPI: PCI Interrupt Link [LNKF] (IRQs *11)
May  9 13:02:55 ubuntu kernel: [   29.418481] ACPI: PCI Interrupt Link [LNKG] (IRQs 10) *0, disabled.
May  9 13:02:55 ubuntu kernel: [   29.418753] ACPI: PCI Interrupt Link [LNKH] (IRQs 11) *10
May  9 13:02:55 ubuntu kernel: [   29.419062] Linux Plug and Play Support v0.97 (c) Adam Belay
May  9 13:02:55 ubuntu kernel: [   29.419982] pnp: PnP ACPI init
May  9 13:02:55 ubuntu kernel: [   29.420028] ACPI: bus type pnp registered
May  9 13:02:55 ubuntu kernel: [   29.425918] pnp: PnP ACPI: found 12 devices
May  9 13:02:55 ubuntu kernel: [   29.425960] ACPI: ACPI bus type pnp unregistered
May  9 13:02:55 ubuntu kernel: [   29.426002] PnPBIOS: Disabled by ACPI PNP
May  9 13:02:55 ubuntu kernel: [   29.426305] PCI: Using ACPI for IRQ routing
May  9 13:02:55 ubuntu kernel: [   29.426347] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May  9 13:02:55 ubuntu kernel: [   29.455879] NET: Registered protocol family 8
May  9 13:02:55 ubuntu kernel: [   29.455919] NET: Registered protocol family 20
May  9 13:02:55 ubuntu kernel: [   29.456026] AppArmor: AppArmor Filesystem Enabled
May  9 13:02:55 ubuntu kernel: [   29.459868] Time: tsc clocksource has been installed.
May  9 13:02:55 ubuntu kernel: [   29.471904] system 00:01: ioport range 0x800-0x83f has been reserved
May  9 13:02:55 ubuntu kernel: [   29.471947] system 00:01: ioport range 0x1000-0x107f has been reserved
May  9 13:02:55 ubuntu kernel: [   29.471990] system 00:01: ioport range 0x1180-0x11bf has been reserved
May  9 13:02:55 ubuntu kernel: [   29.472032] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
May  9 13:02:55 ubuntu kernel: [   29.472075] system 00:01: ioport range 0xfe00-0xfe00 has been reserved
May  9 13:02:55 ubuntu kernel: [   29.472118] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
May  9 13:02:55 ubuntu kernel: [   29.472161] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
May  9 13:02:55 ubuntu kernel: [   29.472204] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
May  9 13:02:55 ubuntu kernel: [   29.472247] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
May  9 13:02:55 ubuntu kernel: [   29.502757] PCI: Bridge: 0000:00:01.0
May  9 13:02:55 ubuntu kernel: [   29.502798]   IO window: 4000-4fff
May  9 13:02:55 ubuntu kernel: [   29.502839]   MEM window: b0100000-b01fffff
May  9 13:02:55 ubuntu kernel: [   29.502880]   PREFETCH window: c0000000-cfffffff
May  9 13:02:55 ubuntu kernel: [   29.502930] PCI: Bus 11, cardbus bridge: 0000:0a:00.0
May  9 13:02:55 ubuntu kernel: [   29.502970]   IO window: 00005800-000058ff
May  9 13:02:55 ubuntu kernel: [   29.503012]   IO window: 00005c00-00005cff
May  9 13:02:55 ubuntu kernel: [   29.503054]   PREFETCH window: 88000000-8bffffff
May  9 13:02:55 ubuntu kernel: [   29.503097]   MEM window: 8c000000-8fffffff
May  9 13:02:55 ubuntu kernel: [   29.503139] PCI: Bridge: 0000:00:1e.0
May  9 13:02:55 ubuntu kernel: [   29.503179]   IO window: 5000-5fff
May  9 13:02:55 ubuntu kernel: [   29.503220]   MEM window: b0200000-b02fffff
May  9 13:02:55 ubuntu kernel: [   29.503262]   PREFETCH window: disabled.
May  9 13:02:55 ubuntu kernel: [   29.503318] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
May  9 13:02:55 ubuntu kernel: [   29.503399] PCI: Setting latency timer of device 0000:00:01.0 to 64
May  9 13:02:55 ubuntu kernel: [   29.503450] PCI: Setting latency timer of device 0000:00:1e.0 to 64
May  9 13:02:55 ubuntu kernel: [   29.503544] PCI: Enabling device 0000:0a:00.0 (0000 -> 0003)
May  9 13:02:55 ubuntu kernel: [   29.503588] ACPI: PCI Interrupt 0000:0a:00.0[A] -> GSI 18 (level, low) -> IRQ 17
May  9 13:02:55 ubuntu kernel: [   29.503680] NET: Registered protocol family 2
May  9 13:02:55 ubuntu kernel: [   29.539889] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  9 13:02:55 ubuntu kernel: [   29.540198] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  9 13:02:55 ubuntu kernel: [   29.540754] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  9 13:02:55 ubuntu kernel: [   29.541083] TCP: Hash tables configured (established 131072 bind 65536)
May  9 13:02:55 ubuntu kernel: [   29.541126] TCP reno registered
May  9 13:02:55 ubuntu kernel: [   29.551977] checking if image is initramfs... it is
May  9 13:02:55 ubuntu kernel: [   29.999771] Switched to high resolution mode on CPU 1
May  9 13:02:55 ubuntu kernel: [   30.003564] Switched to high resolution mode on CPU 0
May  9 13:02:55 ubuntu kernel: [   30.088107] Freeing initrd memory: 7665k freed
May  9 13:02:55 ubuntu kernel: [   30.088288] Simple Boot Flag at 0x36 set to 0x1
May  9 13:02:55 ubuntu kernel: [   30.089025] audit: initializing netlink socket (disabled)
May  9 13:02:55 ubuntu kernel: [   30.089080] audit(1210338076.216:1): initialized
May  9 13:02:55 ubuntu kernel: [   30.089344] highmem bounce pool size: 64 pages
May  9 13:02:55 ubuntu kernel: [   30.091491] VFS: Disk quotas dquot_6.5.1
May  9 13:02:55 ubuntu kernel: [   30.091623] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  9 13:02:55 ubuntu kernel: [   30.091803] io scheduler noop registered
May  9 13:02:55 ubuntu kernel: [   30.091844] io scheduler anticipatory registered
May  9 13:02:55 ubuntu kernel: [   30.091884] io scheduler deadline registered
May  9 13:02:55 ubuntu kernel: [   30.091932] io scheduler cfq registered (default)
May  9 13:02:55 ubuntu kernel: [   30.092157] Boot video device is 0000:01:00.0
May  9 13:02:55 ubuntu kernel: [   30.092309] PCI: Setting latency timer of device 0000:00:01.0 to 64
May  9 13:02:55 ubuntu kernel: [   30.092387] assign_interrupt_mode Found MSI capability
May  9 13:02:55 ubuntu kernel: [   30.092457] Allocate Port Service[0000:00:01.0:pcie00]
May  9 13:02:55 ubuntu kernel: [   30.092781] isapnp: Scanning for PnP cards...
May  9 13:02:55 ubuntu kernel: [   30.444560] isapnp: No Plug & Play device found
May  9 13:02:55 ubuntu kernel: [   30.477141] Real Time Clock Driver v1.12ac
May  9 13:02:55 ubuntu kernel: [   30.477293] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May  9 13:02:55 ubuntu kernel: [   30.477461] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  9 13:02:55 ubuntu kernel: [   30.477605] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 8250
May  9 13:02:55 ubuntu kernel: [   30.478363] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  9 13:02:55 ubuntu kernel: [   30.479270] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May  9 13:02:55 ubuntu kernel: [   30.479393] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May  9 13:02:55 ubuntu kernel: [   30.479568] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
May  9 13:02:55 ubuntu kernel: [   30.481815] i8042.c: Detected active multiplexing controller, rev 1.1.
May  9 13:02:55 ubuntu kernel: [   30.483222] serio: i8042 KBD port at 0x60,0x64 irq 1
May  9 13:02:55 ubuntu kernel: [   30.483266] serio: i8042 AUX0 port at 0x60,0x64 irq 12
May  9 13:02:55 ubuntu kernel: [   30.483313] serio: i8042 AUX1 port at 0x60,0x64 irq 12
May  9 13:02:55 ubuntu kernel: [   30.483366] serio: i8042 AUX2 port at 0x60,0x64 irq 12
May  9 13:02:55 ubuntu kernel: [   30.483413] serio: i8042 AUX3 port at 0x60,0x64 irq 12
May  9 13:02:55 ubuntu kernel: [   30.499568] mice: PS/2 mouse device common for all mice
May  9 13:02:55 ubuntu kernel: [   30.499753] EISA: Probing bus 0 at eisa.0
May  9 13:02:55 ubuntu kernel: [   30.499797] Cannot allocate resource for EISA slot 1
May  9 13:02:55 ubuntu kernel: [   30.499840] Cannot allocate resource for EISA slot 3
May  9 13:02:55 ubuntu kernel: [   30.499881] Cannot allocate resource for EISA slot 4
May  9 13:02:55 ubuntu kernel: [   30.499920] Cannot allocate resource for EISA slot 5
May  9 13:02:55 ubuntu kernel: [   30.499969] EISA: Detected 0 cards.
May  9 13:02:55 ubuntu kernel: [   30.500009] cpuidle: using governor ladder
May  9 13:02:55 ubuntu kernel: [   30.500048] cpuidle: using governor menu
May  9 13:02:55 ubuntu kernel: [   30.500159] NET: Registered protocol family 1
May  9 13:02:55 ubuntu kernel: [   30.500225] Using IPI No-Shortcut mode
May  9 13:02:55 ubuntu kernel: [   30.500290] registered taskstats version 1
May  9 13:02:55 ubuntu kernel: [   30.500430]   Magic number: 8:9:28
May  9 13:02:55 ubuntu kernel: [   30.500475]   hash matches device ttydb
May  9 13:02:55 ubuntu kernel: [   30.500601] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  9 13:02:55 ubuntu kernel: [   30.500641] EDD information not available.
May  9 13:02:55 ubuntu kernel: [   30.500862] Freeing unused kernel memory: 364k freed
May  9 13:02:55 ubuntu kernel: [   30.521302] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May  9 13:02:55 ubuntu kernel: [   30.724172] fuse init (API version 7.9)
May  9 13:02:55 ubuntu kernel: [   30.749344] ACPI: Processor [CPU0] (supports 8 throttling states)
May  9 13:02:55 ubuntu kernel: [   30.749481] ACPI: Processor [CPU1] (supports 8 throttling states)
May  9 13:02:55 ubuntu kernel: [   30.753512] ACPI: Thermal Zone [THM0] (65 C)
May  9 13:02:55 ubuntu kernel: [   30.927212] usbcore: registered new interface driver usbfs
May  9 13:02:55 ubuntu kernel: [   30.927290] usbcore: registered new interface driver hub
May  9 13:02:55 ubuntu kernel: [   30.936311] usbcore: registered new device driver usb
May  9 13:02:55 ubuntu kernel: [   30.938682] USB Universal Host Controller Interface driver v3.0
May  9 13:02:55 ubuntu kernel: [   30.938798] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
May  9 13:02:55 ubuntu kernel: [   30.938907] PCI: Setting latency timer of device 0000:00:1d.0 to 64
May  9 13:02:55 ubuntu kernel: [   30.938962] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May  9 13:02:55 ubuntu kernel: [   30.939254] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
May  9 13:02:55 ubuntu kernel: [   30.939346] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00001800
May  9 13:02:55 ubuntu kernel: [   30.939596] usb usb1: configuration #1 chosen from 1 choice
May  9 13:02:55 ubuntu kernel: [   30.939676] hub 1-0:1.0: USB hub found
May  9 13:02:55 ubuntu kernel: [   30.939731] hub 1-0:1.0: 2 ports detected
May  9 13:02:55 ubuntu kernel: [   31.043164] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
May  9 13:02:55 ubuntu kernel: [   31.043261] PCI: Setting latency timer of device 0000:00:1d.1 to 64
May  9 13:02:55 ubuntu kernel: [   31.043308] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May  9 13:02:55 ubuntu kernel: [   31.043383] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
May  9 13:02:55 ubuntu kernel: [   31.043465] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003000
May  9 13:02:55 ubuntu kernel: [   31.043657] usb usb2: configuration #1 chosen from 1 choice
May  9 13:02:55 ubuntu kernel: [   31.043735] hub 2-0:1.0: USB hub found
May  9 13:02:55 ubuntu kernel: [   31.043784] hub 2-0:1.0: 2 ports detected
May  9 13:02:55 ubuntu kernel: [   31.147115] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17
May  9 13:02:55 ubuntu kernel: [   31.147213] PCI: Setting latency timer of device 0000:00:1d.2 to 64
May  9 13:02:55 ubuntu kernel: [   31.147259] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May  9 13:02:55 ubuntu kernel: [   31.147335] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
May  9 13:02:55 ubuntu kernel: [   31.147415] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00003020
May  9 13:02:55 ubuntu kernel: [   31.147606] usb usb3: configuration #1 chosen from 1 choice
May  9 13:02:55 ubuntu kernel: [   31.147682] hub 3-0:1.0: USB hub found
May  9 13:02:55 ubuntu kernel: [   31.147729] hub 3-0:1.0: 2 ports detected
May  9 13:02:55 ubuntu kernel: [   31.251070] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 17 (level, low) -> IRQ 20
May  9 13:02:55 ubuntu kernel: [   31.251167] PCI: Setting latency timer of device 0000:00:1d.3 to 64
May  9 13:02:55 ubuntu kernel: [   31.251214] uhci_hcd 0000:00:1d.3: UHCI Host Controller
May  9 13:02:55 ubuntu kernel: [   31.251287] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
May  9 13:02:55 ubuntu kernel: [   31.251367] uhci_hcd 0000:00:1d.3: irq 20, io base 0x00003040
May  9 13:02:55 ubuntu kernel: [   31.251577] usb usb4: configuration #1 chosen from 1 choice
May  9 13:02:55 ubuntu kernel: [   31.251652] hub 4-0:1.0: USB hub found
May  9 13:02:55 ubuntu kernel: [   31.251698] hub 4-0:1.0: 2 ports detected
May  9 13:02:55 ubuntu kernel: [   31.304113] SCSI subsystem initialized
May  9 13:02:55 ubuntu kernel: [   31.355085] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
May  9 13:02:55 ubuntu kernel: [   31.355195] PCI: Setting latency timer of device 0000:00:1d.7 to 64
May  9 13:02:55 ubuntu kernel: [   31.355252] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May  9 13:02:55 ubuntu kernel: [   31.355336] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
May  9 13:02:55 ubuntu kernel: [   31.359311] ehci_hcd 0000:00:1d.7: debug port 1
May  9 13:02:55 ubuntu kernel: [   31.359360] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
May  9 13:02:55 ubuntu kernel: [   31.359417] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xb0004000
May  9 13:02:55 ubuntu kernel: [   31.386861] usb 2-1: new low speed USB device using uhci_hcd and address 2
May  9 13:02:55 ubuntu kernel: [   31.398870] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  9 13:02:55 ubuntu kernel: [   31.399077] usb usb5: configuration #1 chosen from 1 choice
May  9 13:02:55 ubuntu kernel: [   31.399153] hub 5-0:1.0: USB hub found
May  9 13:02:55 ubuntu kernel: [   31.399200] hub 5-0:1.0: 8 ports detected
May  9 13:02:55 ubuntu kernel: [   31.423561] libata version 3.00 loaded.
May  9 13:02:55 ubuntu kernel: [   31.503052] r8169 Gigabit Ethernet driver 2.2LK loaded
May  9 13:02:55 ubuntu kernel: [   31.503128] ACPI: PCI Interrupt 0000:0a:03.0[A] -> GSI 21 (level, low) -> IRQ 21
May  9 13:02:55 ubuntu kernel: [   31.503226] PCI: Setting latency timer of device 0000:0a:03.0 to 64
May  9 13:02:55 ubuntu kernel: [   31.503603] eth0: RTL8169sb/8110sb at 0xf8866800, 00:90:f5:3f:9a:19, XID 10000000 IRQ 21
May  9 13:02:55 ubuntu kernel: [   31.504288] sata_promise 0000:0a:02.0: version 2.11
May  9 13:02:55 ubuntu kernel: [   31.504346] ACPI: PCI Interrupt 0000:0a:02.0[A] -> GSI 19 (level, low) -> IRQ 19
May  9 13:02:55 ubuntu kernel: [   31.517946] FDC 0 is a National Semiconductor PC87306
May  9 13:02:55 ubuntu kernel: [   31.532909] scsi0 : sata_promise
May  9 13:02:55 ubuntu kernel: [   31.534273] scsi1 : sata_promise
May  9 13:02:55 ubuntu kernel: [   31.535379] scsi2 : sata_promise
May  9 13:02:55 ubuntu kernel: [   31.535478] ata1: SATA max UDMA/133 mmio m4096@0xb0205000 port 0xb0205200 irq 19
May  9 13:02:55 ubuntu kernel: [   31.535532] ata2: SATA max UDMA/133 mmio m4096@0xb0205000 port 0xb0205280 irq 19
May  9 13:02:55 ubuntu kernel: [   31.535584] ata3: PATA max UDMA/133 mmio m4096@0xb0205000 port 0xb0205300 irq 19
May  9 13:02:55 ubuntu kernel: [   31.846620] ata1: SATA link down (SStatus 0 SControl 300)
May  9 13:02:55 ubuntu kernel: [   32.006542] usb 5-4: new high speed USB device using ehci_hcd and address 3
May  9 13:02:55 ubuntu kernel: [   32.153853] usb 5-4: configuration #1 chosen from 1 choice
May  9 13:02:55 ubuntu kernel: [   32.158455] ata2: SATA link down (SStatus 0 SControl 0)
May  9 13:02:55 ubuntu kernel: [   32.330831] ata3.00: ATA-7: SAMSUNG MP0603H, UD100-14, max UDMA/100
May  9 13:02:55 ubuntu kernel: [   32.330878] ata3.00: 117304992 sectors, multi 0: LBA48 
May  9 13:02:55 ubuntu kernel: [   32.331015] ata3.01: ATA-7: SAMSUNG MP0603H, UD100-14, max UDMA/100
May  9 13:02:55 ubuntu kernel: [   32.331057] ata3.01: 117304992 sectors, multi 0: LBA48 
May  9 13:02:55 ubuntu kernel: [   32.339830] ata3.00: configured for UDMA/100
May  9 13:02:55 ubuntu kernel: [   32.346827] ata3.01: configured for UDMA/100
May  9 13:02:55 ubuntu kernel: [   32.347205] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG MP0603H  UD10 PQ: 0 ANSI: 5
May  9 13:02:55 ubuntu kernel: [   32.347412] scsi 2:0:1:0: Direct-Access     ATA      SAMSUNG MP0603H  UD10 PQ: 0 ANSI: 5
May  9 13:02:55 ubuntu kernel: [   32.348408] PCI: Enabling device 0000:0a:01.0 (0000 -> 0002)
May  9 13:02:55 ubuntu kernel: [   32.348462] ACPI: PCI Interrupt 0000:0a:01.0[A] -> GSI 20 (level, low) -> IRQ 22
May  9 13:02:55 ubuntu kernel: [   32.348550] PCI: Setting latency timer of device 0000:0a:01.0 to 64
May  9 13:02:55 ubuntu kernel: [   32.398369] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[b0204000-b02047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
May  9 13:02:55 ubuntu kernel: [   32.398464] usb 2-1: new low speed USB device using uhci_hcd and address 3
May  9 13:02:55 ubuntu kernel: [   32.399675] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 17
May  9 13:02:55 ubuntu kernel: [   32.399817] PCI: Setting latency timer of device 0000:00:1f.1 to 64
May  9 13:02:55 ubuntu kernel: [   32.399888] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
May  9 13:02:55 ubuntu kernel: [   32.408204] ata_piix 0000:00:1f.1: version 2.12
May  9 13:02:55 ubuntu kernel: [   32.408270] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 17
May  9 13:02:55 ubuntu kernel: [   32.408414] PCI: Setting latency timer of device 0000:00:1f.1 to 64
May  9 13:02:55 ubuntu kernel: [   32.411330] scsi3 : ata_piix
May  9 13:02:55 ubuntu kernel: [   32.411467] scsi4 : ata_piix
May  9 13:02:55 ubuntu kernel: [   32.411565] Driver 'sd' needs updating - please use bus_type methods
May  9 13:02:55 ubuntu kernel: [   32.411714] sd 2:0:0:0: [sda] 117304992 512-byte hardware sectors (60060 MB)
May  9 13:02:55 ubuntu kernel: [   32.411778] sd 2:0:0:0: [sda] Write Protect is off
May  9 13:02:55 ubuntu kernel: [   32.411822] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  9 13:02:55 ubuntu kernel: [   32.411890] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 13:02:55 ubuntu kernel: [   32.412013] sd 2:0:0:0: [sda] 117304992 512-byte hardware sectors (60060 MB)
May  9 13:02:55 ubuntu kernel: [   32.412075] sd 2:0:0:0: [sda] Write Protect is off
May  9 13:02:55 ubuntu kernel: [   32.412119] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  9 13:02:55 ubuntu kernel: [   32.412189] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 13:02:55 ubuntu kernel: [   32.412244]  sda:<6>ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
May  9 13:02:55 ubuntu kernel: [   32.412873] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
May  9 13:02:55 ubuntu kernel: [   32.417784]  sda1
May  9 13:02:55 ubuntu kernel: [   32.417856]  sda: p1 exceeds device capacity
May  9 13:02:55 ubuntu kernel: [   32.417977] sd 2:0:0:0: [sda] Attached SCSI disk
May  9 13:02:55 ubuntu kernel: [   32.418104] sd 2:0:1:0: [sdb] 117304992 512-byte hardware sectors (60060 MB)
May  9 13:02:55 ubuntu kernel: [   32.418168] sd 2:0:1:0: [sdb] Write Protect is off
May  9 13:02:55 ubuntu kernel: [   32.418213] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
May  9 13:02:55 ubuntu kernel: [   32.418286] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 13:02:55 ubuntu kernel: [   32.418412] sd 2:0:1:0: [sdb] 117304992 512-byte hardware sectors (60060 MB)
May  9 13:02:55 ubuntu kernel: [   32.418473] sd 2:0:1:0: [sdb] Write Protect is off
May  9 13:02:55 ubuntu kernel: [   32.418516] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
May  9 13:02:55 ubuntu kernel: [   32.418588] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 13:02:55 ubuntu kernel: [   32.418639]  sdb: unknown partition table
May  9 13:02:55 ubuntu kernel: [   32.433760] sd 2:0:1:0: [sdb] Attached SCSI disk
May  9 13:02:55 ubuntu kernel: [   32.440001] sd 2:0:0:0: Attached scsi generic sg0 type 0
May  9 13:02:55 ubuntu kernel: [   32.440081] sd 2:0:1:0: Attached scsi generic sg1 type 0
May  9 13:02:55 ubuntu kernel: [   32.562370] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.562419] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.562460] Buffer I/O error on device sda1, logical block 58649248
May  9 13:02:55 ubuntu kernel: [   32.562503] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.562543] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.562584] Buffer I/O error on device sda1, logical block 58649249
May  9 13:02:55 ubuntu kernel: [   32.562627] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.562667] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.562708] Buffer I/O error on device sda1, logical block 58649248
May  9 13:02:55 ubuntu kernel: [   32.562750] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.562790] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.562831] Buffer I/O error on device sda1, logical block 58649249
May  9 13:02:55 ubuntu kernel: [   32.562881] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.562922] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.562963] Buffer I/O error on device sda1, logical block 58649278
May  9 13:02:55 ubuntu kernel: [   32.563005] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.563046] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.563086] Buffer I/O error on device sda1, logical block 58649279
May  9 13:02:55 ubuntu kernel: [   32.563129] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.563169] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.563209] Buffer I/O error on device sda1, logical block 58649278
May  9 13:02:55 ubuntu kernel: [   32.563254] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.563295] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.563336] Buffer I/O error on device sda1, logical block 58649279
May  9 13:02:55 ubuntu kernel: [   32.563427] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.563469] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.563544] Buffer I/O error on device sda1, logical block 58649282
May  9 13:02:55 ubuntu kernel: [   32.563588] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.563632] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.563706] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.563755] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.563802] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.563843] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.563888] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.563928] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.563974] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.564015] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.564060] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.564101] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.564148] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.564189] sda: rw=0, want=234597131, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.564230] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.564270] sda: rw=0, want=234597135, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.564318] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.564359] sda: rw=0, want=234597187, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.564400] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.564440] sda: rw=0, want=234597191, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.564487] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.564528] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.564573] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   32.564614] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   32.584867] usb 2-1: configuration #1 chosen from 1 choice
May  9 13:02:55 ubuntu kernel: [   32.587922] usbcore: registered new interface driver libusual
May  9 13:02:55 ubuntu kernel: [   32.594580] Initializing USB Mass Storage driver...
May  9 13:02:55 ubuntu kernel: [   32.594708] scsi5 : SCSI emulation for USB Mass Storage devices
May  9 13:02:55 ubuntu kernel: [   32.594838] usbcore: registered new interface driver usb-storage
May  9 13:02:55 ubuntu kernel: [   32.594884] USB Mass Storage support registered.
May  9 13:02:55 ubuntu kernel: [   32.595053] usb-storage: device found at 3
May  9 13:02:55 ubuntu kernel: [   32.595096] usb-storage: waiting for device to settle before scanning
May  9 13:02:55 ubuntu kernel: [   32.606634] usbcore: registered new interface driver hiddev
May  9 13:02:55 ubuntu kernel: [   32.620940] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input2
May  9 13:02:55 ubuntu kernel: [   32.646220] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.1-1
May  9 13:02:55 ubuntu kernel: [   32.646418] usbcore: registered new interface driver usbhid
May  9 13:02:55 ubuntu kernel: [   32.646466] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
May  9 13:02:55 ubuntu kernel: [   32.746627] ata4.00: ATAPI: UJDA760 DVD/CDRW, 1.00, max UDMA/33
May  9 13:02:55 ubuntu kernel: [   32.918417] ata4.00: configured for UDMA/33
May  9 13:02:55 ubuntu kernel: [   32.918500] ata5: port disabled. ignoring.
May  9 13:02:55 ubuntu kernel: [   32.920059] scsi 3:0:0:0: CD-ROM            MATSHITA UJDA760 DVD/CDRW 1.00 PQ: 0 ANSI: 5
May  9 13:02:55 ubuntu kernel: [   32.920200] scsi 3:0:0:0: Attached scsi generic sg2 type 5
May  9 13:02:55 ubuntu kernel: [   32.927488] Driver 'sr' needs updating - please use bus_type methods
May  9 13:02:55 ubuntu kernel: [   33.129631] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
May  9 13:02:55 ubuntu kernel: [   33.129679] Uniform CD-ROM driver Revision: 3.20
May  9 13:02:55 ubuntu kernel: [   33.129777] sr 3:0:0:0: Attached scsi CD-ROM sr0
May  9 13:02:55 ubuntu kernel: [   33.669778] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090f50000402419]
May  9 13:02:55 ubuntu kernel: [   37.323771] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
May  9 13:02:55 ubuntu kernel: [   37.324629] SGI XFS Quota Management subsystem
May  9 13:02:55 ubuntu kernel: [   37.333097] JFS: nTxBlock = 8192, nTxLock = 65536
May  9 13:02:55 ubuntu kernel: [   37.381075] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.381123] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.381164] printk: 12 messages suppressed.
May  9 13:02:55 ubuntu kernel: [   37.381204] Buffer I/O error on device sda1, logical block 58649248
May  9 13:02:55 ubuntu kernel: [   37.381246] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.381286] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.381328] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.381369] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.381410] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.381450] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.381499] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.381540] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.381581] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.381622] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.381664] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.381704] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.381744] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.381784] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.381871] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.381912] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.381989] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.382030] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.382080] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.382147] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.382195] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.383061] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.383107] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.383148] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.383193] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.383234] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.383280] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.383320] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.383368] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.383409] sda: rw=0, want=234597131, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.383449] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.383489] sda: rw=0, want=234597135, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.383537] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.383578] sda: rw=0, want=234597187, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.383619] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.383667] sda: rw=0, want=234597191, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.383714] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.383755] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.383801] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   37.383842] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   37.587817] usb-storage: device scan complete
May  9 13:02:55 ubuntu kernel: [   37.591941] scsi 5:0:0:0: Direct-Access     GENERIC  USB Storage-SMC  I16A PQ: 0 ANSI: 0 CCS
May  9 13:02:55 ubuntu kernel: [   37.596056] scsi 5:0:0:1: Direct-Access     GENERIC  USB Storage-CFC  I16A PQ: 0 ANSI: 0 CCS
May  9 13:02:55 ubuntu kernel: [   37.600181] scsi 5:0:0:2: Direct-Access     GENERIC  USB Storage-SDC  I16A PQ: 0 ANSI: 0 CCS
May  9 13:02:55 ubuntu kernel: [   37.604304] scsi 5:0:0:3: Direct-Access     GENERIC  USB Storage-MSC  I16A PQ: 0 ANSI: 0 CCS
May  9 13:02:55 ubuntu kernel: [   37.606504] sd 5:0:0:0: [sdc] Attached SCSI removable disk
May  9 13:02:55 ubuntu kernel: [   37.606613] sd 5:0:0:0: Attached scsi generic sg3 type 0
May  9 13:02:55 ubuntu kernel: [   37.607856] sd 5:0:0:1: [sdd] Attached SCSI removable disk
May  9 13:02:55 ubuntu kernel: [   37.607950] sd 5:0:0:1: Attached scsi generic sg4 type 0
May  9 13:02:55 ubuntu kernel: [   37.609097] sd 5:0:0:2: [sde] Attached SCSI removable disk
May  9 13:02:55 ubuntu kernel: [   37.609193] sd 5:0:0:2: Attached scsi generic sg5 type 0
May  9 13:02:55 ubuntu kernel: [   37.610371] sd 5:0:0:3: [sdf] Attached SCSI removable disk
May  9 13:02:55 ubuntu kernel: [   37.610488] sd 5:0:0:3: Attached scsi generic sg6 type 0
May  9 13:02:55 ubuntu kernel: [   39.145897] ISO 9660 Extensions: Microsoft Joliet Level 3
May  9 13:02:55 ubuntu kernel: [   39.180009] ISO 9660 Extensions: RRIP_1991A
May  9 13:02:55 ubuntu kernel: [   42.624955] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.625003] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.625044] printk: 20 messages suppressed.
May  9 13:02:55 ubuntu kernel: [   42.625084] Buffer I/O error on device sda1, logical block 58649248
May  9 13:02:55 ubuntu kernel: [   42.625126] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.625166] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.625209] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.625249] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.625290] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.625330] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.625380] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.625421] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.625462] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.625502] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.625544] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.625584] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.625624] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.625664] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.625749] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.625790] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.625870] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.625913] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.625965] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.626031] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.626078] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.626119] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.626166] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.626206] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.626252] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.626293] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.626339] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.626379] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.626427] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.626468] sda: rw=0, want=234597131, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.626509] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.626549] sda: rw=0, want=234597135, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.626597] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.626638] sda: rw=0, want=234597187, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.626678] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.626718] sda: rw=0, want=234597191, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.626765] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.626806] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   42.626852] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   42.626893] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   43.332669] ISO 9660 Extensions: Microsoft Joliet Level 3
May  9 13:02:55 ubuntu kernel: [   43.366861] ISO 9660 Extensions: RRIP_1991A
May  9 13:02:55 ubuntu kernel: [   46.415638] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.415687] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.415728] printk: 20 messages suppressed.
May  9 13:02:55 ubuntu kernel: [   46.415768] Buffer I/O error on device sda1, logical block 58649248
May  9 13:02:55 ubuntu kernel: [   46.415810] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.415852] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.415895] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.415936] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.415977] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.416017] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.416067] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.416107] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.416149] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.416189] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.416231] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.416271] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.416312] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.416352] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.416437] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.416479] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.416558] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.416599] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.416649] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.416715] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.416763] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.416805] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.416851] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.416892] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.416938] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.416978] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.417024] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.417065] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.417112] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.417153] sda: rw=0, want=234597131, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.417194] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.417234] sda: rw=0, want=234597135, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.417282] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.417323] sda: rw=0, want=234597187, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.417364] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.417404] sda: rw=0, want=234597191, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.417451] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.417492] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.417538] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.417578] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.698710] ISO 9660 Extensions: Microsoft Joliet Level 3
May  9 13:02:55 ubuntu kernel: [   46.733151] ISO 9660 Extensions: RRIP_1991A
May  9 13:02:55 ubuntu kernel: [   46.788631] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.788680] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.788721] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.788762] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.788804] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.788844] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.788885] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.788925] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.788976] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.789017] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.789059] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.789099] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.789141] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.789181] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.789222] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.789262] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.789348] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.789389] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.789466] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.789508] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.789559] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.789625] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.789673] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.789714] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.789761] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.789801] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.789847] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.789888] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.789934] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.789974] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.790022] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.790062] sda: rw=0, want=234597131, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.790103] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.790143] sda: rw=0, want=234597135, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.790191] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.790232] sda: rw=0, want=234597187, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.790273] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.790313] sda: rw=0, want=234597191, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.790360] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.790401] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   46.790447] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   46.790488] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   47.066182] ISO 9660 Extensions: Microsoft Joliet Level 3
May  9 13:02:55 ubuntu kernel: [   47.100651] ISO 9660 Extensions: RRIP_1991A
May  9 13:02:55 ubuntu kernel: [   50.149583] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.149631] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.149672] printk: 41 messages suppressed.
May  9 13:02:55 ubuntu kernel: [   50.149712] Buffer I/O error on device sda1, logical block 58649248
May  9 13:02:55 ubuntu kernel: [   50.149754] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.149795] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.150664] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.150705] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.150746] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.150786] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.150835] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.150876] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.150917] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.150958] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.151000] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.151040] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.151080] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.151120] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.151208] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.151250] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.151328] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.151369] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.151421] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.151487] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.151535] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.151576] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.151622] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.151663] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.151709] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.151749] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.151795] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.151836] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.151883] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.151924] sda: rw=0, want=234597131, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.151965] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.152005] sda: rw=0, want=234597135, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.152053] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.152093] sda: rw=0, want=234597187, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.152134] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.152174] sda: rw=0, want=234597191, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.152221] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.152262] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.152308] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   50.152348] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   50.430208] ISO 9660 Extensions: Microsoft Joliet Level 3
May  9 13:02:55 ubuntu kernel: [   50.464839] ISO 9660 Extensions: RRIP_1991A
May  9 13:02:55 ubuntu kernel: [   53.513773] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.513821] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.513862] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.513903] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.513945] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.513985] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.514026] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.514066] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.514115] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.514156] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.514198] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.514238] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.514280] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.514320] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.514361] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.514401] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.514488] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.514529] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.514608] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.514649] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.514701] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.514767] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.514815] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.514856] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.514902] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.514942] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.514988] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.515029] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.515084] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.515125] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.515174] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.515215] sda: rw=0, want=234597131, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.515256] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.515296] sda: rw=0, want=234597135, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.515344] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.515385] sda: rw=0, want=234597187, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.515426] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.515465] sda: rw=0, want=234597191, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.515512] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.515553] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.515600] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.515640] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.795339] ISO 9660 Extensions: Microsoft Joliet Level 3
May  9 13:02:55 ubuntu kernel: [   53.830085] ISO 9660 Extensions: RRIP_1991A
May  9 13:02:55 ubuntu kernel: [   53.910735] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.910783] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.910825] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.910877] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.910919] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.910960] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.911001] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.911041] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.911090] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.911131] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.911172] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.911212] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.911254] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.911294] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.911335] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.911375] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.911462] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.911503] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.911582] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.911623] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.911675] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.911740] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.911788] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.911829] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.911879] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.911927] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.911975] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.912015] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.912061] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.912102] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.912150] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.912191] sda: rw=0, want=234597131, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.912231] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.912271] sda: rw=0, want=234597135, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.912319] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.912360] sda: rw=0, want=234597187, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.912401] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.912441] sda: rw=0, want=234597191, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.912488] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.912529] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   53.912575] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   53.912615] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   54.309321] ISO 9660 Extensions: Microsoft Joliet Level 3
May  9 13:02:55 ubuntu kernel: [   54.344078] ISO 9660 Extensions: RRIP_1991A
May  9 13:02:55 ubuntu kernel: [   54.630762] Registering unionfs 1.4
May  9 13:02:55 ubuntu kernel: [   54.630813] unionfs: debugging is not enabled
May  9 13:02:55 ubuntu kernel: [   54.641187] loop: module loaded
May  9 13:02:55 ubuntu kernel: [   54.950436] squashfs: version 3.3 (2007/10/31) Phillip Lougher
May  9 13:02:55 ubuntu kernel: [   93.896192] ACPI: Battery Slot [BAT0] (battery present)
May  9 13:02:55 ubuntu kernel: [   95.816107] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.816159] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.816210] printk: 62 messages suppressed.
May  9 13:02:55 ubuntu kernel: [   95.816260] Buffer I/O error on device sda1, logical block 58649248
May  9 13:02:55 ubuntu kernel: [   95.816310] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.816356] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.816403] Buffer I/O error on device sda1, logical block 58649249
May  9 13:02:55 ubuntu kernel: [   95.816451] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.816499] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.816545] Buffer I/O error on device sda1, logical block 58649248
May  9 13:02:55 ubuntu kernel: [   95.816615] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.816670] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.816724] Buffer I/O error on device sda1, logical block 58649249
May  9 13:02:55 ubuntu kernel: [   95.816796] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.816850] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.816902] Buffer I/O error on device sda1, logical block 58649278
May  9 13:02:55 ubuntu kernel: [   95.816958] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.817009] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.817055] Buffer I/O error on device sda1, logical block 58649279
May  9 13:02:55 ubuntu kernel: [   95.817112] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.817162] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.817209] Buffer I/O error on device sda1, logical block 58649278
May  9 13:02:55 ubuntu kernel: [   95.817257] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.817310] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.817361] Buffer I/O error on device sda1, logical block 58649279
May  9 13:02:55 ubuntu kernel: [   95.817504] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.817556] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.817649] Buffer I/O error on device sda1, logical block 58649282
May  9 13:02:55 ubuntu kernel: [   95.817707] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.817758] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.817845] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.817899] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.817966] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.818019] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.818078] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.818130] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.818193] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.818245] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.818306] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.818353] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.818413] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.818464] sda: rw=0, want=234597131, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.818511] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.818556] sda: rw=0, want=234597135, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.818622] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.818673] sda: rw=0, want=234597187, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.818726] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.819734] sda: rw=0, want=234597191, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.819810] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.819858] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [   95.819912] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [   95.819962] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [  116.389768] input: PC Speaker as /devices/platform/pcspkr/input/input3
May  9 13:02:55 ubuntu kernel: [  117.068873] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.068924] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.068968] printk: 12 messages suppressed.
May  9 13:02:55 ubuntu kernel: [  117.069011] Buffer I/O error on device sda1, logical block 58649248
May  9 13:02:55 ubuntu kernel: [  117.069056] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.069100] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.069144] Buffer I/O error on device sda1, logical block 58649249
May  9 13:02:55 ubuntu kernel: [  117.069190] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.069233] sda: rw=0, want=234597059, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.069278] Buffer I/O error on device sda1, logical block 58649248
May  9 13:02:55 ubuntu kernel: [  117.069373] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.069417] sda: rw=0, want=234597063, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.069462] Buffer I/O error on device sda1, logical block 58649249
May  9 13:02:55 ubuntu kernel: [  117.069519] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.069563] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.069607] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.069650] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.069695] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.069739] sda: rw=0, want=234597179, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.069783] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.069827] sda: rw=0, want=234597183, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.069942] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.069988] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.070088] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.070132] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.070192] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.070260] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.070314] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.070358] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.070409] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.070453] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.070504] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.070548] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.070600] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.070643] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.070697] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.070741] sda: rw=0, want=234597131, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.070786] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.070830] sda: rw=0, want=234597135, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.070883] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.070926] sda: rw=0, want=234597187, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.070971] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.071014] sda: rw=0, want=234597191, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.071067] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.071111] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.071163] attempt to access beyond end of device
May  9 13:02:55 ubuntu kernel: [  117.071206] sda: rw=0, want=234597195, limit=117304992
May  9 13:02:55 ubuntu kernel: [  117.220184] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  9 13:02:55 ubuntu kernel: [  117.781079] parport_pc 00:09: reported by Plug and Play ACPI
May  9 13:02:55 ubuntu kernel: [  117.781249] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
May  9 13:02:55 ubuntu kernel: [  117.904972] iTCO_vendor_support: vendor-support=0
May  9 13:02:55 ubuntu kernel: [  118.988640] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  9 13:02:55 ubuntu kernel: [  119.139985] Linux agpgart interface v0.102
May  9 13:02:55 ubuntu kernel: [  119.222649] input: Lid Switch as /devices/virtual/input/input4
May  9 13:02:55 ubuntu kernel: [  119.226157] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
May  9 13:02:55 ubuntu kernel: [  119.226317] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x1060)
May  9 13:02:55 ubuntu kernel: [  119.226430] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
May  9 13:02:55 ubuntu kernel: [  119.253385] ACPI: Lid Switch [LID]
May  9 13:02:55 ubuntu kernel: [  119.253506] input: Sleep Button (CM) as /devices/virtual/input/input5
May  9 13:02:55 ubuntu kernel: [  119.313199] ACPI: Sleep Button (CM) [SLPB]
May  9 13:02:55 ubuntu kernel: [  119.313301] input: Power Button (CM) as /devices/virtual/input/input6
May  9 13:02:55 ubuntu kernel: [  119.353182] ACPI: Power Button (CM) [PWRB]
May  9 13:02:55 ubuntu kernel: [  119.908873] irda_init()
May  9 13:02:55 ubuntu kernel: [  119.908945] NET: Registered protocol family 23
May  9 13:02:55 ubuntu kernel: [  120.040408] ACPI: AC Adapter [ADP0] (on-line)
May  9 13:02:55 ubuntu kernel: [  120.167795] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input7
May  9 13:02:55 ubuntu kernel: [  120.216689] ACPI: Video Device [NVD] (multi-head: yes  rom: no  post: no)
May  9 13:02:55 ubuntu kernel: [  120.325347] intel_rng: FWH not detected
May  9 13:02:55 ubuntu kernel: [  120.603561] Yenta: CardBus bridge found at 0000:0a:00.0 [1558:0900]
May  9 13:02:55 ubuntu kernel: [  120.603632] Yenta: Using CSCINT to route CSC interrupts to PCI
May  9 13:02:55 ubuntu kernel: [  120.603676] Yenta: Routing CardBus interrupts to PCI
May  9 13:02:55 ubuntu kernel: [  120.603722] Yenta TI: socket 0000:0a:00.0, mfunc 0x00001002, devctl 0x64
May  9 13:02:55 ubuntu kernel: [  120.844873] Yenta: ISA IRQ mask 0x0c30, PCI irq 17
May  9 13:02:55 ubuntu kernel: [  120.844923] Socket status: 30000006
May  9 13:02:55 ubuntu kernel: [  120.844966] Yenta: Raising subordinate bus# of parent bus (#0a) from #0a to #0e
May  9 13:02:55 ubuntu kernel: [  120.845021] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
May  9 13:02:55 ubuntu kernel: [  120.845067] cs: IO port probe 0x5000-0x5fff: clean.
May  9 13:02:55 ubuntu kernel: [  120.845509] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
May  9 13:02:55 ubuntu kernel: [  120.887943] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa36eb3, caps: 0x904713/0x10008
May  9 13:02:55 ubuntu kernel: [  120.923583] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
May  9 13:02:55 ubuntu kernel: [  121.010091] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
May  9 13:02:55 ubuntu kernel: [  121.010185] printk: 17 messages suppressed.
May  9 13:02:55 ubuntu kernel: [  121.010235] nsc-ircc, chip->init
May  9 13:02:55 ubuntu kernel: [  121.010596] nsc-ircc 00:0b: disabled
May  9 13:02:55 ubuntu kernel: [  121.758621] cs: IO port probe 0x100-0x3af: clean.
May  9 13:02:55 ubuntu kernel: [  121.760068] cs: IO port probe 0x3e0-0x4ff: clean.
May  9 13:02:55 ubuntu kernel: [  121.760712] cs: IO port probe 0x820-0x8ff: clean.
May  9 13:02:55 ubuntu kernel: [  121.761213] cs: IO port probe 0xc00-0xcf7: clean.
May  9 13:02:55 ubuntu kernel: [  121.761989] cs: IO port probe 0xa00-0xaff: clean.
May  9 13:02:55 ubuntu kernel: [  121.970993] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 17 (level, low) -> IRQ 20
May  9 13:02:55 ubuntu kernel: [  121.971112] PCI: Setting latency timer of device 0000:00:1b.0 to 64
May  9 13:02:55 ubuntu kernel: [  121.997333] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
May  9 13:02:55 ubuntu kernel: [  121.997847] hda_codec: Cannot set up configuration from BIOS.  Using 3-stack mode...
May  9 13:02:55 ubuntu kernel: [  124.412017] ip_tables: (C) 2000-2006 Netfilter Core Team
May  9 13:02:55 ubuntu kernel: [  126.357816] No dock devices found.
May  9 13:02:56 ubuntu NetworkManager: <info>  starting... 
May  9 13:02:57 ubuntu avahi-daemon[10132]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
May  9 13:02:57 ubuntu avahi-daemon[10132]: Successfully dropped root privileges.
May  9 13:02:57 ubuntu avahi-daemon[10132]: avahi-daemon 0.6.22 starting up.
May  9 13:02:57 ubuntu avahi-daemon[10132]: Successfully called chroot().
May  9 13:02:57 ubuntu avahi-daemon[10132]: Successfully dropped remaining capabilities.
May  9 13:02:57 ubuntu avahi-daemon[10133]: chroot.c: open() failed: No such file or directory
May  9 13:02:57 ubuntu avahi-daemon[10132]: Failed to open /etc/resolv.conf: Invalid argument
May  9 13:02:57 ubuntu avahi-daemon[10132]: No service file found in /etc/avahi/services.
May  9 13:02:57 ubuntu avahi-daemon[10132]: Network interface enumeration completed.
May  9 13:02:57 ubuntu avahi-daemon[10132]: Registering HINFO record with values 'I686'/'LINUX'.
May  9 13:02:57 ubuntu avahi-daemon[10132]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1219301322.
May  9 13:02:57 ubuntu kernel: [  130.815003] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May  9 13:02:57 ubuntu kernel: [  130.815010] apm: disabled - APM is not SMP safe.
May  9 13:02:57 ubuntu kernel: [  130.971721] lp0: using parport0 (interrupt-driven).
May  9 13:02:57 ubuntu kernel: [  131.036427] ppdev: user-space parallel port driver
May  9 13:03:01 ubuntu dhcdbd: Started up.
May  9 13:03:03 ubuntu kernel: [  136.677485] ttyS1: LSR safety check engaged!
May  9 13:03:04 ubuntu kernel: [  137.223310] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223320] sda: rw=0, want=234597059, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223325] printk: 6 messages suppressed.
May  9 13:03:04 ubuntu kernel: [  137.223328] Buffer I/O error on device sda1, logical block 58649248
May  9 13:03:04 ubuntu kernel: [  137.223385] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223390] sda: rw=0, want=234597063, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223395] Buffer I/O error on device sda1, logical block 58649249
May  9 13:03:04 ubuntu kernel: [  137.223443] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223448] sda: rw=0, want=234597059, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223452] Buffer I/O error on device sda1, logical block 58649248
May  9 13:03:04 ubuntu kernel: [  137.223499] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223503] sda: rw=0, want=234597063, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223518] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223523] sda: rw=0, want=234597179, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223528] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223532] sda: rw=0, want=234597183, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223537] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223541] sda: rw=0, want=234597179, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223546] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223550] sda: rw=0, want=234597183, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223612] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223617] sda: rw=0, want=234597195, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223623] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223628] sda: rw=0, want=234597195, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223641] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223645] sda: rw=0, want=234597195, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223657] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223660] sda: rw=0, want=234597195, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223671] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223675] sda: rw=0, want=234597195, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223727] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223732] sda: rw=0, want=234597195, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223744] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223748] sda: rw=0, want=234597195, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223762] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223766] sda: rw=0, want=234597131, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223771] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223775] sda: rw=0, want=234597135, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223787] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223792] sda: rw=0, want=234597187, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223797] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223801] sda: rw=0, want=234597191, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223812] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223816] sda: rw=0, want=234597195, limit=117304992
May  9 13:03:04 ubuntu kernel: [  137.223827] attempt to access beyond end of device
May  9 13:03:04 ubuntu kernel: [  137.223831] sda: rw=0, want=234597195, limit=117304992
May  9 13:03:05 ubuntu kernel: [  138.264307] r8169: eth0: link up
May  9 13:03:05 ubuntu NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
May  9 13:03:05 ubuntu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May  9 13:03:05 ubuntu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May  9 13:03:05 ubuntu NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
May  9 13:03:05 ubuntu NetworkManager: <info>  Deactivating device eth0. 
May  9 13:03:05 ubuntu NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
May  9 13:03:05 ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
May  9 13:03:05 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
May  9 13:03:05 ubuntu NetworkManager: <info>  Will activate connection 'eth0'. 
May  9 13:03:05 ubuntu NetworkManager: <info>  Device eth0 activation scheduled... 
May  9 13:03:05 ubuntu NetworkManager: <info>  Activation (eth0) started... 
May  9 13:03:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May  9 13:03:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May  9 13:03:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May  9 13:03:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May  9 13:03:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May  9 13:03:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May  9 13:03:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May  9 13:03:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May  9 13:03:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May  9 13:03:05 ubuntu hcid[10432]: Bluetooth HCI daemon
May  9 13:03:05 ubuntu kernel: [  138.720741] Bluetooth: Core ver 2.11
May  9 13:03:05 ubuntu kernel: [  138.721543] NET: Registered protocol family 31
May  9 13:03:05 ubuntu kernel: [  138.721548] Bluetooth: HCI device and connection manager initialized
May  9 13:03:05 ubuntu kernel: [  138.721553] Bluetooth: HCI socket layer initialized
May  9 13:03:05 ubuntu hcid[10432]: Starting SDP server
May  9 13:03:05 ubuntu kernel: [  138.769461] Bluetooth: L2CAP ver 2.9
May  9 13:03:05 ubuntu kernel: [  138.769468] Bluetooth: L2CAP socket layer initialized
May  9 13:03:05 ubuntu hcid[10432]: Created local server at unix:abstract=/var/run/dbus-QH6jbV7Uqu,guid=934ec738dfe3b93047a6548348244b89
May  9 13:03:05 ubuntu NetworkManager: <debug> [1210338185.606983] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May  9 13:03:05 ubuntu audio[10460]: Bluetooth Audio daemon
May  9 13:03:05 ubuntu audio[10460]: Unix socket created: 5
May  9 13:03:05 ubuntu audio[10460]: audio.conf: Key file does not have key 'Enable'
May  9 13:03:05 ubuntu audio[10460]: audio.conf: Key file does not have key 'Disable'
May  9 13:03:05 ubuntu input[10464]: Bluetooth Input daemon
May  9 13:03:05 ubuntu input[10464]: Registered input manager path:/org/bluez/input
May  9 13:03:05 ubuntu kernel: [  139.030099] Bluetooth: RFCOMM socket layer initialized
May  9 13:03:05 ubuntu audio[10460]: add_service_record: got record id 0x10000
May  9 13:03:05 ubuntu audio[10460]: audio.conf: Key file does not have key 'Disable'
May  9 13:03:05 ubuntu audio[10460]: audio.conf: Key file does not have group 'A2DP'
May  9 13:03:05 ubuntu last message repeated 3 times
May  9 13:03:05 ubuntu audio[10460]: SEP 0x806d248 registered: type:0 codec:0 seid:1
May  9 13:03:05 ubuntu kernel: [  139.030115] Bluetooth: RFCOMM TTY layer initialized
May  9 13:03:05 ubuntu audio[10460]: add_service_record: got record id 0x10001
May  9 13:03:05 ubuntu kernel: [  139.030118] Bluetooth: RFCOMM ver 1.8
May  9 13:03:05 ubuntu audio[10460]: add_service_record: got record id 0x10002
May  9 13:03:05 ubuntu audio[10460]: add_service_record: got record id 0x10003
May  9 13:03:05 ubuntu audio[10460]: Registered manager path:/org/bluez/audio
May  9 13:03:06 ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May  9 13:03:06 ubuntu NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
May  9 13:03:06 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May  9 13:03:08 ubuntu NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
May  9 13:03:08 ubuntu kernel: [  141.403518] NET: Registered protocol family 17
May  9 13:03:08 ubuntu kernel: [  141.463358] NET: Registered protocol family 10
May  9 13:03:08 ubuntu kernel: [  141.464682] lo: Disabled Privacy Extensions
May  9 13:03:10 ubuntu avahi-daemon[10132]: Registering new address record for fe80::290:f5ff:fe3f:9a19 on eth0.*.
May  9 13:03:12 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May  9 13:03:12 ubuntu dhclient: DHCPOFFER of 128.2.146.41 from 128.2.146.3
May  9 13:03:12 ubuntu dhclient: DHCPREQUEST of 128.2.146.41 on eth0 to 255.255.255.255 port 67
May  9 13:03:12 ubuntu dhclient: DHCPACK of 128.2.146.41 from 128.2.146.3
May  9 13:03:12 ubuntu kernel: [  145.427164] [drm] Initialized drm 1.1.0 20060810
May  9 13:03:12 ubuntu avahi-daemon[10132]: Joining mDNS multicast group on interface eth0.IPv4 with address 128.2.146.41.
May  9 13:03:12 ubuntu avahi-daemon[10132]: New relevant interface eth0.IPv4 for mDNS.
May  9 13:03:12 ubuntu avahi-daemon[10132]: Registering new address record for 128.2.146.41 on eth0.IPv4.
May  9 13:03:12 ubuntu avahi-daemon[10132]: Withdrawing address record for 128.2.146.41 on eth0.
May  9 13:03:12 ubuntu avahi-daemon[10132]: Leaving mDNS multicast group on interface eth0.IPv4 with address 128.2.146.41.
May  9 13:03:12 ubuntu avahi-daemon[10132]: Interface eth0.IPv4 no longer relevant for mDNS.
May  9 13:03:12 ubuntu avahi-daemon[10132]: Joining mDNS multicast group on interface eth0.IPv4 with address 128.2.146.41.
May  9 13:03:12 ubuntu avahi-daemon[10132]: New relevant interface eth0.IPv4 for mDNS.
May  9 13:03:12 ubuntu avahi-daemon[10132]: Registering new address record for 128.2.146.41 on eth0.IPv4.
May  9 13:03:12 ubuntu kernel: [  145.756771] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
May  9 13:03:12 ubuntu kernel: [  145.756783] PCI: Setting latency timer of device 0000:01:00.0 to 64
May  9 13:03:12 ubuntu kernel: [  145.756880] [drm] Initialized radeon 1.28.0 20060524 on minor 0
May  9 13:03:12 ubuntu NetworkManager: <debug> [1210338192.571912] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_5d4a_drm_r300_card0'). 
May  9 13:03:12 ubuntu dhclient: bound to 128.2.146.41 -- renewal in 37787 seconds.
May  9 13:03:12 ubuntu NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
May  9 13:03:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
May  9 13:03:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
May  9 13:03:13 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May  9 13:03:13 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
May  9 13:03:13 ubuntu NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
May  9 13:03:13 ubuntu NetworkManager: <info>    address 128.2.146.41 
May  9 13:03:13 ubuntu NetworkManager: <info>    netmask 255.255.255.0 
May  9 13:03:13 ubuntu NetworkManager: <info>    broadcast 128.2.146.255 
May  9 13:03:13 ubuntu NetworkManager: <info>    gateway 128.2.146.1 
May  9 13:03:13 ubuntu NetworkManager: <info>    nameserver 128.2.1.10 
May  9 13:03:13 ubuntu NetworkManager: <info>    nameserver 128.2.1.11 
May  9 13:03:13 ubuntu NetworkManager: <info>    hostname 'jac.res.cmu.edu' 
May  9 13:03:13 ubuntu NetworkManager: <info>    domain name 'res.cmu.edu' 
May  9 13:03:13 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
May  9 13:03:13 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  9 13:03:13 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May  9 13:03:13 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May  9 13:03:13 ubuntu avahi-daemon[10132]: Withdrawing address record for 128.2.146.41 on eth0.
May  9 13:03:13 ubuntu avahi-daemon[10132]: Leaving mDNS multicast group on interface eth0.IPv4 with address 128.2.146.41.
May  9 13:03:13 ubuntu avahi-daemon[10132]: Interface eth0.IPv4 no longer relevant for mDNS.
May  9 13:03:13 ubuntu avahi-daemon[10132]: Withdrawing address record for fe80::290:f5ff:fe3f:9a19 on eth0.
May  9 13:03:13 ubuntu avahi-daemon[10132]: Joining mDNS multicast group on interface eth0.IPv4 with address 128.2.146.41.
May  9 13:03:13 ubuntu avahi-daemon[10132]: New relevant interface eth0.IPv4 for mDNS.
May  9 13:03:13 ubuntu avahi-daemon[10132]: Registering new address record for 128.2.146.41 on eth0.IPv4.
May  9 13:03:15 ubuntu NetworkManager: <info>  Clearing nscd hosts cache. 
May  9 13:03:15 ubuntu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May  9 13:03:15 ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated. 
May  9 13:03:15 ubuntu NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
May  9 13:03:15 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May  9 13:03:15 ubuntu kernel: [  148.573896] [drm] Setting GART location based on new memory map
May  9 13:03:15 ubuntu kernel: [  148.574407] [drm] Loading R300 Microcode
May  9 13:03:15 ubuntu kernel: [  148.574455] [drm] writeback test succeeded in 1 usecs
May  9 13:03:17 ubuntu avahi-daemon[10132]: Registering new address record for fe80::290:f5ff:fe3f:9a19 on eth0.*.
May  9 13:03:17 ubuntu ntpdate[10599]: step time server 91.189.94.4 offset 14398.901963 sec
May  9 17:03:22 ubuntu ubiquity[10616]: Ubiquity 1.8.7
May  9 17:03:24 ubuntu kernel: [  159.191910] eth0: no IPv6 routers present
May  9 17:03:36 ubuntu ubiquity[10616]: log-output -t ubiquity laptop-detect
May  9 17:03:37 ubuntu ubiquity[10616]: log-output -t ubiquity fontconfig-voodoo --auto --force --quiet
May  9 17:03:46 ubuntu ubiquity[10616]: switched to page stepLanguage
May  9 17:03:46 ubuntu localechooser: info: Locale has been preseeded to en_US.UTF-8
May  9 17:03:47 ubuntu localechooser: info: Set languagechooser/language-name = 'English'
May  9 17:03:47 ubuntu localechooser: info: Set countrychooser/shortlist-en = 'US'
May  9 17:03:47 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May  9 17:03:47 ubuntu localechooser: info: LANGNAME=English
May  9 17:03:47 ubuntu localechooser: info: line=English;0;en;US;en_US.UTF-8;UTF-8;;kbd=lat0-sun16(utf8)
May  9 17:03:47 ubuntu localechooser: info: Set debian-installer/language = 'en'
May  9 17:03:47 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May  9 17:03:47 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
May  9 17:03:47 ubuntu localechooser: info: Set debian-installer/country = 'US'
May  9 17:03:47 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'kbd=lat0-sun16(utf8)'
May  9 17:03:47 ubuntu localechooser: info: Set debconf/language = 'en'
May  9 17:03:47 ubuntu localechooser: info: Set debian-installer/country = 'US'
May  9 17:03:47 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May  9 17:03:47 ubuntu ubiquity[10616]: debconffilter_done: Language (current: Language)
May  9 17:03:47 ubuntu ubiquity[10616]: Step_before = stepLanguage
May  9 17:03:51 ubuntu ubiquity[10616]: switched to page stepLocation
May  9 17:03:55 ubuntu localechooser: info: Locale has been preseeded to en_US.UTF-8
May  9 17:03:55 ubuntu localechooser: info: Set languagechooser/language-name-fb = 'English'
May  9 17:03:55 ubuntu localechooser: info: Set countrychooser/shortlist-en = 'US'
May  9 17:03:55 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May  9 17:03:55 ubuntu localechooser: info: Set debconf/language = ''
May  9 17:03:55 ubuntu localechooser: info: Set countrychooser/country-name = 'United States'
May  9 17:03:55 ubuntu localechooser: info: Set debian-installer/country = 'US'
May  9 17:03:55 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May  9 17:03:55 ubuntu ubiquity[10616]: debconffilter_done: Timezone (current: Timezone)
May  9 17:03:55 ubuntu ubiquity[10616]: Step_before = stepLocation
May  9 17:03:56 ubuntu ubiquity[10616]: log-output -t ubiquity setxkbmap -model pc105 -layout us
May  9 17:03:58 ubuntu ubiquity: Your console font configuration will be updated the next time your system
May  9 17:03:58 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
May  9 17:03:58 ubuntu ubiquity[10616]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
May  9 17:03:58 ubuntu ubiquity[10616]: debconffilter_done: ConsoleSetup (current: ConsoleSetup)
May  9 17:03:58 ubuntu ubiquity[10616]: Step_before = stepLocation
May  9 17:03:59 ubuntu kernel: [  193.968209] program parted_devices is using a deprecated SCSI ioctl, please convert it to SG_IO
May  9 17:04:01 ubuntu ubiquity[10616]: debconffilter_done: Partman (current: Partman)
May  9 17:04:01 ubuntu ubiquity[10616]: dbfilter_handle_status: ('Partman', 10)
May  9 17:04:05 ubuntu ubiquity[10616]: dbfilter_handle_status: response -7
May  9 17:04:05 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
May  9 17:04:05 ubuntu ubiquity[10616]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
May  9 17:04:05 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
May  9 17:04:05 ubuntu ubiquity[10616]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^xserver-xorg/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
May  9 17:04:06 ubuntu /usr/sbin/cron[11565]: (CRON) INFO (pidfile fd = 3)
May  9 17:04:06 ubuntu /usr/sbin/cron[11570]: (CRON) STARTUP (fork ok)
May  9 17:04:06 ubuntu /usr/sbin/cron[11570]: (CRON) INFO (Running @reboot jobs)
May  9 17:04:08 ubuntu kernel: [  202.921430] [drm] Setting GART location based on new memory map
May  9 17:04:08 ubuntu kernel: [  202.921906] [drm] Loading R300 Microcode
May  9 17:04:08 ubuntu kernel: [  202.921966] [drm] writeback test succeeded in 1 usecs
May  9 17:04:12 ubuntu gdm[11563]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
May  9 17:04:12 ubuntu gdm[11563]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
May  9 17:04:12 ubuntu gdm[11563]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
May  9 17:04:18 ubuntu pulseaudio[11807]: pid.c: Stale PID file, overwriting.
May  9 17:04:20 ubuntu hcid[10432]: Default passkey agent (:1.27, /org/bluez/passkey) registered
May  9 17:04:20 ubuntu hcid[10432]: Default authorization agent (:1.27, /org/bluez/auth) registered
May  9 17:04:30 ubuntu NetworkManager: <info>  Updating allowed wireless network lists. 
May  9 17:04:30 ubuntu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May  9 17:17:01 ubuntu /USR/SBIN/CRON[12069]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

---

### Post by ago on 2008-05-09
Yep software raids are not supported in wubi. Many hardware raids are in fact software ones.

---

