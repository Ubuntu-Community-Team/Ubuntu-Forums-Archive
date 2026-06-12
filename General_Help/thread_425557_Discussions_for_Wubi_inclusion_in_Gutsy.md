---
title: "Discussions for Wubi inclusion in Gutsy"
date: 2007-04-27
forum: General Help
---

### Post by Henrik on 2007-04-27
Hi,

First, great project! I've been playing with it a bit the past few days. 

At UDS in Seville we will discuss various options for a Windows-based installer. Wubi looks nice at this point, though it is not clear that we would want to go with the loop-mounted approach. The lack of support for Vista is a bit of a show-stopper ATM, but is of course common to all the projects relying on the NT boot loader. 

I've posted my discussion spec [here]("https://blueprints.launchpad.net/ubuntu/+spec/installer-for-windows"). Please note that it is currently technology-neutral. 

I thought you might appreciate the heads-up.

Henrik

---

### Post by tuxcantfly on 2007-04-27
> The lack of support for Vista is a bit of a show-stopper ATM, but is of course common to all the projects relying on the NT boot loader.

About the lack of Vista support, the Windows-based Debian installer supports vista as an experimental feature [http://lists.debian.org/debian-boot/2007/03/msg01168.html](http://lists.debian.org/debian-boot/2007/03/msg01168.html) which we're also trying to implement for Wubi as well. As a last-ditch resort, we could try to have it physically install GRUB to the MBR, though that would be rather invasive, error prone, and more difficult to remove, so we'd rather use something like GRLDR (which unfortunately doesn't support Vista yet).

> Wubi looks nice at this point, though it is not clear that we would want to go with the loop-mounted approach

About the loopmounted vs actual partitioning, Wubi can actually install to a real partition, with a few modifications to the preseed.cfg file; the only reason we use a loopmounted file by default are the risks associated with ntfs resizing, but if that's no longer an issue, we could easily get Wubi to resize and install on the real partition.

About the usage of a livecd, you may want to check out one of my older prototype builds, it's available at [http://cutlersoftware.com/ubuntusetup/releases/ubuntu-livecd-v2.zip](http://cutlersoftware.com/ubuntusetup/releases/ubuntu-livecd-v2.zip) and the installation instructions are at [http://cutlersoftware.com/ubuntusetup/index_old.html](http://cutlersoftware.com/ubuntusetup/index_old.html). It's not exactly an installer, but rather, it allows the user to boot the livecd from an iso file without an acutal cd, and then they can run the installer from there. It uses standard partitions and a standard ubuntu edgy livecd iso. It might have a few issues with booting up, since it's been unmaintained ever since we shifted the focus of development towards lupin, though we could probably merge back the lupin hardware detection changes if needed. It doesn't have a windows-based frontend, since I made it before Wubi was completed, though Wubi could easily be adapted to it.

For actual installation from a livecd, that would likely be more difficult, because ubiquity doesn't support automated installations, so we'd likely need a few modifications to ubiquity to do that, like a command-line interface, unless of course, the method I mentioned above is used; just boot the livecd in live mode from an iso file using a modified initrd, then use ubiquity to install the usual way. It doesn't exactly address all the issues, but it certainly eliminates the issues with burning cds, using portable laptops with no CD drives, and adjusting the BIOS settings.

As for the virtual machines, it's an interesting idea, and given the increasing performance and new features of virtual machines, it probably won't have too many performance issues, but I think it's simply more for hobbyists than for people who actually want to use ubuntu as a production environment; after all, booting 2 operating systems just to do some basic word processing is overkill, and a huge hassle. There's also the issue of direct hardware access, like using openGL applications in ubuntu like compiz or google earth, and stuff like using usb drives and cds as hardware under the virtual machine. Also, of course, using a virtual machine makes it harder to simply ditch Windows; you'll always have to boot Windows to boot Ubuntu, quite ironically, and you can't simply remove Windows and replace it with ubuntu. Of course, the second kind of applies to the current state of Wubi as well, but it's possible to simply remove the lupin-target package, and copy all the files over to the new partition, and install grub to it, and then delete the windows partition, ending up with a standard ubuntu install which can likely be automated with a nice little wizard, or if we decide to go with Wubi + real partition (just a few tweaks to preseed.cfg needed for that), it won't even be an issue at all.

About the fixed disk image size, our source code branch already has the ability to adjust the size, so the next release will probably fix that issue. As for dynamic resizing, I don't think that's really possible with EXT3, because it can't dynamically expand itself while mounted, so it'll need to reboot to expand itself, and use something like Topologilinux's toporesize.exe utility, though if we used reiserfs, which has the ability to expand itself on-the-go, we could probably have dynamic, transparent resizing abilities as well.

Anyhow, it's great to see that our project has been given some attention and consideration for official inclusion. By the way, is there some better place users could place these comments? I don't exactly see a comments page on the blueprint; you might want to add one...

---

### Post by ago on 2007-04-27
> **Henrik said:**
> Hi,

First, great project! I've been playing with it a bit the past few days. 

At UDS in Seville we will discuss various options for a Windows-based installer. Wubi looks nice at this point, though it is not clear that we would want to go with the loop-mounted approach. The lack of support for Vista is a bit of a show-stopper ATM, but is of course common to all the projects relying on the NT boot loader. 

I've posted my discussion spec [here]("https://blueprints.launchpad.net/ubuntu/+spec/installer-for-windows"). Please note that it is currently technology-neutral. 

I thought you might appreciate the heads-up.

Henrik

Thanks Henrik.

First thing, let me tell you that we are honored of having been mentioned. We have always hoped to be incorporated as an "official" installation methods and we would be glad to cooperate to any future project. I have a few considerations:

1) I have also launched this spec [https://blueprints.launchpad.net/ubuntu/+spec/lupin](https://blueprints.launchpad.net/ubuntu/+spec/lupin) with the idea of merging lupin code within the standard initrd + livecd initrd. Please take that into account in your discussions. Lupin has been designed so that it should not be too difficult to incorporate within the "official" initramfs building mechanism. Probably the toughest obstacle is ntfs-3g support out of the box.

2) As for the Vista support, we simply do not have enough resources at the moment and most of us do not have a Vista machine to hack, but that does not mean that it cannot be achieved

3) It is well possible to use loopmounted installation in parallel with dedicated installation. IMO the behaviour should be: if there is free space do a dedicated installation, otherwise do a loopmounted installation. Give the possibility to override in the advanced settings

4) We are not yet ready for prime time, our "final" will be out in a few days, take that into account when you evaluate wubi.

5) I am not sure I will be able to attend, even in a conference call, but I would be glad to discuss any issue beforehand or afterward. I am going to subscribe though.

---

### Post by ago on 2007-04-27
Some further comments

* Does not yet work with Vista:
Yep but as mentioned that might be fixed 

