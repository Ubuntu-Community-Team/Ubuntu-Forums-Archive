---
title: "Lubi: Wubi for Linux: Install *ubuntu on any Linux, no partitioning needed"
date: 2007-05-13
forum: General Help
---

### Post by tuxcantfly on 2007-05-13
[COLOR="Red"]_***LUBI NOW HAS ITS OWN WEBSITE AND GUIDE AT [http://lubi.sourceforge.net/lubi.html](http://lubi.sourceforge.net/lubi.html)***_[/COLOR]

Ever wanted to test the new K/X/Ubuntu 7.04 Feisty, but don't have a spare partition, and don't want to jeopardize your production environment by resizing partitions, dist-updating, or tinkering with its bootloader? Now you can leave your existing Linux distro (Ubuntu, Debian, Sabayon, Fedora, openSUSE, Gentoo, etc.) untouched, while being able to use Ubuntu 7.04 Feisty in a full-fledged install on a loopmounted partition, no partitioning required!

**NOTE: Lubi can only install Ubuntu. If you want to install other distros without a CD such as Fedora, OpenSuse, Mandriva, Debian, or Arch Linux, use UNetbootin; site at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) and forums at [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540) Also, Lubi cannot run from Windows; if you want to do a no-CD install of Linux from Windows, use UNetbootin (for a full, standard, real-partition install) or Wubi (for a loopmounted install). Also, Lubi does not support installing Ubuntu versions other than 7.04; for these, use [UNetbootin]("http://unetbootin.sourceforge.net") instead.**

**Credits**

