---
title: "Wubi-7.10-alpha-rev364.exe crashes on my XP system"
date: 2007-10-23
forum: General Help
---

### Post by molk on 2007-10-23
Wubi-7.10-alpha-rev364.exe crashes as soon as I run it. It doesn't even get to the Wubi Setup window. My system is XP Professional with Intel Centrino Duo 64bit processor. I tried redownloading the executable, but did not help. Wubi-7.10-alpha-rev363.exe runs fine without crashing so this is likely due to a change introduced in revision 364. What's also interesting is that 364 doesn't crash and gets to the Setup Window if I use the --debug switch.

---

### Post by ago on 2007-10-23
can you post the log in %temp%?
clean it up first, then run wubi, make it crash, and post here.

---

### Post by molk on 2007-10-23
Here is what's in the log file


============ Installer ============
PLUGINSDIR=C:\DOCUME~1\jsmith\LOCALS~1\Temp\nso29E.tmp
detect_all
Parsing cmdline "C:\Software\Wubi-7.10-alpha-rev364.exe" 
DetectProcessorArchitecture
arch=amd64
DetectCD
isvalidcd D:\
isvalidcd E:\
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

---

### Post by rawr2010 on 2007-10-23
I used the Alpha and it loaded fine. Did a great job. Then.....I went to reboot after like 3 hours of having my new Ubuntu up and running only to get to the bootloader and all I have is WinXP and the Ubuntu installer. It tries to reinstall again. Im sure everything is still there somewhere but I don't know if GRUB is working because I don't have the choice of Ubuntu, Ubuntu (safe mode) and Memtest. I think I'm missing part of the chain.

---

### Post by molk on 2007-10-24
I could not replicate this crash on a different system. Also the crash seems to only occur if the folder in which Wubi-7.10-alpha-rev364.exe is located in root and the folder's name is 8 to 9 characters in length. 

VERY STRANGE!!! Given how weird that is and that it's only happening on this one system of mine, it's probably better for you not to spend any further effort in trying to figure this one out. Most likely this issue will magically go away for me with the next revision, given that I did not have it in any of the previous revisions.

---

### Post by ago on 2007-10-24
Does the log always stop at DetectUserProfileName? Do you nave an environment variable USERNAME?

---

### Post by molk on 2007-10-24
Yes, the crash log always stops after DetectUserProfileName when the installer crashes and I do have an environmental variable named USERNAME.

---

### Post by ago on 2007-10-24
Can you try now and post the log?

---

### Post by molk on 2007-10-25
I have attached the Dr. Watson mini-dump for my Wubi-7.10-alpha-rev364.exe crash. The crash seems to happen in system.dll

As I was predicting would happen, 368 is not crashing.

---

### Post by ago on 2007-10-25
If 368 does not crash, case closed

---

### Post by KeatonX on 2008-01-27
Same to me, but with the rev386. 

It installed once, but the language was wrong (I have selected the correct one). As I could not understand anything, I've unistalled it. But when I tried to reinstall using the same executable I have used before it crashes.

The log found on %temp% 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Keaton\CONFIG~1\Temp\nsx22.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Keaton\Desktop\Wubi-7.10-alpha-rev386.exe" 
DetectProcessorArchitecture
arch=i386
DetectCD
isvalidcd G:\
isvalid Ubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016)
 cdinfo=Ubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016) cdversion=7.10 cddistro=Ubuntu cdarch=i386 cdcodename=Gutsy Gibbon cdsubversion=Release 
GetDistroInfo distro=Ubuntu cdarch=i386 arch=i386
success Ubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016)
DetectCD Finished cddrive=G:\
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive E:\ubuntu
isInstallationDrive F:\ubuntu
CheckFreeSpace F:
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
IsBackupFolder E:\
IsBackupFolder F:\
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
UserProfileName=Keaton 

It always stuck on 'UserProfileName='. Any idea? :\

**Edit:** by any weird reason, if I run it in command line as "Wubi-7.10-alpha-rev386 --h" it does not crash.
**Update:** the installation did not finish, it stoped on a screen with the folliowing words:

"BusyBox v.1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) _"

And I cannot figure how it work.
**Update:** well, I think it happens why I just reset on windows boot (i forgot to choose so I reseted. :\)
Now I am uninstalling to reinstall.

And the wubi does not crashes if I run using the command line on windows. (they call msdos prompt or something like this)

---

### Post by ago on 2008-01-28
hmm strange, I cannot replicate that though

---