* Uses alternate disc to install from
It can use the Live ISO as well with some mods. Anyway with wubi the ISO which is actually used is completely irrelevant, since the only role of the ISO is to provide a  source of packages and the process is hidden to the user. In fact the word "ISO" is banned within Wubi... There is no point in "live booting" to try it out, since installation takes 10-15 minutes and wubi makes it very easy to uninstall. So you try as you do with any other software: install it first and have a go, if you do not like it, uninstall.

* Fixed size disc image (would be nice to have a dynamic image or manual resize option)
New interface will allow to choose the disk size. Resizing the disk images after they are created is possible but tricky (can be done by copying the existing files onto a new image with a script within ubuntu), I did not investigate the possibility to use "flexible" files, but anything that can be mounted under Linux should work.

* Needs a dash of usplash in a few places
In the final version Usplash will be active on normal boot, but not on install. 

* Needs a graphical installer front-end to d-i
This will be a lesser issue once gtk frontend is available in the alternate ISO (which I assume it will be the case in Gutsy), since then we can use graphical progressbars. It is well possible to use usplash as a frontend for d-i, but that requires a bit more work. 

* Better post-install management features. A control panel running in windows that lets you resize discs, make backups, select between different installed systems
Ditto for resizing. Backups, if anything, are easier, since on top of all Ubuntu tools, you can simply copy the image files from within windows and the home folder is on a separate file by default. As for the latter, we encourage installing multiple desktops from within Ubuntu itself. The main issue at the moment is due to grldr limitations which require a double boot menu, multbooting straight from boot.ini is a bit tricky.

* How efficient is the loop mounted drive?
It has not been tested formally, but in my subjective experience you can hardly notice the difference (it becomes slow only if we miss a required  module...)

* How easy would it be to move such an install out from under windows to a separate partition (perhaps an improved version of the migration tool could be used?)
It should not be too problematic. Once a partition is created you can quite literally dump in there the content of the virtual hard disk file, then setup grub and adjust fstab. Lupin will need some minor mods, but that's about it.


Hope it helps

---

### Post by tuxcantfly on 2007-04-27
I've just stickied this thread; official inclusion is one of our top priorities after all... Subscribing...

---

### Post by Henrik on 2007-04-28
Hi All,

First, thanks for playing along :) I appreciate your willingness to consider different options. I think we all agree on the basic goals of the project:
[LIST=1]
[*]Provide a way to install Ubuntu without a CD ROM
[*]Allow the installation process to be started from Windows using a simple setup.exe file, which is the most natural for many Windows users
[*]Facilitate both a way to get up and running quickly and painlessly with Ubuntu for that all-important first taste that draws people in, while at the same time making it more sticky so the system can be used over some weeks or months (or longer). The Live CD generally fails to be sticky ATM.[/LIST]Within these general goals there is scope for different implementations, with strengths and weaknesses. We should not rush into picking a solution now, but should evaluate different solution from the perspective of a range of use cases.

**On using the Live CD:** 
I mention this because the Live CD is by far our most used medium and something like Wubi would fit in nicely with the WinFOSS section there (*Install now* could be made a prominent option)

Some work has been done on automating ubiquity installs but it did not make it in time for Feisty ([spec]("https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-automation")). If the win-install spec depended on it, it would likely be completed for Gutsy. 

That said, I'm not necessarily advocating booting completely to Gnome only to run a non-interactive ubiquity. One option would be to start only a bare X environment where it would run but I'd also like to look at copying the Live CD SquashFS directly to the partition or image file while running Windows. That way you could run the Wubi install from Windows, reboot (some post-install config would be done under usplash) and you would be done.


**On loopmount vs. partition vs. both: **
We need to figure out what is the best mix of options. One the one hand maximum flexibility would be great, but you also don't want to confuse the user with 20 choices.

Things that would be cool:[LIST]
[*] Ability to choose install from a CD image or from the net
[*] Ability to install either to an image file or to a partition
[*] The ability to convert from one kind to another
[*] Tools for cleaning up such as removing Grub (if used)
[*] Tools to migrate data between systems
[*] Burn the Live CD image from Wubi. This would make the Live CD self-replicating :)[/LIST]A typical scenario that we should keep in mind: Someone emails you a link to the 2mb setup.exe file. You run it and decide to install Ubuntu as an image just to see what it's like. After a month of using it you are convinced and decide to migrate from Windows completely. The Windows app helps you resize the NTFS partition and copies the content of the image file onto the freed space. You reboot and use gParted to remove Windows and resize (needless to say this all needs solid testing). 


Anyway, no need to sort out the technical details just yet, but rather just try to get an overview of the options.

---

