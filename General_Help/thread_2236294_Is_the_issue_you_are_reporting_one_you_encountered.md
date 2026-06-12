---
title: "Is the issue you are reporting one you encountered when upgrading Ubuntu from one rel"
date: 2014-07-25
forum: General Help
---

### Post by Mark_in_Hollywood on 2014-07-25
If a clean install doesn't clear up problems, what does?

I tried to make a clean install on my / partition for 12.04 yesterday. When the new packages were all updated, I updated the video driver as well. Next I tried to upgrade to Tahr. The install failed and a report was sent that asked to include my password. I sent it.

Today, I reinstalled Precise. The / partition was again reformatted during the install. I then updated and installed Gimp, printer driver packages and some other mundane stuff.

Looking at the Update Manager a moment ago, I saw, again, the "New Hardware Support if Available". I clicked the button. Another small window came up with a message about Hardware, which said: "New Hardware Support is Available - Your current Hardware Enablement Stack (HWE) is going out of support on 08/07/2014.  After this date security updates for critical parts (kernel and graphics stack) of your system will no longer be available.

For more information, please see:
http://wiki.ubuntu.com/1204_HWE_EOL"

The next radio button to click reads: "Upgrade". I clicked Upgrade.

Next the Package Manager brought up: "Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

libgl1-mesa-glx-lts-trusty: Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) but 10.1.3-0ubuntu0.1~precise1 is to be installed
                            Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.4.99.1-0ubuntu2.2 is to be installed
                            Depends: libxdamage1 (>= 1:1.1) but 1:1.1.3-2build1 is to be installed
xserver-xorg-lts-trusty: Depends: xserver-xorg-core-lts-trusty (>= 2:1.11) but 2:1.15.1-0ubuntu2~precise1 is to be installed

And a moment later, the Crash Report manager says:  "The Application Update Manager Has Closed Unexpectedly." Next another window pops up saying: "Is the issue you are reporting one you encountered when upgrading Ubuntu from one release to another?"  I don't honestly know the answer to that one. Since I had Precise installed, even thought I'm doing a clean install on the / partition and the /home has the objects saved from over the years on it, I said "Yes".

But this is where I started a few days before. Trying to resolve these unmet dependencies. Some nice helpful person suggested I  manually install/reinstall the few packages. I tried that, the result of which was the loss of the enitre OS due to trying to re-install the xserver-xorg-lts-trusty. That was my fault alone. I should have not allowed apt-get to remove 400 or so pacakges.

So here I am at an entirely new, less than 14 hours old install of Precise. It is giving me the same problems as before. How does one resolve unmet dependencies such as these?