I wrote Lubi and this guide. Lupin [http://launchpad.net/lupin](http://launchpad.net/lupin) is used as the codebase, see the Wubi forum at [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234) and the site at [http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html) for details.

**Tested Versions**

This has been tested on Sabayon 3.3 32-bit, PCLinuxOS 2007 32-bit, openSUSE 10.2 32-bit, Gentoo 2007.0 32-bit, Fedora Core 6 32-bit, Debian Sid 32-bit, Ubuntu 6.10 Edgy 32-bit, Ubuntu 7.04 Feisty 32-bit, and Xubuntu 7.04 Feisty 32-bit as the host systems. Kubuntu 7.04 Feisty 32-bit, Xubuntu 7.04 Feisty 32-bit, and Ubuntu 7.04 Feisty 32-bit were tested as guest systems. Other distros and versions, both 32-bit and 64-bit should work as the host system, just make sure you have the packages installed that are listed below. Distros and versions not based on Ubuntu 7.04 Feisty, and non-x86 architectures can also be used as the guest system, but these will require a custom build of lupin; see [https://launchpad.net/lupin](https://launchpad.net/lupin) for details.* **Installations using LVM as the root filesystem are currently not supported***. If this works/doesn't work for you please post the host/guest distro, version, and architecture.

**What it does**

Basically, it downloads a K/X/Ubuntu alternate i386 iso, creates loopmounted disk images so that they can be installed there, and adds an entry into /boot/grub/menu.lst which starts the d-i installer with that iso, and installs it into the loopmounted disk images. What thus results is a dual-boot system, in which K/X/Ubuntu are installed in loopmounted disk images in the folder /wubi/ on the filesystem, so that they can be installed without requiring any repartitioning, and they are booted using the system's GRUB, with the last menu entry, "Ubuntu", being added by the script to boot the loopmounted disk images.

**Requirements/Dependencies**

Before installing, please ensure that you have zenity (used for the GUI), and GRUB (used as the bootloader) installed. If not, install zenity and grub using emerge, apt-get, yum, yast2, or your distribution's equivalent. For Ubuntu and Debian, these should already have been installed.

**Installing**

You can either follow my step-by-step **video tutorial** at [http://blip.tv/file/331040/](http://blip.tv/file/331040/) or follow the instructions below:

1. Download the latest lubi package (deb for ubuntu/debian-based, tar.bz2 for others) from: [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

2. Then, become root:

For openSUSE and other su-based distros, login as root, while in Ubuntu and other sudo-based distros, enter:
```
sudo -s
```

3. Then, if you are using the deb version, just install it, or if you are using the tar.bz2 version, extract it to the root filesystem

4. Then, either click Applications -> System Tools -> Lubi or enter the command "sudo lubi"

5. Answer the questions asked by the wizard, wait while the iso is downloaded, the disk images are created, and the grub entry is added, and you will then be prompted to reboot; reboot.

6. Upon rebooting, the GRUB menu should have a new line at the end, saying "Ubuntu". Select that one, and it will start the d-i installer in non-interactive mode, and will reboot again

7. Select "Ubuntu" in GRUB to boot your newly installed ubuntu, then upon booting, login with the username and password you supplied to the installer

**Uninstalling/Removal/Undoing Changes**

If using the deb version, enter this command to remove:

```
sudo dpkg --purge lubi
```

For the tar.bz2 version, these commands, entered in the terminal on the host system (NOT in the guest Ubuntu install), will remove your loopmounted Ubuntu install, and undo the changes to GRUB:
```

sudo rm -r /wubi
sudo rm /usr/share/applications/lubi.desktop
sudo rm /usr/share/menu/lubi
sudo mv /boot/grub/menu.lst.bak /boot/grub/menu.lst
```

Use this guide at your own risk, though if you encounter issues related to loopmounted installation, you should ask them in the Wubi forums at [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234) as it is a generic Lupin/Wubi issue, not a Lubi problem. Post any issues related to Lubi here, and include the host and guest distro, architecture, and version. Also post results if installation succeeds on a host/guest distro/version/architecture combination that isn't listed above. The main lubi development page is at [https://launchpad.net/lubi](https://launchpad.net/lubi)

---

### Post by tuxcantfly on 2007-05-13
Ignore this, I'm subscribing to this thread

---

### Post by tuxcantfly on 2007-05-13
for anybody having issues logging on: username and password are:

ubuntu
ubuntu

I'll have this fixed eventually, but until then, that's the workaround

---

### Post by tuxcantfly on 2007-05-16
ok, the username/password issue should now be fixed, ignore the old advice

This thread has been approved into the howtos section, so post any replies there, at [http://ubuntuforums.org/showthread.php?t=442597](http://ubuntuforums.org/showthread.php?t=442597) to avoid a duplicate thread... closing this thread...

---

### Post by tuxcantfly on 2007-05-21
After the latest slew of tests on a variety of distros, Lubi appears to be ready to go, I'm reopening this thread and stickying to bring this version to the users' attention...

---

### Post by nu2this on 2007-05-25
Not quite clear on somethings
1st ```
sudo rm -r /wubi
sudo mv /boot/grub/menu.lst.bak /boot/grub/menu.lst
```
if its lubi I'm removving would that /wubi be /lubi instead?
2nd in a dual boot set up this way as say MYLINUX & Ubuntu is the removal code put into Terminal in Ubuntu or in MYLINUX?

---

### Post by tuxcantfly on 2007-05-25
> Not quite clear on somethings
1st
Code:

sudo rm -r /wubi
sudo mv /boot/grub/menu.lst.bak /boot/grub/menu.lst

if its lubi I'm removving would that /wubi be /lubi instead?

No, it's correct as stated in the instructions; it's because of a couple of issues with lupin that haven't been worked out that hardcode the directory to /wubi and prevent it from working properly with /lubi; it's /wubi.

> 2nd in a dual boot set up this way as say MYLINUX & Ubuntu is the removal code put into Terminal in Ubuntu or in MYLINUX?

In MYLINUX, I've clarified the instructions in my first post

---

### Post by nu2this on 2007-05-25
Thanks! Tuxcantfly I'm all clear now.

---

### Post by tuxcantfly on 2007-05-25
The new version (same download spot) can now work without zenity; simply give it the appropriate command line options from the terminal.
For details, enter:

```
sh lubi.sh -h all
```

---

### Post by dragon_788 on 2007-05-26
Currently attempting to install this on Sabayon Linux 3.4 loop 2 32 bit. Thanks for the great work on Wubi/Lubi, I've installed Wubi at work where I don't have the time to mess with resizing partitions and reformatting and such. 
Has moving a wubi loopback image between systems been tested? I realize that the bootloader would have to be updated but I'm thinking more in terms of moving it between a virtual machine and a physical machine (both running Windows).

---

### Post by Lucho77 on 2007-05-27
I am trying to install 'Ubuntu 7.04' in a 'Dell inspiron 5000 laptop', 
HD 9 GB Total (2 GB for Win98SE, 7 GB as logical so far, I want this one as Ubuntu 7.04)
RAM 64 MB
I downloaded the 'Wubi-7.04-test2.exe' runs good in 'low memory mode' until the the 'rezising partition time comes then sleeps forever in that screen, had to turn off the laptop by pushing the power button 5 secs. Any advice please. Thanks.

---

### Post by tuxcantfly on 2007-05-27
@Lucho77: this is a known issue, and we're in the process of solving it, go see [http://ubuntuforums.org/showthread.php?t=441577](http://ubuntuforums.org/showthread.php?t=441577) for advice on how to fix it. PS, I noticed that you were in the wubi-netboot thread, and it appears that your win9x bootloader was correctly configured this time; if so, just replace the standard wubi initrd and kernel with the ones from the wubi-netboot package, and that'll fix this issue (though it'll install to a dedicated partition, rather than a loopmounted file)
> Has moving a wubi loopback image between systems been tested? I realize that the bootloader would have to be updated but I'm thinking more in terms of moving it between a virtual machine and a physical machine (both running Windows).

I wouldn't quite recommend trying to do that... virtual machines use a different set of hardware, you'll probably be left with a non-functional install if you try that, and you'll have to tinker with lots of hardware config files... it'll be easier simply to do an install from scratch.

PS, this is a thread specifically made for Lubi, if your issues are Wubi issues, ask them in the general Wubi forums [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

---

### Post by dragon_788 on 2007-05-29
Thought I'd report on my progress (or lack thereof) with Lubi in Sabayon on my Gateway CX210X. I got it installed, but every time it tried booting the X server would crash and I was unable to resolve that with any of the methods I tried. I changed display devices, attempted to change drivers, but was unable to install new video drivers because for some reason the onboard NIC in my laptop was unable to properly get an IP, I got an IRQ error. The only way I got it to boot was in VGA mode, but no distro released recently is optimized for it and so I couldn't see half of the information that was trying to be displayed so I gave up. I've booted an Ubuntu LiveDVD on the laptop without any issues so I know the hardware support is there, not quite sure what the issue is.

---

### Post by tuxcantfly on 2007-05-29
> Thought I'd report on my progress (or lack thereof) with Lubi in Sabayon on my Gateway CX210X. I got it installed, but every time it tried booting the X server would crash and I was unable to resolve that with any of the methods I tried. I changed display devices, attempted to change drivers, but was unable to install new video drivers because for some reason the onboard NIC in my laptop was unable to properly get an IP, I got an IRQ error. The only way I got it to boot was in VGA mode, but no distro released recently is optimized for it and so I couldn't see half of the information that was trying to be displayed so I gave up. I've booted an Ubuntu LiveDVD on the laptop without any issues so I know the hardware support is there, not quite sure what the issue is.

Interesting issue... this Ubuntu LiveDVD you booted with, is it a standard Feisty (Ubuntu 7.04) version? Or is it an older Edgy (6.10) or Dapper (6.06LTS) release? I've heard that there were some regressions on Xorg support for some ATI cards in Feisty, that might be the issue... Also, is it a CD or DVD? The standard Ubuntu disks aren't on DVDs, but on CDs... perhaps you were using the "Ultimate Edition" or some similar version with extra bundled drivers (fglrx, in particular)? My guess would be that your Radeon card isn't supported by Feisty, only through the fglrx drivers (included in unofficial Ubuntu DVD versions, and Sabyon by default) or maybe by the default drivers of some older Ubuntu versions... Maybe the same issue would be the same with the networking...

Unless the issue has something to do with the partitioning scheme and the mounting process in booting, which apparently worked, Lubi/Wubi shouldn't technically be the cause of these issues, since it just uses the standard Ubuntu d-i code used in the installer...

Have you tried doing a sudo dpkg-reconfigure xserver-xorg and selected a different resolution, or tried the "vesa" or "radeon" driver? Those might help with the video card issues... Apart from that, I have no clue, if you were using a different version of Ubuntu than 7.04 as your live disk, or some unofficial DVD version, could you try booting with the Ubuntu 7.04 Desktop CD, to see if it really is a bug with the Wubi/Lubi/Lupin hardware configuration process, or is just a general Feisty hardware regression issue?

2 other potential issues: 1) Are you using LVM on your Sabayon install? Lubi won't work if you are... 2) Did you use the alternate i386 k/x/ubuntu iso, and verified its MD5sums for corruption?

---

### Post by adewale on 2007-06-09
i use ubuntu edgy and would like to install fiesty using lubi. i have a copy of the iso on my home folder and want to install. i don't want it to redownload the iso can you help me thanks

---

### Post by tuxcantfly on 2007-06-09
> i use ubuntu edgy and would like to install fiesty using lubi. i have a copy of the iso on my home folder and want to install. i don't want it to redownload the iso can you help me thanks

First of all, make sure you're using the feisty alternate iso, NOT the desktop one. The filename should be ubuntu-7.04-alternate-i386.iso, if you have something else you're out of luck, you'll need to let Lubi download the right one. Wubi/Lubi/Lupin doesn't support the desktop/live version yet, just the alternate, due to the lack of ubiquity automation, which will only be completed in gutsy.

When you start the script, a dialog should pop up asking if you want to to download the iso or use your own iso; select the use your own iso option, and give it the file location in the browser dialog that pops up, and that's all you'll need. Again, this will ONLY work on alternate isos, not on the desktop ones.

---

### Post by pongster on 2007-07-06
hey tux, great tut!  say i wanted to use Dreamlinux as a guest OS, what custom version of lupin would i need?

---

### Post by tuxcantfly on 2007-07-06
> hey tux, great tut! say i wanted to use Dreamlinux as a guest OS, what custom version of lupin would i need?

Someone would need to run the lupin build script on the targeted platform once, so that there would be a lupin binary for that particular kernel (we only currently have a build for feisty's kernel 2.6.20)...

EDIT: Seems like Dreamlinux is only available in a livecd... Could anyone point me to the alternate, or install-only iso (I can only find a livecd on their site); Lupin (the backend for both Lubi and Wubi) only currently supports distros that have d-i, that is ubuntu and debian, and distros based on them...

---

### Post by pongster on 2007-07-07
> **tuxcantfly said:**
> Someone would need to run the lupin build script on the targeted platform once, so that there would be a lupin binary for that particular kernel (we only currently have a build for feisty's kernel 2.6.20)...

EDIT: Seems like Dreamlinux is only available in a livecd... Could anyone point me to the alternate, or install-only iso (I can only find a livecd on their site); Lupin (the backend for both Lubi and Wubi) only currently supports distros that have d-i, that is ubuntu and debian, and distros based on them...

I think Dream only comes as a livecd... but its based on debian etch if it makes any difference...

Will lupin support linuxmint as a guest? since mint is based on feisty?  thanks:)

---

### Post by tuxcantfly on 2007-07-07
> Will lupin support linuxmint as a guest? since mint is based on feisty? thanks

Not that either... They don't supply an alternate iso, only a livecd image (make sure to tell us if there is one, though) (only the installer, not livecd isos are supported), but then again, in the gutsy version, it probably will, due to ubiquity-automation (which allows ubiquity to be used in a d-i interface, so lupin would work on the livecds with ubiquity-automation), but that's not in feisty...

---

### Post by tuxcantfly on 2007-07-07
This guide is currently broken due to the latest revisions in lupin, I've finished the code adaptions but haven't yet updated the entire guide... Here's a temporary guide...

the deb package is at:
[http://cutlersoftware.com/ubuntusetup/lubi/downloads/lubi_68_all.deb](http://cutlersoftware.com/ubuntusetup/lubi/downloads/lubi_68_all.deb)

the command to install is:
```
sudo lubi
```

the command to remove is:
```
sudo dpkg --purge lubi
```

---

### Post by tuxcantfly on 2007-07-07
I've moved the downloads to sourceforge (more bandwidth than cutlersoftware), releases will now be at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) and a website is in the works...

---

### Post by tuxcantfly on 2007-07-08
website for lubi and lvpm is here: [http://lubi.sourceforge.net/](http://lubi.sourceforge.net/)

---

### Post by tuxcantfly on 2007-07-24
new version is out (7.04.02), updates the lupin core to the same one as used in wubi 7.04.04

---

### Post by moshazat on 2007-07-31
can i use lubi, in ubuntu which i boot using wubi on windows?

its like (windows(ubuntu(openSuse)))

---

### Post by tuxcantfly on 2007-08-01
> can i use lubi, in ubuntu which i boot using wubi on windows?

No. If you only have Windows, just use Wubi; you'll see more details at [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
> 
its like (windows(ubuntu(openSuse)))

I don't think you quite understand the point of Lubi; it's meant to install Ubuntu and its derivatives under basically any type of Linux/*nix, not the other way around. You can install Ubuntu under openSuse using Lubi, but not the other way around.

---

### Post by moshazat on 2007-08-02
owh sory2, i misunderstand to lubi function... ok ok now i understand... thanx for the explanation :D sory k

---

### Post by CyberCod on 2007-08-05
My question about Lubi is "where does the Ubuntu installation go?"

I'm running Ubuntu Dapper, and its partition is nearly full... although I have another partition with some room on it... 

I wanna install Ubuntu Studio, but don't want to lose everything I have or have a big ole hassel.  Is there some way of stipulating where the new installation gets put?  And can it be put on a Fat32 partition?

I'm assuming of course, that its installed to a virtual partition...

Can someone clarify a bit?  PlzThnx

---

### Post by tuxcantfly on 2007-08-05
> My question about Lubi is "where does the Ubuntu installation go?"

/wubi, on the drive you specified to the installer.

> I'm assuming of course, that its installed to a virtual partition...

you're correct, it is

> And can it be put on a Fat32 partition?

yes, only you'll have to keep the virtual disk files smaller than 4GB

---

### Post by CyberCod on 2007-08-05
Ok... so if I'm understanding this right, I only need to mount my other partition (hda2) at /wubi... right?  Will the installation harm the files in there? or will it just add a new folder?

Will the new installation be able to see partitions outside of its virtual disk?

namely, can I mount hda2 in it even though its in a file inside of hda2?

---

### Post by tuxcantfly on 2007-08-05
> Ok... so if I'm understanding this right, I only need to mount my other partition (hda2) at /wubi... right? Will the installation harm the files in there? or will it just add a new folder?

Will the new installation be able to see partitions outside of its virtual disk?

namely, can I mount hda2 in it even though its in a file inside of hda2?

Sounds right, but I've never tried doing that. Just wait a little, I'm building a new version that can handle different installation targets...

---

### Post by CyberCod on 2007-08-05
Awesome... That sounds like it would be much easier and less risky than trying something like I mentioned in my above post.

That would be a very useful feature...Many people splice their Ubuntu installations up into multiple partitions... so that /home and/or /boot can be kept when re-installing.    
The root directory and namely new folders in it (ie: /wubi) may only contain a small portion of a user's entire drive.  On my main box, for instance, I've got 6GB dedicated to Ubuntu, 2GB as a swap, and 250+GB as storage space on hda2 still formatted in Fat32 from when I was dual booting with Win.  I just installed another box today with 5 GB for Ubuntu, 5GB for an as yet undecided distro, 300MB for /boot, and 29GB for /home.  (not sure how I will like this set up yet, I'm just experimenting)

I wish there was a tool that could change the format of a partition without losing its contents... but thats probably never going to happen :(
the 4GB limit on Fat32 gets on my nerves, but I'd have to burn over 200GB of data just to clean it off to change its filesystem.

Any ETA on the version you're working on with that capability?  No rush, mind you, just curious.

---

### Post by tuxcantfly on 2007-08-06
> Any ETA on the version you're working on with that capability? No rush, mind you, just curious.

New version has been released, Lubi-7.04.04, featuring the ability to install to non-root partitions. Also added a makeself-based self-extracting installer for non-Ubuntu/Debian-based distros to use. Please see the download page at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

---

### Post by tuxcantfly on 2007-08-06
I just posted a step-by-step video tutorial of how to use Lubi (basically until the reboot point, after which everything is automatic) at blip.tv (5.7 MB, ogg theora format, but you can use the java-based player if on Windows/Mac), see [http://blip.tv/file/331040/](http://blip.tv/file/331040/)

---

### Post by tuxcantfly on 2007-08-07
Website has been updated, see the new and improved version at [http://lubi.sourceforge.net/](http://lubi.sourceforge.net/)

---

### Post by CyberCod on 2007-08-11
Question...

if I install this to my partition hda2, will the rest of the partition be visible to the Lubi installed ubuntu install?

I keep media on hda2, and if I install it there, in a folder, will I be able to mount it to watch media contained on it via the lubi installed ubuntu?

---

### Post by tuxcantfly on 2007-08-22
> if I install this to my partition hda2, will the rest of the partition be visible to the Lubi installed ubuntu install?

I keep media on hda2, and if I install it there, in a folder, will I be able to mount it to watch media contained on it via the lubi installed ubuntu?

The drive you installed to will be at /media/host and the other drives can be mounted manually

---

### Post by mirak63 on 2007-10-05
Can this work for any linux distro ?
what is the mandatory thing ?
only lupin module in the kernel ?

---

### Post by tuxcantfly on 2007-10-05
> **mirak63 said:**
> Can this work for any linux distro ?
what is the mandatory thing ?
only lupin module in the kernel ?

Lubi can run from basically any distro, but it can only install Ubuntu, due to some portability issues in the loopmounting code we developed (lupin) and its dependency on d-i. However, if you want something that can run off either Windows or Linux, and can install several distros without a CD (currently Ubuntu, Fedora, OpenSuse, Mandriva, Debian, and Arch Linux, more coming soon), you might want to check out another tool I developed, UNetbootin, the site is at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) and I have a forum thread at [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)

---

### Post by hifi25nl on 2007-10-14
I have some problems installing Kubuntu in my debian system with lubi. When I reboot I have some errors about not finding the right file and some suggestions about checking find= 
I have configured lubi with an image already downloaded (kubuntu-7.10-beta-desktop-i386) that lubi has copied to /wubi/install
Wubi is installed in /dev/hda1. Same problem if I try an install in /dev/sda1, the hard disk from where I am booting debian.
I have tried some changes to menu.lst of grub withuout success.
What can I do?

Piero

This is my system menu.lst:
-----------------------------------------
title		Debian GNU/Linux, kernel 2.6.22.6-roo-1
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22.6-roo-1 root=UUID=4b9e99b7-87b1-4e42-b1be-e8b365d0a228 ro ramdisk_size=100000 lang=us apm=power-off nomce vga=0x317 
initrd		/boot/initrd.img-2.6.22.6-roo-1

### END DEBIAN AUTOMAGIC KERNELS LIST

title Ubuntu
root (hd1,0)
configfile /wubi/boot/grub/menu.lst
____________________________

This is my /wubi/boot/grub/menu.lst:

----------------------------------------
title Ubuntu
root (hd1,0)
kernel /wubi/boot/linux find=/wubi/boot/linux quiet ro
initrd /wubi/boot/initrd
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
root (hd1,0)
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=kubuntu-7.10-beta-desktop-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot
------------------------------------------------

Thsi is the part of my fstab concerning hard disks (one is serial ata, from where I am booting, dev/sda1, the other is dev/hda1):

------------------------------------------------

UUID=4b9e99b7-87b1-4e42-b1be-e8b365d0a228	      /               reiserfs defaults        0       1
UUID=c2ec2405-da78-4d24-9f36-8e67f3ab5ded	      /media/hda1     reiserfs defaults,users  0       1
UUID=d3d3c463-0039-4ffc-8970-b0b1b86cc103	      none            swap    sw              0       0

---

### Post by tuxcantfly on 2007-10-14
> **hifi25nl said:**
> I have some problems installing Kubuntu in my debian system with lubi. When I reboot I have some errors about not finding the right file and some suggestions about checking find= 
I have configured lubi with an image already downloaded (kubuntu-7.10-beta-desktop-i386) that lubi has copied to /wubi/install
Wubi is installed in /dev/hda1. Same problem if I try an install in /dev/sda1, the hard disk from where I am booting debian.
I have tried some changes to menu.lst of grub withuout success.
What can I do?

Piero

This is my system menu.lst:
-----------------------------------------
title		Debian GNU/Linux, kernel 2.6.22.6-roo-1
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22.6-roo-1 root=UUID=4b9e99b7-87b1-4e42-b1be-e8b365d0a228 ro ramdisk_size=100000 lang=us apm=power-off nomce vga=0x317 
initrd		/boot/initrd.img-2.6.22.6-roo-1

### END DEBIAN AUTOMAGIC KERNELS LIST

title Ubuntu
root (hd1,0)
configfile /wubi/boot/grub/menu.lst
____________________________

This is my /wubi/boot/grub/menu.lst:

----------------------------------------
title Ubuntu
root (hd1,0)
kernel /wubi/boot/linux find=/wubi/boot/linux quiet ro
initrd /wubi/boot/initrd
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
root (hd1,0)
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=kubuntu-7.10-beta-desktop-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot
------------------------------------------------

Thsi is the part of my fstab concerning hard disks (one is serial ata, from where I am booting, dev/sda1, the other is dev/hda1):

------------------------------------------------

UUID=4b9e99b7-87b1-4e42-b1be-e8b365d0a228	      /               reiserfs defaults        0       1
UUID=c2ec2405-da78-4d24-9f36-8e67f3ab5ded	      /media/hda1     reiserfs defaults,users  0       1
UUID=d3d3c463-0039-4ffc-8970-b0b1b86cc103	      none            swap    sw              0       0

Lubi won't work using the 7.10 desktop iso. Use the 7.04 alternate iso, or if you want to install Ubuntu 7.10, use UNetbootin [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by sam1985 on 2008-02-04
Can someone tell me the  username and password for ubundu 7.04?
I downloaded it from [http://wubi-installer.org/]("http://wubi-installer.org/") , but it wants the login name and pass

[IMG]http://img119.imageshack.us/img119/1177/pic0011mv1.jpg[/IMG]


 thanks 
Samir

---

### Post by tuxcantfly on 2008-02-05
> **sam1985 said:**
> Can someone tell me the  username and password for ubundu 7.04?
I downloaded it from [http://wubi-installer.org/]("http://wubi-installer.org/") , but it wants the login name and pass

[IMG]http://img119.imageshack.us/img119/1177/pic0011mv1.jpg[/IMG]


 thanks 
Samir

The username and password should be whatever you provided during the initial installation prompt; there's no "master password" (for obvious security reasons). If you typed in what you originally entered, and it still spewed out an error, then that's a bug with Wubi (perhaps file a bug report, though given that the Wubi 7.04 branch isn't being maintained any longer since the focus is now on newer versions, I doubt it'll get fixed).

Anyhow, why are you installing Ubuntu 7.04? 7.10 has been out for a while, and has several improvements (and bugfixes) over the 7.04 version, so I'd install that instead. The 7.10 version of Wubi is available at [http://wubi.sourceforge.net/devel/minefield/](http://wubi.sourceforge.net/devel/minefield/) while the UNetbootin 7.04/7.10 versions are available at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) use whichever one works better for you; both can install Ubuntu without a CD, the difference being that UNetbootin provides more flexibility and does a proper Ubuntu install (like the standard CD), while Wubi is somewhat more user-friendly for novice users, though more problematic in the long run due to its usage of loopmounted partitions.

PS This is the Lubi thread, not the Wubi one. Ask questions about Wubi in the general Wubi forum at [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234) and UNetbootin questions at [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540) to keep topics nicely seperated and organized.

---

### Post by hackel on 2008-03-09
I am experiencing the same problem that hifi25nl mentioned above.  I'm using hardy-alternate-i386.iso from kubuntu-kde 8.04-alpha6.

Is it not possible yet to use lubi with Ubuntu 8.04?  Does lubi actually need to be updated for each version of Ubuntu that is released?  It would be nice if it could be done in a more general way.  In any case, any advice would be appreciated.

Cheers,
Ryan

---

### Post by tuxcantfly on 2008-03-09
> **hackel said:**
> I am experiencing the same problem that hifi25nl mentioned above.  I'm using hardy-alternate-i386.iso from kubuntu-kde 8.04-alpha6.

Is it not possible yet to use lubi with Ubuntu 8.04?  Does lubi actually need to be updated for each version of Ubuntu that is released?  It would be nice if it could be done in a more general way.  In any case, any advice would be appreciated.

Cheers,
Ryan

Yes, it does have to be updated for every version of Ubuntu that is released, because the various hacks required for loopmounted booting have changed with every Ubuntu version (and I haven't yet updated it for versions newer than 7.04; I've been working primarily on UNetbootin in my spare time these days). If you need a more "general" way, use UNetbootin [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) which can load/install any distro without a CD (just provide it with your own disk image/kernel/initrd if it isn't among those in the drop-down list).

---

### Post by pmorton on 2008-03-24
I am trying to load Ubuntu on a CD-less Thinkpad 240. 

Debian Etch is running on boot partition hda1; swap is hda2. (As an aside - the 3 Debian boot floppies do a great job of net-installing Debian on this machine, if you have a pcmcia network card).

I have set up spare ext3 partition hda3, 8.5GB in size, for Ubuntu. I have the Ubuntu 7.04 Alternate ISO on USB flashdrive sda1. I run lubi as root in Debian.  It asks for target partition and I choose /dev/hda3, which fstab has mounted at /media/hda3.  I choose default root/home/swap sizes. I point to sda1's mount point for the Ubuntu ISO, and Lubi says it is copying the ISO (apparetly to destination hda3). A progress bar shows, but doesn't fill. However, the USB flashdrive flashes away for a while, and seems to have copied over the ISO; folder wubi appears on hda, containing install, boot etc. Lubi invites me to reboot and select Ubuntu from grub. I do, but the installation halts with the error message:-

ERROR:
Unable to access Alternate ISO - probably the installation was interrupted.
Please run the installer again.

I have now tried this many times, and each time it fails with the same message. Any assistance will be much appreciated.

---

### Post by tuxcantfly on 2008-03-24
> **pmorton said:**
> I am trying to load Ubuntu on a CD-less Thinkpad 240. 

Debian Etch is running on boot partition hda1; swap is hda2. (As an aside - the 3 Debian boot floppies do a great job of net-installing Debian on this machine, if you have a pcmcia network card).

I have set up spare ext3 partition hda3, 8.5GB in size, for Ubuntu. I have the Ubuntu 7.04 Alternate ISO on USB flashdrive sda1. I run lubi as root in Debian.  It asks for target partition and I choose /dev/hda3, which fstab has mounted at /media/hda3.  I choose default root/home/swap sizes. I point to sda1's mount point for the Ubuntu ISO, and Lubi says it is copying the ISO (apparetly to destination hda3). A progress bar shows, but doesn't fill. However, the USB flashdrive flashes away for a while, and seems to have copied over the ISO; folder wubi appears on hda, containing install, boot etc. Lubi invites me to reboot and select Ubuntu from grub. I do, but the installation halts with the error message:-

ERROR:
Unable to access Alternate ISO - probably the installation was interrupted.
Please run the installer again.

I have now tried this many times, and each time it fails with the same message. Any assistance will be much appreciated.

**EDIT:** Nevermind, didn't notice some details in your post. It's likely some bug in the 7.04 version of the loopmounted-booting scripts (Lupin), which is pretty much unmaintained these days, since most effort is going into the version to be incorporated into 8.04. Unless you have some dire need to use a loopmounted partition, which, given that you're already running Debian, you probably don't need (ext3, and even NTFS partition resizing is quite safe and reliable these days), you should probably use UNetbootin, as described below (see the portion on using the HD-Media kernel/initrd to re-use your existing alternate iso), instead.

As for the progressbar, that's due to Lubi being implemented as a series of shellscripts with zenity as a makeshift GUI. UNetbootin doesn't have such issues; I'll most likely simply port the newer fronted code to C++/Qt4 and use it in conjunction with UNetbootin, thereby unifying the codebases required for the Windows, Linux, and future Mac OSX versions (with the exception of OS-specific bootloader-editing code), and essentially eliminating the need for the standalone Wubi/Lubi frontend codebases.

(ignore the following, I've reread the post more carefully and you seem to already have answered the questions; it isn't any of these issues; this is here only for reference, in case it helps)

What version of the iso are you using? Lubi currently only supports installing Ubuntu 7.04 and its derivatives (the loopmounted-booting code changed drastically over the releases, so it's rather difficult to add support for the newer versions; it'll most likely require a rewrite).

UNetbootin [http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net) or [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) however, supports installing any Ubuntu version (6.06-8.04) (as well as a slew of other distributions), the only difference being that it does a proper partition install, not a loopmounted-boot one, so if all you're looking for is a way to install Ubuntu without a CD, that should do the job.

Also, are you attempting to make a bootable USB flash drive for installing Ubuntu, rather than installing to a partition? That may also be the reason why you're encountering such errors; GRUB sometimes behaves awkwardly when installed on removable media. Try using UNetbootin; select the "USB Drive" install mode and it will install Syslinux to your USB drive; if you want to re-use your existing iso rather than use the netboot install approach, simply download the HD-Media kernel and initrd files from archive.ubuntu.com and select those on the "kernel" and "initrd" lines.

---

### Post by adromidon on 2008-07-27
If Lubi is so hard to crack for loopmounting then would Wubi not be the same as far as functionality? If so why not take the Wubi code and port it back to Linux to make an 8.0.4 compatible Lubi version?

---

### Post by Orlsend on 2008-10-25
Hello I am using Ubuntu installed with wubi, Could I use lubi to boot other OS's inside my wubi installation?

---

### Post by Ani on 2009-04-14
Does not seem to work for Ubuntu 9.04

It is looking for /cdrom/install/vmlinuz
however in Ubuntu 9.04 that file is located at /cdrom/casper/vmlinuz

---

### Post by jegHegy on 2010-03-06
I think Lubi would be a wonderful addition to the official Ubuntu repositories &#8212; however, it currently does not support EXT4, which has been the filesystem by default since 9.04.

This is a shame because it would make alpha/betatesting Ubuntu really easy. Actually I am baffled as to why the developers of Ubuntu haven't focused on this tool to make testing of Ubuntu development releases more convenient, without the hassle of partitioning.

edit: Forgot my actual question: Are there any plans to add support for EXT4?

---

### Post by sogeking99 on 2011-03-29
hey guys, i tried to use lubi but i messed up the size of the home and root, how can i delete it and try again?

---