### Post by ago on 2007-04-28
**Using a Live CD as base for Wubi/Lupin:**
The main advantage is that people can use a CD as opposed to download the ISO, and LiveCDs are more likely to be around than alternate CDs. Moreover, as you suggested, you can burn the live CD (let's be honest, an alternate CD is not as fancy). The main disadvantage is that the d-i installer (alternate ISO) is widely used by other debian based distros, moreover the user does not really "see" the ISO when installing, he should not be even aware of the existence of an ISO, and since most users would simply download the frontend and let that download the required files as opposed to burn an ISO, the advantage of a LiveCD would be arguable. In either case it would be good to have wubi inside the CD so that it is autostarted when the CD is played in windows.

Another possibility is to have wubi to boot the LiveISO without burning a CD. The problem with this approach is that the user has to go through 2 different wizards: one in windows which is required to modify the bootloader (and when there is no CD to download the ISO) + ubiquity. IMO 2 wizards is a no go. I think it is better to have just a windows frontend, which has a big advantage since it can autodetect most settings from a working OS, and use the live ISO only as a source of packages.

What is more interesting is to move away from nsis in favor of some frontend which is easy to port to other platforms. In this respect python + gtk is a possibility (a bit heavy but it will do), and in that case it might even be feasible to port ubiquity to windows.

As for using the live ISO in the backend, even after copying the squashfs there would be other d-i tasks to be accomplished.

**On loopmount vs. partition vs. both**
My view is simple: as soon as you mention the word "formatting" you loose 80% of the audience. The best option IMO is a loopmounted file with an easy way to migrate to a proper partition later on. The advantages of a "real" installation over a loopmounted one are also to be proven before people can justify the additional inconveniences due to repartitioning. Moreover, if you have support for a loomounted file, the installer becomes greatly simplified: no questions asked. Compare this to a partitioner GUI, it does not matter how you design the GUI, it is still going to be 2 or 3 extra clicks with some obscure and scary (for many) option, and you have to ask at least twice before touching the hard disk. Most people do not know what a partition is and there will never be an easy way to explain that, but if I go around and say that Wubi creates a folder with a few files in there, everybody is happy with the explanation. Finally, if you use a real installation, you cannot really uninstall and restore everything as it was before. The inability to uninstall cleanly is another show stopper. Uninstalling a loopmounted installation is fairly trivial: delete the fie/folder.

**Ability to choose install from a CD image or from the net**
If there is a CD it should be autodetected and used automatically. Same thing if there is an ISO laying around somewhere (we already do that). This is the main reason why it is convenient to base the installer on the live CD as opposed to the alternate CD. The option to pre-download the ISO vs downloading the files as required during installation from Linux is a no brainer since in the latter case you cannot guarantee that networking will be up, therefore it is strongly preferable to pre-download.

**Ability to install either to an image file or to a partition**
Wubi is based on d-i, so real installation is clearly possible, we have simply disabled the parted bits for now but it would not be to problematic to reactivate them... Netinstall is also a possibility (since that too uses d-i), but I do not think it is desirable.

**The ability to convert from one kind to another**
Agreed, but that is more likely a separate project. I think we should keep things simple to begin with.

**Tools for cleaning up such as removing Grub (if used)**
When wubi is uninstalled the system is restored to its previous state and everything is removed/restored, including grldr/menu.lst/boot.ini... Restoring the system to its original state after installing to a dedicated partition would be far more complicated.

**Tools to migrate data between systems**
New wubi version will include migration-assistant to import settings from windows.

**Burn the Live CD image from Wubi.**
We had this feature, it was removed since we were using the alternate ISO which is not as fancy once burned. There were also some licensing issues with the burner software.

---

### Post by ago on 2007-04-28
Regarding vista support, there is some code in the debian installer using bcedit and grldr.mbr, we will see if that works out well in the coming days.

---

### Post by konungursvia on 2007-04-28
I think one of the most important issues is font rendering. We need linux to surpass MS and Apple or at least keep abreast of them, otherwise, few will go with Linux as their main.

---

### Post by tuxcantfly on 2007-04-28
I've renamed this thread to Discussions for Wubi inclusion in Gutsy since people appear to be mistaking it for one of those general gutsy idea brainstorms

**Transferring from a loopmounted partition to a real one**

Slap on a GUI onto this code, and we'll have that bit done and addressed... Note that this won't yet work with the current version of Wubi, only with the one in the minefield source tree that will soon be released...

1. open gparted, shrink partitions and create a new ext3 one
2. sudo mount /dev/sda1 /media/extra
3. sudo cp -r / /media/extra
4. sudo chroot /media/extra
sudo dpkg --purge lupin-target
6. grub-install (hd0,0)

And that should do the trick... As for going back:

1. dd if=/dev/zero of=disk.img bs=1000 count=0 seek=$[1000*1000*10]
2. sudo mkfs.ext3 disk.img
3. sudo mount -o loop disk.img /media/extra
4. sudo cp -r / /media/extra
5. sudo chroot /media/extra
sudo dpkg -i lupin-target.deb
[B]
Loopmounted partition vs real one[/B]

If you ask me, the best long-term solution would be to simply to use NTFS as a root filesystem, and install straight onto the windows partition without formatting it; that way, we could have the entire installer run straight from windows, because windows can read/write ntfs, and when the user reboots, it boots straight into a fully installed ubuntu. The only problem is, of course, is that ntfs-3g doesn't yet have permissions support, and we don't know whether or not they'll be done within 6 months for Gutsy, if ever, so we're left with loopmounted vs real install.

I still fail to see any major advantages of an installation on a real partition, though. The only major disadvantage we have had until now was the kernel/initrd upgrading, which we have recently fixed. As for the performance overhead, modern hard drives are fast enough so that it's not noticeable at all, and if the user wants to remove Windows, they can simply transfer to a real install using a nice wizard made of the steps mentioned above, and they'll be free to remove windows. I think ease-of-install and removal and safety should take priority to a slight performance boost, so while we should provide an option to install to a real partition, the default behavior should simply be  a loopmounted install.

---

### Post by Henrik on 2007-04-29
I want to reply to your points, but I just want to add that I'm not speaking for the whole distro team, just myself. We will discuss this in detail at UDS and I'm just doing some preliminary research ATM. As an example, I quite like the loop mounted approach but others may give more weight to other considerations than me and prefer a real install.

When we are talking about the possibility of making this part of the default install it is important that we consider a range of scenarios and use cases, not just those that seem a natural fit to Wubi at present. 

I agree that a loop mounted install is more elegant, and ago makes a very good point about the extra scary screens you get with partitioning/formating. But consider the wider picture for a moment: 

Ubuntu is after all a complete operating system, not an application that runs under Windows. We don't want there to be confusion about that. We also don't want to be at the mercy of problems in Windows. A fragmented disk will cause performance problems. If you upgrade from XP to Vista after Ubuntu is installed you will loose access to it (also problematic with Grub). What about version upgrades within Ubuntu, do they work well? What happens if you run out of disk space on the Ubuntu image, how do you recover? What if you want to switch from a loop mounted to a clean install but don't have enough disc space to juggle it? What if Microsoft decides to push out a 'security update' in XP that b0rks the bootloader, making people unable to access Ubuntu?

These are the types of questions that will be asked. The more answers we can find the better.

My *personal view* is that the loop mounted install wins for a very simple reason: when you are making first contact with a user there is a very low tolerance for problems and confusion. Everything needs to work smoothly, the less scary questions the better, as ago says. When the time comes to migrate to Ubuntu completely we already have the goodwill of the user: he/she is now convinced that Ubuntu is a good system and will be much more willing to read some documentation or follow a slightly complex procedure. The migration procedure should be clear and reliable, but it is not essential that it be 3-click-simple in the way that the first install has to be.

**Live CD vs. alternate:**

The main advantage of the Live CD is that it is more widely available than the alternate, though with the background download this vis not an issue. Let's be clear on this: *having two separate wizards in a row is not an option*, we agree on that. For the Live version to work pre-seeding would have to be complete and the install would have to be completely non-interactive after the Windows-based wizard. 

Other advantages of the live CD would be: *speed* -
copying the entire OS to the image file from an iso file takes about two minutes, which is a fair bit faster than the alternate install (in any case you need some post install config). *eye-candy* - With X up and running you can show a fancy slide shot while installing.

The main advantage of the alternate is that a working implementation already exists, while the live implementation still requires a fair bit of work.

---

### Post by ago on 2007-04-29
I can start answering some of the questions:

> **Henrik said:**
> A fragmented disk will cause performance problems.
Sure, but windows (the user benchmark) will be slower too...

> If you upgrade from XP to Vista after Ubuntu is installed you will loose access to it (also problematic with Grub).
That is always true whatever the installation method

> What about version upgrades within Ubuntu, do they work well?
They used to, there were some regressions I am fixing, should be ok in the final.

> What happens if you run out of disk space on the Ubuntu image, how do you recover?
Same thing as if you run out of space on your HD. Linux can still work, you delete some files and can use the extra.virtual.disk to increase the available space (works as an extra hard disk to which you can move /usr for instance).

> What if you want to switch from a loop mounted to a clean install but don't have enough disc space to juggle it?
Of course you need the space for both the virtual disk and the real partition. We might support portable HD for migration purposes.

> When the time comes to migrate to Ubuntu completely we already have the goodwill of the user
Exactly.

> copying the entire OS to the image file from an iso file takes about two minutes
v. good point. As soon as we finish with this version of wubi I will work on LiveCD support.

> With X up and running you can show a fancy slide shot while installing.
I guess you could do that with a framebuffer d-i frontend as well. 

> The main advantage of the alternate is that a working implementation already exists, while the live implementation still requires a fair bit of work.
agreed ;)