I have pasted some of the 17,000 lines of install run at: [http://paste.ubuntu.com/7859451/](http://paste.ubuntu.com/7859451/)

Could not install the upgrades 

The upgrade has aborted. Your system could be in an unusable state. A 
recovery will run now (dpkg --configure -a). 

dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on checkbox-gui; however:
  Package checkbox-gui is not installed.
 ubuntu-desktop depends on ubuntu-session; however:
  Package ubuntu-session is not installed.
 ubuntu-desktop depends on unity-control-center; however:
  Package unity-control-center is not installed.
 ubuntu-desktop depends on unity-settings-daemon; however:
  Package unity-settings-daemon is not installed.

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-desktop

Upgrade complete 

The upgrade has completed but there were errors during the upgrade 
process.

---

### Post by bapoumba on 2014-07-25
Why did not you fresh installed 14.04 rather than installing 12.04 and upgrading ? If you are using ppas or other repos for the video drivers, release upgrades can be problematic.
And not even talking about this : [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264)
You seem to run into that bug.

---

### Post by kansasnoob on 2014-07-25
If you want to end up with 14.04 why not just install 14.04.1?

[http://releases.ubuntu.com/trusty/](http://releases.ubuntu.com/trusty/)

The Precise HWE EOL upgrade is very buggy so I'm recommending that people just wait until about August 8th before even trying it. If for some reason you want to stay on Precise you should install Precise using the archived 12.04.1 images:

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

They don't use the HWE stuff at all! Please read what I typed here:

[http://ubuntuforums.org/showthread.php?t=2236096&page=2&p=13082770#post13082770](http://ubuntuforums.org/showthread.php?t=2236096&page=2&p=13082770#post13082770)

Also read what I said here:

[http://ubuntuforums.org/showthread.php?t=2236253&p=13082735#post13082735](http://ubuntuforums.org/showthread.php?t=2236253&p=13082735#post13082735)

The bug report I linked to there is why you can't upgrade from Precise to Trusty with the Trusty HWE installed in Precise. I wish I'd caught it earlier but I am just a human being, an older one at that ;)

More about the whole LTS HWE support cycle here:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

And HWE EOL here:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

---

### Post by Mark_in_Hollywood on 2014-07-25
In response to bapoumba's question:

[COLOR="#FF0000"]Why did not you fresh installed 14.04 rather than installing 12.04 and upgrading ?[/COLOR]

I was under the impression that **upgrading** is the preferred method in Ubuntu. I wanted the OS to be un-problematic. Precise has been the workhorse for me. I believed a fresh install would have cleared the HWE EOL problems. My misunderstanding. I had tried to install "New Hardware Support is Available" packages and that has failed several times. As the Precise is running robustly otherwise, I was trying the conservative approach. My fault!

[COLOR="#FF0000"]In response to kansasnoob's questions:[/COLOR]

I had not read that the upgrade to 14.04.1 would be problematic anywhere. My fault. I will d/l the 64-bit PC (AMD64) desktop image, as I have an AMD-64 cpu. Only one question on that subject: I want to preserve my /sda2 or /home. Is this "desktop image" the right one for that? That is, will it offer the "Other" option during install and not re-format the partitions automatically? I remember that one image was "alternative install", that is the one that allowed preserving partitions.

So using the TT will obviate the problems with the hardware and warning about EOL for it?

I'm not trying to keep Precise. I'm trying to upgrade to Trusty Tahr (hereinafter TT). 

Per your suggestion to read the two posts about the problems. I guess I can wait until August, if that's the best way. If it isn't, please advise about a clean install of 14.04.1 on my /sda1 or "/" in Unix speak.

Thanks to both of you. You guys do Yeoman's jobs, almost without thanks, everyday.

PS - My Ubuntu "Backup" package ran today, flawlessly. Everything in my /home is backed up, safely, on an external hard drive. AFAIK.

---

### Post by bapoumba on 2014-07-26
Please post your current fstab, what do you have on sda2 ? :
```
cat /etc/fstab
```

During the install process, yes choose "do something else". The basic idea is to use your current root partition for Trusty during the install process (or any other spare partition should you want to multiple boot with your current install) - use ext4 - format. Choose your current /home - do not format, to have your new install use that /home. You can also choose a mount point for any other partition - do not format if you want to keep as is.
Once the install is finished and you reboot, all of these should be mounted in the new fstab and available.

---

### Post by Mark_in_Hollywood on 2014-07-26
OK, trusting to my sense that Ubuntu is really, really smart, I fired up the 14.04.1 LTS I put on a dvd, the day before yesterday. Install offered to preserve "/home" - although the words on the screen don't use "/home" they talk about files, music, etc.

Install ran in jig time. Fastest ever install. Wow!

Mr. B. I'm closing this and marking as Solved. 

Many thanks, sir.


```
mark@Lexington:/etc$ sudo blkid
/dev/sdb1: UUID="cbf68277-e2c3-4e5b-9b5d-8c531d42e00d" TYPE="ext4" 
/dev/sdb2: UUID="715fe15a-f2df-408b-b36c-bab4f424588b" TYPE="ext4" 
/dev/sdb3: UUID="27c7ef11-a0a6-4f6b-9be3-812c4aee7442" TYPE="swap" 
```

```
mark@Lexington:/etc$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=cbf68277-e2c3-4e5b-9b5d-8c531d42e00d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=715fe15a-f2df-408b-b36c-bab4f424588b /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=27c7ef11-a0a6-4f6b-9be3-812c4aee7442 none            swap    sw              0       0
```

---

