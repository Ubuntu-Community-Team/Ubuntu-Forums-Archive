---
title: "Wubi 7.10 did not save anything..."
date: 2007-11-26
forum: General Help
---

### Post by linuxblind on 2007-11-26
I installed Wubi 7.10, it work but do not save any thing, include desktop setting and home directory. What can I do to config it?

or

due to install with live CD, Wubi 7.10 can not save any thing?

---

### Post by ago on 2007-11-26
The wubi version that ships with the live CD has limited features, it only allows you to boot the live cd, i.e. it only works in r/o mode. To get the full version see: [http://www.wubi-installer.org/devel/minefield](http://www.wubi-installer.org/devel/minefield)

---

### Post by dsmalle on 2007-11-26
Ago,
I tried the link you're referencing ([http://www.wubi-installer.org/devel/minefield/Wubi-7.10-alpha-rev386.exe](http://www.wubi-installer.org/devel/minefield/Wubi-7.10-alpha-rev386.exe)), but I had the same problem, I couldn't save settings. Indeed like a R/O setup.
Is there another way to setup that must be used to get 7.10 R/W?

---

### Post by ago on 2007-11-26
Do you see an icon with "install ubuntu" on your desktop?

---

### Post by dsmalle on 2007-11-26
yes indeed, that icon was there. I removed all since, but I remember deleting it because I thought it was to install full ubuntu on a partition.

---

### Post by ago on 2007-11-26
Then you are still booting from the old setup. Uninstall wubi. Then install again.

---

### Post by dsmalle on 2007-11-26
I've re-installed, and I have that icon again... I've installed to my D: drive (before it was on C:) and, again, wubi doesn't remember settings.

How can I know for sure there's no old setup remaining???

One thing more: when wubi starts, I have a 40 seconds black screen ("no signal") after the "system settings" icon.

---

### Post by ago on 2007-11-26
How much free space do you have? If you have less than 5GB the read-only installation is the only option.

---

### Post by linuxblind on 2007-11-26
> **ago said:**
> How much free space do you have? If you have less than 5GB the read-only installation is the only option.
I used recommended setting, 8GB for Wubi. And D: partition have 56GB free. I also see Install icon

---

### Post by ago on 2007-11-26
When you uninstall wubi, make sure there is no "ubuntu" folder around and no menu.lst. 
Also after installation, type %temp% in the windows file manager and look at the log (or post it here).

---

### Post by linuxblind on 2007-11-26
> **ago said:**
> When you uninstall wubi, make sure there is no "ubuntu" folder around and no menu.lst. 
Also after installation, type %temp% in the windows file manager and look at the log (or post it here).
Sorry, I have given up already. I installed a fresh version to my hard disk, so I don't have log file. Hope your project is perfect soon. Regardness

---

### Post by dsmalle on 2007-11-28
OK I've followed all advice here: uninstalled wubi, removed all iso files in the path, checked menu.lst file and ubuntu directories, I left the ubuntu-backup directory to avoid downloading again.

I chose install on my D: drive, 111GB free.
After installing again, I have the same problems but some more detail:
- after the "initializing system services" the screen goes black (no signal) but now I've noticed that touching mouse or keyboard brings the screen back up.
- the "Install" icon is still there
- the windows regional / keyboard settings are not used
- it doesn't remember settings (monitor, keyboard, ...) after a restart.

The log file refuses to attach here, so I've pasted the contents below.
Thanks for helping out!

-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\danny\LOCALS~1\Temp\nst54.tmp
detect_all
Parsing cmdline "C:\temp\Wubi-7.10-alpha-rev386.exe" 
DetectProcessorArchitecture
arch=i386
DetectCD
isvalidcd E:\
isvalidcd G:\
isvalidcd C:\
isvalidcd D:\
DetectCD Finished cddrive=
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
CheckFreeSpace c:
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
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
UserProfileName=danny 
ShowMainPage
ChangeInstallationDrive
ChangeInstallationSize
PopulateDistroList
DetectIso
IsValidIso ispoath=D:\ubuntu-backup\kubuntu-7.10-desktop-i386.iso
ExtractIsoInfo
C:\DOCUME~1\danny\LOCALS~1\Temp\nst54.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\danny\LOCALS~1\Temp D:\ubuntu-backup\kubuntu-7.10-desktop-i386.iso
C:\DOCUME~1\danny\LOCALS~1\Temp\nst54.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: D:\ubuntu-backup\kubuntu-7.10-desktop-i386.iso

Extracting  .disk\info

Everything is Ok
 
  
 
isvalid Kubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016.1)
 cdinfo=Kubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016.1) cdversion=7.10 cddistro=Kubuntu cdarch=i386 cdcodename=Gutsy Gibbon cdsubversion=Release 