As mentioned by tux, direct mounting is also an interesting option, but then FAT users will be out...

---

### Post by tuxcantfly on 2007-04-29
By the way, I just created a stripped-down version of Wubi that is basically a clone of the Windows-based debian installer; it uses grldr/grub.exe to boot to the netboot initrd/kernel, then does a standard (not loopmounted) ubuntu installation from the internet, no CD required.

Basically, this doesn't address the issue of partitioning, but it does fix the issues with burning the CD and tweaking the BIOS to boot from it. Also, this allows for creating a "real" ubuntu installation with its dedicated partitions.

Since this functions in basically the same way as the win32-loader does, I've added it to your specification page under the name Wubi-netboot, since it isn't actually Wubi, though it's based on the same code, and uses the netboot initrd method

Download the executable at [http://www.cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/wubi-7.04-netboot.exe](http://www.cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/wubi-7.04-netboot.exe)

Source code (GNU GPL) at [http://www.cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/wubinetboot.nsi](http://www.cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/wubinetboot.nsi)

More detailed howto and info at at [http://ubuntuforums.org/showthread.php?t=427793](http://ubuntuforums.org/showthread.php?t=427793)

---

### Post by Henrik on 2007-04-30
OK, lots of good technical material here. That will give us a good background for the talks at UDS.


That reminds me of another issue we need to address: language and accessibility. As you know, the live CD has some function key options at the first boot screen that will let users set the language, some display settings and an accessibility profile for the Live session.

I suppose the language setting in Windows can be detected and used for the install. In fact the Wubi installer should really be translated in launchpad.

The accessibility setting are also very important, because some users rely on it to use and install the system. I recommend you try booting the Live CD with one or two of the F5 settings if you've not yet done so. The Wubi installer itself should be accessible (I assume NSIS does this to an extent, as would GTK). But more importantly, there needs to be an option for activating those features in the completed install. See [here]("http://www.ubuntu.com/products/whatisubuntu/accessibility"), [here]("http://www.ubuntu.com/node/691") and [here]("https://wiki.ubuntu.com/Accessibility") for more details.

See what I mean by 'we need to consider a range of use cases'? :)

---

### Post by ago on 2007-04-30
> **Henrik said:**
> That reminds me of another issue we need to address: language and accessibility. As you know, the live CD has some function key options at the first boot screen that will let users set the language, some display settings and an accessibility profile for the Live session.

We will have that too in the next version, the language is autodetected but the user has the option to change the locale (which affects both installation and installer)... We do not have many translations at the moment. The only issue there is that nsis localization mechanism does not play too nicely with rosetta and po files since it is based on key-value pairs as opposed to gettext.

> Wubi installer itself should be accessible (I assume NSIS does this to an extent, as would GTK).
I guess the installer is displayed according to the windows settings, so if the user has accessibility mode on, that will apply to the installer (one of the advantages of using native frontends...). As for the installed version of Ubuntu you can turn that on once installed. If there is a way to detect the accessibility mode in windows we could also preset an equivalent accessibility mode within Ubuntu. We do not do that at the moment, but it should be feasible. In fact it might be a good idea to include such detection features within migration-assistant (and since we support migration-assistant as well, we should be covered anyway ;) )

---

### Post by tuxcantfly on 2007-04-30
Sorry for any confusion the wubi-netboot release may have caused, it was by no means meant to replace the standard Wubi/Lupin developments, nor a shift in direction away from the loopmounted partitions concept; it was only meant as a temporary way to allow users to install Ubuntu 7.04 onto a dedicated partition without a CD until the Wubi/Lupin codebase supports it.

Eventually, support for installation onto real partitions will be included in newer Wubi releases, so thus, wubi-netboot will then be entirely replaced by Wubi and will no longer be needed.

For this reason, I've removed wubi-netboot from the spec considerations, since Wubi will eventually support its feature (installation on a dedicated partition), and more.

No further development on wubi-netboot will occur, and development on features to Wubi, such as the ability to install on a dedicated partition, will continue.

Just clarifying to avoid any confusion...

---

### Post by Henrik on 2007-05-01
> **ago said:**
> 
I guess the installer is displayed according to the windows settings, so if the user has accessibility mode on, that will apply to the installer (one of the advantages of using native frontends...). 

It will depend on how well the Windows access tools work, but that will be the same for any Windows application really, and it's not really our problem to fix. If there is a way of adding extra access support in NSIS then we should, but otherwise there is not much we can do.

> 
As for the installed version of Ubuntu you can turn that on once installed. Unfortunately it's not that easy. If you boot a blind user into an environment without a screen reader there is no simple way for him to turn it on, same goes for magnification, contrast and sticky keys. We've found a reasonable solution for this with the Live CD and removing that functionality in the Windows installer would be a serious regression. We could probably solve it with an advanced button or tab in Wubi.

> If there is a way to detect the accessibility mode in windows we could also preset an equivalent accessibility mode within Ubuntu. 
Yes, that would be interesting. I'm not sure there is an easy way. Search the register for ZoomText and WindowsEyes keys perhaps. An advanced tab with the explicit choice would be nice anyway though.

---

### Post by ago on 2007-05-01
> **Henrik said:**
> If there is a way of adding extra access support in NSIS then we should, but otherwise there is not much we can do.

What we are trying to do on our side is to simplify the GUI design. You will see in the new version that we have (tango) icons close to each field, and less text. Moreover the new version is designed to get a working installation with a single click (+password), that alone should greatly improve accessibility. 

> Unfortunately it's not that easy. If you boot a blind user into an environment without a screen reader there is no simple way for him to turn it on, same goes for magnification, contrast and sticky keys. We've found a reasonable solution for this with the Live CD and removing that functionality in the Windows installer would be a serious regression. We could probably solve it with an advanced button or tab in Wubi.
As mentioned the best way to address that is probably via autodetection, so that there is no need to press any button. It is a fairly safe assumption that if a user does not have a screen reader when running the installer, then chances are that (s)he will be able to turn accessibility on/off in Ubuntu as well without help of a screen reader. If (s)he does have a screen reader when Wubi is running, we should be able to detect that and activate orca or equivalent in Ubuntu. By running the installer in an live OS we have a big advantage: we can detect the running processes and see what the user needs, and we should take advantage of that.

---

### Post by ago on 2007-05-01
Henrik,

decision tree (with my answers):

**Choice 1: "real" installation vs virtual machine**
My opinion is that vm at the moment is only good as a demo, lack of performance and direct hw access are show stoppers. Moreover you want to get people trying to really use the new OS as opposed to quickly glance at it as a curiosity and go back to outlook as soon as they have to send an email. Not to mention that you need to boot the host OS just to run Ubuntu, that alone puts Ubuntu on a lower step compared to the host system... I am in favor of supporting prebuilt VM-friendly images, but I do not see how that can be used as main installation vehicle. Things will change here but it is not yet the time to go the VM route at full steam. Prebuilt VM images should be supported, but there is no alternative to "real" installation.

**Choice 2 (assuming "real" installation): shall we allow to launch the installer without having to burn a CD?**
If the answer is yes, all remaining options have now one thing in common: a windows front-end that has to modify the bootloader, so you can start working on the frontend without reading the following questions... In my experience, burning the CD is a major obstacle for a lot of users, I have run into a LOT of people having problems with that. That said the live CD (and the alternate ISO) are invaluable tools in a lot of situations and they are here to stay, but providing the option to install without CD can only improve adoption.

**Choice 3 (assuming ISO booting): shall we collect information within windows or delegate to a different wizard running in Linux?**
I am in favour of collecting information in windows since: 1)  that allows you to observe a live OS (for instance to detect whether a screen reader is in use), 2) in the second case you have to go through 2 separate wizards since the windows one is needed at the very least to modify the bootloader.

