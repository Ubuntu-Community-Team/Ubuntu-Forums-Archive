---
title: "Doesn't load in vista"
date: 2008-03-05
forum: General Help
---

### Post by marhyo on 2008-03-05
HI!

I just installed wubi-8.04-alpha-rev446.exe and it finished just fine. Afterwards the computer rebooted and nothing. No option to run ubuntu. How do I run ubuntu? Faq says to just reboot and use ubuntu for ubuntu and windows for windows. But there's no menus for that. Please help.

---

### Post by ago on 2008-03-05
Hi marhyo, that might be becasue you lack the required privileges.

I would appreciate if you could attach the log files. You will find them in the temp folder (type %temp% in windows explorer). I will see if it is something that can be fixed, since even if you have no permission you should be prompted to escalate the privileges.

---

### Post by marhyo on 2008-03-05
Sorry, but what files are those logs? I mean the name. There are many files in windows/temp directory in vista.

---

### Post by ago on 2008-03-05
Should be 

Wubi-8.04-alpha-rev447.log

or something like that, will be in the UserProfile\Local Settings\Temp (shortcut to that is %temp%)

---

### Post by marhyo on 2008-03-05
============ Installer ============
PLUGINSDIR=C:\Users\Mario\AppData\Local\Temp\nso7B3D.tmp
detect_all
Parsing cmdline "F:\Wubi-8.04-alpha-rev446.exe" 
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD F:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive F:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in F: is 30158
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
GMT=1
Country=IT
Locale=en_US.UTF-8
LayoutCode=it
TimeZone=Europe/Rome
Domain=localdomain
HostName=Mario
ComputerName=MARIO
EnvUsername=Mario
UserDomain=MARIO
UserInfoName=Mario
UserProfileFolder=C:\Users\Mario
UserProfileName=Mario 
ShowMainPage
Making drive list
Drive & Path name 1742; Volume name ; Max #/chars in vol name 3031568; Volume Serial # -660817955; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Skipping drive C:, not enough free space 3452 <= {MinSizeMB}
Drive & Path name 1742; Volume name Mario; Max #/chars in vol name 3031580; Volume Serial # 1075876180; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Adding drive F:
Drive list = F:
ChangeInstallationDrive to F:
ChangeInstallationSize to 10
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
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 4
LeaveMainPage
ChangeInstallationSize to 6
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created F:\ubuntu\Uninstall.exe
Created C:\Windows\Uninstall.exe
Created reg key 1
Created reg key 2
CopyDistFolders
GetIso
DetectCD
      Is Valid CD F:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
No CD found
DetectIso
Checking/Downloading Ubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink)
get_md5 [http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink)
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg md5=
Download status=The requested URL returned error: 404
Error downloading [http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg](http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg), The req
Trying remote metalink2: [http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink)
get_md5 [http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink)
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=success:F:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:F:\ubuntu\install\MD5SUMS
      Verifying signature F:\ubuntu\install\MD5SUMS.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 02/28/08 21:54:35 Central Europe Standard Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing F:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=success:F:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=F:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from F:\ubuntu\install\hardy-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name F:\ubuntu\install\hardy-desktop-i386.iso; Volume name Mario; Max #/chars in vol name ; Volume Serial # 1075876180; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
C:\Users\Mario\AppData\Local\Temp\nso7B3D.tmp\wubibcd.exe 
 1:0 
 2:Operation completed successfully. New ID is {447928fc-eaa4-11dc-9e9b-000129745071}
 
 3:HDD 
 4:3
