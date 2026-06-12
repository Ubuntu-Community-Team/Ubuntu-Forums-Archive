---
title: "New minefield is out, please test it as it will be test4"
date: 2007-06-18
forum: General Help
---

### Post by ago on 2007-06-18
[http://www.cutlersoftware.com/ubuntusetup/minefield.html](http://www.cutlersoftware.com/ubuntusetup/minefield.html)

Please let us know if it works or not. 

In  particular pay attention to timezone autodetection and uninstaller.

Migration-Assistant should now be enabled.
Vista should now be supported.

---

### Post by Mizarus on 2007-06-19
i use vista ultimate x64 and just finished installing wubi with the new minefield version, i selected 15gb for the instalation size and unbutustudio version, it worked very well unlike the previous versions i could boot to both OS's from the very first time i rebooted my system (after it downloaded the iso) instalation seemed to be faster then before.
great job Ago and many thanks

---

### Post by CrazyGuy123 on 2007-06-19
Works great for me on XP.  Forgot to check the timezone I'm afraid tho.

Windows 95/98 support seems broken.
I've attached the error as a screenshot.  I understand that supporting these old OS's with new software is hard, so I suggest that if the fix isn't easy (and I suspect it's not as the downloader/crc checker don't seem to have the required components installed (DUN, Winsock, IE4/5/5.5)), that it might be best to disable the download option in old OS's, and direct the user to download the iso manually, and re-run setup.  This is especially the case since I think most systems old enough to still have Windows 95 (and to some extent 98 ) are too old to run even xubuntu well, and very few people still use them, let alone would try to run a new OS on them.

Note that in this case, neither the downloader or the CRC checker work - both give the same error.

Note that Windows 95 doesn't have TCP/IP networking by default anyway, so it's impossible to download/access the internet - I got that error after installing TCPIP manually.


EDIT:  I also just noticed that Windows Me also isn't supported.  Windows Me doesn't have any support for multi-booting as far as I know  (it's bootloader has no menu).  Is there demand for Windows Me support?  The only solutions I can think of are:

A. Install a real GRUB to the MBR - risky
B.  Offer to make a "Wubi boot disk", which is GRUB on a floppy disk.
C.  Add a notice to the installer to inform users that Windows Me isn't supported BEFORE they download the iso.


On a similar note, there should be windows version detection in the installer (can read HKLM\Software\Windows NT\CurrentVersion\CurrentVersion), and it SHOULD NOT install unless it's a tried and tested windows version, because otherwise there are reasonable chances it won't work, and in the worst case we might do damage.

---

### Post by ago on 2007-06-19
Hmm the error above is not about the download but about loading up metadl component from the disk (you can check in c:\tmp). That would be required anyway, not sure why it's not available.

---

### Post by CrazyGuy123 on 2007-06-19
Metadl.dll does exist, just it can't be loaded probably because it requires some libraries that aren't present on windows 95 (win95 comes with basicly no optional supporting librarys).  I'm not quite sure the meaning of the cryptic error message - I presume translate is one of it's parameters?

Also, under Windows 95, disks over 4GB are allowed when they shouldn't be.  (the installer should presume that under win95/98 that no files larger than 4GB are allowed).

Anyway, I consider the win95 issue unimportant for a test release.  The allowing disks over 4GB may be more of an issue tho, since installation will fail.

---

### Post by ago on 2007-06-19
> **CrazyGuy123 said:**
> Metadl.dll does exist, just it can't be loaded probably because it requires some libraries that aren't present on windows 95 (win95 comes with basicly no optional supporting librarys).  I'm not quite sure the meaning of the cryptic error message - I presume translate is one of it's parameters?
Does it work with 98? If it's only win 95 I am not too concerned, 98 might be more annoying.

> Also, under Windows 95, disks over 4GB are allowed when they shouldn't be.  (the installer should presume that under win95/98 that no files larger than 4GB are allowed).
The total disk size is allowed to be larger than 4GB because that size gets split into files <= 4GB, up to 4 files are used (system, home, programs, swap). I have never tested that, so you may want to check if that works well.

---

### Post by ago on 2007-06-19
> **ago said:**
> The total disk size is allowed to be larger than 4GB because that size gets split into files <= 4GB, up to 4 files are used (system, home, programs, swap). I have never tested that, so you may want to check if that works well.

To be more precise, system can be split in up to 2 files so if the allocation of system is > x you will start to see a programs.virtual.disk as well. That covers you up until 8GB. Those do not include home and swap. Note to me: home is not actually expanded to make up for any difference.

---

### Post by Mizarus on 2007-06-19
about the timezone, it works, at least it did worked for me, so far iam having no problems what so ever with wubi it seems to be working 100% on vista now and i cant tell the diference betwen the normal instalation and this one, i tought there would be some kind of performance loss but that dosent seem to be the case.

---

### Post by CrazyGuy123 on 2007-06-19
ago:  kk - didn't actually do the install, just saw 7GB available in the installer drop down and presumed it was a bug.

Also, for some reason [http://www.wubi-installer.org/](http://www.wubi-installer.org/) doesn't seem to be properly redirecting at the moment.  If you're moving hosts or something, I'll put a vote in to have the minefield builds hosted somewhere faster, as I feel the wubi community is using a lot of resources from cutlersoftware.  (looking at the download.com download stats, I presume the main site has had a lot more than that)

I don't know how to go about it, but I think it would be goot to replace the old versions on download.com and "Windows Marketplace" (same source I think), since new versions are a lot better, and those sites are getting high search engine rankings and a lot of downloads.

---

### Post by ago on 2007-06-19
> **CrazyGuy123 said:**
> 
Also, for some reason [http://www.wubi-installer.org/](http://www.wubi-installer.org/) doesn't seem to be properly redirecting at the moment.  If you're moving hosts or something, I'll put a vote in to have the minefield builds hosted somewhere faster, as I feel the wubi community is using a lot of resources from cutlersoftware.  (looking at the download.com download stats, I presume the main site has had a lot more than that)
We are "moving" to sourceforge as I was not able to contact cutlersoftware admin in a while and this is a reason of concern for us. I'll try to do the migration tonight. We will still keep cutlersoftware, but the main downloads will be in sourceforge from test4 onward.

> I don't know how to go about it, but I think it would be goot to replace the old versions on download.com and "Windows Marketplace" (same source I think), since new versions are a lot better, and those sites are getting high search engine rankings and a lot of downloads.
Once I finish with sourceforge I'll take care of that too. 

If you guys find any bug with current release please let me know asap

---

### Post by CrazyGuy123 on 2007-06-19
sorry to go off topic on your thread, but while you're doing the site, I noticed it doesn't render properly in old versions of IE due to mistakes in the markup.  I've fixed them and it now validates and renders better  (old IE versions still don't support png, but at least there's no onscreen junk).  New file attached.  changes:  marked charset in meta tag since it's served as html not xml, added alt tag to feed icon, corrected imbalanced tags (some things opened but never closed or vice versa).  The css also has a bug in the margin: line of #container, - it should read "margin : 0 auto auto;"



Last Minute Edit:   Could someone with Vista just confirm if the installer runs at all?  (ie. does it even open up to the first screen?)  Maybe I've got it partially installed, or maybe a bug...

---

### Post by ago on 2007-06-19
Thanks a lot for that. I am going to use php for the new site and I might change quite a few things. Would you mind giving it a look once I am done?

---

### Post by CrazyGuy123 on 2007-06-19
It seems the latest version of the installer DOES NOT work on vista - it won't even open the main window.  build 207.57 works, 214.59 doesn't.  I suspect it's todo with the timezone detection maybe, since that seems to be the only big change between versions.

I can test something between 207 and 214 if someone else builds it - Haven't got a build environment set up here.

---

### Post by ago on 2007-06-19
that's unlikely. You can start it with the --debug parameter to have more info.

---

### Post by CrazyGuy123 on 2007-06-19
When started with the debug parameter:

wingmt:1
country:GB
LayoutCode:gb
Locale:en_GB
TimeZone:Europe/London
installationDrive:c:
DriveListBoxString:
Domain:localdomain
LayoutCode:gb
HostName:DELL
ComputerName:DELL
EnvUserName:MyUsername
UserDomain:DELL
UserInfoName:MyUserName
systemsize:
homesize:
swapsize:
NameServer:

All the parameters listed are correct. While that message box is shown, it has created it's temp folder and extracted the files.  As soon as I ok the message box, it deletes it temp folder and quits, with no indication why.

The old build (207) has a few less things, but also has installationDir and KeyMaps, which the new one doesn't have.


EDIT: - in reply to a question from earlier, yep I can look through the php.

EDIT2:  I think the bugs in line 20 and 21 of /src/pages/main.nsh (revision 214).  Can't find where those flags are set tho.

EDIT3:  solved it - the bug happens if wubi is installed, the folder moved or copied to another drive, then uninstalled.  see line 153 in /src/inspector/inspector.nsh (revision 214).  That causes wubi to try to uninstall, but it finds no uninstaller string in the registry, so fails to uninstall and quits.  Prehaps make wubi uninstaller more persistant to uninstall all wubi folders, not just the one in the registry, or just run install again if the registry key for the uninstaller can't be found (suggesting it's already been uninstalled)

---

### Post by ago on 2007-06-19
> **CrazyGuy123 said:**
> EDIT3:  solved it - the bug happens if wubi is installed, the folder moved or copied to another drive, then uninstalled.  see line 153 in /src/inspector/inspector.nsh (revision 214).  That causes wubi to try to uninstall, but it finds no uninstaller string in the registry, so fails to uninstall and quits.  Prehaps make wubi uninstaller more persistant to uninstall all wubi folders, not just the one in the registry, or just run install again if the registry key for the uninstaller can't be found (suggesting it's already been uninstalled)
Pls file a bug we'll take care of that in next build

---

### Post by Mizarus on 2007-06-19
i also had a previous wubi version installed and that bug did not happend to me, were you running wubi as an adimin?

---

### Post by ago on 2007-06-19
I uploaded the new release [http://ubuntuforums.org/showthread.php?t=478921](http://ubuntuforums.org/showthread.php?t=478921)

It's basically the same as the latest minefield

---

### Post by ago on 2007-06-20
Crazy Gui can you pls check the new website against IE-old?

Do you know how to "replace the old versions on download.com"? They do not seem to have an option for that.

---

### Post by acowboydave on 2007-06-20
Hello, earlier I downloaded The latest Wubi. Reinstalled Feisty with it. It went smooth and alot faster than the previous versions. No problems except the time was off, easy to fix. But the home partition was only 1.7G. I need more than that. So uninstalled Feisty, A small surprise, Wubi made a folder called Wubi-Save and in it was my Feisty download and a file called home virtual disk. The download that I had of Feisty was gone from my usb stick so I just moved it back to it. On the reinstall I bumbed the space for Feisty to 30G since I had the room. Install was fast and smooth again. Now I have 12G in home and 14,8G in I guess root. Any beginner thinking of installing Ubuntu in a dual boot should really look hard into this software. Or anyone else, going to go have some fun now.[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

### Post by ago on 2007-06-21
> **acowboydave said:**
> The download that I had of Feisty was gone from my usb stick so I just moved it back to it.
No need, the installer will look for a wubi-save folder and use that if found.

---

### Post by acowboydave on 2007-06-21
That good to know, but I want to use my stick on another compter. ;)

---