**Choice 4: shall we pre-download the required files?**
IMO it is a no brainer. Netinstall, in its pure form is a no go. If you like netinstall then you probably should go for its cousin instead: hd-media ([http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/)). The only difference is that in the first case the packages are downloaded from within Linux, in the second case you pre-download the packages from within Windows. The second approach is safer, since you are not in danger of leaving the user to fix networking within d-i, and can work in offline mode. You guessed it, we had an hd-media implementation a long time ago', you can still think of Wubi as an hd-media implementation even if it does no longer use the hd-media initrd... 

**Choice 5: shall we target a real partition, a loopfile or both?**
I have already discussed pros and cons. But I like to reiterate. Loopinstall allows to install/uninstall an OS as any other application, i.e. the trade off is between having the easiest OS installer ever created (quite literally), vs the reliability/performance of a dedicated partition. In a server room it would be a no brainer, but the context here is not a server room but a home desktop, and reliability/performance gains would be hardly noticeable to the average user, while the simplified installation procedure would be quite evident and far more reassuring. IMO reliability/performance does not count for much if the user does not install your OS... From a techical point of view both approaches would probably be based on hd-media. In the case of real-partition installation there is little to do as far as the backend goes. In the case of loopfile you need to adjust the hd-media installer, the Ubuntu initrd and you have to pre-install ntfs-3g by default. That said the required changeset is already available in Lupin, it might need some further fine-tuning but most of the work is available... Note that at this stage whatever the choice, you would be using the same windows front-end. In fact even today, it would be possible to use the current hd-media initrd (=direct partition installation) with wubi frontend with very little modifications... Since loopinstall is an add-on to hd-media, the real choice from a technical point of view is whether to limit yourself to direct partition installation or whether to invest some time to also support loopinstallation.

**Choice 6: (assuming hd-media) Shall we source installation files from live ISO or alternate ISO?**
That depends in part on Choice 3. Alternate ISO is easier to implement: just use the hd-media and the d-i frontend comes with it (gtk based). That will work both in interactive or non-interactive mode. If you go for Live ISO, you need to boot the live ISO and get to X/FB. In interactive mode you may want to start a full desktop (which is equivalent to booting the Live CD), in non-interactive mode you may want an init sequence which launches a full-screen slimmed version of Ubiquity (basically to show the progress bars while it copies the files from squashfs and finishes installation). Since the hd-media initrd is designed to work with the aternate ISO, that would need to be modified. The initrd would need to find the ISO, mount the squashfs and boot it using the appropriate init process (possibly passing the preseed file along). Lupin does that already.

If there is enough interest in the live ISO route I am more than willing to create a version of lupin which uses that instead. If adding loopinstallation capabilities to the initrd/iso is deemed a desirable route, I would be glad to help on that too.

---

### Post by tuxcantfly on 2007-05-01
There's only one major problem with the hd-media, or any other approach that involves using a pre-downloaded alternate (or desktop/livecd) iso file: NTFS (or just about any filesystem except reiserfs) partitions can't be resized while mounted (assuming we want an installation on a real partition and not a loopmounted one), and if they are forcefully resized, data corruption is likely.

Since the files are being fetched from the iso, which is on the disk itself, the partition will have to be mounted throughout the installation. Since the partition will be mounted, there's going to be no way to resize it, at least during the installation itself, and since it needs a partition to install to and store the files on, the installation is thus made impossible unless the partitioning has already been done prior to starting the d-i portion of the installer, and there is a free partition to install to. For the typical hd-media installations, this isn't a problem, because those users always either have the disk partitioned with multiple partitions, with the alternate iso on one partition and not on the installation target partition, so that the partition with the installation files doesn't have to be resized, or the user is storing the installation iso and files some other media, such as a usb drive, that isn't affected by the hard drive partitioning/mounting. However, since the majority of Windows users only have 1 partition, which eliminates the ability of storing the installation files on a separate partition, and Wubi is meant to run from the hard drive, not a usb stick, this will be more difficult to implement the hd-media approach for.

Now, it would be nice and easy if the windows-based portion of the installer could do the resizing bit, but this is simply not possible. There exists no free NTFS resizer that runs in standard Windows, as far as I know, and even if there were one, that would be extremely unsafe; any changes to the filesystem, any writes, any fragmentation that occurs during the resize process (due to background programs and such running) will likely cause data corruption, so it's not a feasible method.

Another way that we can work around this problem is to either copy the alternate iso, or at least the necessary parts, onto a ramdisk, so that we can resize and install without having the NTFS partition mounted. The only problem is, we can't rely on the ramdisk, because we don't know how much ram the system has. We can't simply assume that they have 512MB or however much is needed to accommodate the necessary bits of the alternate iso, or else installation will fail on computers with limited RAM. So, this is probably not a feasible method.

So, the only method that's really left is to do the resizing from as soon as the installer initrd boots, but before the d-i installation phase and mounting occurs. In other words, all of the resizing tools (ntfstools, reiserfstools, ext2tools, msdostools, jfstools, hfstools, xfstools, etc. because we can't simply assume that they're using a particular filesystem, especially since lupin is meant to be cross-platform), and all their dependencies will likely have to be included in the initrd, which will probably lead to a rather large increase in size (couple of MB or so), which will increase the llikelihood of the issue with the fragmented initrd being unbootable occurring, and we can't separate it into 2 initrds over 2 reboots (1 for partition resizing, 1 for installation), since that'll increase the install time significantly, and the users will become impatient from having to reboot that many times.