GetDistroInfo distro=Kubuntu cdarch=i386 arch=i386
success Kubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016.1)
AddDistroToList Ubuntu-i386
AddDistroToList Ubuntu-amd64
AddDistroToList Kubuntu-i386
AddDistroToList Kubuntu-amd64
AddDistroToList Xubuntu-i386
AddDistroToList Xubuntu-amd64
AddDistroToList Edubuntu-i386
AddDistroToList Edubuntu-amd64
PopulateLanguageListBox
GetDistroInfo distro=Kubuntu cdarch=i386 arch=i386
InitMainPageToolTips
LeaveMainPage
ChangeInstallationDrive
ChangeInstallationSize
LeaveMainPage
ChangeInstallationSize
LeaveMainPage
DetectLocale
GetDistroInfo distro=Kubuntu cdarch=i386 arch=i386
CreateInstallationFolders
MakeUninstall
Created D:\ubuntu\uninstall-ubuntu.exe
Created C:\WINDOWS\uninstall-ubuntu.exe
Created reg key 1
Created reg key 2
CopyDistFolder
GetIso
DetectCD
isvalidcd E:\
isvalidcd G:\
isvalidcd C:\
isvalidcd D:\
DetectCD Finished cddrive=
DetectIso
IsValidIso ispoath=D:\ubuntu-backup\kubuntu-7.10-desktop-i386.iso
ExtractIsoInfo
C:\DOCUME~1\danny\LOCALS~1\Temp\nst54.tmp\7z.exe e -y -i!.disk/info -oC:\DOCUME~1\danny\LOCALS~1\Temp D:\ubuntu-backup\kubuntu-7.10-desktop-i386.iso
C:\DOCUME~1\danny\LOCALS~1\Temp\nst54.tmp\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: D:\ubuntu-backup\kubuntu-7.10-desktop-i386.iso

Extracting  .disk\info

Everything is Ok
 
  
 
isvalid Kubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016.1)
 cdinfo=Kubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016.1) cdversion=7.10 cddistro=Kubuntu cdarch=i386 cdcodename=Gutsy Gibbon cdsubversion=Release 
