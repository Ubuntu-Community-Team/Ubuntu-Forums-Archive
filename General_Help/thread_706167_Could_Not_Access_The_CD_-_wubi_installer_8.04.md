---
title: "Could Not Access The CD - wubi installer 8.04"
date: 2008-02-24
forum: General Help
---

### Post by joethecomputer on 2008-02-24
Each time i try the wubi installer for the alpha5 disk on vista, the installer fails after "Creating Image..." gets to 100%.
I then get an error message reading "**Could Not Access The CD, please make sure other applications are not using it and try again**"

any help would be appreciated

---

### Post by ago on 2008-02-24
Type %temp% in windows explorer location bar, there should be a wubi log. Attach it here.

---

### Post by joethecomputer on 2008-02-24
log is attatched...

---

### Post by ago on 2008-02-24
I see:

CD2ISO failed: LastError = 23 Data error (cyclic redundancy check).


In which case repeating the stap seems like a reasonable action, couldn't you select retry? Did you checksum the CD/ISO?

---

### Post by joethecomputer on 2008-02-24
i tried repeating, to no success. i've just checked the md5, and it has failed, so i am now re-downloading the iso file


could it be to do with vista?

---

### Post by joethecomputer on 2008-02-24
i tried again with an iso which matches the md5, to no success... any help?

---

### Post by ago on 2008-02-24
> **joethecomputer said:**
> i tried again with an iso which matches the md5, to no success... any help?

I will investigate that. 

Anyway do not burn the CD, simply put the ISO in the same folder where you have wubi (8.04) exe. Make sure that other ISOs are not around...

---

### Post by bshibley on 2008-03-07
I'm having the same problem, but haven't checked %temp% yet.  The media check passes.  Both install from CD AS WELL AS install from harddrive with the iso in the wubi.exe location.  Both give the message "Could Not Access The CD, please make sure other applications are not using it and try again" when the "Creating image..." gets to 100%.  This is on a brand new install of XP with SP2 installed and most updates installed.  This is with the Desktop i386 alpha 6 iso.

---

### Post by bmwracer0 on 2008-04-03
3 re-downloads, alpha 5 and beta, both wont install wubi. md5 checks out and everything. i did click retry, still didnt work

---

### Post by ago on 2008-04-03
when does it happen? at the end of the "creating image" or at the beginning?

---

### Post by bmwracer0 on 2008-04-03
at the end, right after it hits 100%

---

### Post by ago on 2008-04-03
if you wait a few mins I will push something up to test

---

### Post by ago on 2008-04-03
can you please test rev 478?

---

### Post by bmwracer0 on 2008-04-03
i didnt see 478, but 479 is not working for me.

---

### Post by ago on 2008-04-04
what is the exact error in the wubi log (in %temp% directory)?

---

### Post by ago on 2008-04-04
if 479 does not work, pls try 

[http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev479B.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev479B.exe)

---

### Post by bmwracer0 on 2008-04-04
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Michael\LOCALS~1\Temp\nsn2E1.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Michael\Desktop\Wubi-8.04-beta-rev479.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1013 MB
arch=i386
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
Found CD D:
Found CD cddrive=D:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1709; Volume name SQ004033P03; Max #/chars in vol name 1846504; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem E:
Drive & Path name 1709; Volume name My Book 500; Max #/chars in vol name 1846512; Volume Serial # 278846377; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive E: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1709; Volume name My Book 250; Max #/chars in vol name 1846516; Volume Serial # 1746946680; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem G:
Drive & Path name 1709; Volume name My Book 320; Max #/chars in vol name 1846520; Volume Serial # -599912659; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive G: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1452440; Volume name SQ004033P03; Max #/chars in vol name 60; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = G:
FreeSpace in G: is 109817
DetectBackupFolder
Found BackupFolder C:\ubuntu-backup
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=toshiba-user
ComputerName=TOSHIBA-USER
EnvUsername=Michael
UserDomain=TOSHIBA-USER
UserInfoName=Michael
UserProfileFolder=C:\Documents and Settings\Michael
UserProfileName=Michael 
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1752; Volume name SQ004033P03; Max #/chars in vol name 1859552; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem E:
Drive & Path name 1752; Volume name My Book 500; Max #/chars in vol name 1859560; Volume Serial # 278846377; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive E: has valid filesystem NTFS
Adding drive E:
IsValidFileSystem F:
Drive & Path name 1752; Volume name My Book 250; Max #/chars in vol name 1859564; Volume Serial # 1746946680; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Adding drive F:
IsValidFileSystem G:
Drive & Path name 1752; Volume name My Book 320; Max #/chars in vol name 1859568; Volume Serial # -599912659; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive G: has valid filesystem NTFS
Adding drive G:
Drive list = C:|E:|F:|G:
ChangeInstallationDrive to C:
ChangeInstallationSize to 7
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
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
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
Found CD D:
Found CD cddrive=D:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
We are connected and can get the ISO md5, skipping CheckCD
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: LastError = 1 Incorrect function.