Then, since we don't want to have the user answering any scary partitioning questions from within the 2nd stage (installation initrd booting), we'll have to have the nice partitioner in the windows interface store the values for the partitioner somewhere, like the preseed, and pass them on to the initrd so that it can do the acutal partitioning automatically; and that's assuming that the user didn't try to modify anything with their partitions since they last ran the wubi installer from windows.

So, while it is certainly possible to have an installation to a real partition, using the hd-media or modified lupin approach, a proper, safe implementation will likely be a bit more difficult if we're fetching the files from a loopmounted iso file on the filesystem, than simply the expected few modifications to the preseed for lupin and addition to the wubi frontend, due to this issue with resizing partitions while mounted. Of course, wiping out the partition would work fine, but that wouldn't quite please those who want to dual-boot (our target audience), and loopmounting would work fine too, but some will likely want a "real" installation.

Also, I'm not exactly sure if this is the right place to discuss this, but this kind of caught my eye, since it appears to contradict everything I've stated above:

> You guessed it, we had an hd-media implementation a long time ago

Exactly which version is this referring to? Wubi/Lupin has always used the loopmounted filesystem, alternate iso and d-i approach, and as for the really old versions I released before ago joined the development team (I assume ago is referring to those), the Windows-based Ubuntu Installer prototype v1 and v2 used a hybrid partial direct-mount with ntfs-3g and partial loopmounted filesystem approach, prototype v3 used a preconfigured loopmounted filesystem image, and livecd-v1 and v2 ran into this exact same problem; they were unable to resize partitions during the installation because they had to be mounted for the installation to occur. So unless I misinterpreted this statement, I'm pretty sure this hasn't been done before for Wubi/Lupin, so the code that has to be added to wubi/lupin to do this will have to be written from scratch.

I'm not, of course, suggesting that Wubi shouldn't, or can't, have the ability to install to real partitions; It's just going to be more difficult than it appears to implement it in a way that can safely do it in a clean, easy-to-use way that has the files being pre-downloaded to the hard drive partition.

---

### Post by ago on 2007-05-02
As for hd-media it is still possible to load the required d-i components, umount the host system, resize and remount. That does not required to load up in memory the full ISO, only the required d-i udebs, which should take way less than 64MB... I am not sure whether you can resize the f/s when it is mounted r/o, in which case even the above is superfluous. 