vistaBootDriveCode = {447928fc-eaa4-11dc-9e9b-000129745071} <=> {447928fc-eaa4-11dc-9e9b-000129745071}
vistaBootDriveCode {447928fc-eaa4-11dc-9e9b-000129745071}
Drive & Path name /Users/Mario; Volume name Mario; Max #/chars in vol name F:\ubuntu\install\hardy-desktop-i386.iso; Volume Serial # 1075876180; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=F:\ubuntu\disks\root.disk size=9000
AllocFile filename=F:\ubuntu\disks\home.disk size=0
AllocFile filename=F:\ubuntu\disks\swap.disk size=1000
UncompressFilesAfterInstall
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\Mario\AppData\Local\Temp\nshFEBA.tmp
detect_all
Parsing cmdline "F:\Wubi-8.04-alpha-rev446.exe" 
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD F:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive F:\ubuntu
Found InstallationDrive F:\ubuntu
AlreadyInstalled=true OldInstallationDrive=F: InstallCompleted=true
FreeSpace in F: is 19905
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
GMT=1
Country=IT
Locale=en_US.UTF-8
LayoutCode=it
TimeZone=Europe/Rome
Domain=localdomain
HostName=Mario
ComputerName=MARIO
EnvUsername=Mario
UserDomain=MARIO
UserInfoName=Mario
UserProfileFolder=C:\Users\Mario
UserProfileName=Mario 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=C:\Users\Mario\AppData\Local\Temp\nsn663E.tmp

---

### Post by ago on 2008-03-05
Hi Mario, I cannot see anything abnormal in the log, which makes your case that much more interesting. Will bring on board the Vista master...
Do you have any peculiar boot setup I should be aware of? Or is it just vista on your machine?

---

### Post by marhyo on 2008-03-05
Hehe. It seems that ubuntu doesn't like me.

---

### Post by ago on 2008-03-05
Not yet a final release, bugs are expected... But the idea is to fix them... 

Anyway you can try to fix/clarify the issue using EasyBCD.

Please let me know if you find out anything.

---

### Post by marhyo on 2008-03-05
As you probably figured it out that I'm not very good in these booting things. I already tried easy BCD and I have no clue what to do there.

---

### Post by ago on 2008-03-05
I have asked easybcd author (who is also the developer that wrote the Vista bootloader component in wubi) to have a look at the above we might wait for him...

---

### Post by marhyo on 2008-03-05
OK, thanx for your help and patience.

---

### Post by Keltenbleich on 2008-03-05
Good day....excuse me...what do you mean with  " doesn't load in Vista" ? I am a beginner on the LINUX platform (Ubuntu) and I thought this is about LINUX...I have been using MAC OS since 1998 so far...Thanks for your prompt reply...

---

### Post by ago on 2008-03-05
My understanding is that after using Wubi, there should be a "Ubuntu" item in the vista boot menu, but it's not in there, so that when you reboot you end up in Vista again.

Marhyo, now that I think of it, in the past one issue was that the timeout was zero. That should have been fixed but you'd better check.

If you use EasyBCD, after installing Wubi, it will list the entries in the Vista boot menu. Can you do a fresh installation of Wubi, then run EasyBCD and paste here your Vista boot configuration.

---

### Post by marhyo on 2008-03-05
There are a total of 2 entries listed in the Vista Bootloader.
Bootloader Timeout: 10 seconds.
Default OS: Microsoft Windows Vista

Entry #1

Name:  Microsoft Windows Vista
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #2

Name:  Ubuntu
BCD ID:  {447928fc-eaa4-11dc-9e9b-000129745071}
Drive:  U:\
Bootloader Path:  \ubuntu\winboot\wubildr.mbr



And the debug mode:

Windows Boot Manager
--------------------
identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
default                 {e42ac1de-25b1-11dc-a03f-c808fe2d712b}
displayorder            {e42ac1de-25b1-11dc-a03f-c808fe2d712b}
                        {447928fc-eaa4-11dc-9e9b-000129745071}
toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout                 10

Windows Boot Loader
-------------------
identifier              {e42ac1de-25b1-11dc-a03f-c808fe2d712b}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  en-US
inherit                 {6efb52bf-1766-41db-a6b3-0ee5eff72bd7}
osdevice                partition=C:
systemroot              \Windows
resumeobject            {e42ac1df-25b1-11dc-a03f-c808fe2d712b}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {447928fc-eaa4-11dc-9e9b-000129745071}
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu

---

### Post by ago on 2008-03-05
Marhyo, the bcd output looks good to me... Not sure why the Wubi item does not appear when you boot. Do you use any other bootloader?

---

### Post by marhyo on 2008-03-05
Not that I would know of.

---

### Post by ago on 2008-03-05
U: is a local drive? Can you try installing to another drive?

---

### Post by marhyo on 2008-03-05
Well, there should be no u drive on my computer. I have only c where the vista is, then there are d e for 2 dvd drives and f is the second HDD where wubi is installed. So I guess it should be f instead of u.

