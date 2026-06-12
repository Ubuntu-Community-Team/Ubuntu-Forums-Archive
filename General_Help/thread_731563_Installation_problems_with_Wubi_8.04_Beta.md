---
title: "Installation problems with Wubi 8.04 Beta"
date: 2008-03-22
forum: General Help
---

### Post by double051 on 2008-03-22
Hey guys, I just downloaded the new Hardy Beta .iso today and wanted to install it using Wubi. Here's the steps I followed...

1. download and burn Hardy .iso to a CD
2. use Wubi to install Ubuntu to my D: drive with 8GB of space
3. let Wubi generate an install file by gathering info from the CD
4. eject CD as prompted and restart
5. boot into Ubuntu from the Windows boot manager

now from there, i see some text flash and the Ubuntu logo with a loading bar beneath it, but then I come to a command prompt. It says something about "BusyBox (Debian1:1.x.x. Ubuntu??) yadda yadda yadda type help to see list of commands"

(initramfs):_

then it sits and waits for me to give it a command, but at this point I ctrl+alt+delete to restart and boot into windows...

Help?

---

### Post by ago on 2008-03-22
Type 

cat /casper.log

(watch the space)
scroll with shift + pgup and see if there is any error message

---

### Post by double051 on 2008-03-22
Thanks for the help, this is what i get...
```
/init: /init: 1: cannot open /dev/hdd: No medium found
stdin: error 0
/init: /init: 1: cannot open /dev/sbd: No medium found
/init: /init: 1: cannot open /dev/sbd: No medium found
/init: /init: 1: cannot open /dev/sbc: No medium found
/init: /init: 1: cannot open /dev/sbc: No medium found
/init: /init: 1: cannot open /dev/sdd: No medium found
/init: /init: 1: cannot open /dev/sdd: No medium found
/init: /init: 1: cannot open /dev/sde: No medium found
/init: /init: 1: cannot open /dev/sde: No medium found
/init: /init: 1: cannot open /dev/hdc: No medium found
/init: /init: 1: cannot open /dev/hdc: No medium found
/init: /init: 1: cannot open /dev/hdd: No medium found
/init: /init: 1: cannot open /dev/hdd: No medium found
stdin: error 0
/init: /init: 1: cannot open /dev/sbd: No medium found
/init: /init: 1: cannot open /dev/sbd: No medium found
/init: /init: 1: cannot open /dev/sbc: No medium found
/init: /init: 1: cannot open /dev/sbc: No medium found
/init: /init: 1: cannot open /dev/sdd: No medium found
/init: /init: 1: cannot open /dev/sdd: No medium found
/init: /init: 1: cannot open /dev/sde: No medium found
/init: /init: 1: cannot open /dev/sde: No medium found
Unable to find a medium containing a live file system
(initramfs) _
```
that fills up the screen and repeats all the way up several times. Does this help at all?

EDIT: My hard drive is partitioned into a C: and D: drive. Wubi is installing on the D: drive

---

### Post by renegadeshock on 2008-03-22
Hi, I have the same problem as mentioned by* double051*. I have tried installing Ubuntu 8.04 beta Desktop Edition using Wubi and I ended up with the same problem. 

I tried running the log file & here's what I found:

[COLOR="Red"]stdin: I/O error
/init: /init: 1:cannot open /devsdc: No medium found
/init: /init: 1:cannot open /devsdc: No medium found
/init: /init: 1:cannot open /devsdd: No medium found
/init: /init: 1:cannot open /devsdd: No medium found
/init: /init: 1:cannot open /devsde: No medium found
/init: /init: 1:cannot open /devsde: No medium found
/init: /init: 1:cannot open /devsdf: No medium found
/init: /init: 1:cannot open /devsdf: No medium found
/init: /init: 1:cannot open /devscd0: No medium found
/init: /init: 1:cannot open /devscd0: No medium found
Unable to find a medium containing live file system
[/COLOR]

I have installed Wubi through XP. I have a RAID 0 Configuration with a dual boot of XP & Vista.

---

### Post by xecutionx on 2008-03-22
At least I am not on the sinking ship by myself...
> Failed to read last sector (251903997): Invalid Arguement
Perhaps the volume is a RAID/LDM but it wasnt setup yet...
Failed to mount '/dev/sda1': Invalid arguement

Thats just a short bit of the message I get.  Thanks for any help.

---

### Post by ago on 2008-03-22
What filesystem was wubi installed into? Do you have any raid? Looks like wubi fails to mount the windows filesystem (you should also see some errors about mounting /dev/sdaX).

Normally you should be able to mount it manually with something like

mount -t vfat /dev/sda1 /mnt 

or 

mount -t ntfs /dev/sda1 /mnt 

where sda1 is the first partition of the first disk, change to sda2 if you installed on the second partition and so on...

---

### Post by xecutionx on 2008-03-22
No raid here, just a 250GB hdd partitioned about 5 times.  
I'll try it in 20 minutes, and ill post back.  Thanks.

---

### Post by renegadeshock on 2008-03-22
Installed Wubi on NTFS file system. I have a RAID 0 configuration on my Laptop. 

I tried using the command you suggested for manual mount, but it showed some errors saying that you either have a bad hard disk or you have a RAID configured. Activate it & see the dmraid documentation. 

What do you suggest ?  

Thanks

---

### Post by double051 on 2008-03-22
Mine was installed on the second partition of the drive, which is an NTFS partition. Maybe I should try to first partition...

---

### Post by scythe000 on 2008-03-22
I'm having the same problem. 8.04, Windows Vista, raid 0 NTFS.

---

### Post by xecutionx on 2008-03-23
Wait, so theres four of us with the same problem?  Im running Vista, what are you guys running?

