---
title: "Wubi-7.04-test2 - bug reports, regression issues"
date: 2007-05-12
forum: General Help
---

### Post by tuxcantfly on 2007-05-12
Wubi-7.04-test2 (minefield0.7) has just been released.

New features/fixes (compared to -test1)

* Fix for Grldr Error 17
* Included UbuntuStudio
* Should have fixed Xubuntu ISO detection
* Avoids creating empty images
* Minor bugfixes
* Fat detection (avoids images > 4GB) without crashes
* Progress bar during virtual disk formatting in lupin
* Raid 0 support

Report bugs, comments or any major regressions here...

---

### Post by ferjat on 2007-05-12
Hi!

It doesn´t work formatting virtual disk. It stops in 33%. I have to reboot the laptop (Compaq Evo n800c) and the next problem is kernel panic, no found the image iso.

Tested with wubi-test1 and with wubi-test2

---

### Post by lokemo on 2007-05-12
Hi

I've got exactly the same problem (laptot Packard Bell Easy Note E3).

---

### Post by adamscabana on 2007-05-12
I have a dual boot XP/Vista machine and I get to 88% on formatting the virtual drive and then it hangs.  I don't see any disk activity.  The last status it reprots has to do with preparing the virtual home. 
Am I doing something wrong?  

:confused:

---

### Post by linlay on 2007-05-12
i'm still getting the Error 17 while trying to boot into ubuntu :(

tried contig to defragment everything, but it's still not working

---

### Post by ago on 2007-05-12
> **ferjat said:**
> Hi!

It doesn´t work formatting virtual disk. It stops in 33%. I have to reboot the laptop (Compaq Evo n800c) and the next problem is kernel panic, no found the image iso.

Tested with wubi-test1 and with wubi-test2

If that is formatting the virtual disks it could take a while.. Just let it go. If you stop it half way through installation you have to run wubi again and reinstall

---

### Post by ago on 2007-05-12
> **linlay said:**
> i'm still getting the Error 17 while trying to boot into ubuntu :(

tried contig to defragment everything, but it's still not working

That's more interesting, is that wubi test2?

---

### Post by mwilley on 2007-05-12
Is there a way to install this new version of Wubi, without having to reinstall Ubuntu?

---

### Post by jegHegy on 2007-05-12
> **tuxcantfly said:**
> Wubi-7.04-test2 (minefield0.7) has just been released.
* Included UbuntuStudio


I just installed Studio through Wubi. It worked fine except it only installed a sort of "base" system. "Base" because it's actually a fully functional GNOME desktop without some ubuntustudio meta packages. I'm guessing this is because the text installer pops up a question during installation asking whether or not it should install audio/graphics/video software which Wubi bypasses with the unattended setup thing, so I had to manually add them in Synaptic once the "base" install finished.

