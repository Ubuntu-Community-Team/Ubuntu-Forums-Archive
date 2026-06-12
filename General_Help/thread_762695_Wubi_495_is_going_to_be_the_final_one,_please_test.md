---
title: "Wubi 495 is going to be the final one, please test it!"
date: 2008-04-22
forum: General Help
---

### Post by ago on 2008-04-22
Please test it and report any issue immediately!

You can get it from wubi-installer.org

1. uninstall any previous wubi installation, delete \ubuntu-backup
2. download wubi 495 [http://wubi-installer.org/latest.php](http://wubi-installer.org/latest.php) and let it download the ISO for you
3. reboot and install normally

More point if you can also test installation off a CD. You can use Daemon Tools or similar to emulate a CD device without actually burning the ISO.

We also have rev 500 here [http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev500.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev500.exe) . This will not go on the CD, but it is a candidate for the website. The main advantage is that the md5 checksum algorithm is far faster and the whole installation takes about half the time (excluding download time). Please test that too.

---

### Post by ago on 2008-04-22
When you use rev 495, please replace C:\ubuntu\install\initrd.gz with [http://people.ubuntu.com/~cjwatson/tmp/initrd-lupin-fix.gz](http://people.ubuntu.com/~cjwatson/tmp/initrd-lupin-fix.gz) (i386 only!!! skip this step if you are using the amd64 ISO). Do this BEFORE rebooting

---

### Post by ago on 2008-04-22
Please also test it with a Ubuntu 8.04 Release Candidate i386 Desktop CD in the tray!

[http://releases.ubuntu.com/8.04/ubuntu-8.04-rc-desktop-i386.iso](http://releases.ubuntu.com/8.04/ubuntu-8.04-rc-desktop-i386.iso)

---

### Post by flamelab on 2008-04-22
What about the amd64 ISO ?

Till now , I have been facing problems after the installation.

I think I have already posted a photo .

The problem was about a tty loop problem . The system would'nt log in.

---

### Post by ago on 2008-04-22
If the issue was due to X failing it is out of my domain (but would like to know nevertheless).
Could you be so kind to try with latest daily builds and report any issue? Skip the initrd replacement step if you use amd64 ISOs.

---

### Post by flamelab on 2008-04-22
> **ago said:**
> If the issue was due to X failing it is out of my domain (but would like to know nevertheless).
Could you be so kind to try with latest daily builds and report any issue? Skip the initrd replacement step if you use amd64 ISOs.

&#925;&#959; &#935; problem (I saw the xorg log), tty (console user) issue though.

Really strange, because I had a native (real partition) installation done a week ago (on the same PC, with Core2Duo with Intel64) and everything went great.

If that happens again, I'll inform you .

I'm now downloading x86 and x86_64 .


The whole reason for that bugtesting is that I'm maintaining an Ubuntu tutorial in Greece , that helps installing the distro via Wubi. I haven't updated it yet because there were those strange problems on amd64 installation.


P.S. Can I use as swap an already existing swap (1 GB) partition in my laptop ?

---

### Post by ago on 2008-04-22
> **flamelab said:**
> 
If that happens again, I'll inform you .
please

> P.S. Can I use as swap an already existing swap (1 GB) partition in my laptop ?
Absolutely, after installation simply replace the swap line in /etc/fstab. You will gain hibernation too.

---

### Post by flamelab on 2008-04-22
> **ago said:**
> Absolutely, after installation simply replace the swap line in /etc/fstab. You will gain hibernation too.

With UUID ? Or /dev/sdX ?

---

### Post by ago on 2008-04-22
> **flamelab said:**
> With UUID ? Or /dev/sdX ?

same thing, you can copy the line from your other installation.

---

### Post by flamelab on 2008-04-22
Three problems already before even Wubi installation.

1)The MD5SUM check of the ISO takes a lot of time to finish .
2) The mirrors for the installation files (? what are they ...?) don't let me connect and only the last one (cdimage.ubuntu.com) let me at last . But ... I have already the ISO downloaded next to Wubi executable ...
3)After the long cheksuming , Wubi started downloading a new ISO !

Everything with the last revision and I started from the amd64 ISO.

---

### Post by ago on 2008-04-22
> **flamelab said:**
> 
1)The MD5SUM check of the ISO takes a lot of time to finish .

hehe if you can provide a faster md5sum algorithm I'll be glad to merge it in! You can use --skipmd5check to avoid that.

> 2) The mirrors for the installation files (? what are they ...?) don't let me connect
That is because the first 2 mirrors are the final release ones, but they are not oviously up yet 