---

### Post by darco on 2008-03-23
> **double051 said:**
> Hey guys, I just downloaded the new Hardy Beta .iso today and wanted to install it using Wubi. Here's the steps I followed...

1. download and burn Hardy .iso to a CD
2. use Wubi to install Ubuntu to my D: drive with 8GB of space
3. let Wubi generate an install file by gathering info from the CD
4. eject CD as prompted and restart
5. boot into Ubuntu from the Windows boot manager

now from there, i see some text flash and the Ubuntu logo with a loading bar beneath it, but then I come to a command prompt. It says something about "BusyBox (Debian1:1.x.x. Ubuntu??) yadda yadda yadda type help to see list of commands"

(initramfs):_

then it sits and waits for me to give it a command, but at this point I ctrl+alt+delete to restart and boot into windows...

Help?

I am running Wubi on Vista SP1 X64 (PC) and Vista SP1 x32 (laptop). On the PC I d/l the HH X64 beta .ISO first, d/l Wubi, moved the .ISO to the same folder as Wubi and it installed quick and clean, no issues. Did the same w/my laptop. Not sure if your method is better or worse?

darco

---

### Post by scythe000 on 2008-03-23
Windows Vista 64 bit on an Intel C2D x6800, 4 gigs DDR2 800 RAM, 1TB Raid 0 SATA2, EVGA 780i SLI MCP, 2x nVidia 8800GTXs.

-whew-

---

### Post by Theoforx on 2008-03-23
I have the exact same problem.
Running Vista on an HP Pavillion dv1000

---

### Post by bobby2000 on 2008-03-23
hey... same problem, however im on xp sp2...

---

### Post by ago on 2008-03-23
Seems most of you have raid 0 with ntfs on the partition where wubi was installed.
Is that correct, what type of raid is that exactly? Is it hardware or software?

---

### Post by bobby2000 on 2008-03-23
yup, raid 0, ntfs

---

### Post by scythe000 on 2008-03-23
Hardware.

---

### Post by blake_rateliff on 2008-03-23
having same problem
Windows XP
CPU : AMD  Opteron 165
MB : Abit KN8 SLI
Video Card : Nvidia8800gt
HDD's:
IDE 20GB Windows installation C: 
IDE 200GB Files D:         
SATA 320GB Files G:
No raid on any drives
all single partition drives formatted with NTFS
have run checkdisk on all volumes recently
Wubi installed on G:

---

### Post by renegadeshock on 2008-03-24
it seems to be because of the RAID 0 configuration .....I removed RAID & installed it, it works fine. But now I nstalled it on the first hard disk .....& I formatted the second hard disk into NTFS using the partition editor that comes with Ubuntu Live CD. Now when I try to install Windows XP using a bootable CD it just doesn't recognize the hard drives & the ntfs partition. it just shows unknown device everywhere & a blue screen error pops up.

What could be the problem? how can I install XP as a second OS. I have already installed Ubuntu & now want to install XP on other hard drive. 

Please help

---

### Post by scythe000 on 2008-03-24
That's really a question for a different thread, but the short answer is format with the XP CD, install XP, then install Ubuntu.

---

### Post by double051 on 2008-03-24
So I uninstalled Wubi then reinstalled Wubi 8.04 onto my C: drive and it worked...

---

### Post by scythe000 on 2008-03-24
I've tried three times. No good. Now my Boot managerhas three false Ubuntu entires, and I can't seem to edit them in Vista.

---

### Post by ago on 2008-03-24
Use easybcd to edit vista boot menu "manually"

---

### Post by scythe000 on 2008-03-25
Thanks, ago!

---

### Post by bobby2000 on 2008-03-25
i tried uninstalling wubi and then booting into the disk. when i go to install it just comes up with that kernal again... ideas?

---

### Post by ago on 2008-03-25
> **bobby2000 said:**
> i tried uninstalling wubi and then booting into the disk. when i go to install it just comes up with that kernal again... ideas?

Sorry didn't understand what is happening can you please expand a bit?

---

### Post by bobby2000 on 2008-03-26
i get this is i either install wubi or boot from the disk : 

unable to read config index 0 descriptor /all

usb 3-3 : can't read configurations erro -110

---

### Post by ago on 2008-03-26
Can you try with usb devices unplugged?

---

### Post by bobby2000 on 2008-03-26
some things i need plugged in (ie mouse and keyboard)... should i unplug wireless and external hard drive?

---

### Post by ago on 2008-03-26
You might want to try that since the rest of the installation is non-interactive

---

### Post by bobby2000 on 2008-03-26
ok. tried again.. no matter how i try to install, i click install, it says "loading kernel"... then the ubuntu boot screen runs, and the kernal opens saying something about busybox... type help for list of commands.


ideas?

---

### Post by ago on 2008-03-26
at the busybox run

cat /casper.log

scroll with shift+gup, see if there is any relevant error

---

### Post by ago on 2008-03-26
> **ago said:**
> Seems most of you have raid 0 with ntfs on the partition where wubi was installed.
Is that correct, what type of raid is that exactly? Is it hardware or software?

I can confirm that fakeraid is not supported at the moment and it is unlikely to be supported for 8.04. The only workaround is to install on a partition which is not on fakeraid.

---

### Post by scythe000 on 2008-03-26
What about actual raid?

---

### Post by ago on 2008-03-27
What is exactly your raid configuration?
EVGA 780i SLI MCP?

---

### Post by bobby2000 on 2008-03-27
the errors coming up are generally dev /sdf and dev/sde     no medium found.

---

### Post by scythe000 on 2008-03-27
> **ago said:**
> What is exactly your raid configuration?
EVGA 780i SLI MCP?