---

### Post by Computer Guru on 2008-03-05
Drive U: is what EasyBCD puts in the box when the drive for an entry is (as defined by Vista) unknown.

The data you posted above isn't enough to debug the situation though, can you please paste the contents of "Detailed Mode" from the EasyBCD home screen?

Thanks.

---

### Post by ago on 2008-03-05
Ah the cavalry has arrived... ;D

---

### Post by Computer Guru on 2008-03-05
I missed you too, ago!

:P

---

### Post by ago on 2008-03-05
I can confirm from wubi logs that F: was indeed targeted, didn't notice at first that the drive letter didn't match with the BCD entry. This is the drive info I can gather from the wubi logs (not that is very helpful here...):

Drive & Path name /Users/Mario; Volume name Mario; Max #/chars in vol name F:\ubuntu\install\hardy-desktop-i386.iso; Volume Serial # 1075876180; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255

---

### Post by Computer Guru on 2008-03-05
ago, so 
wubi.exe /d F: ....... 

was executed?

---

### Post by ago on 2008-03-05
> **Computer Guru said:**
> ago, so 
wubi.exe /d F: ....... 

was executed?

Should be. Cannot gather the exact call from the logs, but I would be surprised if it is any different. Here is the relevant log extract

C:\Users\Mario\AppData\Local\Temp\nso7B3D.tmp\wubibcd.exe
1:0
2:Operation completed successfully. New ID is {447928fc-eaa4-11dc-9e9b-000129745071}

3:HDD
4:3
vistaBootDriveCode = {447928fc-eaa4-11dc-9e9b-000129745071} <=> {447928fc-eaa4-11dc-9e9b-000129745071}
vistaBootDriveCode {447928fc-eaa4-11dc-9e9b-000129745071}
Drive & Path name /Users/Mario; Volume name Mario; Max #/chars in vol name F:\ubuntu\install\hardy-desktop-i386.iso; Volume Serial # 1075876180; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255

---

### Post by Computer Guru on 2008-03-05
I've seen this error before with other Linux & XP entries in EasyBCD, and I don't think it is related to the program or method used to add the entry nor how it was done.... Usually it's caused by a problem with the Vista BCD store, but I'll need the detailed EasyBCD output to be sure.

---

### Post by ago on 2008-03-05
marhyo, ball in your half...

---

### Post by marhyo on 2008-03-05
Well I posted it before. Where it says debug mode...it's detailed (debug mode). Here it is again.

And the debug mode:

Windows Boot Manager
--------------------
identifier {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device partition=C:
description Windows Boot Manager
locale en-US
inherit {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
default {e42ac1de-25b1-11dc-a03f-c808fe2d712b}
displayorder {e42ac1de-25b1-11dc-a03f-c808fe2d712b}
{447928fc-eaa4-11dc-9e9b-000129745071}
toolsdisplayorder {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout 10

Windows Boot Loader
-------------------
identifier {e42ac1de-25b1-11dc-a03f-c808fe2d712b}
device partition=C:
path \Windows\system32\winload.exe
description Microsoft Windows Vista
locale en-US
inherit {6efb52bf-1766-41db-a6b3-0ee5eff72bd7}
osdevice partition=C:
systemroot \Windows
resumeobject {e42ac1df-25b1-11dc-a03f-c808fe2d712b}
nx OptIn

Real-mode Boot Sector
---------------------
identifier {447928fc-eaa4-11dc-9e9b-000129745071}
path \ubuntu\winboot\wubildr.mbr
description Ubuntu

---

### Post by Computer Guru on 2008-03-05
Sorry, I must have missed it the first time.

Well, this command should fix your problem (assuming wubildr.mbr is on drive F:\), but I don't see any sign of trouble in the Vista BCD to trigger this behavior in the first place.

EasyBCD->Useful Utilities->Power Console:
```
bcdedit.exe /set {447928fc-eaa4-11dc-9e9b-000129745071} device partition=F:
```

---

### Post by ago on 2008-03-05
It would be nice to know what triggered that, so that we can have the fix directly in Wubi...

---

### Post by Computer Guru on 2008-03-05
I'm not sure.... WubiBCD does that *exact* call in the code, so I doubt you can add a fix:

```
Installer.StartInfo.Arguments = String.Format("/set {0} device partition={1}", ID, drive);
```

For some reason, the command just didn't take... I'm 98% sure that this is just a Vista glitch, but I could be wrong...

---

### Post by marhyo on 2008-03-05
I will try that tomorrow.

---

### Post by Gilean on 2008-03-06
Ciao ago, ho appena installato l'ultima alpha di hardy ed ho fatto partire wubi proprio da questa (uso vista). L'installazione e' andata a buon fine, poi ho abilitato i drivers ristretti (ho una ati radeon x1950 xtx) e da allora ubuntu pare caricare e poi lo schermo si spegne....sai a cosa puo' essere dovuto?

---

### Post by ago on 2008-03-06
> **Gilean said:**
> Ciao ago, ho appena installato l'ultima alpha di hardy ed ho fatto partire wubi proprio da questa (uso vista). L'installazione e' andata a buon fine, poi ho abilitato i drivers ristretti (ho una ati radeon x1950 xtx) e da allora ubuntu pare caricare e poi lo schermo si spegne....sai a cosa puo' essere dovuto?

Probablimente c'e' qualche problema con i video drivers. 
Usa Ctrl+Alt+F2 quindi esegui:

sudo dpkg-reconfigrue xserver-xorg

Quindi scegli vesa lasciando stare gli altri settings. Questo ti permette di avviare nuovamente in modalita' grafica e da li' puoi provare altre opzioni. Essendo Ubuntu ancora in alpha e' possibile che ci sono degli aggiustamenti su alcuni pacchetti. Controlla su questo forum se ci sono notizie che riguardano la tua scheda video.

---

### Post by marhyo on 2008-03-06
Italian doesn't really help me, btw. I tried that command mentioned and I got this:

The element data type specified is not recognized, or does not appy to the specified entry.
Run "bcdedit /?" for command line assistance.

---

### Post by marhyo on 2008-03-06
Now I have a feeling that my vista really hates ubuntu and is much stronger. Hehe.

---

### Post by ago on 2008-03-06
Is this what you used (watch the white spaces)?

bcdedit.exe /set {447928fc-eaa4-11dc-9e9b-000129745071} device partition=F:

---

### Post by Gilean on 2008-03-06
ok i'll speak in english. Tnx Ago for the quick reply, but i think i'll wait for final release, i think in my pc configuration, The alpha 5 is almost unstable :(

---

### Post by ago on 2008-03-06
> **Gilean said:**
> ok i'll speak in english. Tnx Ago for the quick reply, but i think i'll wait for final release, i think in my pc configuration, The alpha 5 is almost unstable :(

Alphas/betas tend to be okish after a new release, i.e. things should get better for alph6 in a couple of days, they tend to become more flimsy in between releases. So if you want to use alphas, a good strategy is to upgrade just after a release date.

---

### Post by ago on 2008-03-06
Anyway if you find any problem when trying the alpha betas, what you should do is:

* try to nail it down as much as possible
* check launchpad if anyone else had the same issue
* submit a bug report in launchpad.

Bug reports are important, and the more precise (with appropriate logs) the easier it is to fix them. In particular if you provide instructions so that a developer can replicate the same issue or a log that points clearly to the problematic area, things get fixed sooner.

---

### Post by marhyo on 2008-03-06
> **ago said:**
> Is this what you used (watch the white spaces)?

bcdedit.exe /set {447928fc-eaa4-11dc-9e9b-000129745071} device partition=F:

Yes

---

### Post by ago on 2008-03-06
The command seem correct (see for instance [http://technet2.microsoft.com/windowsserver2008/en/library/85cd5efe-c349-427c-b035-c2719d4af7781033.mspx?mfr=true](http://technet2.microsoft.com/windowsserver2008/en/library/85cd5efe-c349-427c-b035-c2719d4af7781033.mspx?mfr=true))

I cannot check now because I have no vista, make sure that the number within brackets is correct and actual, but using easybcd

---

### Post by marhyo on 2008-03-06
Whatever I tried, always the same error lines pop up. That command doesn't work here.

---

### Post by Computer Guru on 2008-03-06
Well, that explains the earlier error at any rate.... good to know it's not a WubiBCD problem.

Try these steps:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

