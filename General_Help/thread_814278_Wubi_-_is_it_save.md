---
title: "Wubi - is it save?"
date: 2008-05-31
forum: General Help
---

### Post by VanDeUlk on 2008-05-31
Heyho out there! :)

First and foremost: I hope I have not missed these questions in one of the Wubi-FAQs and the forums.

I'm currently planning to buy a new notebook and install Ubuntu on it. To get a feel for it I intend to give it a try on my Desktop-system. Wubi sounds like the perfect solution for this, but there are some questions left...

- If I uninstall Wubi, will everything reset to the situation before? Any need to wrestle with corrupt boot-managers etc?

-I've got some quite sensible data on my computer. I've read about Wubi causing some problems with dirty shutdown, but this should'nt be the case here. Anyway I wonder whether wubi might cause some problems that could damage any partitions, my data or windows?

_ I've read about wubi supporting anything a user might use - is this the case for drivers, too (graphic-card etc.)?

Thanks for any answers and a wonderful weekend,
Ulk :)

---

### Post by arinlares on 2008-05-31
Don't mean to scare you or anything, but I currently have an issue with the boot menu from when I took Wubi off of my computer.  It still prompts me to select which OS i want to load (XP Home or Recovery Console, which are all I have on my computer now).  So far as I know it is reversible in XP and Vista (looking now).  I've heard that a "hard reset" (hibernate or anything else that causes the computer to suddenly stop processing) will corrupt the Wubi files in the Microsoft system (chkdsk can fix it). Don't take my word for gospel, wait for more responses (i'm telling you what i know/have heard).

---

### Post by Cookie1456 on 2008-05-31
When you install Ubuntu/Kubuntu through wubi, it is the full system, so it's everything a CD installed system is. Wubi (from my experience) can't screw up windows, with your question regarding the boot loader, when you use the wubi uninstall program it removes itself clean, so you wont have a problem. With a hard power off (the power button) or hibernation, it will screw up the Ubuntu data, not the windows data (though maybe there is a chance, wait for more replies). I don't experience problems like that cause I just installed Wubi to a separate fat drive though.

---

### Post by rohitsb on 2008-05-31
Had no probs with Wubi. Ran Wubi to install Ubuntu and Kubuntu on XP and Vista both, on 2 different notebooks. Worked like a charm. Boot configuration was handled smoothly. Use the latest wubi though, older version had an issue with Vista.

---

### Post by abn91c on 2008-05-31
the only problem with wubi hard reboot, at least for my dell laptop is you may get to an initrams prompt, if you do just do a normal reboot, let the computer get to windows log in screen so it can "mount" the wubi drives. Rebooting again and it will let you start wubi normally.

---

### Post by VanDeUlk on 2008-06-01
Man, I don't get it...
Downloaded the appropiate image (from the site suggested in the Wubi-FAQ) for my system and checked for the correct md5-sum. 

When I put the image into the Wubi-folder, Wubi starts to download it (exactly the same file) again from the internet and does not give anything on the existing file. 
If I burn the image on CD and start Wubi from there, I get a "Could not access the CD"-error at about 99%. Burned it twice with different speeds and opened it up in different drives - no chance to make it work.

:(

(Maybe using a virtual drive alá Daemon Tools might work?)

---

### Post by Cookie1456 on 2008-06-01
Try daemon tools, thats what I did (the whole reason I used wubi is my install disks wouldn't work =/)

---

### Post by ago on 2008-06-02
> **VanDeUlk said:**
> Man, I don't get it...
Downloaded the appropiate image (from the site suggested in the Wubi-FAQ) for my system and checked for the correct md5-sum. 

When I put the image into the Wubi-folder, Wubi starts to download it (exactly the same file) again from the internet and does not give anything on the existing file. 
If I burn the image on CD and start Wubi from there, I get a "Could not access the CD"-error at about 99%. Burned it twice with different speeds and opened it up in different drives - no chance to make it work.

:(

(Maybe using a virtual drive alá Daemon Tools might work?)

Look at the log in your user temp folder for reasons why wubi doesn't like your ISO.

---

### Post by VanDeUlk on 2008-06-02
So I've got this...

> [...]

DetectCD
      Is Valid CD E:
      IsValid Ubuntu 8.04 "Hardy Heron" - Release i386 (20080601)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080601 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release i386 (20080601)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=ecc2eb5341c58dd0b1f7d2ede333ee38
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO D:\ubuntu\install\installation.iso
CD2ISO failed: LastError = 1 Unzulässige Funktion.

Asking user to retry CD2ISO
User did not select to retry CD2ISO, quitting.

I've decided against retrieing as this would produce the same error again.

---

### Post by ago on 2008-06-02
Can you please provide the log when trying to use an ISO as opposed to a CD?

---

### Post by VanDeUlk on 2008-06-02
Oh, I'm sorry. 

This time I've used the 32b-ISO (with the "--32b" argument for the wubi.exe) because a friend of mine warned me of incompabilities that I might face if I install the 64b-version.

Nevertheless, same problem:

> [...]

DetectIso
      IsValidIso ispoath=C:\Dokumente und Einstellungen\*******\Eigene Dateien\wubi\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOKUME~1\*******\LOKALE~1\Temp\nsp46.tmp\7z.exe e -y -i!.disk\info -oC:\DOKUME~1\*******\LOKALE~1\Temp C:\Dokumente und Einstellungen\*******\Eigene Dateien\wubi\hardy-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Release i386 (20080601)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080601 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release i386 (20080601)
Copying C:\Dokumente und Einstellungen\*******\Eigene Dateien\wubi\hardy-desktop-i386.iso -> D:\ubuntu\install\hardy-desktop-i386.iso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Checking/Downloading Ubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink](http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink)
get_md5 [http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink](http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04/MD5SUMS-metalink.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04/MD5SUMS-metalink md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink
      Verifying signature D:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: error loading `iconv.dll': Das angegebene Modul wurde nicht gefunden.


gpgv: Signature made 04/24/08 09:37:24 Westeuropäische Sommerzeit using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS-metalink
Found md5 22eefa07792160d5b0f398024b397349
Downloading: trymefirst=D:\ubuntu\install\hardy-desktop-i386.iso url=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink md5=22eefa07792160d5b0f398024b397349
Download status=cancel
User cancelled download, quitting.

The problem seems to be linked to "error loading `iconv.dll'". Google afforded quite a lot of downloads for this file. Maybe this might be the solution? Is downloading a .dll from the Internet save?

Anyway I want to thank you for the great support! :KS

---

### Post by ago on 2008-06-02
You are using a daily ISO
Wubi checks the md5 against the official release

Wubi daily releases are not ready yet

---

### Post by VanDeUlk on 2008-06-02
Oh...

I used the Downloads provided by the link in the official [Wubi-FAQ]("http://wubi-installer.org/faq.php") at "Can I use an existing ISO/CD instead of letting Wubi download a new one?"

Confusing. *g*

---