Asking user to retry CD2ISO
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: LastError = 1 Incorrect function.

Asking user to retry CD2ISO
User did not select to retry CD2ISO, quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Michael\LOCALS~1\Temp\nsl43B.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Michael\Desktop\Wubi-8.04-beta-rev479B.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1013 MB
arch=i386
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
Found CD D:
Found CD cddrive=D:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1709; Volume name SQ004033P03; Max #/chars in vol name 1843912; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1449808; Volume name SQ004033P03; Max #/chars in vol name 60; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 10696
DetectBackupFolder
Found BackupFolder C:\ubuntu-backup
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=toshiba-user
ComputerName=TOSHIBA-USER
EnvUsername=Michael
UserDomain=TOSHIBA-USER
UserInfoName=Michael
UserProfileFolder=C:\Documents and Settings\Michael
UserProfileName=Michael 
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1752; Volume name SQ004033P03; Max #/chars in vol name 1854008; Volume Serial # 1820842477; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 7
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 6
LeaveMainPage
ChangeInstallationSize to 6
LeaveMainPage
ChangeInstallationSize to 6
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
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta i386 (20080319)
Found CD D:
Found CD cddrive=D:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
We are connected and can get the ISO md5, skipping CheckCD
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: LastError = 1 Incorrect function.
 : The number of bytes written doesn't equal the disk size!
Asking user to retry CD2ISO
User did not select to retry CD2ISO, quitting.


thanks for all your help! (thats with the revision B one)

---

### Post by Ubuntakos on 2008-04-25
Im experiencing the same problem.
First i thought it was the download so i redownloaded it and burned a second cd.
But no luck.

I tried it on my XP sp2 and on my laptop with vista but i get the same error with you on both!

PS: Im using the final version of 8.04 (downloaded 25-04-2008)

---