Hardware, 2x500gb Seagates, Striped (Raid 0).
Raid disc is drive 0, C:, which has windowsan Wubi.
Only other drive is D:, a 750gb WD drive.

---

### Post by ago on 2008-03-27
> **bobby2000 said:**
> the errors coming up are generally dev /sdf and dev/sde     no medium found.

Look into /casper.log there should be some errors about mounting /dev/sda or /dev/sdb (first and second disk)
use "cat" or "more" to see the content of the file, shift+pgup to scroll

---

### Post by bobby2000 on 2008-03-27
stdin: error 0
/init: /init: 1: Cannont open /dev/sdb: No such file
stdin: error 0
/init: /init: 1: cannont open /dev/sdd : No medium found

Unable to find live filesystem

---

### Post by ago on 2008-03-27
grep sda /casper.log

---

### Post by bobby2000 on 2008-03-27
i tried typing this is but it did nothing

---

### Post by ago on 2008-03-27
do you see a file /casper.log?
there are 2 white spaces in the command above

---

### Post by bobby2000 on 2008-03-27
that file does not come up

---

### Post by ago on 2008-03-27
Does the error happen immediately after rebooting from windows or after second reboot (after linux side installation)?

---

### Post by ago on 2008-03-27
> **scythe000 said:**
> Hardware, 2x500gb Seagates, Striped (Raid 0).
Raid disc is drive 0, C:, which has windowsan Wubi.
Only other drive is D:, a 750gb WD drive.

Looks like you are also on fakeraid...

---

### Post by vinicri on 2008-03-27
hi. I have 1 disk and 3 partitions. So I changed the first line to (hd0,2)/ubuntu/disks. Now it says that an error 42 occurred. 

error 42: an device name should not be used on the file path.

edit: I forgot to say that error 15 was occurring before.

---

### Post by ago on 2008-03-27
If you have only one disk there should be no need to changed (hdX,Y). What was the original value by the way?

---

### Post by vinicri on 2008-03-27
I'll check in a moment, but it was a directory that didnt exist, something with linuz (not linux) in the end. My wubi is the latest, i downloaded yesterday.

---

### Post by vinicri on 2008-03-27
And I  trying to install kubuntu with kde4

---

### Post by ago on 2008-03-27
vmlinuz is ok, that is the name of the linux kernel

---

### Post by vinicri on 2008-03-27
that what is on the normal mode option

find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz boot=casper debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/hardy-desktop-i386.iso quiet splash ro automatic-ubiquity locale=en_AU.UTF-8 noprompt --  
initrd /ubuntu/install/boot/initrd.gz
boot

---

### Post by ago on 2008-03-27
looks ok to me, do you have /ubuntu/install/boot/vmlinuz?

---

### Post by vinicri on 2008-03-27
no, the only folder in boot is grub and inside it there's a menu file. there's nothing more.

---

### Post by ago on 2008-03-27
There should be a log in %temp% (user temp folder)
can you pls attach it here?

Are you looking into

/ubuntu/disks/boot

or 

/ubuntu/install/boot?

---

### Post by bobby2000 on 2008-03-28
i get the errors as soon as i choose to install ubuntu through the live CD menu, of when i try to boot into it after installing wubi

---

### Post by ago on 2008-03-28
> **bobby2000 said:**
> i get the errors as soon as i choose to install ubuntu through the live CD menu
What happens in this case?

---

### Post by vinicri on 2008-03-28
I was looking at install folder.

But in \ubuntu\disks\boot\grub there is only this folder grub and no file.

Here is the log. 

> ============ Installer ============
PLUGINSDIR=C:\DOCUME~1\VINICIUS\LOCALS~1\Temp\nst181.tmp
detect_all
Parsing cmdline "D:\Wubi-8.04-beta-rev457.exe" 
debug=, 32bit=, cdboot=
arch=amd64
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD N:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in D: is 5920
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=-3
Country=BR
Locale=en_AU.UTF-8
TimeZone=America/Fortaleza
Domain=localdomain
HostName=Liu-Kang
ComputerName=LIU-KANG
EnvUsername=Vinícius
UserDomain=LIU-KANG
UserInfoName=Vinícius
UserProfileFolder=C:\Documents and Settings\Vinícius
UserProfileName=Vinícius 
ShowMainPage
Making drive list
Drive & Path name 1734; Volume name ACER; Max #/chars in vol name 1809288; Volume Serial # 160319913; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Skipping drive C:, not enough free space 417 <= {MinSizeMB}
Drive & Path name 1734; Volume name ACERDATA; Max #/chars in vol name 1809292; Volume Serial # -1609602538; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Adding drive D:
Drive list = D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 4
PopulateDistroList
DetectIso
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\VINICIUS\LOCALS~1\Temp\nst181.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\VINICIUS\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid Kubuntu-KDE4 8.04 "Hardy Heron" - Beta i386 (20080318.2)
      cdversion=8.04 cddistro=Kubuntu-KDE4 cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrfullname=Kubuntu-KDE4-i386 distro= cddistro=Kubuntu-KDE4 cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/kubuntu-kde4-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Kubuntu-KDE4 8.04 "Hardy Heron" - Beta i386 (20080318.2)
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
      GetDistroInfo distrfullname=Kubuntu-KDE4-i386 distro=Kubuntu-KDE4 cddistro=Kubuntu-KDE4 cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/kubuntu-kde4-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Kubuntu-KDE4
Changing icon to Kubuntu-KDE4.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_AU.UTF-8
      GetDistroInfo distrfullname=Kubuntu-KDE4-i386 distro=Kubuntu-KDE4 cddistro=Kubuntu-KDE4 cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/kubuntu-kde4-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created D:\ubuntu\Uninstall.exe