GetDistroInfo distro=Kubuntu cdarch=i386 arch=i386
success Kubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016.1)
Moving D:\ubuntu-backup\kubuntu-7.10-desktop-i386.iso -> D:\ubuntu\install\kubuntu-7.10-desktop-i386.iso
Checking/Downloading kubuntu-7.10-desktop-i386.iso
ConnectInternet
Trying to use remote metalink: [http://wubi-installer.org/metalinks/kubuntu-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/kubuntu-desktop-i386.iso.metalink)
CopyKernel
Extracting with 7z kernel/initrd from D:\ubuntu\install\kubuntu-7.10-desktop-i386.iso
7z 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: D:\ubuntu\install\kubuntu-7.10-desktop-i386.iso

Extracting  casper\vmlinuz

Everything is Ok
 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: D:\ubuntu\install\kubuntu-7.10-desktop-i386.iso

Extracting  casper\initrd.gz

Everything is Ok
 
 0
UncompressFilesPriorInstall
isFatFilesystem=false systemsize=16233 homesize=13000, swapsize=767, usrsize=0
systemsize=16233 homesize=13000, swapsize=767, usrsize=0
isFatFilesystem=false systemsize=16233 homesize=13000, swapsize=767, usrsize=0
systemsize=16233 homesize=13000, swapsize=767, usrsize=0
AllocFile filename=D:\ubuntu\disks\root.disk size=16233
AllocFile filename=D:\ubuntu\disks\home.disk size=13000
AllocFile filename=D:\ubuntu\disks\swap.disk size=767
UncompressFilesAfterInstall
EjectCD

---

### Post by ago on 2007-11-28
can you post /ubuntu/install/boot/grub/menu.lst and /ubuntu/install/preseed.cfg?

---

### Post by dsmalle on 2007-11-28
/ubuntu/install/boot/grub/menu.lst and
/ubuntu/install/preseed.cfg 
attached in zip.

---

### Post by ago on 2007-11-28
All good there. Do you have /ubuntu/disks/boot/menu.lst?

---

### Post by dsmalle on 2007-11-28
under D:\ubuntu\disks\boot, there's nothing except an empty grub directory. Under D:\ubuntu\disks there's home.disk, root.disk and swap.disk, and an empty shared directory.

---

### Post by ago on 2007-11-28
When you boot does it try to do an installation (should last 10+ minutes, with a chocolate fudge background and lots of progressbars in a grey dialog) or does it log you into the desktop environment?

---

### Post by dsmalle on 2007-11-28
> **ago said:**
> When you boot does it try to do an installation (should last 10+ minutes, with a chocolate fudge background and lots of progressbars in a grey dialog) or does it log you into the desktop environment?

it logs me straight into the desktop environment. except for the black screen I mentioned before that disappears when moving the mouse. Never seen the installation - I never see any progressbars except the "kubuntu" screen with the bar that goes left to right and back and then as a normal progress bar.

---

### Post by ago on 2007-11-28
Then you should have some other menu.lst file lying around which is loaded instead. Pressing "ins" rapidly as soon as you select Ubuntu on the boot menu might help

---

### Post by dsmalle on 2007-11-29
> **ago said:**
> Then you should have some other menu.lst file lying around which is loaded instead. Pressing "ins" rapidly as soon as you select Ubuntu on the boot menu might help

I've searched *everywhere* and the only 2 menu.lst files are both in the /ubuntu directories. One refers to the other.

Pressing "Ins" gets me in a kind of step per step mode for loading but doesn't tell me much; pressing "Esc" further on shows me the menu that is presented in the second menu.lst file (and indeed that menu speaks about installing...).

I've uninstalled again. I'll move the ubuntu-backup directory to the C: drive and I'll try installing to C: instead, see if that makes a difference.

---

### Post by ago on 2007-11-29
Basically you have to boot with the following kernel line, I have highlighted the important bits:


kernel /ubuntu/install/boot/vmlinuz **boot=casper find_preseed=/ubuntu/install/preseed.cfg find_iso=/ubuntu/install/kubuntu-7.10-desktop-i386.iso** quiet splash ro -- **automatic-ubiquity** locale=en_GB console-setup/layoutcode=us console-setup/variantcode=

---

### Post by dsmalle on 2007-11-29
When I interrupt the booting with Ins and then later in the Grub menu I edit the command to see the full line, it's exactly as the line you typed here above (and the line that is present in the menu.lst...)

What else can I check? logs, debug settings, ... ?

---

### Post by ago on 2007-11-29
/var/log/syslog 

after it boots to desktop +

cat /proc/cmdline

---

### Post by dsmalle on 2007-11-29
> **ago said:**
> /var/log/syslog 

after it boots to desktop +

cat /proc/cmdline

syslog is added in the attached zip. 

cat /proc/cmdline gives:

ubuntu@ubuntu:~$ cat /proc/cmdline
boot=casper find_preseed=/ubuntu/install/preseed.cfg find_iso=/ubuntu/install/ku                                                 buntu-7.10-desktop-i386.iso quiet splash ro -- automatic-ubiquity locale=en_GB c                                                 onsole-setup/layoutcode=us console-setup/variantcode=
ubuntu@ubuntu:~$ cat /proc/cmdline
boot=casper find_preseed=/ubuntu/install/preseed.cfg find_iso=/ubuntu/install/ku                                                 buntu-7.10-desktop-i386.iso quiet splash ro -- automatic-ubiquity locale=en_GB c                                                 onsole-setup/layoutcode=us console-setup/variantcode=
ubuntu@ubuntu:~$

---

### Post by ago on 2007-11-29
ctrl+alt+f2   #this will bring you to a console, do a login
sudo /etc/init.d/gdm stop
sudo /etc/init.d/ubiquity-automatic start    #do not remember the exact name on top of my head, it's something like "ubiquity-automatic". See what it says.

---

### Post by dsmalle on 2007-11-29
> **ago said:**
> ctrl+alt+f2   #this will bring you to a console, do a login
sudo /etc/init.d/gdm stop
sudo /etc/init.d/ubiquity-automatic start    #do not remember the exact name on top of my head, it's something like "ubiquity-automatic". See what it says.

sudo: /etc/init.d/gdm: command not found

for ...ubiquity.. as well

---

### Post by ago on 2007-11-29
as mentioned look for ubiquity in /etc/init.d, I am not on a linux machine at the moment

---

### Post by dsmalle on 2007-11-29
sudo /etc/init.d/ubiquity start
 *Starting Ubiquity...
Traceback (most recent call last):
 File "/usr/bin/ubiquity-dm", line 122, in <module>
  sys.exit(dm.run(*sys.argv[31]))
 File "/usr/bin/ubiquity-dm", line 67, in run
  raise XStartupError, "X server failed to start after 60 seconds"
__main__.XStartupError: X server failed to start after 60 seconds
$



next?

---

### Post by dsmalle on 2007-11-30
Ago,

is there something more that I can check? I can do re-installs of other builds if you want..., whatever.

---

### Post by ago on 2007-11-30
In a terminal run, 

ubiquity --automatic

Then post syslog and /var/cache/debconf/config.dat

---

### Post by dsmalle on 2007-11-30
> **ago said:**
> In a terminal run, 

ubiquity --automatic

Then post syslog and /var/cache/debconf/config.dat

This launched an automatic install process [in a window]. Up to detecting hardware... I'll post this before it reboots,,/ at least I expect it to do that... the rest will follow

---

### Post by dsmalle on 2007-11-30
As I expected, it did a reboot. So after rebooting I took the 2 files you requested, they are attached in zip.
I've changed regional settings, keyboard etc and monitor. I'll reboot now and see if it remembers this.

---

### Post by dsmalle on 2007-11-30
And, fantastic! Now it stores its settings. If you want to find out why it didn't do this automatically, I can be guinea pig, no problems.

One thing: wubi remembers the usercode/password I gave on the install dialog, but the keyboard settings for the login are wrong ("us" settings, and I changed to "be" settings for Belgium). After login, it is correct. As log as I know where the "a" and "w" are on an English keyboard... but it would be better if I could change this.

---

### Post by dsmalle on 2007-11-30
for whoever reads this thread and has problems with the login screen using a different keyboard layout as in the gui: change the /etc/X11/xorg.conf file, In the section "InputDevice", change the option "XkbLayout" to the appropriate one for your keyboard model.

---

