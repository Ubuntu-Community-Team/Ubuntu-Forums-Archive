---
title: "WUBI 8.04.1 PRE-RELEASE IS OUT! It addresses most known issues."
date: 2008-06-21
forum: General Help
---

### Post by ago on 2008-06-21
The pre-release of 8.04.1 is available here:

[http://wubi-installer.org/devel/minefield/Wubi-8.04.1-rev505.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04.1-rev505.exe)

This addresses most issues that emerged after release. If you have trouble with Wubi 8.04 give this a shot, and please let me know if it works or not.

Note that it **requires the latest 8.04.1 DAILY DESKTOP ISO** (run it with --skipmd5check to use an older 8.04.1 daily ISO). It is recommended to let Wubi download one for you. In any case the correct ISOs are available here:

[http://cdimage.ubuntu.com/hardy/daily-live/current](http://cdimage.ubuntu.com/hardy/daily-live/current)

The 8.04 final ISO will not work, alternate and DVD ISOs will not work either whatever the version.

---

### Post by ago on 2008-06-21
In particular 8.04.1 addresses the following problems:

 * LP217348: Ubuntu cannot boot when there are multiple hard disks
 * LP224311: Ubuntu gets stuck at reboot with the message: "Turning on gate A20" or "...upper memory..." 
 * LP204128: Vista jams Wubi when ejecting the CD
 * LP222690: install failed during "import document and setting" at 88% - French windows XP
 * LP223250: Improved country detection
 * LP226622: Wubi has unclear error message on NTFS dirty flag
 * LP224697: Disable hibernation if swap is on file
 * LP136682: File with non-C/special characters in host computer disappear
 * LP226622: Wubi has unclear error message on NTFS dirty flag
 * LP236741: Wubi may erase the wrong ubuntu directory when uninstalling
 * LP227023: Vista bootloader does not get updated in some circumstancesae
 * LP223155: Wubi failed to install with 255.488MB of RAM (this is now a warning)

What 8.04.1 does not fix:

 * LP230716: Installer get stacked when extracting the ISO file from CD
 * Installation over (software) RAID 0 or 1 is NOT supported, this will be supported in the 8.10 release
 * Installation over encrypted disks
 * Whenever regular Ubuntu requires workarounds for incompatible hardware such as special boot paramters (acpi=off or all_generic_ide) or incorrect video driver, the same applies to Wubi (press ESC at boot to get a list of common workarounds).
 * Installation with fragmented swap file may fail (in this case run JKDefrag on your drive and reinstall Wubi).
 * DVD ISO and Alternate ISO are NOT supported, again this version only supports the 8.04.1 DESKTOP DAILY ISO (pay attention to the .1 at the end...)

---

### Post by rawlwear on 2008-06-22
I got it to run I tried kubuntu , i only noticed one thing that it was having problem updating, when i would click fetch updates it will load all the ones to download but wouldn't let me click appy, i tried restarting to see if that would work but no luck with that. 


I uninstalled that verison and went to reinstall version 8.04 but it keeps saying the download was interrupted with an error? whats with that?

---

### Post by brettfromokla on 2008-06-23
I am having the same problem as rawlwear. my download stops and shuts down the install.

---

### Post by ago on 2008-06-23
> **rawlwear said:**
> I got it to run I tried kubuntu , i only noticed one thing that it was having problem updating, when i would click fetch updates it will load all the ones to download but wouldn't let me click appy, i tried restarting to see if that would work but no luck with that.
That does not sound like a wubi problem 


> I uninstalled that verison and went to reinstall version 8.04 but it keeps saying the download was interrupted with an error? whats with that?
It probably means that the server is down. You can download manually and place the iso in the same folder.

---

### Post by ago on 2008-06-23
> **brettfromokla said:**
> I am having the same problem as rawlwear. my download stops and shuts down the install.

This sounds more like a segfault, try to download the ISO manually then

---

### Post by sbeattie on 2008-06-24
Excellent, that's good to know!

I'd like to point out that a few of fixes are still siting in the hardy-proposed queue awaiting verification that the fix actually addresses the issue. It would be great if some Wubi users could go through and confirm that the issues are indeed fixed.

In particular, the following Wubi-related bugfixes are marked as needing verification in Launchpad:

* LP230716: Installer get stacked when extracting the ISO file from CD
* LP217348: Ubuntu cannot boot when there are multiple hard disks
* LP136682: File with non-C/special characters in host computer disappear
* LP222690: install failed during "import document and setting" at 88% - French windows XP
* LP226622: Wubi has unclear error message on NTFS dirty flag
* LP238701: Support bindmounts when detecting the target mountpoint

To verify, first try to recreate the problem with the original 8.04 Wubi, then attempt to reproduce the problem in the 8.04.1 Wubi pre-release. Finally report whatever you learn from that in a comment to the bug you're trying to verify. The steps you took, whether you were successful or not, and any other problems/regressions you might have noticed are all useful information to report. More information about doing bugfix verifications is available at [URL="https://wiki.ubuntu.com/QATeam/PerformingSRUVerification"]https://wiki.ubuntu.com/QATeam/PerformingSRUVerification
[/URL].
Also, going on today (June 26, 2008) is a Bug Hug day dedicated specifically to trying to verify fixes that are currently sitting in hardy-proposed and waiting to be released as an update. So if you want guidance on doing trying to verify these WUBI fixes, please join the #ubuntu-bugs IRC channel on irc.freenode.org. More information on the Bug Hug day is at [https://wiki.ubuntu.com/UbuntuBugDay/20080624]("https://wiki.ubuntu.com/UbuntuBugDay/20080624").

Thanks for helping to make Wubi and the rest of Ubuntu Hardy Heron better!

---

### Post by rawlwear on 2008-06-24
well i fianlly got 8.40.1 back installed, but I have one other problem  whenever I ever try to install an app it says "break install", i tried from the add/remove, and from the package manger etc but still wont work. it sad something like the installation of some packages is pending/broken in cache. any help?

---

### Post by Unixus on 2008-06-25
Anything changed/being done about wubi downloading the cd image through a http proxy?

---

### Post by ago on 2008-06-25
> **Unixus said:**
> Anything changed/being done about wubi downloading the cd image through a http proxy?

No, that will be addressed in 8.10. For the time being you can download the ISO manually and place it in the same folder as wubi.exe.

---

### Post by ago on 2008-06-26
VERIFICATION NEEDED:

* LP207137 Installer get stacked when extracting the ISO file from CD
* LP136682: File with non-C/special characters in host computer disappear 
* LP224311: Ubuntu gets stuck at reboot with the message: "Turning on gate A20" or "...upper memory..."
* LP223250: Improved country detection
* LP236741: Wubi may erase the wrong ubuntu directory when uninstalling
* LP227023: Vista bootloader does not get updated in some circumstances
* LP223155: Wubi failed to install with 255.488MB of RAM (this is now a warning)

Please help testing 8.04.1 and report success/failures in the respective bug reports in [http://bugslaunchpd.net](http://bugslaunchpd.net)

VERIFICATION DONE:

* LP230716: Allow casper to boot off a directory (there is a new bug #243105 though)
* LP217348: Ubuntu cannot boot when there are multiple hard disks
* LP222690: install failed during "import document and setting" at 88% - French windows XP
* LP204128: Vista jams Wubi when ejecting the CD
* LP224697: Disable hibernation if swap is on file
* LP226622: Wubi has unclear error message on NTFS dirty flag. Half done, the patch is ok but the panic message is not always displayed because of a different bug.

---

### Post by beameup on 2008-06-30
So I have to reinstall to update?

Not having any problems with my initial install from the 8.04 CD.

---

### Post by ago on 2008-06-30
> **beameup said:**
> So I have to reinstall to update?

Not having any problems with my initial install from the 8.04 CD.

No reason, 8.04.1 is only useful for people experiencing problems installing with wubi 8.04. For all the rest regular updates will do the job just fine.

---