> But ... I have already the ISO downloaded next to Wubi executable ...
3)After the long cheksuming , Wubi started downloading a new ISO !
Probably because the ISO you had is not the latest one so the md5 does not match the one in the server. ...Which is probably my fault because wubi will try the latest daily ISO (if it cannot find the final), while the link above is for RC... I will fix the link above. You can avoid redownloading by running wubi with --skipmd5check (assuming that the ISO was not overwritten/deleted.

---

### Post by flamelab on 2008-04-22
> **ago said:**
> hehe if you can provide a faster md5sum algorithm I'll be glad to merge it in! You can use --skipmd5check to avoid that.

Bit difficult to find a new algorithm [img]http://www.adslgr.com/forum/images/smilies/tongue.gif[/img]


> That is because the first 2 mirrors are the final release ones, but they are not oviously up yet 

OK then.


> Probably because the ISO you had is not the latest one so the md5 does not match the one in the server. ...Which is probably my fault because wubi will try the latest daily ISO (if it cannot find the final), while the link above is for RC... I will fix the link above. You can avoid redownloading by running wubi with --skipmd5check (assuming that the ISO was not overwritten/deleted.

I guess the amd64 one was rejected because the server from which I downloaded hadn't synced with [daily] from Canonical . The x86 ISO was downloaded from the local University (ftp.ntua.gr) and everything went fine . I uninstalled it though because I want to test the amd64 Ubuntu .

---

### Post by ago on 2008-04-22
Please also test to run wubi with a CD in the tray. You can use Daemon Tools or similar to emulate a CD without actually burning one...

---

### Post by ago on 2008-04-22
New ISO are out! Those include the new initrd, so nothing special to do other than testing Wubi. Those ISOs are very close to the final ones!

---

### Post by flamelab on 2008-04-22
No luck with amd64 ISO , even though it is from the same server. Wubi keeps wanting to download another ISO ,even though it didn't do the same with x86.

I'll download x86-64 from [daily] to check.

edit : Only alternate ISOs :( I would prefer them, but ... are they installable by Wubi ?)
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by ago on 2008-04-22
flamelab, the mirrors have been updated few minutes ago' see my message above, if you downloaded the ISO manually, it might be that by the time you run wubi the new metalink (=md5) was already up. The best way is to let wubi download the ISO for you, this way the metalink is downloaded first and the ISO later... If you do it manually it is the other way around...

---

### Post by flamelab on 2008-04-22
I saw it ,ago , but I hesitate because it the downloading is extremely slow (with Wubi) 

[ATTACH]66780[/ATTACH]

It is will take a day to finish .

Edit : OK , i found the metalink .

---

### Post by tuxpenguin on 2008-04-22
I have the latest wubi installer and the release cadidate .iso in the same folder...but wubi keeps trying to download the daily build...is this right? Are the daily build and the RC the same? I want to try the release candidate.

-Matt

---

### Post by ago on 2008-04-22
> **tuxpenguin said:**
> I have the latest wubi installer and the release cadidate .iso in the same folder...but wubi keeps trying to download the daily build...is this right? Are the daily build and the RC the same? I want to try the release candidate.

-Matt

Yes that is normal, see the messages above. In short Wubi will accept either the Final ISO or the latest daily ISO. And will check any local ISO against those (which now means the latest daily). Let wubi download its own ISO or run wubi with "--skipmd5check" to use a different ISO.

---

### Post by tuxpenguin on 2008-04-22
Thanks ago!

---

### Post by flamelab on 2008-04-22
:guitar::guitar::guitar:

Works like a charm . 

From amd64 Ubuntu 8.04 .

There is also an (ignorable ?) error , something about unrecognisable fs (I guess it means the NTfs , not ext3 ) , during grub countdown . I'll post a photo soon .

---

### Post by flamelab on 2008-04-22
[attach]66795[/attach]

---

### Post by ago on 2008-04-22
That should be ok (provided you do not install on that drive)

---

### Post by ago on 2008-04-22
> **ago said:**
> hehe if you can provide a faster md5sum algorithm I'll be glad to merge it in! You can use --skipmd5check to avoid that.

Well in fact I found it myself... [http://www.fourmilab.ch/md5/](http://www.fourmilab.ch/md5/) It turns out that the algorithm we use is about one to two orders of magnitudes slower... 

Should have done some benchmarking long time ago'... It will not make the CD :(

But it will hopefully be on the stand-alone (website download)!

---

### Post by flamelab on 2008-04-22
> **ago said:**
> Well in fact I found it myself... [http://www.fourmilab.ch/md5/](http://www.fourmilab.ch/md5/) It turns out that the algorithm we use is about one to two orders of magnitudes slower... 

Should have done some benchmarking long time ago'... It will not make the CD :(

But it will hopefully be on the stand-alone (website download)!

Are there goin' to be more releases ? Revisions ?

A thought of expanding Wubi to other distros ?If difficult, to Ubuntu/Debian based ...?

---

### Post by ago on 2008-04-22
> **flamelab said:**
> Are there goin' to be more releases ? Revisions ?
On CD it is going to be rev 495. There will be another official CD in July (8.04.1).
On the website we are more flexible of course.

> A thought of expanding Wubi to other distros ?If difficult, to Ubuntu/Debian based ...?
Eh it's open source ;), I even added a section in the wubi guide on how to customize Wubi... For Ubuntu derivatives it is fairly straightforward. Debian derivatives may need to integrate some backend components (Ubuntu had quite a few patches to fully support loopinstallations), but the frontend should work as is. For non-debian distros it may require additional changes to the frontend. I am aware of at least three other distros that are using wubi or planning to do so.

---

### Post by ago on 2008-04-23
> **flamelab said:**
> Are there goin' to be more releases ? Revisions ?

A thought of expanding Wubi to other distros ?If difficult, to Ubuntu/Debian based ...?

[http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev496.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev496.exe) 

This contains the new md5 checksum, should be way faster, and is a candidate for the website. Please try it out.

---

### Post by flamelab on 2008-04-23
The distros (that could use Ubiquity***** )

No 1 : Sidux .

No 2 : Knoppix

No 3 : Kanotix .

The first is the easiest to install, even easier than Ubuntu .

If I find time to customise Wubi, I shall propose a way to install Sidux.



Many thanks, ago. The program is simply perfect.


*isn't that the GUI installer ? Or is it called another way ?:mrgreen:

---

### Post by ago on 2008-04-23
Did you try 496?

---

### Post by ago on 2008-04-23
In fact rev 500 will be faster still (for md5)

---

### Post by flamelab on 2008-04-23
I'll try 496 during the weekend I guess, i'm in ArchLinux now :mrgreen:  . 495 is just perfect (only the md5sum issue that is solved in 496 ) .

---

### Post by ago on 2008-04-23
500 is the fast one...
PS do you have vista or XP?

---

### Post by Knight319 on 2008-04-23
So when 8.04 final hits tonight, will Wubi (rev 495 or 500) automatically download the final version's .iso?

---

### Post by ago on 2008-04-23
Look now ;)

---

### Post by flamelab on 2008-04-24
> **ago said:**
> 500 is the fast one...
PS do you have vista or XP?

Windows Vista x64 Ultimate and next to it, Archlinux.

---------------------

There is also an issue with the BCD options.

If someone installs Wubi and then uninstalls it, the BCD option for Ubuntu remains in Vista boot sequence.

It is easily removed with EasyBCD , but i've got no idea why that happens [img]http://www.adslgr.com/forum/images/smilies/what.gif[/img]

---

### Post by enobrev on 2008-04-25
Just downloaded the amd64 dvd (torrent) this afternoon, which I burned to a DVD, and wubi (501, i think - the latest as of about 2 hours ago).  Wubi is crashing after the checksums.  Here's my log output.

============ Installer ============
PLUGINSDIR=D:\DOCUME~2\Mark\LOCALS~1\Temp\nsj2AB.tmp
detect_all
Parsing cmdline "D:\Files\D\Wubi-8.04.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1918 MB
arch=amd64
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
      IsValid Ubuntu 8.04 "Hardy Heron" - Release amd64 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release amd64 (20080423)
Found CD F:
Found CD cddrive=F:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1711; Volume name ; Max #/chars in vol name 1909304; Volume Serial # -527025838; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1711; Volume name Documents; Max #/chars in vol name 1909308; Volume Serial # -2006688758; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1427752; Volume name ; Max #/chars in vol name 58; Volume Serial # -527025838; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 6947
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-4
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=enobrev
ComputerName=ENOBREV
EnvUsername=Mark
UserDomain=ENOBREV
UserInfoName=Mark
UserProfileFolder=D:\Documents and Settings\Mark
UserProfileName=Mark 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1773; Volume name ; Max #/chars in vol name 1817440; Volume Serial # -527025838; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1773; Volume name Documents; Max #/chars in vol name 1817444; Volume Serial # -2006688758; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Skipping drive D:, not enough free space 294 <= 5000
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 5
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
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
      IsValid Ubuntu 8.04 "Hardy Heron" - Release amd64 (20080423)
      cdversion=8.04 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080423 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release amd64 (20080423)
Found CD F:
Found CD cddrive=F:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=d3536b1c900c6e700bb8399e58c261a6
Checking md5 of F:\casper\filesystem.squashfs
CheckCD raw status = success:F:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso


Mark

---

### Post by ago on 2008-04-25
You cannot use the DVD you have to use a CD ISO. I didn't have time to add the code to distinguish between the two.

---

### Post by enobrev on 2008-04-25
Ah!  Thank you!!

Mark

---