edit: Apparently it also skipped installing a lot more than just those ubuntustudio metas. (OpenOffice being one of them, I'm sure there are a lot more.)

---

### Post by adamscabana on 2007-05-12
> **adamscabana said:**
> I have a dual boot XP/Vista machine and I get to 88% on formatting the virtual drive and then it hangs.  I don't see any disk activity.  The last status it reprots has to do with preparing the virtual home. 
Am I doing something wrong?  

:confused:


The install actualy gets to 83% (not 88%).  It hangs on trying ot format the home drive.
I let it go for probably 20 minutes.  I can't imagine it takes longer than that.

---

### Post by Dark Legacy on 2007-05-13
> **tuxcantfly said:**
> Wubi-7.04-test2 (minefield0.7) has just been released.

New features/fixes (compared to -test1)

* Fix for Grldr Error 17
* Included UbuntuStudio
* Should have fixed Xubuntu ISO detection
* Avoids creating empty images
* Minor bugfixes
* Fat detection (avoids images > 4GB) without crashes
* Progress bar during virtual disk formatting in lupin
*** Raid 0 support**

Report bugs, comments or any major regressions here...

Edit: It's working, it's working...
[img]http://img182.imageshack.us/img182/5003/linuxboot9ot6.jpg[/img]

Ahh.. aghh.. no.
[img]http://img182.imageshack.us/img182/7223/linuxboot10ss4.jpg[/img]

It's not working. :(

---

### Post by Jerick on 2007-05-13
I'm getting the same problem too. at 83%, it freezes. Nothing happens between the hard drive and anything else, although the "Lock" keys work perfectly well.

---

### Post by ago on 2007-05-13
> **jegHegy said:**
> I just installed Studio through Wubi. It worked fine except it only installed a sort of "base" system. "Base" because it's actually a fully functional GNOME desktop without some ubuntustudio meta packages. I'm guessing this is because the text installer pops up a question during installation asking whether or not it should install audio/graphics/video software which Wubi bypasses with the unattended setup thing, so I had to manually add them in Synaptic once the "base" install finished.

edit: Apparently it also skipped installing a lot more than just those ubuntustudio metas. (OpenOffice being one of them, I'm sure there are a lot more.)

What are the metapackages installed by ubuntustudio?

---

### Post by ago on 2007-05-13
> **Jerick said:**
> I'm getting the same problem too. at 83%, it freezes. Nothing happens between the hard drive and anything else, although the "Lock" keys work perfectly well.

It's probably formatting the home virtual drive, that can take a while depending on disk size. Press alt+f4 for more feedback

---

### Post by jegHegy on 2007-05-13
> **ago said:**
> What are the metapackages installed by ubuntustudio?

I think you might need to look a bit deeper than that to solve this problem, as I've mentioned before, more than the metas are missing. I've spoken to the Studio devs and they've told me they use tasksel in the installer (Ubuntu Server also uses this). If things are not clear I suggest you try and get a hold of the Studio devs themselves, I'm sure you'll have it figured out in a jiffy. (#ubuntustudio@freenode)

Oh, and thank you for your efforts so far, much appreciated as I am really eager to try this OS out in its full glory. (Without having to create another partition. :D)

---

### Post by adamscabana on 2007-05-13
> **ago said:**
> It's probably formatting the home virtual drive, that can take a while depending on disk size. Press alt+f4 for more feedback

I found the fix.
When I installed the first time I did not select a home drive size.  I completly uninstalled and reinstalled...making sure to select a home drive size.  The install worked perfectly after I did that.

---

### Post by ago on 2007-05-13
> **adamscabana said:**
> I found the fix.
When I installed the first time I did not select a home drive size.  I completly uninstalled and reinstalled...making sure to select a home drive size.  The install worked perfectly after I did that.

Hmmm, that should use a default size anyway, and if you have selected a zero size it will not create the home drive at all (which should result in the home folder being within the system virtual drive). What size was the home virtual disk?

---

### Post by ago on 2007-05-13
> **jegHegy said:**
> I think you might need to look a bit deeper than that to solve this problem, as I've mentioned before, more than the metas are missing. I've spoken to the Studio devs and they've told me they use tasksel in the installer (Ubuntu Server also uses this).
We use that too, but I need to know what packages are required. For instance ubuntu requires a package called "ubuntu-desktop". Kubuntu requires a package called "kubuntu-desktop". And so on... Therefore I was assuming ubuntustudio would require "ubuntustudio-desktop". If that is not the case, I need to know the names of the required metapackages to use with tasksel, it's an easy fix.

---

### Post by ago on 2007-05-13
> **Dark Legacy said:**
> It's not working. :(

What raid0 do you use exactly?

---

### Post by jegHegy on 2007-05-13
> **ago said:**
> We use that too, but I need to know what packages are required. For instance ubuntu requires a package called "ubuntu-desktop". Kubuntu requires a package called "kubuntu-desktop". And so on... Therefore I was assuming ubuntustudio would require "ubuntustudio-desktop". If that is not the case, I need to know the names of the required metapackages to use with tasksel, it's an easy fix.

[https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)
Here is the package list for the metas. Would the missing metas explain the other missing packages though, like OpenOffice.org? I tried installing UbuntuStudio on VirtualBox before using Wubi and trying it out for real, and on VirtualBox I had OO.o by default, and I don't see it in the Package List on the Wiki. Wouldn't that suggest that there's some other problem as well?

---

### Post by ago on 2007-05-13
> **jegHegy said:**
> [https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)
Here is the package list for the metas.
Thanks it will  be fixed in next release

> Would the missing metas explain the other missing packages though, like OpenOffice.org?
It does not look to me like OpenOffice is included in UbuntuStudio at all from your package list... 

> Wouldn't that suggest that there's some other problem as well?
Normally oo is included within the *buntu-desktop package. You may want to ask the ubuntustudio devs for an explanation.

---

### Post by MetalMusicAddict on 2007-05-13
There is a ubuntustudio-desktop package. It is the base. The additional tasksel options would pull (if the users chooses) ubuntustudio-audio, ubuntustudio-audio-plugins, ubuntustudio-video or ubuntustudio-graphics.

These are options. Our installer isn't a all or nothing install.

Also, all of our packages aren't in the Ubuntu repos yet. It was a time issue with Feisty but will be fixed for Gutsy.

As far as the OO.o stuff goes because of depends -core is pulled. Its not on our WIKI but is just a side effect we hope to remedy for the next release. I think Xubuntu suffers from this as well.

---

### Post by ago on 2007-05-13
> **MetalMusicAddict said:**
> There is a ubuntustudio-desktop package. It is the base. The additional tasksel options would pull (if the users chooses) ubuntustudio-audio, ubuntustudio-audio-plugins, ubuntustudio-video or ubuntustudio-graphics.

These are options. Our installer isn't a all or nothing install.

Also, all of our packages aren't in the Ubuntu repos yet. It was a time issue with Feisty but will be fixed for Gutsy.

As far as the OO.o stuff goes because of depends -core is pulled. Its not on our WIKI but is just a side effect we hope to remedy for the next release. I think Xubuntu suffers from this as well.

Hi there,

We are using preseed to decide what packages to install. If the packages are available within the ISO, I would prefer to install everything in one go from wubi (ubuntustudio-audio, ubuntustudio-audio-plugins, ubuntustudio-video or ubuntustudio-graphics). People that would use wubi to install ubuntustudio would likely want to have the full monty and our approach is to have as little options as possible. If there is any other package I need to include/exclude by default, just let me know. Hopefully wubi will help out to increase the userbase of ubuntustudio as well.

---

### Post by mwilley on 2007-05-13
I did a clean install of Wubi with Ubuntu...  It gets to the second screen in the installation, then stops at 33%.  The text "killed" appears a few times, then freezes.  I rebooted (after waiting for at least 20 minutes) and I get this:

```
--------------------------------------------------------------
Error!
Unable to access alternate ISO
--------------------------------------------------------------
Setting up file system, please wait...
mount, Mounting none on /proc failed! Device or resource busy

[9.832000] Kernel panic -- not syncing: Attempting to kill init!
[9.832000]
```

---

### Post by ago on 2007-05-13
> **mwilley said:**
> I did a clean install of Wubi with Ubuntu...  It gets to the second screen in the installation, then stops at 33%.  The text "killed" appears a few times, then freezes.  I rebooted (after waiting for at least 20 minutes) and I get this

When you kill it you have to reinstall. If it locks at 33%, let it go for a few minutes, if it takes more than 10-15 minutes, reinstall and make sure all drives of 4GB or less

---

### Post by sammm on 2007-05-13
> **ferjat said:**
> 
It doesn´t work formatting virtual disk. It stops in 33%.


I have the same issue.
I installed wubi with default settings on the defragmented C:\ drive of my winXP install, which is a SCSI ATA drive.
The ubuntu-7.04-alternate-i386.iso file was downloaded on beforehand and the md5sum was checked.
With contig, I made sure grldr, initrd and menu.lst are contiguous.
It stops during formatting of the virtual disk. The hard drive shows no activity whatsoever.
Pressing Alt-F4 gives me the screen below, which stays like that for more than one hour.
I also provide the log files (changed the file extensions).
Hopefully, you can fix this. I highly appreciate your efforts.

---

### Post by Jerick on 2007-05-13
Apparently, uninstalling and reinstalling did the trick, I guess the image file or something or other was messed up, but now I'm on Kubuntu and it works. Thanks for the help. (:

---

### Post by mwilley on 2007-05-13
> **ago said:**
> When you kill it you have to reinstall. If it locks at 33%, let it go for a few minutes, if it takes more than 10-15 minutes, reinstall and make sure all drives of 4GB or less
I reinstalled it with all drives at 4GB or less, but got the same results...  Any ideas?

---

### Post by Dark Legacy on 2007-05-13
> **ago said:**
> What raid0 do you use exactly?

I have an eVGA 680i Motherboard, and I'm using the Nvidia-RAID onboard RAID controller, which as the screenshot shows - it detected perfectly well...

"Detected Nvidia and Sil, using "Nvidia" - that's correct, but I'm STILL wondering as to why it can't install/boot up Ubuntu. :(

---

### Post by ago on 2007-05-14
> **Dark Legacy said:**
> I have an eVGA 680i Motherboard, and I'm using the Nvidia-RAID onboard RAID controller, which as the screenshot shows - it detected perfectly well...

"Detected Nvidia and Sil, using "Nvidia" - that's correct, but I'm STILL wondering as to why it can't install/boot up Ubuntu. :(

If you know a bit of CLI, once you are at the shell try to mount it manually. Probably the device is mapped to some place we do not look into (we look into /dev/hdX, /dev/sdX, dev/mapper). If you can find your device, I'll fix it for next release.

---

### Post by pjalegria on 2007-05-14
Same problem here, 33% hung up...I hope they can fix that...

Tank you

---

### Post by ago on 2007-05-14
> **pjalegria said:**
> Same problem here, 33% hung up...I hope they can fix that...

Tank you

If you get stacked at 33%, please see: [http://ubuntuforums.org/showpost.php?p=2652202&postcount=21](http://ubuntuforums.org/showpost.php?p=2652202&postcount=21)

---

### Post by MetalMusicAddict on 2007-05-14
> **ago said:**
> Hi there,

We are using preseed to decide what packages to install. If the packages are available within the ISO, I would prefer to install everything in one go from wubi (ubuntustudio-audio, ubuntustudio-audio-plugins, ubuntustudio-video or ubuntustudio-graphics). People that would use wubi to install ubuntustudio would likely want to have the full monty and our approach is to have as little options as possible. If there is any other package I need to include/exclude by default, just let me know. Hopefully wubi will help out to increase the userbase of ubuntustudio as well.

I understand. 

Installing: ubuntustudio-desktop ubuntustudio-audio, ubuntustudio-audio-plugins, ubuntustudio-video or ubuntustudio-graphics overtop of ubuntu-minimal or a CLI system *kinda* gets you Ubuntu Studio. Our installer sets some options for users as well.

My only issue will be the things that arise from people that install this way and then come to us for possible errors and or missing settings. As well as it deviating from the way we want to give users choice on install. 

I would really rather wait till our 2nd release for Wubi to support Ubuntu Studio as we are working with Canonical to build our disks and all our packages will be in Gutsy. It should make for less issues this way.

---

### Post by ago on 2007-05-14
> **MetalMusicAddict said:**
> I understand. 

Installing: ubuntustudio-desktop ubuntustudio-audio, ubuntustudio-audio-plugins, ubuntustudio-video or ubuntustudio-graphics overtop of ubuntu-minimal or a CLI system *kinda* gets you Ubuntu Studio. Our installer sets some options for users as well.
Is there any package that might be legally problematic in some jurisdictions? Why aren't the settings in the packages postinst? 

> As well as it deviating from the way we want to give users choice on install.
We cover a different target: people that do not want too many options, they just want everything up and ready in 1 click, and everything out of the way in 1 click. More advanced users, do not really need wubi, but less advanced users would probably never try UbuntuStudio without Wubi...

> I would really rather wait till our 2nd release for Wubi to support Ubuntu Studio as we are working with Canonical to build our disks and all our packages will be in Gutsy. It should make for less issues this way.

We are still in beta, I would suggest that we keep it and see how it goes. If it works out, it will bring you guys quite a few customers, if it doesn't and you see many tickets coming from us, let me know and we will remove it. My view though is that installing the metapackages (and possibly having a single metapackage, ubuntustudio-ultimate or something) should be self sufficient, using wubi or the live iso should not make any difference.

---

### Post by MetalMusicAddict on 2007-05-14
> **ago said:**
> Is there any package that might be legally problematic in some jurisdictions? Why aren't the settings in the packages postinst? 

Just worked out that way.
> We cover a different target: people that do not want too many options, they just want everything up and ready in 1 click, and everything out of the way in 1 click.
I know. Its just different from the way we want Ubuntu Studio presented.
> More advanced users, do not really need wubi, but less advanced users would probably never try UbuntuStudio without Wubi...
I dont agree but whatever.
> We are still in beta, I would suggest that we keep it and see how it goes. If it works out, it will bring you guys quite a few customers, if it doesn't and you see many tickets coming from us, let me know and we will remove it. My view though is that installing the metapackages (and possibly having a single metapackage, ubuntustudio-ultimate or something) should be self sufficient, using wubi or the live iso should not make any difference.
We don't belive in making it a all-or-nothing choice for users. In the end, I can't stop you from doing this nor would I try but I can't support issues that *might* arise from this install method.

---

### Post by ago on 2007-05-14
> **MetalMusicAddict said:**
> We don't belive in making it a all-or-nothing choice for users. In the end, I can't stop you from doing this nor would I try but I can't support issues that *might* arise from this install method.

Of course you can. If you guys do not want us to include ubuntustudio, we won't. It's that simple. But then we will send people that ask us to include ubuntustudio to your fourm ;P (and we already had a few requests...). That said, I do not really understand your concerns: either wubi does not properly install ubuntustudio and we can remove it, or it does, and therefore you will not have any "special" tickets to address... Wubi does a straightforward d-i installation using YOUR alternate ISO, so in that respect I would be quite surprised if the end system is any different from the one you get from using your installer... As for showing tasksel, it is not going to happen in wubi, we will either preinstall the most reasonable combination of packages or nothing at all.

---

### Post by jegHegy on 2007-05-14
I understand both of you guys' points, and I'm sure you can find a compromise about this. To me, it looks like it boils down to these questions: Can Wubi be made to provide advanced settings for the users that want to selectively only install audio/graphics/video packages (maybe even during the win32 installer?), and more importantly (at least to me), can it apply the special options/tweaks UbuntuStudio provides?

For the good of the users. :)

---

### Post by MetalMusicAddict on 2007-05-14
> **ago said:**
> Of course you can. If you guys do not want us to include ubuntustudio, we won't. It's that simple. But then we will send people that ask us to include ubuntustudio to your fourm ;P (and we already had a few requests...). That said, I do not really understand your concerns: either wubi does not properly install ubuntustudio and we can remove it, or it does, and therefore you will not have any "special" tickets to address... Wubi does a straightforward d-i installation using YOUR alternate ISO, so in that respect I would be quite surprised if the end system is any different from the one you get from using your installer... As for showing tasksel, it is not going to happen in wubi, we will either preinstall the most reasonable combination of packages or nothing at all.

I looked again. We did move all the settings to packages inside ubuntustudio-desktop.

I'm concerned with presentation. It was alot of work in the D-I to give users the choice on the disk. MANY users have come to the channel applauding this.

The power of free software is that I can't "make" you do anything. :) If your users want it then go ahead. Thats how your system works. I'm just unhappy with the all-or-nothing approach thats pushed on the user who wants to try Ubuntu Studio.

---

### Post by ago on 2007-05-14
> **jegHegy said:**
> Can Wubi be made to provide advanced settings for the users that want to selectively only install audio/graphics/video packages
Technically yes, in practice no. Wubi is intended to be a 1 click installer, if we add a few options for each distro we ship we'll soon end up as a boeing 747 panel and I do not want that to happen. We are not supposed to replace all installers, we only want to target more inexperienced users and we want to give them a reasonable setup, with 1 click.

> can it apply the special options/tweaks UbuntuStudio provides?
Wubi will simply install the specified (meta) packages, all settings should be inside the meta package postinstallation scripts, anything outside that will not be installed (and should not be installed).

---

### Post by jegHegy on 2007-05-14
What about the user who is considering to completely switch to Linux from Windows but wants to try out if he has the time/patience to customize it to his own needs, and if he doesn't like it he could go back to Windows painlessly? (i.e. without juggling with partitions and making full-disk backups to avoid data loss)

(It's me.)

---

### Post by ago on 2007-05-15
I have added all ubuntustudio packages see how if it works [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.8.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.8.exe)

---

### Post by jegHegy on 2007-05-15
Thank you, I'll have time to try it this afternoon and I will report back to you.

---

### Post by jegHegy on 2007-05-15
edit: Disregard this post, I will update soon.

---

### Post by ago on 2007-05-15
Does the above work with ubuntu, yesterday night I did not have time to test

---

### Post by ragingmon on 2007-05-15
ohhh tnx..I'll try this now

---

### Post by ragingmon on 2007-05-15
> **ago said:**
> I have added all ubuntustudio packages see how if it works [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.8.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.8.exe)

ohh I've tried using this...
And still, I see no software package installed..
no blender, no gimp, no nothing.. T_T

just the same with my first install using the Wubi-7.04-test2.exe in the wubi site...
pls help...

---

### Post by ago on 2007-05-15
I'll test it tonight and republish, I could not test it yesterday night

---

### Post by jegHegy on 2007-05-15
Just posting to confirm ragingmon's results. Installed using minefield 0.8 and the audio/graphics/video packages are not installed.

---

### Post by ago on 2007-05-15
can you please redownload 0.8 and try again? I uploaded a quick fix.

---

### Post by adj on 2007-05-15
Hi -- since I am installing this specifically to try Ubuntu as a DAW, I installed Wubi-7.04-minefield0.8.exe for Ubuntu Studio.

Seemed to install OK , but after reboot a lot of warning messages flashed by very quickly saying something about the bios, then I got as far as the nice ubuntu loading screen and then my monitor went out of range.

Is the monitor out of range thing because my monitor only supports a 1024x768 resolution and your default is higher than that? If so, can you default it to a lower rate like 1024x768? My graphics card is the latest nVidia GFX6600GT but my monitor is an older style with a top rate of only 1024x768. 

Cheers & Thanks,
Alex The Total Linux N00bie

---

### Post by jegHegy on 2007-05-16
> **ago said:**
> can you please redownload 0.8 and try again? I uploaded a quick fix.

Just installed using this, the extra packages are there! :D Installed the lowlatency kernel by default as well, and added the necessary line to /etc/security/limits.conf as intended. OpenOffice.org seems to be missing still though, though MetalMusicAddict mentioned something about it not being Wubi's fault. Another small thing I noticed is that Scribus' icon gets installed twice, once in the Graphics menu, and once in Office. (I don't remember this happening in my VirtualBox install of UbuntuStudio.)

All in all, very nice progress and I'm very glad the lowlat kernel works out of the box like with a native install!

---

### Post by Fuller42 on 2007-05-16
> **adj said:**
> Hi -- since I am installing this specifically to try Ubuntu as a DAW, I installed Wubi-7.04-minefield0.8.exe for Ubuntu Studio.

Seemed to install OK , but after reboot a lot of warning messages flashed by very quickly saying something about the bios, then I got as far as the nice ubuntu loading screen and then my monitor went out of range.

Is the monitor out of range thing because my monitor only supports a 1024x768 resolution and your default is higher than that? If so, can you default it to a lower rate like 1024x768? My graphics card is the latest nVidia GFX6600GT but my monitor is an older style with a top rate of only 1024x768. 

Cheers & Thanks,
Alex The Total Linux N00bie

I had an identical problem, and this happened with kubuntu 7.04 alternate. To add a little information, I have a dual monitor setup - both on 1280 x 1024 reolution. My main monitor on a digital output went blank, but my 2nd monitor on an analogue connection said "out of range"

---

### Post by adj on 2007-05-16
> **Fuller42 said:**
> I had an identical problem, and this happened with kubuntu 7.04 alternate. To add a little information, I have a dual monitor setup - both on 1280 x 1024 reolution. My main monitor on a digital output went blank, but my 2nd monitor on an analogue connection said "out of range"

Ahh... So what was the fix? Were you ever able to get it to work? Am I SOL if my monitor doesn't go above 1024x768?

Thanks,
Alex

---

### Post by ago on 2007-05-16
You have to edit c:\wubi\boot\grub\menu.lst. Everywhere you see "quiet splash" replace with "quiet". 

That disables usplash, then, once in ubuntu, select a theme of the appropriate resolution and make sure that /etc/uspash.conf is in line with the theme res. There are a few guides around and even some graphical utilities to configure usplash. When that is done you can reset menu.lst to what it was before.

---

### Post by ragingmon on 2007-05-16
When I installed UbuntuStudio using minefield 0.8 the software packages are there..
Tnx it was a success...tnx so much for the fix.. :D

I just want to ask something noobish...
Does this installation will identify my ATI Radeon 9250 or it won't???
Because I just found out that it didn't identify my graphics card..T_T

And also I want to change my resolution to 1152x768..
and I think my graphics card will help me out with the resolution I want..

btw, tnx in advance...

---

### Post by ago on 2007-05-16
> **ragingmon said:**
> 
I just want to ask something noobish...
Does this installation will identify my ATI Radeon 9250 or it won't???
Because I just found out that it didn't identify my graphics card..T_T
The radeon driver should be fine. You can also try the restricted modules.

glxinfo|grep direct

to see if you have 3D acceleration
> And also I want to change my resolution to 1152x768..
and I think my graphics card will help me out with the resolution I want..
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

> btw, tnx in advance...
np fujiko

---

### Post by Fuller42 on 2007-05-16
> **ago said:**
> You have to edit c:\wubi\boot\grub\menu.lst. Everywhere you see "quiet splash" replace with "quiet". 

That disables usplash, then, once in ubuntu, select a theme of the appropriate resolution and make sure that /etc/uspash.conf is in line with the theme res. There are a few guides around and even some graphical utilities to configure usplash. When that is done you can reset menu.lst to what it was before.

Thanks mate, I'll give this a go once I've got home from work.

EDIT - I'm afraid it didnt work. The splash screen dissapeared, but it got to the end of the boot up procedure and just hung and screens went blank :(

---

### Post by adj on 2007-05-16
> **ago said:**
> You have to edit c:\wubi\boot\grub\menu.lst. Everywhere you see "quiet splash" replace with "quiet". 

That disables usplash, then, once in ubuntu, select a theme of the appropriate resolution and make sure that /etc/uspash.conf is in line with the theme res. There are a few guides around and even some graphical utilities to configure usplash. When that is done you can reset menu.lst to what it was before.

Didn't work -- same 'out of signal range' message on my monitor. :(

---

### Post by Dark Legacy on 2007-05-16
> **ago said:**
> If you know a bit of CLI, once you are at the shell try to mount it manually. Probably the device is mapped to some place we do not look into (we look into /dev/hdX, /dev/sdX, dev/mapper). If you can find your device, I'll fix it for next release.

I don't know any CLI, but I'm a quick and avid learner, so if you could please link to some source as to learn how to use CLI, I'd gladly try to sort this issue out. :popcorn: 

Edit: I found a nice resource for learning Linux CLI, and it reminds me quite alot of DOS that I used to use back as a kid. I can navigate DOS extremely well, even creating virtual file trees within my mind, so I suppose this can't be that far-fetched.

(I'm currently learning C++, on the side.) :p

---

### Post by adj on 2007-05-17
Well -- I guess there's no answer on the monitor resolution problem then...  :confused: 

uninstalling and  moving on...

---

### Post by Spegelius on 2007-05-17
> **Dark Legacy said:**
> I don't know any CLI, but I'm a quick and avid learner, so if you could please link to some source as to learn how to use CLI, I'd gladly try to sort this issue out. :popcorn: 

Edit: I found a nice resource for learning Linux CLI, and it reminds me quite alot of DOS that I used to use back as a kid. I can navigate DOS extremely well, even creating virtual file trees within my mind, so I suppose this can't be that far-fetched.

(I'm currently learning C++, on the side.) :p

Ok, could you post what files are on the /dev/mapper-folder? Use this in initramfs prompt:

ls /dev/mapper

Currently lupin searches for files which name ends like ...RAID0-9 in /dev/mapper. It might be that dmraid generates different named files for different RAID setups, so in yout case it might simply overlook your RAID device. That search criteria is based on my RAID0 setup on Intel chipset (and i have Wubi on RAID0 ;) ).

---

### Post by ShrimpCrackers on 2008-05-15
Hi is Ubuntu Studio no longer supported in Wubi? It definitely isn't in there anymore. I would definitely love to try Ubuntu Studio and I think its safe to show friends if Wubi came with it or there was a distro of Wubi that handled Ubuntu Studio as well.

---

### Post by ago on 2008-05-15
You can install regular Ubuntu, and then install the ubuntustudio packages via synaptic

---