Created C:\WINDOWS\Uninstall.exe
Created reg key 1
Created reg key 2
CopyDistFolders
GetIso
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD N:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\VINICIUS\LOCALS~1\Temp\nst181.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\VINICIUS\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid Kubuntu-KDE4 8.04 "Hardy Heron" - Beta i386 (20080318.2)
      cdversion=8.04 cddistro=Kubuntu-KDE4 cdarch=i386 cdcodename=Hardy Heron cdsubversion=Beta 
      GetDistroInfo distrfullname=Kubuntu-KDE4-i386 distro=Kubuntu-KDE4 cddistro=Kubuntu-KDE4 cdarch=i386 arch=amd64
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/kubuntu-kde4-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Kubuntu-KDE4 8.04 "Hardy Heron" - Beta i386 (20080318.2)
Using D:\ubuntu-backup\hardy-desktop-i386.iso
Checking/Downloading Kubuntu-KDE4-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://wubi-installer.org/metalinks/8.04-final/kubuntu-kde4-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04-final/kubuntu-kde4-desktop-i386.iso.metalink)
get_md5 [http://wubi-installer.org/metalinks/8.04-final/kubuntu-kde4-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04-final/kubuntu-kde4-desktop-i386.iso.metalink)
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg md5=
Download status=The requested URL returned error: 404
Error downloading [http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg](http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg), The req
Trying remote metalink2: [http://wubi-installer.org/metalinks/8.04/kubuntu-kde4-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04/kubuntu-kde4-desktop-i386.iso.metalink)
get_md5 [http://wubi-installer.org/metalinks/8.04/kubuntu-kde4-desktop-i386.iso.metalink](http://wubi-installer.org/metalinks/8.04/kubuntu-kde4-desktop-i386.iso.metalink)
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:D:\ubuntu\install\MD5SUMS
      Verifying signature D:\ubuntu\install\MD5SUMS.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 03/26/08 20:17:02 E. South America Standard Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS
Found md5 71246645235529fd783751ff2e7c4c1b
Downloading: trymefirst=D:\ubuntu-backup\hardy-desktop-i386.iso url=http://wubi-installer.org/metalinks/8.04/kubuntu-kde4-desktop-i386.iso.metalink md5=71246645235529fd783751ff2e7c4c1b
Download status=success:D:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=D:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from D:\ubuntu\install\hardy-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name D:\ubuntu\install\hardy-desktop-i386.iso; Volume name ACERDATA; Max #/chars in vol name ; Volume Serial # -1609602538; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size D:
rootSize=3800 homesize=0, swapsize=200, usrsize=0
Drive & Path name D:\ubuntu\install\hardy-desktop-i386.iso; Volume name ACERDATA; Max #/chars in vol name ; Volume Serial # -1609602538; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size D:
rootSize=3800 homesize=0, swapsize=200, usrsize=0
AllocFile filename=D:\ubuntu\disks\root.disk size=3800
AllocFile filename=D:\ubuntu\disks\home.disk size=0
AllocFile filename=D:\ubuntu\disks\swap.disk size=200
UncompressFilesAfterInstall
Installation completed successfully!

---

### Post by ago on 2008-03-28
Log is fine and it is normal that /ubuntu/disks/boot is empty since that gets filled after reboot.

---

### Post by vinicri on 2008-03-28
why am I getting error 15? do you have an suggestion?

thanks

---

### Post by bobby2000 on 2008-03-28
right.. i boot into the live cd as tho im going to install it.. the kernal loads.. so i put in the grep sda /casper.log and it does nothing

---

### Post by ago on 2008-03-28
> **bobby2000 said:**
> right.. i boot into the live cd as tho im going to install it.. the kernal loads.. so i put in the grep sda /casper.log and it does nothing

try
grep mount /casper.log

---

### Post by bobby2000 on 2008-03-28
still - nothing happens

---

### Post by ago on 2008-03-28
try to mount your windows partition and copy over casper.log, then pls attach it here

---

### Post by bobby2000 on 2008-03-28
where would i find the casper.log as i have not managed to install ubuntu

---

### Post by ago on 2008-03-28
> **bobby2000 said:**
> where would i find the casper.log as i have not managed to install ubuntu

That is produced by the boot process whenever you boot off c:\ubuntu\install\boot\
And it is in /casper.log accessible after you get to the busybox command prompt within Linux

You can also try to press esc at boot and select verbose mode

---

### Post by bobby2000 on 2008-03-28
that didnt work...

---

### Post by MolsonH on 2008-03-30
So I am getting the same situation here, but i'm getting a somewhat different error.
stdin: error 0
/init: /init: 1: cannot open /dev/scd0: no medium found
is it looking for a CD? I don't know much about Linux, this was going to be my first attempt and it doesn't seem to be going very well :P
Thanks

---

### Post by scheng924 on 2008-03-31
hmmm the computer I have ubuntu on doesn't even have windows... it only has one hard drive and this drive is dedicated to ubuntu.. 7.1 was fine but i'm having the same issue as you guys..
the busybox v1.1.3 stuff

worst part is.. i can't even type... none of my USB devices are on... i have a USB keyboard/mouse :(

---

### Post by airjer on 2008-04-17
I'm getting the same BusyBox msg after the Ubuntu logo screen. I do not have raid configured nor fakeraid, but still seem to get this msg along with a few revalidation failed msgs before it appears. Using Vista x64... any help would be appreciated.

---

### Post by ago on 2008-04-17
See if any of that helps: [https://wiki.ubuntu.com/WubiGuide#head-a2f73efbce9a94cf460a095713c599594c3a05d1](https://wiki.ubuntu.com/WubiGuide#head-a2f73efbce9a94cf460a095713c599594c3a05d1)

Otherwise report the exact message, and the content of 

cat /proc/cmdline
tail /casper.log

---

### Post by ringostar on 2008-04-17
I give my feedback

I have runed wubi rev487 on an intel 64 bits PC Dell Optiplex 320
It didnt worked on the first boot, I had a *Kernel Alive , Kernel direct mapping to xxxx* and nothing more
then I tried with another grub option ( somethinhg with ACPI...) and it worked.

---

### Post by airjer on 2008-04-17
> **ago said:**
> See if any of that helps: [https://wiki.ubuntu.com/WubiGuide#head-a2f73efbce9a94cf460a095713c599594c3a05d1](https://wiki.ubuntu.com/WubiGuide#head-a2f73efbce9a94cf460a095713c599594c3a05d1)

Otherwise report the exact message, and the content of 

cat /proc/cmdline
tail /casper.log

The message before the BusyBox prompt comes up is:

ata4: failed to recover some devices, retrying in 5 seconds

Messages prior to this are pretty much the same just for ata3.01/.0

I can't really give you the contents of the commands you provided because commands continue to scroll not allowing enough time for me to write them down. The casper.log had listed something about not being able to find a live file system though?

Here's my Wubi log in the %temp% folder.

```
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsz916A.tmp
detect_all
Parsing cmdline "C:\Users\da.m4nn\Desktop\Wubi-8.04-beta-rev490.exe" 
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
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 6069448; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 6069460; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 6069468; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 5485080; Volume name ; Max #/chars in vol name 40; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 37291
DetectBackupFolder
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
Existing installation detected, calling old uninstaller and quitting.
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nskEB23.tmp
detect_all
Parsing cmdline "C:\Users\da.m4nn\Desktop\Wubi-8.04-beta-rev490.exe" 
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
Drive & Path name 1711; Volume name ; Max #/chars in vol name 6751992; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 6752004; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 6752012; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6256384; Volume name ; Max #/chars in vol name 39; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 52299
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
Drive & Path name 1773; Volume name ; Max #/chars in vol name 6889448; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem F:
Drive & Path name 1773; Volume name Data; Max #/chars in vol name 6889460; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Adding drive F:
IsValidFileSystem H:
Drive & Path name 1773; Volume name Games; Max #/chars in vol name 6889468; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
Adding drive H:
Drive list = C:|F:|H:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\hardy-desktop-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nskEB23.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-amd64.iso
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
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nskEB23.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-amd64.iso
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
No file C:\ubuntu\install\hardy-desktop-amd64.iso
Could not retrieve some essential files
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsr8792.tmp
detect_all
Parsing cmdline "C:\Users\da.m4nn\Desktop\Wubi-8.04-beta-rev490.exe" 
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
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 3238664; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 3238676; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 3238684; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2669720; Volume name ; Max #/chars in vol name 39; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 52297
DetectBackupFolder
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
Drive & Path name 1773; Volume name ; Max #/chars in vol name 3411944; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem F:
Drive & Path name 1773; Volume name Data; Max #/chars in vol name 3411956; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Adding drive F:
IsValidFileSystem H:
Drive & Path name 1773; Volume name Games; Max #/chars in vol name 3411964; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
Adding drive H:
Drive list = C:|F:|H:
ChangeInstallationDrive to C:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\ubuntu-7.10-desktop-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsr8792.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\ubuntu-7.10-desktop-amd64.iso
      IsValid Ubuntu 7.10 "Gutsy Gibbon" - Release amd64 (20071016)
      cdversion=7.10 cddistro=Ubuntu cdarch=amd64 cdcodename=Gutsy Gibbon cdsubversion=Release cdbuild=20071016 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different version 8.04 != 7.10
CDInfo cleared
      IsValidIso ispoath=C:\Users\da.m4nn\Desktop\hardy-desktop-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsr8792.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\Users\da.m4nn\Desktop\hardy-desktop-amd64.iso
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
      IsValidIso ispoath=C:\ubuntu-backup\ubuntu-7.10-desktop-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsr8792.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\ubuntu-7.10-desktop-amd64.iso
      IsValid Ubuntu 7.10 "Gutsy Gibbon" - Release amd64 (20071016)
      cdversion=7.10 cddistro=Ubuntu cdarch=amd64 cdcodename=Gutsy Gibbon cdsubversion=Release cdbuild=20071016 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different version 8.04 != 7.10
CDInfo cleared
      IsValidIso ispoath=C:\Users\da.m4nn\Desktop\hardy-desktop-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsr8792.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\Users\da.m4nn\Desktop\hardy-desktop-amd64.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Release Candidate amd64 (20080417)
      cdversion=8.04 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release Candidate cdbuild=20080417 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release Candidate amd64 (20080417)
Copying C:\Users\da.m4nn\Desktop\hardy-desktop-amd64.iso -> C:\ubuntu\install\hardy-desktop-amd64.iso
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
Using C:\ubuntu\install\hardy-desktop-amd64.iso but skipping checksum since no metalink file could be found
ISO file hardy-desktop-amd64.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\hardy-desktop-amd64.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\hardy-desktop-amd64.iso
UncompressFilesPriorInstall
Drive & Path name d; Volume name ; Max #/chars in vol name ; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsr8792.tmp\wubibcd.exe 
 1:0 
 2:Employing Vista x64 sysnative workaround.
Operation completed successfully. New ID is {dc0245c4-0ac9-11dd-b663-00508db55b7b}
 
 3:HDD 
 4:3
vistaBootDriveCode = {dc0245c4-0ac9-11dd-b663-00508db55b7b} <=> peration completed successfully. New I
vistaBootDriveCode {dc0245c4-0ac9-11dd-b663-00508db55b7b}
Drive & Path name /Users/da.m4nn; Volume name ; Max #/chars in vol name d; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
UncompressFilesAfterInstall
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsq71C1.tmp
detect_all
Parsing cmdline "C:\Users\da.m4nn\Desktop\Wubi-8.04-beta-rev490.exe" 
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
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 3712960; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 3712972; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 3712980; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 3191944; Volume name ; Max #/chars in vol name 30; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 37224
DetectBackupFolder
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
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsb74BE.tmp
un.install
un.BackupIso
Backup C:\ubuntu\install\hardy-desktop-amd64.iso
un.CleanBcd
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive F:\
un.CleanThisDrive H:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsvEE20.tmp
detect_all
Parsing cmdline "C:\ubuntu-backup\Wubi-8.04-beta-rev490.exe" 
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
Drive & Path name 1711; Volume name ; Max #/chars in vol name 3803456; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 3803468; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 3803476; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 3322416; Volume name ; Max #/chars in vol name 39; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 52208
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
Drive & Path name 1773; Volume name ; Max #/chars in vol name 3970536; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem F:
Drive & Path name 1773; Volume name Data; Max #/chars in vol name 3970548; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Adding drive F:
IsValidFileSystem H:
Drive & Path name 1773; Volume name Games; Max #/chars in vol name 3970556; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
Adding drive H:
Drive list = C:|F:|H:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\hardy-desktop-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsvEE20.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-amd64.iso
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
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsvEE20.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-amd64.iso
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
C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsvEE20.tmp\wubibcd.exe 
 1:0 
 2:Employing Vista x64 sysnative workaround.
Operation completed successfully. New ID is {dc0245c5-0ac9-11dd-b663-00508db55b7b}
 
 3:HDD 
 4:3
vistaBootDriveCode = {dc0245c5-0ac9-11dd-b663-00508db55b7b} <=> peration completed successfully. New I
vistaBootDriveCode {dc0245c5-0ac9-11dd-b663-00508db55b7b}
Drive & Path name /Users/da.m4nn; Volume name ; Max #/chars in vol name d; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
UncompressFilesAfterInstall
Installation completed successfully!
============ Uninstaller ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsg3FF3.tmp
un.install
un.BackupIso
Backup C:\ubuntu\install\hardy-desktop-amd64.iso
un.CleanBcd
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive F:\
un.CleanThisDrive H:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nspC1BA.tmp
detect_all
Parsing cmdline "C:\ubuntu-backup\Wubi-8.04-beta-rev490.exe" 
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
Drive & Path name 1711; Volume name ; Max #/chars in vol name 6281720; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 6281732; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 6281740; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 5751360; Volume name ; Max #/chars in vol name 40; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 52206
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
Drive & Path name 1773; Volume name ; Max #/chars in vol name 6445384; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem F:
Drive & Path name 1773; Volume name Data; Max #/chars in vol name 6445396; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Adding drive F:
IsValidFileSystem H:
Drive & Path name 1773; Volume name Games; Max #/chars in vol name 6445404; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
Adding drive H:
Drive list = C:|F:|H:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\hardy-desktop-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nspC1BA.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-amd64.iso
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
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nspC1BA.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-amd64.iso
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
C:\Users\DAE508~1.M4N\AppData\Local\Temp\nspC1BA.tmp\wubibcd.exe 
 1:0 
 2:Employing Vista x64 sysnative workaround.
Operation completed successfully. New ID is {dc0245c6-0ac9-11dd-b663-00508db55b7b}
 
 3:HDD 
 4:3
vistaBootDriveCode = {dc0245c6-0ac9-11dd-b663-00508db55b7b} <=> peration completed successfully. New I
vistaBootDriveCode {dc0245c6-0ac9-11dd-b663-00508db55b7b}
Drive & Path name /Users/da.m4nn; Volume name ; Max #/chars in vol name d; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
UncompressFilesAfterInstall
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsxF81C.tmp
detect_all
Parsing cmdline "C:\ubuntu-backup\Wubi-8.04-beta-rev490.exe" 
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
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 2847288; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 2847300; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 2847308; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2535944; Volume name ; Max #/chars in vol name 27; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 38232
DetectBackupFolder
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
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsyFA8D.tmp
un.install
un.BackupIso
Backup C:\ubuntu\install\hardy-desktop-amd64.iso
un.CleanBcd
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive F:\
un.CleanThisDrive H:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsk8AB7.tmp
detect_all
Parsing cmdline "C:\ubuntu-backup\Wubi-8.04-beta-rev490.exe" 
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
Drive & Path name 1711; Volume name ; Max #/chars in vol name 6094816; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 6094828; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 6094836; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 5550640; Volume name ; Max #/chars in vol name 33; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 52237
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
Drive & Path name 1773; Volume name ; Max #/chars in vol name 6214432; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem F:
Drive & Path name 1773; Volume name Data; Max #/chars in vol name 6214444; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Adding drive F:
IsValidFileSystem H:
Drive & Path name 1773; Volume name Games; Max #/chars in vol name 6214452; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
Adding drive H:
Drive list = C:|F:|H:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\hardy-desktop-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsk8AB7.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-amd64.iso
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
ChangeInstallationDrive to H:
ChangeInstallationSize to 15
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created H:\ubuntu\Uninstall-Ubuntu.exe
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
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsk8AB7.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-amd64.iso
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
CopyKernel isokernel=casper\vmlinuz, iso=H:\ubuntu\install\hardy-desktop-amd64.iso, cddrive=
Extracting with 7z kernel/initrd from H:\ubuntu\install\hardy-desktop-amd64.iso
UncompressFilesPriorInstall
Drive & Path name d; Volume name Games; Max #/chars in vol name ; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 
Drive H: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsk8AB7.tmp\wubibcd.exe 
 1:0 
 2:Employing Vista x64 sysnative workaround.
Operation completed successfully. New ID is {dc0245c7-0ac9-11dd-b663-00508db55b7b}
 
 3:HDD 
 4:3
vistaBootDriveCode = {dc0245c7-0ac9-11dd-b663-00508db55b7b} <=> peration completed successfully. New I
vistaBootDriveCode {dc0245c7-0ac9-11dd-b663-00508db55b7b}
Drive & Path name /Users/da.m4nn; Volume name Games; Max #/chars in vol name d; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive H: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=H:\ubuntu\disks\root.disk size=14000
AllocFile filename=H:\ubuntu\disks\home.disk size=0
AllocFile filename=H:\ubuntu\disks\swap.disk size=1000
UncompressFilesAfterInstall
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsb4C86.tmp
detect_all
Parsing cmdline "C:\ubuntu-backup\Wubi-8.04-beta-rev490.exe" 
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
Found InstallationDrive H:\ubuntu
AlreadyInstalled=true OldInstallationDrive=H: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 50308304; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 50308316; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 50308324; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6584824; Volume name ; Max #/chars in vol name 30; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 52936
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
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsx4F74.tmp
un.install
un.BackupIso
Backup H:\ubuntu\install\hardy-desktop-amd64.iso
un.CleanBcd
un.RemoveInstallationFolder H:\ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive F:\
un.CleanThisDrive H:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsl4CC4.tmp
detect_all
Parsing cmdline "C:\ubuntu-backup\Wubi-8.04-beta-rev490.exe" 
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
Drive & Path name 1711; Volume name ; Max #/chars in vol name 2585784; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 2585796; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 2585804; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2519568; Volume name ; Max #/chars in vol name 28; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 51191
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
Drive & Path name 1773; Volume name ; Max #/chars in vol name 3202936; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem F:
Drive & Path name 1773; Volume name Data; Max #/chars in vol name 3202948; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Adding drive F:
IsValidFileSystem H:
Drive & Path name 1773; Volume name Games; Max #/chars in vol name 3202956; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
Adding drive H:
Drive list = C:|F:|H:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\ubuntu-8.04-beta-alternate-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsl4CC4.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\ubuntu-8.04-beta-alternate-amd64.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta amd64 (20080318.1)
      cdversion=8.04 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Beta cdbuild=20080318.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta amd64 (20080318.1)
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
      IsValidIso ispoath=C:\ubuntu-backup\ubuntu-8.04-beta-alternate-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsl4CC4.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\ubuntu-8.04-beta-alternate-amd64.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta amd64 (20080318.1)
      cdversion=8.04 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Beta cdbuild=20080318.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta amd64 (20080318.1)
Using C:\ubuntu-backup\ubuntu-8.04-beta-alternate-amd64.iso
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
Using C:\ubuntu-backup\ubuntu-8.04-beta-alternate-amd64.iso but skipping checksum since no metalink file could be found
ISO file ubuntu-8.04-beta-alternate-amd64.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\ubuntu-8.04-beta-alternate-amd64.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\ubuntu-8.04-beta-alternate-amd64.iso
UncompressFilesPriorInstall
Drive & Path name d; Volume name ; Max #/chars in vol name ; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsl4CC4.tmp\wubibcd.exe 
 1:0 
 2:Employing Vista x64 sysnative workaround.
Operation completed successfully. New ID is {dc0245c8-0ac9-11dd-b663-00508db55b7b}
 
 3:HDD 
 4:3
vistaBootDriveCode = {dc0245c8-0ac9-11dd-b663-00508db55b7b} <=> peration completed successfully. New I
vistaBootDriveCode {dc0245c8-0ac9-11dd-b663-00508db55b7b}
Drive & Path name /Users/da.m4nn; Volume name ; Max #/chars in vol name d; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
UncompressFilesAfterInstall
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsvD8EC.tmp
detect_all
Parsing cmdline "C:\ubuntu-backup\Wubi-8.04-beta-rev490.exe" 
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
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 6631640; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 6631652; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 6631660; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6578392; Volume name ; Max #/chars in vol name 26; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 36892
DetectBackupFolder
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
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsbDB7C.tmp
un.install
un.BackupIso
Backup C:\ubuntu\install\ubuntu-8.04-beta-alternate-amd64.iso
un.CleanBcd
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive F:\
un.CleanThisDrive H:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsa4C37.tmp
detect_all
Parsing cmdline "C:\ubuntu-backup\Wubi-8.04-beta-rev490.exe" 
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
Drive & Path name 1711; Volume name ; Max #/chars in vol name 3635936; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 3635948; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 3635956; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 3191344; Volume name ; Max #/chars in vol name 29; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 51192
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
Drive & Path name 1773; Volume name ; Max #/chars in vol name 41901480; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem F:
Drive & Path name 1773; Volume name Data; Max #/chars in vol name 41901492; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Adding drive F:
IsValidFileSystem H:
Drive & Path name 1773; Volume name Games; Max #/chars in vol name 41901500; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
Adding drive H:
Drive list = C:|F:|H:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\ubuntu-8.04-beta-alternate-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsa4C37.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\ubuntu-8.04-beta-alternate-amd64.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta amd64 (20080318.1)
      cdversion=8.04 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Beta cdbuild=20080318.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta amd64 (20080318.1)
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
      IsValidIso ispoath=C:\ubuntu-backup\ubuntu-8.04-beta-alternate-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsa4C37.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\ubuntu-8.04-beta-alternate-amd64.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Beta amd64 (20080318.1)
      cdversion=8.04 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Beta cdbuild=20080318.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Beta amd64 (20080318.1)
Using C:\ubuntu-backup\ubuntu-8.04-beta-alternate-amd64.iso
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
Using C:\ubuntu-backup\ubuntu-8.04-beta-alternate-amd64.iso but skipping checksum since no metalink file could be found
ISO file ubuntu-8.04-beta-alternate-amd64.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\ubuntu-8.04-beta-alternate-amd64.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\ubuntu-8.04-beta-alternate-amd64.iso
UncompressFilesPriorInstall
Drive & Path name d; Volume name ; Max #/chars in vol name ; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsa4C37.tmp\wubibcd.exe 
 1:0 
 2:Employing Vista x64 sysnative workaround.
Operation completed successfully. New ID is {dc0245c9-0ac9-11dd-b663-00508db55b7b}
 
 3:HDD 
 4:3
vistaBootDriveCode = {dc0245c9-0ac9-11dd-b663-00508db55b7b} <=> peration completed successfully. New I
vistaBootDriveCode {dc0245c9-0ac9-11dd-b663-00508db55b7b}
Drive & Path name /Users/da.m4nn; Volume name ; Max #/chars in vol name d; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
UncompressFilesAfterInstall
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nslF0A0.tmp
detect_all
Parsing cmdline "C:\ubuntu-backup\Wubi-8.04-beta-rev490.exe" 
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
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 10050984; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 10050996; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 10051004; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 9269800; Volume name ; Max #/chars in vol name 37; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 36878
DetectBackupFolder
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
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nscF285.tmp
un.install
un.BackupIso
Backup C:\ubuntu\install\ubuntu-8.04-beta-alternate-amd64.iso
un.CleanBcd
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive F:\
un.CleanThisDrive H:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Installer ============
PLUGINSDIR=C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsg6249.tmp
detect_all
Parsing cmdline "C:\ubuntu-backup\Wubi-8.04-beta-rev490.exe" 
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
Drive & Path name 1711; Volume name ; Max #/chars in vol name 9882080; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem F:
Drive & Path name 1711; Volume name Data; Max #/chars in vol name 9882092; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
IsValidFileSystem H:
Drive & Path name 1711; Volume name Games; Max #/chars in vol name 9882100; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 9286184; Volume name ; Max #/chars in vol name 36; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 51198
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
Drive & Path name 1773; Volume name ; Max #/chars in vol name 9889304; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem F:
Drive & Path name 1773; Volume name Data; Max #/chars in vol name 9889316; Volume Serial # -596758248; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Adding drive F:
IsValidFileSystem H:
Drive & Path name 1773; Volume name Games; Max #/chars in vol name 9889324; Volume Serial # 1048998856; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive H: has valid filesystem NTFS
Adding drive H:
Drive list = C:|F:|H:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\ubuntu-backup\hardy-desktop-amd64.iso
      ExtractIsoInfo
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsg6249.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-amd64.iso
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
      C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsg6249.tmp\7z.exe e -y -i!.disk\info -oC:\Users\DAE508~1.M4N\AppData\Local\Temp C:\ubuntu-backup\hardy-desktop-amd64.iso
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
C:\Users\DAE508~1.M4N\AppData\Local\Temp\nsg6249.tmp\wubibcd.exe 
 1:0 
 2:Employing Vista x64 sysnative workaround.
Operation completed successfully. New ID is {dc0245ca-0ac9-11dd-b663-00508db55b7b}
 
 3:HDD 
 4:3
vistaBootDriveCode = {dc0245ca-0ac9-11dd-b663-00508db55b7b} <=> peration completed successfully. New I
vistaBootDriveCode {dc0245ca-0ac9-11dd-b663-00508db55b7b}
Drive & Path name /Users/da.m4nn; Volume name ; Max #/chars in vol name d; Volume Serial # 206859459; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
UncompressFilesAfterInstall
Installation completed successfully!

```

Just realized that the contents of the log are for every install... as you can see I've been trying quite a few times to get this working, haha.

---

### Post by airjer on 2008-04-19
No clue?

---

### Post by Stench on 2008-05-08
Was there ever a solution for this?

I have a hardware raid, and I am getting these errors.  Same on two different computers both with hardware raids.

Did anyone come up with a solution to get this to boot into Ubuntu?

Thanks.

---

### Post by airjer on 2008-05-09
> **Stench said:**
> Was there ever a solution for this?

I have a hardware raid, and I am getting these errors.  Same on two different computers both with hardware raids.

Did anyone come up with a solution to get this to boot into Ubuntu?

Thanks.

Try hitting the esc button when booting to enter the menu. Hit 'e' to edit the first line. Scroll down to the second line and hit 'e' again. Input 'irqpoll' at the end of the line. Hit enter and then press 'b' to boot. See if that helps.

---

### Post by scythe000 on 2008-05-09
> **Stench said:**
> Was there ever a solution for this?

I have a hardware raid, and I am getting these errors.  Same on two different computers both with hardware raids.

Did anyone come up with a solution to get this to boot into Ubuntu?

Thanks.

I never did. I finally installed Ubuntu via Wubi onto a single drive. I still wound up having to edit the grub file by hand. Wubi is not yet ready for showtime.

---

### Post by ago on 2008-05-09
Software raids are not supported. Many so called "hardware raids", are in fact software ones.
Multiple disks will be properly supported in the point release in July (still no software raids until 8.10 though).

---