### Post by ago on 2008-04-25
[https://wiki.ubuntu.com/WubiGuide#head-100b63cc0192113d19fa119a9d472412e42ac1a8](https://wiki.ubuntu.com/WubiGuide#head-100b63cc0192113d19fa119a9d472412e42ac1a8)

---

### Post by Fajer on 2008-04-27
I have the same very problem with instalation from cd in cd-rom drive.

instalation from hdd with iso of cd dosen't work - wubi force to download iso from server.

---

### Post by ago on 2008-04-27
> **Fajer said:**
> I have the same very problem with instalation from cd in cd-rom drive.

instalation from hdd with iso of cd dosen't work - wubi force to download iso from server.

Please provide the wubi log in your user temp folder (%temp%)

---

### Post by polyclef on 2008-04-27
I have the same problem.  Tried from a CD and also running Wubi with the iso in the folder. Gets right to the end of installing the image and throws this error.

Attached is the wubi log

---

### Post by randome on 2008-04-28
Same error here.
Wubi stopes at 100%.
And wubilog ends with 
CD2ISO failed: LastError = 1 Incorrect function.
its wubi-8.04-beta-rev495

Gonna try using wubi.exe and .iso file.
Same error..

---

### Post by ago on 2008-04-28
Was the CD finalized? What medium did you use? CD-R, CR-RW, DVD-R, DVD+R...
Can you try burning at low speed with a different support and making sure the CD is finalized?

The simple workaround is to put ISO and wubi.exe in the same folder but the above info will help to handle future cases.

---

### Post by Fajer on 2008-04-28
> **ago said:**
> The simple workaround is to put ISO and wubi.exe in the same folder but the above info will help to handle future cases.
For me it doesn't work either. Wubi start to download iso from the web.

---

### Post by ago on 2008-04-28
Is that the latest CD DESKTOP ISO? If wubi downloads it, it means that it is the wrong ISO or it is corrupted, or that another wrong ISO is found on the same path (/ubuntu-backup is scanned too).

---

### Post by Zakhafr on 2008-04-28
> **ago said:**
> Was the CD finalized? What medium did you use? CD-R, CR-RW, DVD-R, DVD+R...
Can you try burning at low speed with a different support and making sure the CD is finalized?

Hello, I don't think it comes from a kind of burning problem.

I have the same problem with Ubuntu.
Kubuntu & Kubuntu remix show another problem on my Windows French version (but I thing you already are on this bug also), because as iso for Wubi install are not on the CD they are downloaded. Apparently Ubuntu is found on the CD because it does not download anything.

To be sure it was not a "burn" problem what I did is mount the Ubuntu iso with Daemon Tools (the same iso I burned to the CD-RW).
So when you tell Daemon Tools to mount that iso file, it appears as a new CD-ROM on Windows, it shows the little pop up asking for install, as if you inserted a real CD.
You select Wubi from here, and you have the same bug described here.

I'll try to elaborate, let's say the Ubuntu iso is 689,1MB, the Wubi install displays a small gauge while "Creating image" and a counter saying 243,4MB / 689,1MB, etc...

At the end you can see :
689,1MB / 689,1MB
... then ...
689,2MB / 689,1MB

Of course, as the CD (mounted through Daemon Tools or Burned to a real CD does the same, and the MD5 have been checked) has only 689,1MB you cannot read at address 689,2MB

Immediately after that you have a message box saying that the program cannot read from the CD (obviously !).

I'll do it again tonight (at work at the moment... Paris time) and post the log as indicated here if this can help.

---

### Post by ago on 2008-04-28
Can you please post your finding at [https://bugs.launchpad.net/wubi/+bug/207137](https://bugs.launchpad.net/wubi/+bug/207137)

---

### Post by Zakhafr on 2008-04-28
> **ago said:**
> Can you please post your finding at [https://bugs.launchpad.net/wubi/+bug/207137](https://bugs.launchpad.net/wubi/+bug/207137)

Yes I will do that... but I have to register to Launchpad and I cannot do it from work (external mails blocked). So I'll do it this evening (CEST).

---

### Post by Zakhafr on 2008-04-28
Sorry at the moment I cannot reproduce the bug, it seems to work now (still trying).

If it helps, I have a message at the _begining_ of the copy with this configuration :
- mount ISO on **another** PC of your network
- share this virtual driv on the network
- map a drive to this shared device on the PC you want to install to.
- it should pop-up the screen once you accept to mount the network drive.
- clic on the Wubi install (2nd button of popup)
- checksum runs OK
- Error message

The log shows:
[INDENT][SIZE="1"]Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
Found CD Y:
Found CD cddrive=Y:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=3879aa51ef0b4b1b7bf9472744208417
Checking md5 of Y:\casper\filesystem.squashfs
CheckCD raw status = success:Y:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: LastError = 5 Accès refusé.

Asking user to retry CD2ISO
User did not select to retry CD2ISO, quitting.[/SIZE][/INDENT]

There is nothing special such as read-only or any protection on my C: drive.
[By the way I say that because on the last message : Accès refusé translates to **Access denied**]

Using network drives/folders (eg not mapped to a drive letter) produces a lot of unexpected results, such as umenu.exe crashing if you try to launch it, or complaining that it is not a CDROM.

... but I assume it was not meant to be network-launched !

---

### Post by Zakhafr on 2008-04-28
False alert !

I read more carefully the log, and there is indeed an error 23 (CRC check error) on the CD.
It must have happened at the end of the CD, so that's why I had this behaviour, and could reproduce it.

I'll reburn the CD.

---

### Post by Grayghost on 2008-05-03
Hi FWIW I have the same problem and are yet to find a satisfactory answer for this problem yet.
I initially installed this on my old AMD Athlon XP1800+ PC running WinXP SP2 & it gave me the dreaded "Could Not Access The CD...." message. So I thought I burnt a corrupted copy. Downloaded another mirror from my ISP here in Oz and burnt onto a different brand CD at only 4x (the slowest Nero would offer me) and ran it. Same problem. Googled the issue and came across this thread. Extracted the iso and placed the wubi.exe file in the same directory as the iso from which it was sourced. Still didn't work. Instead it appeared to be downloading the image again on the fly. I didn't want that so I cancelled it. Cracked it and tried one of the imaged disks on my laptop, an IPM T43P Thinkpad also running WinXP SP2. Same bloody problem, gets to 100% of the image and hangs with the same message. Checked the log file and here's an excerpt of the end of the file FWIW - but appears to be the same problem that everyone else is having "CD2ISO failed".

md5=3879aa51ef0b4b1b7bf9472744208417
Checking md5 of D:\casper\filesystem.squashfs
CheckCD raw status = success:D:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: LastError = 1 Incorrect function.

Asking user to retry CD2ISO
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO failed: LastError = 1 Incorrect function.

Asking user to retry CD2ISO
User did not select to retry CD2ISO, quitting.


Again I would like to reiterate that it appears that I have not found a satisfactory solution to this problem. Was looking forward to switching from Micro...t because I had had a gutful of the wastefulness and unreliablity of the OS and can't afford another Mac in my home. Hoping to install what is being published now in the mainstream as a supposedly great maturing open OS - very disillusioning to say the least!!!

**HELP PLEASE!!!**

---

### Post by xeonicxpression on 2008-05-03
I think I might be having the same problem, but I'm not sure.  Wubi finishes in windows and i reboot and select ubuntu it boots up and does its install.  Once it gets to the end I get some error about CD something or other.  I don't get time to read it.  The computer reboots and I get a message saying 

Booting Ubuntu 8.04, Kernel 2.6.24-16-generic
Filesystem Tpye is NTFS, partition type is 0x7
Kernel/boot/vmlinuz-2.6.24-16-generic root=UUID=A2F40E29F40DFFF1 loop='ubuntu/disks/root.disk ro quiet splash
Error 15: File Not Found

When I boot into windows and goto C:\ubuntu\disks\ root.disk is clearly there.  Any advice?  I've tried downloading Wubi twice, used rev495 one day and rev501 today.  I'll attach both logs.  I've also downloaded 8.04 twice the second time I did the MD5Sum check and it was ok.

---

### Post by Grayghost on 2008-05-03
I also notice on threads some gurus talking about version builds. How can I establish whether what build I have of UHH 8.04 I have, or for that matter which one I am about to download/install. I can't seem to find any version information or build info on the Ubuntu site. Having a lot of problems!! ](*,)
Probably all my fault :oops:

---

### Post by ago on 2008-05-03
There is only one 8.04 release: [http://releases.ubuntu.com/releases/8.04](http://releases.ubuntu.com/releases/8.04)

---

### Post by Grayghost on 2008-05-06
Got the guru at work to try and install 8.04 on his laptop - also an IBM T43P - same problem as I had.

I can't understand if I have tried this in 3 different ways on 3 different computers and get the same problem why this does not appear to be a more common problem out there....

It would appear I will not be joining the Ubuntu community any time soon as it would appear that what is supposed to be a viable alternative to Windows is truly not the case!!

Why does nobody have any answers - ago seems to be the only one that is even responding to this situation:confused:

---

### Post by ago on 2008-05-06
Please try to download the ISO and wubi.exe (rev 501) from the same folder.

If it does not work attach the wubi log, which is in your user temp folder.

---

### Post by rstaker on 2008-05-08
Hi,  I am having the same problem with a win2k box.  At the end of creating image, I get the "could not access the CD" message  Re-running it doesn't fix it.  Neither does installing from an alternate drive.  I have both a cd and cd/dvd drive.  Neither works.

Please reply if fix becomes available to [email]rstaker@gmail.com[/email]

Thank you.

---

### Post by ago on 2008-05-09
[https://wiki.ubuntu.com/WubiGuide#head-151bf4941a0a676cc1ee296015f8fa3d7c1a0f47](https://wiki.ubuntu.com/WubiGuide#head-151bf4941a0a676cc1ee296015f8fa3d7c1a0f47)

---

### Post by Vladislav Mkrtychev on 2008-05-16
I had the same problem.
What I did is I shut down my firewall (Comodo)
and installation went on.
Then I was asked to reboot - I did that.
Then I needed to boot in Ubuntu - I did that too.
And that's where I got the new error message - something about inability to boot in ubuntu.
I was given several choices to boot in. One of them was 
Ubuntu in recovery  mode or something.
I chose to boot in XP instead.
So that's where I am stuck at...

---

### Post by ago on 2008-05-16
[https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230](https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230)

---

### Post by ago on 2008-06-26
Hi, this one is fixed in wubi 8.04.1

We need confirmation though that the issue is resolved. 

If you were affected by this bug, please test using Wubi 8.04.1 rev 504+ ([http://wubi-installer.org/devel/minefield/Wubi-8.04.1-rev504.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04.1-rev504.exe)) and a CD created from the latest daily ISO ([http://cdimage.ubuntu.com/hardy/daily-live/current/](http://cdimage.ubuntu.com/hardy/daily-live/current/)), then add a comment in 

[https://bugs.edge.launchpad.net/wubi/+bug/207137](https://bugs.edge.launchpad.net/wubi/+bug/207137)

---

### Post by SamSharpe on 2008-06-29
ago,

I'm new to this, but given your instructions, how do you know what hardy-desktop you're downloading?  What if I'm interested in the AMD64 version rather than i386?

---

### Post by ago on 2008-06-29
Unfortunately the fix for the CD extraction had to be reverted for 8.04.1 because another bug was blocking. It is still helpful though to test 8.04.1.

---

### Post by ThatOneDoood on 2008-08-14
OK. So I've been using Ubuntu for a few years now and have never had any problems that I couldn't solve... until now. For reasons unknown I am getting the same exact error, the same exact log info, and the same frustration as everyone else here. I have tried everything mentioned in this post and more, and still nothing. BUT... before this whole dilemma started, I installed Ubuntu successfully on a friends hp laptop. Weird right? So I tried figuring out what the dealio was with these two installs, and this is what I have come up with. I used the same exact CD to install, so I KNOW its not the CD. I can establish two conclusions from this alone. The CD-ROM is actually being used by another application or process. Or... Windows "thinks" that it is being used? I have tried killing every single application, process, and service that is not vital for system operation with no luck. *sigh* I am still very confused as to why it would install perfectly fine on one machine (and a few more times for testing), and as to why it wont on another. Btw, my friend is/was using vista home basic, I am using vista home premium. If anyone would like to know more about the hardware in both machines, let me know. (If u think that might be an issue.) The log files can both be provided as well, but they seem like a waste of time to me. Again, if anyone has any questions or insight I'll be happy to listen. 



Hope this can be worked out.

---

### Post by subsam on 2008-09-02
good morning sir;
i have the same problem , and i traid to find wubi 505 
but i can't
all the links for it were faild
sam

---

### Post by ago on 2008-09-03
You have to use the ISO directly as opposed to a physical CD, the error is due to a windows bug and depends on the medium/cd drive.

---

### Post by ThatOneDoood on 2008-09-13
ok so... when i try to install it never finds my iso file... it just tries to download a new one... i've put the iso file in the same folder as wubi and i've also put the iso file in the destination folder... what am i doing wrong.

i like windows, i love ubuntu... but together i hate them so far lol

---

### Post by daveydc on 2008-12-16
Hi, 
I had exactly the same problem, and solved it simply by burning it onto a DVD as a DVD image with Nero then it installed properly, hope this helps you guys.

David

---

### Post by Fajer on 2008-12-16
anyway it's a shame, that final, stable realase, burned on original CD from factory doesn't work.

...is there anyone testing this stuff **before** sending image to the cd burning facility?

---

### Post by ago on 2008-12-19
> **Fajer said:**
> anyway it's a shame, that final, stable realase, burned on original CD from factory doesn't work.

...is there anyone testing this stuff **before** sending image to the cd burning facility?

Yes, we were well aware of that, but as it happens this is a windows bug which is poorly documented and difficult to replicate, and it only affects a few people, so we decided to go ahead anyway.

---

### Post by Fajer on 2008-12-19
yes, **I** understand, but many peoples don't.

I wanted to show new brilliant features of Ubuntu to my college... and I've showed him problems with CD and installation. He is laughing at me because of it till now...

...and "Linux - simply doesn't work" spreads again. That&#8217;s sad.

---

### Post by wbrady4927 on 2009-02-20
The solution for me was running Wubi without the CD (just putting the iso file in the same directory). It worked fine and I was getting the error every time with Vista.

---

### Post by PsY. on 2009-02-26
un I also followed all these steps you have mentioned so far but I had not even 1x success during the installation of Kubuntu 8:10 ever presented with the error "Could Not Access The CD ...."
but when I'd like to install with wubi time of par was good cider when they start to
for the second time
from 733.3MB to 733.3MB error than ...

---

### Post by edgarme on 2009-04-11
I had the same problem but resolved it by burning the image with alcohol 120%,,,, try works!!!

---

### Post by crhylove on 2009-07-07
I had the same problem as everyone above.  (Though I was using Linux Mint, which I recommend, actually).

The solution for me was to use the Microsoft Virtual CD Control Panel:

[http://support.microsoft.com/kb/916902](http://support.microsoft.com/kb/916902)

Just click Driver Control ...
Then select Install Driver
Then click Start
Then click add drive
Then click Mount and browse for your Mint or Ubuntu ISO.

The fact that all this is required is a major barrier to Linux adoption for n00bs though.  This should be fixed ASAP!

In the meantime, let me know if Virtual CD Control Panel works for you!
):P

---