> **tuxcantfly said:**
> Exactly which version is this referring to? Wubi/Lupin has always used the loopmounted filesystem, alternate iso and d-i approach
The very first prototype I released, was using d-i with a modified hd-media initrd ([http://ubuntuforums.org/showthread.php?p=2036194&highlight=hd-media#post2036194](http://ubuntuforums.org/showthread.php?p=2036194&highlight=hd-media#post2036194)). But as always it was patched to target a loopmounted FS so we did not have to worry about partitioning issues. Then I moved to the standard Ubuntu initrd adding to it  hd-media like capabilities to search for and boot an alternate ISO, using dynamically patched d-i installation files in there and chrooting into the ISO to perform the actual installation. This way the same initrd was used for installation and normal boot (1 to reduce download size and 2 because kernel upgrade was not possible at the time). Now that we can update the kernel from within Ubuntu (thanks to tux patches), I was planning to split the functionality and go back to a patched hd-media for installation and a modified stock initrd for normal booting. I hope such patches can be merged upstream directly in Ubuntu, that is why I launched this blueprint [https://blueprints.launchpad.net/ubuntu/+spec/lupin](https://blueprints.launchpad.net/ubuntu/+spec/lupin). This way we can add the ability to boot from loopfiles to the stock initrd and the ability to install to loopmounted files to the hd-media initrd. 

>  the Windows-based Ubuntu Installer prototype v1 and v2 used a hybrid partial direct-mount with ntfs-3g and partial loopmounted filesystem approach
The early prototypes simply loopmounted a pre-made image file. That is not what I am taling about. Those prototypes were not really "installing", they were not using d-i, nor an official initrd (neither hd-media nor stock initrd).

---

### Post by Henrik on 2007-05-16
We had detailed talks about this in Seville including a scheduled session where ago participated on the phone.

We decided to move forward with an installer based on Wubi for the Gutsy release. A few changes should be made but the basic idea of loop-mounting remains. Lots of polish and testing will of course also be needed.

Specifically:

 * We want to use  the Live CD iso because it's faster, more widely available, and more useful for related projects like virtualbox
 * We will integrate it with the Live CD WinFOSS browser. One click on the front screen of that will load the wubi installer
 * Branding and artwork - The naming and design must fit in well with the rest of the distribution (we'll get input and images from our artist and the art team)
 * We want to make it clear in some way that this is not a standard install of Ubuntu and that if you want to run it long-term you should install it directly on the hard drive


I'll update the spec.

---

### Post by ago on 2007-05-16
> **Henrik said:**
> We had detailed talks about this in Seville including a scheduled session where ago participated on the phone.

We decided to move forward with an installer based on Wubi for the Gutsy release. 

I was holding off releasing the news... Well I guess now there is no reason: wubi will be an official ubuntu installer!!!  

Thanks a lot to Henrik that helped push our project at Seville!!!

> A few changes should be made but the basic idea of loop-mounting remains. Lots of polish and testing will of course also be needed.
As mentioned in the past, you can count on us for that.

>  * We want to use  the Live CD iso because it's faster, more widely available, and more useful for related projects like virtualbox
Sounds good, as soon as we have a stable release, I'll start migrating from alternate ISO to Live CD.

>  * Branding and artwork - The naming and design must fit in well with the rest of the distribution (we'll Get input and images from our artist and the art team)
All yours. Let me know what we should do with the website, logo, graphics in the meantime.

>  * We want to make it clear in some way that this is not a standard install of Ubuntu and that if you want to run it long-term you should install it directly on the hard drive
Fair enough. 

Quick update on our side: tuxcantfly has started working on a tool to migrate wubi virtual disks to real partitions ([https://launchpad.net/lvpm](https://launchpad.net/lvpm)). Usplash should have been fixed. Vista support is coming (thanks to ecology2007). Grldr issues have been fixed by bean123 (need testing). MetaLink support coming soon (=automatic mirror selection + resume capabilities, thanks to hampus). Still some unresolved issues with freeze during mkfs and hybernation. Migration-Assistant not working yet.  


PS there are several technical issues we need to discuss, I don't think they were discussed in seville (I am not sure since I could not hear very well what you guys were saying)...

---

### Post by open2linux on 2007-05-17
> **ago said:**
> I was holding off releasing the news... Well I guess now there is no reason: wubi will be an official ubuntu installer!!!  

Wow ! These are great news !!. Just two lines to say to ago, tuxcantfly, ecology2007, bean123, hampus,...
[SIZE="4"][COLOR="Red"]C O N G R A T U L A T I O N S !!![/COLOR][/SIZE]

=D>

---

### Post by Henrik on 2007-05-18
> **ago said:**
> 
All yours. Let me know what we should do with the website, logo, graphics in the meantime.

I was mostly thinking of making the installer itself look slick. I have some design experience so I can lead that, and we'll get help from our artist, Ken. 

As for the wubi website, that seems fine as it is (with a new URL perhaps). As far as Ubuntu is concerned, it is an upstream project. You can of course close wubi completely and simply do it as an internal Ubuntu project. Up to you. We will make downloads available from ubuntu.com simply described as an ubuntu installer (good wording for this needed).

I'm not sure how we will explain that it's not a full ubuntu install. It very nearly is a real install, and most people won't see the difference, so we won't make a big deal of it. However we do have to explain why we use a fairly small disk and we don't want people using it for 3 years this way.

btw, we plan to enhance the migration assistant to handle importing from the loopmount. We think that is a cleaner approach than dd-ing the image. People want to keep their documents and bookmarks but with generally be happy to have a clean system install.
[B]
Other issues:[/B]

**Building it** - I guess it's built on someones local machine ATM. For the versions we ship we might want to have  it built centrally (except we dont have Windows build machines ATM)
**Size** - Space on the Live CD is always precious and 10 MB is rather large. Are you using the LZMA compression option in NSIS?
**Using the physical Live CD **- How can we use the existing physical CD when it is available (to avoid downloads)? Do we need to create an ISO from it or should we let wubi use the physical CD (slower)?
**Password security** - How is the password info managed? Is it in encrypted form, and is the file containing it deleted when rebooting to Windows?

---

### Post by Henrik on 2007-05-18
> **ago said:**
> 
All yours. Let me know what we should do with the website, logo, graphics in the meantime.

I was mostly thinking of making the installer itself look slick. I have some design experience so I can lead that, and we'll get help from our artist, Ken. 

As for the wubi website, that seems fine as it is (with a new URL perhaps). As far as Ubuntu is concerned, it is an upstream project. You can of course close wubi completely and simply do it as an internal Ubuntu project. Up to you. We will make downloads available from ubuntu.com simply described as an ubuntu installer (good wording for this needed).

I'm not sure how we will explain that it's not a full ubuntu install. It very nearly is a real install, and most people won't see the difference, so we won't make a big deal of it. However we do have to explain why we use a fairly small disk and we don't want people using it for 3 years this way.

btw, we plan to enhance the migration assistant to handle importing from the loopmount. We think that is a cleaner approach than dd-ing the image. People want to keep their documents and bookmarks but with generally be happy to have a clean system install.
[B]
Other issues:[/B]

**Building it** - I guess it's built on someones local machine ATM. For the versions we ship we might want to have  it built centrally (except we dont have Windows build machines ATM)
**Size** - Space on the Live CD is always precious and 10 MB is rather large. Are you using the LZMA compression option in NSIS?
**Using the physical Live CD **- How can we use the existing physical CD when it is available (to avoid downloads)? Do we need to create an ISO from it or should we let wubi use the physical CD (slower)?
**Password security** - How is the password info managed? Is it in encrypted form, and is the file containing it deleted when rebooting to Windows?

---

### Post by ago on 2007-05-18
> **Henrik said:**
> I was mostly thinking of making the installer itself look slick. I have some design experience so I can lead that, and we'll get help from our artist, Ken.
Have fun! You have cart blanch.

> As for the wubi website, that seems fine as it is (with a new URL perhaps).
We have purchased wubi-insatller.org, we will be glad to redirect that to the appropriate ubuntu page once it is ready and pass the domain ownership to Ubuntu.

> As far as Ubuntu is concerned, it is an upstream project. You can of course close wubi completely and simply do it as an internal Ubuntu project. Up to you.
Our original goal was to become an official Ubuntu installation method, so we would be quite honoured to merge with Ubuntu. I will probably still keep the alternate ISO implementation alive so that 1) other debian distros that do not use ubiquity can take advantage of that, 2) if ubiquity preseed does not happen in time we have a fallback. It would be nice if we could keep the current launchpad projects to show continuity with our past efforts.

> We will make downloads available from ubuntu.com simply described as an ubuntu installer (good wording for this needed).
Since you will need a name anyway, I have no problem if you want to call that wubi. Wubi is an acronym for Windows UBuntu Installer, which is what users will probably call that anyway to distinguish from the LiveCD/Alternate ISO installers. It is as good a name as any. We will grant all copyright stuff to ubuntu.  Even now, when wubi is launched, the title reads "Ubuntu SetUp" the only mention to "Wubi" is in the installer version (greyed), in the folder name, in the executable name and registry keys. Those can easily be eliminatd since I assume there will be no need to have a separate installer version in there and the folder will be called "ubuntu" anyway. In this scheme, "wubi" will only remain as a project name, like "ubiquity".  


Once we are here, I would also suggest "lubi" (for the linux frontend on which tuxcantfly has started to work), and "mubi" for the mac version.

> I'm not sure how we will explain that it's not a full ubuntu install.
I have been thinking about that too and could not come out with any good answer. You want to convey the message without having to explain technical details.

> 
**Building it** - I guess it's built on someones local machine ATM. For the versions we ship we might want to have  it built centrally (except we dont have Windows build machines ATM)
Wubi does not require windows machines to be built, Wine is enough. We have already preliminary make scripts that take care of most things. It should be enough to run make within lupin and then within wubi. It is not a fully "conventional" configure/make mechanism (the configure part is missing and required configuration has been merged within the make script...), but that can be changed...

> **Size** - Space on the Live CD is always precious and 10 MB is rather large. Are you using the LZMA compression option in NSIS?
What takes space is the initrd. But in a live CD we can reuse the kernel/initrd in there. Without kernel/initrd the size would go down to ~ 1MB. That means though that we have to merge the lupin features within the Live ISO initrd. Current initrd is not optimized and uses for instance glibc which is a waste of 1-2MB (see bug on that). 

> **Using the physical Live CD **- How can we use the existing physical CD when it is available (to avoid downloads)? Do we need to create an ISO from it or should we let wubi use the physical CD (slower)?

I think we should use the physical CD directly without copying the ISO in windows. No problem doing that in lupin... There is no point in having the user wait for the copying to take place within Windows in order to save him time copying the files later on within Linux... 

My proposal is to merge lupin functionality within the LiveCD initrd. Then the LiveCD initrd (patched with lupin code) is copied also on the HD and boot.ini is edited as usual. Wether the machine is booted from CD or from HD the initrd will work the same way (since lupin relies on heuristic).... It will scan the HD for signs of a "ubuntu" folder and preseed, if it finds those and all checks are ok (vergin virtual disks are there) it will work as lupin and start the installation in unattended mode (using ubiquity-preseed), if it doesn't, it will work as a LiveCD. The same initrd will also be used in the stand-alone version of the installer (the one that relies on ISOs).

> **Password security** - How is the password info managed? Is it in encrypted form, and is the file containing it deleted when rebooting to Windows?
The password is hashed within the preseed file. The preseed file is deleted as soon as the Linux installer starts.

---

### Post by ago on 2007-05-18
> **Henrik said:**
> I was mostly thinking of making the installer itself look slick. I have some design experience so I can lead that, and we'll get help from our artist, Ken.
Have fun! You have cart blanch.

> As for the wubi website, that seems fine as it is (with a new URL perhaps).
We have purchased wubi-insatller.org, we will be glad to redirect that to the appropriate ubuntu page once it is ready and pass the domain ownership to Ubuntu.

> As far as Ubuntu is concerned, it is an upstream project. You can of course close wubi completely and simply do it as an internal Ubuntu project. Up to you.
Our original goal was to become an official Ubuntu installation method, so we would be quite honoured to merge with Ubuntu. I will probably still keep the alternate ISO implementation alive so that 1) other debian distros that do not use ubiquity can take advantage of that, 2) if ubiquity preseed does not happen in time we have a fallback. It would be nice if we could keep the current launchpad projects to show continuity with our past efforts.

> We will make downloads available from ubuntu.com simply described as an ubuntu installer (good wording for this needed).
Since you will need a name anyway, I have no problem if you want to call that wubi. Wubi is an acronym for Windows UBuntu Installer, which is what users will probably call that anyway to distinguish from the LiveCD/Alternate ISO installers. It is as good a name as any. We will grant all copyright stuff to ubuntu.  Even now, when wubi is launched, the title reads "Ubuntu SetUp" the only mention to "Wubi" is in the installer version (greyed), in the folder name, in the executable name and registry keys. Those can easily be eliminatd since I assume there will be no need to have a separate installer version in there and the folder will be called "ubuntu" anyway. In this scheme, "wubi" will only remain as a project name, like "ubiquity".  


Once we are here, I would also suggest "lubi" (for the linux frontend on which tuxcantfly has started to work), and "mubi" for the mac version.

> I'm not sure how we will explain that it's not a full ubuntu install.
I have been thinking about that too and could not come out with any good answer. You want to convey the message without having to explain technical details.

> 
**Building it** - I guess it's built on someones local machine ATM. For the versions we ship we might want to have  it built centrally (except we dont have Windows build machines ATM)
Wubi does not require windows machines to be built, Wine is enough. We have already preliminary make scripts that take care of most things. It should be enough to run make within lupin and then within wubi. It is not a fully "conventional" configure/make mechanism (the configure part is missing and required configuration has been merged within the make script...), but that can be changed...

> **Size** - Space on the Live CD is always precious and 10 MB is rather large. Are you using the LZMA compression option in NSIS?
What takes space is the initrd. But in a live CD we can reuse the kernel/initrd in there. Without kernel/initrd the size would go down to ~ 1MB. That means though that we have to merge the lupin features within the Live ISO initrd. Current initrd is not optimized and uses for instance glibc which is a waste of 1-2MB (see bug on that). 

> **Using the physical Live CD **- How can we use the existing physical CD when it is available (to avoid downloads)? Do we need to create an ISO from it or should we let wubi use the physical CD (slower)?

I think we should use the physical CD directly without copying the ISO in windows. No problem doing that in lupin... There is no point in having the user wait for the copying to take place within Windows in order to save him time copying the files later on within Linux... 

My proposal is to merge lupin functionality within the LiveCD initrd. Then the LiveCD initrd (patched with lupin code) is copied also on the HD and boot.ini is edited as usual. Wether the machine is booted from CD or from HD the initrd will work the same way (since lupin relies on heuristic).... It will scan the HD for signs of a "ubuntu" folder and preseed, if it finds those and all checks are ok (vergin virtual disks are there) it will work as lupin and start the installation in unattended mode (using ubiquity-preseed), if it doesn't, it will work as a LiveCD. The same initrd will also be used in the stand-alone version of the installer (the one that relies on ISOs).

> **Password security** - How is the password info managed? Is it in encrypted form, and is the file containing it deleted when rebooting to Windows?
The password is hashed within the preseed file. The preseed file is deleted as soon as the Linux installer starts.

---

### Post by jettplane on 2007-05-18
Congrats on inclusion in Gutsy.  Good work...

I only had one comment  before the news.  I am a Windows guy who discovered Ubuntu at 6.10.  I ran it in a virtual machine (VMWare-VMWare Player and VMWare Server.)  When 7.04 came out, I came across Wubi. The difference in speed  with Wubi was huge (Dell Inspiron 6000).  Even in VMWare, start up and low load programs ran fast enough to impress me, but video was horribly slow in Server, barely ok in Player and slower than Windows.  I can't rule out I was doing something wrong with the virtual machine, but Wubi has worked much faster than either of the other choices with zero need for me to configure settings.  Virtual machine was a pain to tweak.

Still needs work on hibernation, but otherwise I think all of my problems are Ubuntu not Wubi in test 1 so far.

---

### Post by tuxcantfly on 2007-05-18
> I was mostly thinking of making the installer itself look slick. I have some design experience so I can lead that, and we'll get help from our artist, Ken.

This link will help with the "making it look slick" part, for NSIS:
[http://skincrafter.com/nsis_plugin.html](http://skincrafter.com/nsis_plugin.html)

It could be used to give it a slick brown-orange ubuntu tint, with a more "modern" (glassy?) interface, that would certainly be an eye-catcher...

I know the designer tool is not GPL, but it can still be freely used and doesn't place restrictions on generated code, and I have yet to find anything that could match it in terms of functionality...

Anyhow great to hear that Wubi's going official, we've been working hard for that... And seconding ago's views, while it should be merged into Ubuntu (the original goal), it would still be useful to keep the existing work in place, for future work on extending it to other host and guest platforms, like other GNU/Linux distros as hosts and guests and a Mac OS X host, though of course, the main focus should currently be on pushing out a solid release for inclusion in the Gutsy Desktop CD.

And by any chance, would it be possible to get the GNU/Linux version, Lubi [https://launchpad.net/lubi](https://launchpad.net/lubi) [http://ubuntuforums.org/showthread.php?t=442597](http://ubuntuforums.org/showthread.php?t=442597) into the (universe?) repos once it's gotten an adequate amount of testing and refining (it's still currently a rather immature project, but that'll soon change)? I would have to consult MOTU and REVU for that, correct?

---

