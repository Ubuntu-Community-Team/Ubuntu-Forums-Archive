---
title: "Gutsy inclusion progress"
date: 2007-05-18
forum: General Help
---

### Post by Henrik on 2007-05-18
I'm creating a new thread where we can track the technical changes we need to make towards Gutsy inclusion.

I'm now setting the [**spec**]("https://blueprints.launchpad.net/ubuntu/+spec/installer-for-windows") to Review status. 

ago: the dependencies on the spec are backwards: Lupin is a prerequisite for the install spec not a consequence. Please remove the link from the lupin spec and I'll add one from this spec.

(mods: you might want to stick this thread and unstick the old Gutsy one)

---

### Post by ago on 2007-05-18
> **Henrik said:**
> ago: the dependencies on the spec are backwards: Lupin is a prerequisite for the install spec not a consequence. Please remove the link from the lupin spec and I'll add one from this spec.
Will do. Edit: done. 

I did that to mean that there was no point in implementing lupin spec if you had choosen another installation method... Not that I wanted to put undue pressure on you guys or anything... ;P

I have unstuck the old thread, for the ones that missed the Wubi inclusion story, here it is: [http://ubuntuforums.org/showthread.php?t=425557](http://ubuntuforums.org/showthread.php?t=425557)

---

### Post by CrazyGuy123 on 2007-06-25
Since wubi is going official, shouldn't lupin-target find it's way into the official resporitories so it can be updated through ubuntus normal update system.  That should also mean testers using gutsy (and when it's released the end users) will be able to update without much hassle.

---

### Post by ago on 2007-06-25
> **CrazyGuy123 said:**
> Since wubi is going official, shouldn't lupin-target find it's way into the official resporitories so it can be updated through ubuntus normal update system.
Lupin-target is used to patch a normal installation so that it supports loop installation booting/rebooting. Hopefully once we are merged lupin-target will not be need at all since all required changes will already be upstream.

---

### Post by Henrik on 2007-06-29
> **ago said:**
> Lupin-target is used to patch a normal installation so that it supports loop installation booting/rebooting. Hopefully once we are merged lupin-target will not be need at all since all required changes will already be upstream.

Right. Could someone make a list of the features that we should merge in to gutsy to make this work smoothly? The I can present that to the relevant developers. My list currently is:

[LIST]
[*]Merge lupin changes
[*]Make pre-seeding work on the Live CD so wubi can use that[/LIST]
Anything else?

---

### Post by ago on 2007-06-29
Henrik I drafted a first list here: [https://wiki.ubuntu.com/LupinMerge](https://wiki.ubuntu.com/LupinMerge)
I can probably take care of most points in there. I am also drafting a more detailed todo plan. I will post it on the wiki.

Where I need help is:

* Solving this bug properly: [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/87763](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/87763)
Keybuk is the best man to coordinate the efforts probably, I have already talked to him, but I did not follow up. If you can chase him that would be great.

* Solving hibernation/suspend issues. Here I am out of my depth completely. I have talked to mjg59, he mentioned he would give it a look, but I had no reply since. Same as above... ;) If we cannot fix that we should disable hibernation/suspend.

* Improve the robustness of the hosting/hosted filesystem under hard reboots in a "compatible way". The issue is that hard reboots are not tolerated too well in a nested filesystem and our users do hard reboot quite a lot. So the aim is to find a good compromise between robustness and performance under such scenario. I have talked to ntfs-3g dev Szabolcs  and as a result have tweaked /etc/sysctl.conf. But again I am out of my depth.

* Default inclusion of ntfs-3g

All of the above would be much, much simpler if ntfs-3g was incoporated inside a kernel module as opposed to be fuse based (userspace). I will mention that to Szabolcs, but I doubt that will happen in time for Gutsy. I do not know if Ubuntu kernel devs might be able to help here.

* Then we need some help testing/improving lvpm. Tuxcantfly has been working on that and I did not have much time so far to look at the code. We plan to include it in our final to extend testing.

* Non-interactive ubiquity. It might be very desirable to have ubiquity launched full screen (X or FB) in a streamlined init process, so that it can be used for progress feedback and some input. 

* Username/Password entry. Colin mentioned that username/password should be handled after reboot. Stripping that out of the windows frontend is trivial, but we require some appropriate Ubiquity inputting, which relates to the above issue.

* Improve downloader. Now we support multiple mirror but the algorithm that choses the mirror is less than ideal, we plan to have segmented downloads. HampusW is the man here. I'd leave that to him.

* Accessibility. We might want to improve keyboard layout detection, our algorithm is okish but less than perfect. Also when the language is changed that affects the installation but not the installer.  We might want to detect if the user has screen reader on and so forth.

* As for the windows interface we might want to use python + wxwindows (or equivalent) as opposed to nsis. That will increase the download size, but it will make coding much easier and it will be portable to other platforms.

* Vista support in migration-assistant

* Fix os-prober to support mounted / fuse filesystems. I already have some preliminary patches for that.

---

### Post by Henrik on 2007-07-02
Thanks. I have forwarded some points to distro team members.

> **ago said:**
> 
* Solving this bug properly: [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/87763](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/87763)
Keybuk is the best man to coordinate the efforts probably, I have already talked to him, but I did not follow up. If you can chase him that would be great.

This would also be solved by integrated ntfs kernel support right?

> * Solving hibernation/suspend issues. Here I am out of my depth completely. I have talked to mjg59, he mentioned he would give it a look, but I had no reply since. Same as above... ;) If we cannot fix that we should disable hibernation/suspend.Is this fairly simple to disable if we have to? Do we just pass acpi=off on boot?

> All of the above would be much, much simpler if ntfs-3g was incoporated inside a kernel module as opposed to be fuse based (userspace). I will mention that to Szabolcs, but I doubt that will happen in time for Gutsy. I do not know if Ubuntu kernel devs might be able to help here.I've emailed pkl about this.

> * Then we need some help testing/improving lvpm. Tuxcantfly has been working on that and I did not have much time so far to look at the code. We plan to include it in our final to extend testing.Nice feature of course, but how crucial is this for the gutsy release? I take it this will require a GUI as well.

> * Non-interactive ubiquity. It might be very desirable to have ubiquity launched full screen (X or FB) in a streamlined init process, so that it can be used for progress feedback and some input. Yes, this would be great (I've contacted Evan and Colin), but we shouldn't block on it for Gutsy. (We'll continue with the alternate if we have to)

> * Improve downloader. Now we support multiple mirror but the algorithm that choses the mirror is less than ideal, we plan to have segmented downloads. HampusW is the man here. I'd leave that to him.Do you simply use a list of Ubuntu mirrors? Do you still support BT?

> * Accessibility. We might want to improve keyboard layout detection, our algorithm is okish but less than perfect. Also when the language is changed that affects the installation but not the installer.  We might want to detect if the user has screen reader on and so forth.I've posted a request for testing on the accessibility list. I expect there will be some problems with the various boot loaders not being accessible. It might help if there was an option to make Ubuntu the first boot option. That way it would be non-interactive.

> * As for the windows interface we might want to use python + wxwindows (or equivalent) as opposed to nsis. That will increase the download size, but it will make coding much easier and it will be portable to other platforms.I think that's a good idea. It will make it more flexible. I don't think it should be a gutsy target though. We have an NSIS-based system that works now and this would be starting from scratch on the GUI.

---

### Post by Henrik on 2007-07-02
I'd like to see up put this on tribe 3 so we can get some testing done. There are a few structural things we need to implement IMO to make that work smoothly. 

[LIST]
[*]We need an Ubuntu build that is separate from Wubi (which is upstream) so we can make Ubuntu-specific changes such as artwork. This should ideally be hosted in bzr on launchpad and we need to find a good way of building and making binaries available.
[*]Flavours - we need to figure out what to do with the flavours. Either:[LIST]
[*]Create one build for each flavour with different artwork (though you can still choose to download/install any version from it); or[/LIST][LIST]
[*]Add parameter functionalty to change artwork at runtime; or[/LIST][LIST]
[*]Make an Ubuntu branded version and use that everywhere for tribe 3 (options 1 and 2 can then be revisited later).[/LIST]
[*]Start using the bugtracker in Launchpad to report bugs instead of forum threads.
[*]Use Gutsy images as install medium. How fragile is the lupin patching WRT changes in the ISO it patches? Will daily image updates cause daily breakage?[/LIST]

---

### Post by ago on 2007-07-02
> **Henrik said:**
> This would also be solved by integrated ntfs kernel support right?

Yes but... ...This is the answer from szaka (ntfs-3g author) about making ntfs-3g into a module:

> > I know you have been asked this question dozens of times, but I'll ask
> anyawy: any chance of seeing ntfs-3g as a kernel module any time soon?

It doesn't make sense. Here they are some of the reasons:

  - much more work work because the kernel rapidly changes and one must 
    keep learning and redo the same thing for the different interfaces 
    which should be also backward compatible for the older kernels
  - much slower development (see above)
  - much harder (see above)
  - much slower user adaption: people can't keep installing kernel modules
  - much less testing (see above)
  - much less quality (see above)
  - much more unreliable operation: the kernel bugs could result
    NTFS corruption and people would blame the driver not the really
    broken kernel parts. Now they are isolated.


I do not agree with the above arguments by the way, but I have little say in this matter. Feel free to try to convince him (the email is on ntfs-3g website).  

> Is this fairly simple to disable if we have to? Do we just pass acpi=off on boot?
Ideally we should start to fix it first. There are 2 separate issues: swap inside a mounted partition (for suspend to disk) and use of userspace filesystem (for both suspend and hibernate). Hence hibernation might be more complex to fix (since it get affected by both) but suspend might be doable (in fact it should work already with lupin on ext3 and wubi on fat32). We can disable either with acpi=off or by adding a script in the acpi sleep sequence. The second option has an advantage since this way we can turn it off only when we know we cannot suspend/hybernate. The issue with it is that the hyberanate/suspend buttons will still be "active" even if they will have no effect. So ideally there should be a hal? script to investigate hibernation/suspend capabilities taking into account issues typical of loopmounted setups.

> Nice feature of course, but how crucial is this for the gutsy release? I take it this will require a GUI as well.
Agreed, it's not necessary but very handy. Lvpm does not have to be embedded, so we can develop it and distribute it separately, but I wanted to mention it so that we can hopefully include it in the official repos and live cd (at the moment it is only a few Ks). We are now shipping it with the initrd (to increase audience and testing), but having in the repos would be a better option.

> Do you simply use a list of Ubuntu mirrors? Do you still support BT?
We use metalink files now, which are basically a "list of Ubuntu mirrors". Those do not yet support BT. But in the next release they might support both segmented download and/or BT. IMO segmented download is good enough in most cases except for the first 1-2 days after the release when all servers are under pressure. On the plus side, current downloader already supports partial checksums and resume capabilities.

One issues is proxies. The downloader supports it, but we have no interface/detection for it.

> I think that's a good idea. It will make it more flexible. I don't think it should be a gutsy target though. We have an NSIS-based system that works now and this would be starting from scratch on the GUI.
Agreed. The python idea would be nicer since we could make the downloader in python as well (now it's in c) as well as other bits and pieceses.

Another point was branding. I understood that colin wants a branded version for each Ubuntu flavor. My suggestion is this: let's keep the desktop selector, but let's preselect the appropriate desktop environment whenever a CD/ISO is detected. Selecting a desktop will change the title and the banner graphics accordingly. This way we can use the same program as stand-alone or bundled with CD.

Linked to the above I would add the following change: the initrd/kernel is not acutually bundled with the installer. It is extracted from the CD/iso. This will greatly reduce the size of the installer. The issue here is to find a way to mount an ISO under windows (have not investigated that). This also implies that the LiveCD initrd has to work in dual mode: whether booted from hard disk or whether booted from CD.

---

### Post by ago on 2007-07-02
> **Henrik said:**
> I'd like to see up put this on tribe 3 so we can get some testing done. There are a few structural things we need to implement IMO to make that work smoothly. 

That's the 19th of july correct? 
Ok I will then stop working on wubi as it is currently, I will merge my latest code and start working on the Lupin merge actively (I wanted to push out a wubi final before that, but it will be postponed then).

That also mean that I will need to pacth upstream the initrd of the alternate ISO (since I assume that there is no time to target the live ISO at the moment).


> 
[*]We need an Ubuntu build that is separate from Wubi (which is upstream) so we can make Ubuntu-specific changes such as artwork. This should ideally be hosted in bzr on launchpad and we need to find a good way of building and making binaries available.

What about having a new branch from the Wubi project which is owned by the ubuntu-installer team? (by the way could I be added there?). The build mechanism is not really "standard", and it needs a bit of love, but it does the job. It should be sufficient to run "make" within the bzr branch. It does require a link to a wine folder (for nsis compilation) and to lupin/dist folder (which is created by running make within a lupin branch). 

> [*]Flavours - we need to figure out what to do with the flavours. Either:[LIST]
[*]Create one build for each flavour with different artwork (though you can still choose to download/install any version from it); or[/LIST][LIST]
[*]Add parameter functionalty to change artwork at runtime; or[/LIST]
I give my vote to the second option.

> [*]Make an Ubuntu branded version and use that everywhere for tribe 3 (options 1 and 2 can then be revisited later).[/LIST]
I mentioned to colin and he agreed, that we would desire to be merged and that the project can continue to be called wubi (to show continuity with our past efforts). Of course wubi will be only an internal project name and all rebranding can take place as usual. That said at the moment the title already reads "Ubuntu Setup", and the only explicit mention of wubi is in: the version (grayed out), folder name, file name, banner.

> [*]Start using the bugtracker in Launchpad to report bugs instead of forum threads.
We do already, we use the thread as a "filter".

> [*]Use Gutsy images as install medium. How fragile is the lupin patching WRT changes in the ISO it patches? Will daily image updates cause daily breakage?
They shouldn't. Particularly if patches are moved upstream.

---

### Post by ago on 2007-07-02
One big question is what to do with partman for test3.

At the moment I disable partman and grub installation (in the alternate iso), then I create the filesystem into the loopmounted files using a custom script. Ideally partman should be able to target a loopmounted filesystem using only preseed arguments.

I am not sure what is the stage of that. Colin might be the person to ask.

---

### Post by Henrik on 2007-07-02
> **ago said:**
> One big question is what to do with partman for test3.

At the moment I disable partman and grub installation (in the alternate iso), then I create the filesystem into the loopmounted files using a custom script. Ideally partman should be able to target a loopmounted filesystem using only preseed arguments.

I am not sure what is the stage of that. Colin might be the person to ask.

Yes, he is clearly not fond of the partman solution used now. He would like to see this implemented directly before we deploy it on the CD, so it probably looks like we will miss tribe 3. That's OK, we can target tribe 4 instead and in the meantime appeal for wider testing via blogs and forums. There are still quite a few other things to sort out. I'll speak with Colin and other team members at our meeting next week about partman, ntfs and artwork.


[I]This would also be solved by integrated ntfs kernel support right?
Yes but... ...This is the answer from szaka (ntfs-3g author) about making ntfs-3g into a module:[/I]

My use of the word module might have been wrong here. The key is to get read/write support into Ubuntu: [https://wiki.ubuntu.com/WriteSupportForNTFS](https://wiki.ubuntu.com/WriteSupportForNTFS)


*Another point was branding. I understood that colin wants a branded version for each Ubuntu flavor. My suggestion is this: let's keep the desktop selector, but let's preselect the appropriate desktop environment whenever a CD/ISO is detected. Selecting a desktop will change the title and the banner graphics accordingly. This way we can use the same program as stand-alone or bundled with CD.*

That sounds good. You would also be able to start it with a given parameter? (distro=kubuntu, say)

[I]
Linked to the above I would add the following change: the initrd/kernel is not acutually bundled with the installer. It is extracted from the CD/iso. This will greatly reduce the size of the installer. The issue here is to find a way to mount an ISO under windows (have not investigated that). This also implies that the LiveCD initrd has to work in dual mode: whether booted from hard disk or whether booted from CD.[/I]

CD space is always at a premium so this would be great, but it potentially sounds hard and fragile. A very small custom kernel might be an alternative later.

*I mentioned to colin and he agreed, that we would desire to be merged and that the project can continue to be called wubi (to show continuity with our past efforts). Of course wubi will be only an internal project name and all rebranding can take place as usual. That said at the moment the title already reads "Ubuntu Setup", and the only explicit mention of wubi is in: the version (grayed out), folder name, file name, banner.*

Yes, the point here is not to obscure the origin of Wubi but just make sure we can have the slick custom artwork and tight branding we need for Ubuntu while allowing Wubi do do it's own thing in he standard version downloaded from your site. You might want to add options for Debian and Guadalinex for example.

---

### Post by ago on 2007-07-02
> **Henrik said:**
> Yes, he is clearly not fond of the partman solution used now.
I do not like it either, I had a bug reprot to remind me to improve on it ([https://bugs.launchpad.net/lupin/+bug/87846](https://bugs.launchpad.net/lupin/+bug/87846) ), but I never bothered since the proper solution is to use partman as opposed to skip it and so far the code, even if it is ugly, did not create any issues.

> He would like to see this implemented directly before we deploy it on the CD, so it probably looks like we will miss tribe 3.
I think we should still start importing as much code as possible. The idea is that any code insertion should be a complete pass-through under normal installation, so that is still a good test. Moreover we can keep the current hacks on a conditional basis: if we are doing a wubi-type installation use ugly hacks otherwise use normal code. Then we replace the ugly hacks by tribe 4. Pls let me know what is colin view on this.

> I'll speak with Colin and other team members at our meeting next week about partman, ntfs and artwork.

The full list of issues worth mentioning is:

[list]
[*] Rebooting issues (fuse should be taken care of properly by killall5), colin already knows about it
[*] Hard reboot issues. This is very important! Users do hard reboot since they do not know how to handle new situations, corruption might make the hosted fs unrecoverable (if journaling data is lost) and the hosting fs corrupted (requiring chkfs). This makes for some annoying pubblicity. At the moment I have "safe" values in sysctl.conf. But this is up to the kernel devs to decide what set of options are safe (given performance constraints) and up to the ntfs-3g devs to make sure that hard reboots are handled reasonably well (I'll see if szaka can do something about it).
[*] Apparently hibernation is impossible (since swap is inside another partition) and suspend is difficult whenever fuse is used (since fuse might get frozen before other processes that use the disk), so that both might have to be disabled. mjg59 might be able to make suspend to ram work in time for Gutsy.
[*] Partman: I think that it is up to colin to include support for loopmounted file targets, it's probably not worth to change the old code. 
[*] Lots of disk device modules are now pre-loaded into the initrd (in order to mount the host fs at full speed), there should be a mechanism such that root is mounted r/o and then remounted r/w after modules are loaded. (/etc/init.d/checkroot & co might be affected).
[*] host folder has to be pre-mounted r/w and it's not a good idea to umount that.
[*] ntfs-3g has to be in by default and uninstalling that will create problems (basically the machine will be unbootable).
[*] /boot folder has to be a folder on the hosting filesystem with r/w access or it would not be possible to upgrade the kernel. One issue is that menu.lst entries will appear under a path in Linux and a different path when booted from the host OS. For instance at the moment the boot folder is mounted under /media/host/wubi/boot which is symlinked to /boot. This means that under linux the kernel is visible as /boot/vlinuz... but under windows (when menu.lst is actually used) it is visible under C:\wubi\boot\vlinux. Hence update-grub does not get it right... I have no good way to make this process work under both a normal installation and a wubi installation.
[*] There is no fsck in ntfs-3g and you cannot mount r/w (and hence boot) from a system that is flagged as "dirty". You have to fix it up from windows first.
[/list]

> My use of the word module might have been wrong here. The key is to get read/write support into Ubuntu: [https://wiki.ubuntu.com/WriteSupportForNTFS](https://wiki.ubuntu.com/WriteSupportForNTFS)

There are 2 separate issues: 

1. Having write support by default for the hosting fs (namely ntfs). We do need that otherwise we have to ship the ntfs-3g package inside the initrd as we are doing now (which would be ugly).

2. Having write support offered as a kernel module as opposed to have it in userspace. Having the root filesystem on top of a userspace process creates problems. Hibernation and rebooting pop to mind, but you could also simply kill the fuse userspace processes by mistake... Fuse is very nice, but IMO not for root. Unfortunately we do not have much choice. 

EDIT: talked also with mjg59 and he agrees with szaka: #2 is not going to happen, so we'd better learn to live with fuse.

> That sounds good. You would also be able to start it with a given parameter? (distro=kubuntu, say)
Yes we do support parameters. For the moment only "debug", but we could of course do that. If we support that there is not much point to look for a CD/ISO at startup (we still look for ISO during installation).

This raises another question:

What do we do when a Ubuntu CD is used? Do we extract the ISO or do we assume that the CD is going to be inserted once you reboot (we might have a message for that)? 

> CD space is always at a premium so this would be great, but it potentially sounds hard and fragile. A very small custom kernel might be an alternative later.
That serves several purposes not just space savings. For instance at the moment you can only install an ISO that uses the same kernel of the one shipped with wubi. This means that you need to ship as many wubi versions as there are architectures/kernel builds. Which is fine for a version bundled with the ISO but it is an unnecessary complication for the stand-alone version. I do not think that such a solution would be fragile, but I am not sure how to handle the ISO mounting in windows. Any hint here would be handy.

> Yes, the point here is not to obscure the origin of Wubi but just make sure we can have the slick custom artwork and tight branding we need for Ubuntu while allowing Wubi do do it's own thing in he standard version downloaded from your site. You might want to add options for Debian and Guadalinex for example.
I would rather have our project completely incorporated, then Debian and Guadalinex are more than welcome to do their own rebranding. We would be unlikely to have more than 4-5 desktop environments anyway, since that would be considered confusing, therefore there would be little point to keep wubi as a separate branch once it is used in Ubuntu. And personally I would welcome the opportunity to help with official ubuntu code.

---

### Post by ago on 2007-07-02
> **ago said:**
> That serves several purposes not just space savings. For instance at the moment you can only install an ISO that uses the same kernel of the one shipped with wubi. This means that you need to ship as many wubi versions as there are architectures/kernel builds. Which is fine for a version bundled with the ISO but it is an unnecessary complication for the stand-alone version. I do not think that such a solution would be fragile, but I am not sure how to handle the ISO mounting in windows. Any hint here would be handy.

Hmm a quick google search shows that 7zip (LGPL) is capable or extracting from an ISO. That's all we need...

Assuming that lupin patches are already within the ISO initrd, we can either copy kernel/initrd from a mounted CD or from the target ISO.  

Henrik, do you have any reason to think that this might not be appropriate?

---

### Post by ago on 2007-07-02
Another idea is to have the drive dropdown to also include an option to simply boot the iso/cd:

**Installation Drive:**
C: 
D: 
Don't install, just run the CD.

Handy for persons with no CD rom that still want to do a full installation, also handy to go around bios problems and to spare people the trouble of burning the ISO. Uninstalling removes the boot.ini menu entry and the kernel and initrd (extracted from CD/ISO, see above).

Other option still is to add a direct installation options within the GUI:

**Installation Drive:**
C: (do not modify existing partitions)
C: (resize and create a new partition)
D: (do not modify existing partitions)
D: (resize and create a new partition)
Use available free space (shown if enough free/unpartitioned space is detected)
Don't install, just run the CD.

The interface is still clean and simple, and the operation is fairly safe (there is no option to format a partition actually containing data). The main issues against that are: 

1. if you use a dedicated partition you cannot guarantee a "full uninstallation", 
2. many people will be scared off even if the operation is fairly safe
3. if you can boot the live ISO, you can use that to do a full installation
4. the "language" above is too complex for the target audience

---

### Post by tuxcantfly on 2007-08-24
If anybody's still tracking this, the discussions on inclusion progress have moved to the ubuntu-installer mailing list. Also, the tool to transfer the loopmounted partitions to dedicated partitions (LVPM) could also be integrated into Gutsy's Ubiquity or be used as a small, standalone app installed once Ubuntu has been installed to a loopmounted partition.

---

### Post by ago on 2007-09-11
If anyone is curious, here is an update on what we have been working on.

What to expect:

* Lupin functionality (back-end code) has been merged by Ubuntu devs within the LiveCD and regular Ubuntu initrd
* Two new installation options have been added: "Dedicated Partition", and "Read Only Mode". The first will ask about partitioning info after reboot (via ubiquity), the second will simply boot the LiveCD/ISO (from there you can run the classic installer as well). Handy if you have adverse bios settings or no CD player.
* ntfs-3g, which is required by Wubi, will be installed by default in Ubuntu (so, as a side benefit, r/w access to your Windows partitions should be easier)
* Wubi will work with the LiveCD ISO as opposed to the alternate ISO
* It will be possible to run Wubi with a physical CD as well
* The blue text-based installation screens you used to see after first reboot got a face-lift, you will now get a fully graphical interface based on ubiquity.
* Hampus is working to improve the downloader adding segmented downloads (much faster), but not sure when that will be ready.
* Wubi has been put on diet, it now weights only 600K (down from 10000K!).

What _not_ to expect:

* Suspend/Hibernation will not work, suspend might be fixed in Hardy, but it's not going to happen in Gutsy.
* Filesystem robustness to hard reboots is not going to be much better than what we have at the moment
* When "dedicated partition" is selected, the above issues will be addressed, but you will only be able to uninstall the windows files, not to remove grub and the installed partition.
* Resizable disk images will not be available for the time being

As mentioned above, Tuxcantfly started discussing the possibility of having LVPM as an official Ubuntu product, its functionalities might get incorporated within Ubiquity and will allow you to upgrade smoothly from a loopfile installation to a dedicated partition installation. 

You can expect a wubi-gutsy pre-release version in the coming days, so stay tuned since we will need heavy testing, your feedback is highly welcome (as usual).

---

### Post by trommas on 2007-09-21
So is this a different iso, or should we just download the daily build?

---

### Post by ago on 2007-09-21
> **trommas said:**
> So is this a different iso, or should we just download the daily build?

The backend is still broken at the moment and requires quite a bit of manual intervention to make it work, I'll let you know as soon as there is something you can play with. If you are curious the builds are in 

[http://wubi-installer.org/devel/minefields/](http://wubi-installer.org/devel/minefields/)

---

### Post by ago on 2007-09-21
In fact to make it work try that:

1. Download the daily build and burn a CD
2. Run wubi and select 4Gb installation
3. Before rebooting edit c:/ubuntu/install/grub/menu.lst and delete find_iso=XYZ
4. Reboot without the CD inserted
5. When asked instert the CD

Let me know how it goes. Probably not very far...

---

### Post by trommas on 2007-09-21
> **ago said:**
> The backend is still broken at the moment and requires quite a bit of manual intervention to make it work, I'll let you know as soon as there is something you can play with. If you are curious the builds are in 

[http://wubi-installer.org/devel/minefields/](http://wubi-installer.org/devel/minefields/)

Nice! :)

But this won't work at all at the moment, or?

---

### Post by ago on 2007-09-21
[http://ubuntuforums.org/showpost.php?p=3403193&postcount=20](http://ubuntuforums.org/showpost.php?p=3403193&postcount=20)

---

### Post by trommas on 2007-09-21
> **ago said:**
> In fact to make it work try that:

1. Download the daily build and burn a CD
2. Run wubi and select 4Gb installation
3. Before rebooting edit c:/ubuntu/install/grub/menu.lst and delete find_iso=XYZ
4. Reboot without the CD inserted
5. When asked instert the CD

Let me know how it goes. Probably not very far...

Sorry, my cdplayer doesn't work at the moment (that's why I install from windows). Again, sorry :(

---

### Post by ago on 2007-09-21
> **trommas said:**
> Sorry, my cdplayer doesn't work at the moment (that's why I install from windows). Again, sorry :(

You can still use the new wubi for a read-only installation without CD. No need to pre-download anything.

If you have other partitions on your machine you can use the installer you will find in the read-only desktop to install to the other partitions. The read-only installation can be uninstalled from windows as usual, the one done via the Ububuntu installer is instead a real installation.

---

### Post by ago on 2007-09-21
> **ago said:**
> You can still use the new wubi for a read-only installation without CD. No need to pre-download anything.

And that should even work!

---

### Post by ago on 2007-09-21
To be precise, if you are used to the old wubi, the new one has 3 installation modes:

* Use CD: only shown if a CD is detected, it simply helps booting the CD without having to tweak the Bios. This one should work at the moment.

* Read-Only: will basically use an ISO on the hard disk and boot that as if it was a live CD, good to play with wubi if you do not have a CD player or if you have little space on the HD. You can then launch the classic installer from there but it will only be able to install onto a different partition (you cannot install the real Ubuntu on the partition where you installed wubi). This one should work at the moment.

* Loop-Installation: same as our current installer. At the moment it does not work unless you use the trick above (and even with that it might be problematic).

---

### Post by trommas on 2007-09-21
> **ago said:**
> And that should even work!

It looks promising, but to not mess things up: I have dowloaded wubi to d: (ntfs). I have an empty ext3 partition u: - but wubi only lists d: as an alternative. What should I do?

---

### Post by trommas on 2007-09-21
Thanks!

---

### Post by ago on 2007-09-21
> **trommas said:**
> It looks promising, but to not mess things up: I have dowloaded wubi to d: (ntfs). I have an empty ext3 partition u: - but wubi only lists d: as an alternative. What should I do?

Make sure that the ISO is called gutsy-desktop-i386.iso and is in the same folder as wubi
Run wubi and in the size selector choose: 1GB (Read Only). 
In the installation drive select C: or D: (any windows partition, NOT the ext3 partition, which should not be visible anyway)
Reboot into ubuntu. You can use it as it is, but it's read only. If you do not like it you can uninstall from windows.
If you want a real installation in the Ubuntu desktop run "Install", this will launch the classic installer. There you shuld be able to select the empty partition.

---

### Post by trommas on 2007-09-22
> **ago said:**
> Make sure that the ISO is called gutsy-desktop-i386.iso and is in the same folder as wubi
Run wubi and in the size selector choose: 1GB (Read Only). 
In the installation drive select C: or D: (any windows partition, NOT the ext3 partition, which should not be visible anyway)
Reboot into ubuntu. You can use it as it is, but it's read only. If you do not like it you can uninstall from windows.
If you want a real installation in the Ubuntu desktop run "Install", this will launch the classic installer. There you shuld be able to select the empty partition.

Sorry, this should probably be posted in a new thread...

This is exactly what I want :) After choosing "Read Only", it downloaded an iso, then it started searching through my windows folders (my program files etc.), then it aborted with the message: "Could not retrieve some essential files".. So close!

---

### Post by ago on 2007-09-22
Can you try with the latest wubi/iso?
Should be rev296, delete the old iso.

If it repeats try to start wubi with the "--debug" option

---

### Post by trommas on 2007-09-23
> **ago said:**
> Can you try with the latest wubi/iso?
Should be rev296, delete the old iso.

If it repeats try to start wubi with the "--debug" option

Of course :) But the file at [http://wubi-installer.org/devel/minefields/](http://wubi-installer.org/devel/minefields/) seems to be the same that I used earlier. Also: would you like me to let wubi download the iso by it self, or should I pick the latest nightly build?

---

### Post by ago on 2007-09-25
> **trommas said:**
> Of course :) But the file at [http://wubi-installer.org/devel/minefields/](http://wubi-installer.org/devel/minefields/) seems to be the same that I used earlier. Also: would you like me to let wubi download the iso by it self, or should I pick the latest nightly build?

We update the files more than once a day. That is true both for wubi and for the ISO.

At the moment wubi will only work with a physical CD or in Read Only Mode.

---

### Post by akb on 2007-10-06
Hi,

I'm trying to install Gutsy using the minefield build, but it doesn't detect my cd drive. Any idea how to work around this? Is it a known bug or am I the first? :-)

---

### Post by ago on 2007-10-06
> **akb said:**
> Hi,

I'm trying to install Gutsy using the minefield build, but it doesn't detect my cd drive. Any idea how to work around this? Is it a known bug or am I the first? :-)

Are you using a physical CD or an ISO? Also make sure you download the latest version (not the cdboot one).

---

### Post by akb on 2007-10-06
I've tried both executables found in the minefield.

Ubuntu-7.10-alpha.exe:

Started the program and when it tried to access wubi-installer.org it ran into an endless loop of "Trying again in 5 seconds..." tries. I tried to avoid this by downloading the alternate install cd of the beta (AMD64 version like --debug told me) and renaming it to gutsy-desktop-amd64.iso, as it tried to access the iso under this name and --debug also told me it had correctly identified the iso... but it got once more into the endless loop to retrieve the meta info file.

Then I read here that you mentioned to install gutsy was only possible when using the cdboot version, so I tried this one.

Ubuntu-cdboot-7.10-alpha.exe:

This one doesn't even start. It tells just at start "Could not find any appropriate CD" [edit: burned the cd and put it into my one and only cd drive]. When starting it with --debug I got the message "cddrive=", so it doesn't seem to detect the drive at all. After checking this with the normal installer again, --debug tells the same there too, no cddrive.

---

### Post by ago on 2007-10-06
> **akb said:**
> I tried to avoid this by downloading the alternate install cd of the beta (AMD64 version like --debug told me)
there is a bug at the moment in the arch detection, it always returns amd64. Moreover the metalinks for amd64 are missing. I will fix it probably tonight.

 
> Ubuntu-cdboot-7.10-alpha.exe:
That one only works with a physical CD in the tray.

---

### Post by akb on 2007-10-06
> **ago said:**
> there is a bug at the moment in the arch detection, it always returns amd64. Moreover the metalinks for amd64 are missing. I will fix it probably tonight.
okay, nice... and thank you :-)
one quick question: does the amd64 release work with core2duos too? don't know how far amd64 and intels 64bit architecture are compatible and/or if Ubuntu is released for amd and intel 64bit combined or severed.
> That one only works with a physical CD in the tray.
the burned cd has been in the tray

---

### Post by ago on 2007-10-06
> **akb said:**
> okay, nice... and thank you :-)
one quick question: does the amd64 release work with core2duos too?
no clue. But now that you mention it, the arch detection might not be that off after all...

> the burned cd has been in the tray
hmm that's strange... And very urgent to fix. Will upload something soon.

---

### Post by akb on 2007-10-06
Yes... but I don't think it's got something to do with the iso, but rather with the drive detection at all.

heres a screenshot:

[IMG]http://dl1.upload.ws/image-1488741.jpg[/IMG]

Could it be a problem that my cd drive is not my last connected drive letter?

---

### Post by ago on 2007-10-06
I am going to turn on some more debugging code and upload

---

### Post by ago on 2007-10-06
The image should be up (rev 314). If you run with --debug you should see a message for each drive scanned

I added the metalink files. But the arch detection will be tricked into believing that you have an amd64 if you use a core duo 64bit.

---

### Post by akb on 2007-10-06
it now lists all the checked drive letters, but doesnt use the right one for "cddrive=", therefor doesn't work, just like before.

Ubuntu-7.10-alpha.exe --debug (after chosing installation type and so on):

```
arch=amd64
DetectCD
Testing D:
Testing C:
Testing Q:
Testing V:
cddrive=
DetectIso
IsValidIso ispoath=Q:\ubuntu\install\gutsy-desktop-amd64.iso
7z [...] Everything is Ok
isvalid Ubuntu 7.10 "Gutsy Gibbon" - Beta amd64 (20070925.1)
cdinfo=Ubuntu 7.10 "Gutsy Gibbon" - Beta amd64 (20070925.1) cdversion=7.10
cddistro=Ubuntu cdarch=amd64 cdcodename=Gutsy Gibbon cdsubversion=Beta
Success Ubuntu 7.10 "Gutsy Gibbon" - Beta amd64 (20070925.1)
Using iso in Q:\ubuntu\install\gutsy-desktop-amd64.iso
```

Then it hangs in the retry-loop for:
```
Retrieving installation files ubuntu-desktop-amd64.iso.metalink
Connecting to http://wubi-installer.org/...
Retrying in 5 seconds...
```

Ubuntu-cdboot-7.10-alpha.exe --debug (with CD inserted in D:):

```
arch=amd64
DetectCD
Testing D:
Testing C:
Testing Q:
Testing V:
cddrive=
Could not find any appropriate CD
```

---

### Post by ago on 2007-10-06
> **ago said:**
>  But the arch detection will be tricked into believing that you have an amd64 if you use a core duo 64bit.

That in fact might not be an issue since on ubuntu website I read:

"64bit AMD and Intel computers"

So arch detection is fine.

---

### Post by akb on 2007-10-06
Okay, thanks. Remains "just" the problem with either the cd detection (cdboot) or the metalink download (normal installer) :-(

---

### Post by ago on 2007-10-06
> **akb said:**
> Okay, thanks. Remains "just" the problem with either the cd detection (cdboot) or the metalink download (normal installer) :-(

If you can make it on irc freenode #wubi it will be easier

---

### Post by akb on 2007-10-06
> **ago said:**
> If you can make it on irc freenode #wubi it will be easier
joined it.

---

### Post by ago on 2007-10-07
I have uploaded a new version that should be able to complete a 7.10 loopinstallation.

[http://wubi-installer.org/devel/minefields/Ubuntu-7.10-alpha.exe](http://wubi-installer.org/devel/minefields/Ubuntu-7.10-alpha.exe)

You will need to edit /ubuntu/disks/boot/grub/menu.lst to boot the installed system

kernel /boot/vmlinuz* root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.gz

Change sda1 with whatever is appropriate for your case (note that often it should be sdaX instead of hdaX even for ata drives)

If you have previous versions of wubi, uninstall them first

Those are very early builds so watch out!

---

### Post by BernardB on 2007-10-08
Tried it; partitioner hangs at 57% while scanning disks. :(

Ready for another version when you are. :razz:

---

### Post by ago on 2007-10-08
> **BernardB said:**
> Tried it; partitioner hangs at 57% while scanning disks. :(

Ready for another version when you are. :razz:

That takes a bit of time. (~10minutes) Just wait a bit.
Tonight by the way I may have a version that fixes the grub issues (now you need to edit the menu.lst file manually).

---

### Post by ago on 2007-10-08
Make sure you use the latest version from the website. Also remove any previous installation.

---

### Post by ago on 2007-10-08
If you get stacked for any reason avoid hard reboots:

Try ctrl+alt+f2 to get a console and reboot from there, if that does not work try ctrl+alt+backspace to kill X, if that does not work keep pressed Alt+SysRq and type REISUB.

If you end up with a messed up ntfs use RC.iso  and run chkdsk /r.

---

### Post by BernardB on 2007-10-09
Just tried the newest version; now it hangs at 30% while "Installing System", "Copying files...".

---

### Post by ago on 2007-10-09
> **BernardB said:**
> Just tried the newest version; now it hangs at 30% while "Installing System", "Copying files...".

Hmm that should work well. It takes a few minutes to complete did you wait a bit? Also please use the latest build rev320+.
You can look into var/log/syslog for hints

---

### Post by BernardB on 2007-10-09
Yes, I always use the latest version and know how to wait long enough to know HDD I/O isn't doing anything at all.

I cannot navigate to var/log/syslog as my keyboard does not seem to work in this state - I am unable to type anything into the console and when I use the shutdown button to shut it down it does not seem to respond to the ENTER-key when asked to press it after all drives have been cleared. 

BTW, when I hold the shutdown button to shut down or when I drop to console  I get error codes which looks like this (where the beginning number constantly changes):
> [ 736.481596 ] bcm43xx: Error: Microcode: "bcm43xx_microcode5.fw" not available or load failed
Unless they look familiar to you I assume they are related to some Broadcom ethernet chip this laptop probably has.

---

### Post by ago on 2007-10-09
If you cannot shutdown use the sysctl key combinations (that should work regardless). Apparently there is still a general bug in unionfs which might explain that. What ISO did you use? Try the latest daily build, not the beta.

---

### Post by BernardB on 2007-10-09
I have indeed been using the AMD64-desktop beta.
So I downloaded the latest AMD64-desktop build; it now stops with an error message stating it doesn't want to mount / on a ntfs filesystem. 
I guess something went wrong with the virtual filesystem (or Lupin).
Keyboard seemed to work though.

---

### Post by ago on 2007-10-09
Do a clean install and run chkdsk /r 
I'll upload a new rev soon though, you may want to wait for that

---

### Post by ago on 2007-10-09
rev 323

---

### Post by BernardB on 2007-10-10
Used yesterday's gutsy desktop build (i386 first and later amd64, simply renamed i386 to amd64; I am assuming Lupin can handle that) and the latest installer but i386 hangs at 31% while copying files and amd64 hangs at 44% while copying files.

I have run chkdsk /r before and in between these two installations but that apparently won't stop it from having such trouble.

As the keyboard worked (I might have accidentally enabled scroll lock in some of the previous tries) I tried to navigate to /var/logs/syslog after the i386 hung, but nothing happened after I entered "nano /var/log/syslog" (might've been erroneous but I couldn't break it). The amd64 refused to respond at 44% (couldn't even move the mouse).

---

### Post by ago on 2007-10-10
Can you try to find out if its the following bug?

[https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/145012](https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/145012)

---

### Post by ago on 2007-10-10
Also what you can try is to remove the "automatic-ubiquity" from install/boot/grub/menul.lst
This will boot into gnome.
Then mount /var/log on a separate filesystem (or remote syslog server)
Then run the installer by running "ubiquity --automatic" or "ubiquity --automatic --debug"
So after a crash you can still access the logs.

---

### Post by ago on 2007-10-10
You can post the syslog/+installer logs/casper.log here (zipped).

---

### Post by BernardB on 2007-10-10
> **ago said:**
> Can you try to find out if its the following bug?

[https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/145012](https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/145012)
Doubt it. I always set it to English and despite the strange Broadcom errors ethernet does seem to work (the errors probably refer to a Broadcom Wi-Fi chip).
Plus, install/boot/grub/menu.lst claims locale is set to "en_EG".
> **ago said:**
> Also what you can try is to remove the "automatic-ubiquity" from install/boot/grub/menul.lst
This will boot into gnome.
Then mount /var/log on a separate filesystem (or remote syslog server)
Then run the installer by running "ubiquity --automatic" or "ubiquity --automatic --debug"
So after a crash you can still access the logs.
GNOME boots nicely. Used the renamed i386 but it hung while copying files, I am guessing somewhere around 30%. When it hangs the entire GUI freezes but the mouse still works; after dropping to a console I can type "ls" and hit ENTER but no response appears.

Some remarks:
The live (unionfs?) filesystem size is about 1.1GB.
I always leave size in the installer at the default of 15GB. Generally, after crashes Windows indeed confirms that the size of C:/ubuntu is about 13-15GB. However, after running the installer filesystem size only goes down from about 44GB to about 42GB and removing the 15GB-sized C:/ubuntu folder only gives back those 2GB's.
I have never seen such inconsistent filesystem behaviour from Windows before.
EDIT:
Ah, the ubuntu folder has a size of 14,9GB but "size on disk", whatever that means, is only 1,99GB.


I don't have a remote syslog server or any other common Linux filesystem on this laptop, but I just realised that Ubuntu now does NTFS out of the box (and I have a USB stick as well) - if still very relevant, I'll do my best to obtain such logs before tonight.

---

### Post by ago on 2007-10-10
I'd try the following things.

0. Uninstall and Select 4GB size
1. Before rebooting set the language in install/preseed.cfg and menu.lst to en_US (ps, what is your country?)
2. Remove automatic-ubiquity from /install/boot/grub/menu.lst and boot 
3. Edit /bin/autopartition-loop, look for "dd", make sure it zeroes the whole image (the first part of the if block zeroes the full image but only for swap, take that out of the if block and delete the rest so that all images are completely zeroed (it will take several minutes).
4. Mount your usb disk as /var/log (sudo mount /dev/sda2 /var/log)
5. Run the installer

---

### Post by BernardB on 2007-10-10
/dev/sda2 is apparently some sort of recovery partition, and sda3 also seems to contain Dell tools; I was unable to find the USB stick in this way (it won't let me do a "sudo mount /media/SWISSMEMORY /var/log") but rebooted to be sure I didn't mount things incorrectly and then used /dev/sda2 because I know how to reach it from Windows.

Succeeded in 0-5, but the automatic installer claimed no root filesystem was selected (not sure how that suddenly happened) - I suppose I can try to manually select it in the non-automatic installer and see how it goes?

---

### Post by ago on 2007-10-11
> **BernardB said:**
> Succeeded in 0-5, but the automatic installer claimed no root filesystem was selected (not sure how that suddenly happened) - I suppose I can try to manually select it in the non-automatic installer and see how it goes?

Run chkdsk and start from a clean installation. If that comes back send me the logs

---

### Post by BernardB on 2007-10-11
Did that, still got the same error message.
Attached are the only logs found in /dev/sda2; hope it makes any sense.

Since this particular problem doesn't hang the system it could also be repeated without mounting /var/log on /dev/sda2; doing this right now.

---

### Post by ago on 2007-10-11
hmm no I'd need syslog mostly

---

### Post by BernardB on 2007-10-11
> **BernardB said:**
> Since this particular problem doesn't hang the system it could also be repeated without mounting /var/log on /dev/sda2; doing this right now.
Here we go...

---

### Post by ago on 2007-10-11
can you check that you have a valid recipe in install/preseed.cfg?

---

### Post by BernardB on 2007-10-11
See attachment.

---

### Post by ago on 2007-10-11
do a fresh install then please send me 

/var/cache/debconf/config.dat (get that file BEFORE running ubiquity)

run ubiquity --automatic (no debug)

send me /var/log/casper, /var/log/syslog and /var/log/installer

thanks for the trouble

---

### Post by BernardB on 2007-10-11
See the attachments. Hope they help.
Used a renamed i386 release candidate and set locale to en_US and zeroed like earlier.
Still got the no root filesystem detected bug. Wondering whether the normal automatic-ubiquity route still crashes or works or gives the same bug.

---

### Post by ago on 2007-10-12
Those look good to me. not quite sure what happened.

---

### Post by BernardB on 2007-10-12
Tried to do a fresh install with the new installer and renamed i386 RC but the installer says "Could not retrieve some essential files".

---

### Post by ago on 2007-10-12
If you have 7zip installed try to uninstall it temporarily. You can run with --debug, but i am quite sure it is a 7z issue

---

### Post by BernardB on 2007-10-12
No, I don't have 7-Zip installed; the installer seems to detect I am using a renamed i386 RC.
In fact, removing the renamed iso, removing the installer and installing again (so letting it download a new amd64 RC) crashes the program, I think while getting the metalink file.
The only peculiar thing I find in --debug is this:
> different isoname ubuntu-7.10-rc-desktop-amd64.iso != gutsy-desktop-amd64.iso

Edit: Removed some old ISO's I had on my HDD; still crashes, --debug seems to show it thinks some ISO which has nothing to do with Ubuntu is the required ISO.
After renaming the file and changing its file extension it still attempts to use it - very peculiar bug.
Then again, after moving the specific ISO to another partition it is still crashing without any apparent cause.

---

### Post by BernardB on 2007-10-15
Messed with it a zillion times but it still crashes after getting the metalink on that laptop; I tried it out on another 32-bit Vista laptop and it did seem to work there.

Regardless, I tried installing it on a very similar laptop as the one I have done all the tests on (main difference is XP and single core instead of X2) a few hours ago and installing went flawlessly. The only issues I encountered were:
1. GRUB´s menu.lst was incorrect; for root it referred to hd(0,0) while for the kernel it referred to /dev/sda2. Also it still included automatic ubiquity and the locale setting; I assume this should not have been there after the installation.
2. X.Org (I think Usplash) is having problems starting. For the moment, I am assuming this has to do with ATI´s magnificent drivers.

---

### Post by ago on 2007-10-15
> **BernardB said:**
> Messed with it a zillion times but it still crashes after getting the metalink on that laptop; I tried it out on another 32-bit Vista laptop and it did seem to work there.
The issue at the moment is that if you have an iso in the backup folder it will crash. If you start with a new installation w/o backup or select a different iso it should go through.

> 1. GRUB´s menu.lst was incorrect; for root it referred to hd(0,0) while for the kernel it referred to /dev/sda2.
That one is interesting!

> Also it still included automatic ubiquity and the locale setting; I assume this should not have been there after the installation.
That is also interesting, will have a look. I assume you are talking about /ubuntu/disks/boot/grub/menu.lst as opposed to /install//boot/grub/menu.lst

> 2. X.Org (I think Usplash) is having problems starting. For the moment, I am assuming this has to do with ATI´s magnificent drivers.
Shouldn't have much to do with wubi.

That pretty much sums up my current priorities.

---

### Post by BernardB on 2007-10-15
> **ago said:**
> The issue at the moment is that if you have an iso in the backup folder it will crash. If you start with a new installation w/o backup or select a different iso it should go through.
No, I doubt it is that easy, by "zillion times" I also mean I constantly delete the backup folder and any other ubuntu ISO´s I have on the hard disc. Maybe if you can put a slightly older version online I can check whether it still functions correctly in that one.
> **ago said:**
> That one is interesting!
...
That is also interesting, will have a look. I assume you are talking about /ubuntu/disks/boot/grub/menu.lst as opposed to /install//boot/grub/menu.lst
Indeed I am; the one in /install is I assume only used for the one-time installation.

Regarding GRUB again, after a kernel update it seems to have broken menu.lst again; what should have been root=/dev/sda2 now is root=/host/ubuntu/disks/root.disk and the entire loop part is gone.
Also, I left the installer at the default 15GB size and now the "size" of C:\ubuntu is 14,6GB, the "size on disk" is 4,76GB while / in Ubuntu seems to have a size of around 10GB; I wonder how this will stretch up as I fill it.

Keep up the good work though, I believe projects like these have a huge impact on attracting new Linux users.

---

### Post by ago on 2007-10-15
> **BernardB said:**
> 
Regarding GRUB again, after a kernel update it seems to have broken menu.lst again; what should have been root=/dev/sda2 now is root=/host/ubuntu/disks/root.disk and the entire loop part is gone.
It'd be interesting to know whether update-grub was also updated.

> Also, I left the installer at the default 15GB size and now the "size" of C:\ubuntu is 14,6GB, the "size on disk" is 4,76GB while / in Ubuntu seems to have a size of around 10GB; I wonder how this will stretch up as I fill it.
NTFS and ext3 support sparse files. Those are the ones used at the moment, even though I'll probably move to an hybrid approach (first 4GB preallocated and then 20GB sparse).

---

### Post by ago on 2007-10-18
Update:

Most of lupin (wubi backend) is now in Gutsy, thanks to the efforts of 2 of the leading Ubuntu developers, Colin Watson and Evan Dandrea, as well as myself. Lots of other improvements were also made in projects Wubi relies upon: namely grub4dos (Tinybit and Bean123) and MetaDl (Hampus Wessamn). Tuxcantfly has been focusing mostly on LVPM, LUBI and Unetbootini (hopefully LVPM will be merged with Ubiquity in the next release cycle). 

Unfortunately we have been blocked by other projects (unionfs in particular) and testing has been very difficult until literally a couple of days before beta. That was too short time to solve the remaining issues and hence it was decided to only include a limited version of wubi in the LiveCD (wubi-cdboot) which will help people boot a physical CD going around bios issues (so instead of having to change the boot order in the bios, you can now use wubi-cdboot). We are still in for Hardy as far as the Live CD goes. 

That said our main strength is the standalone installer which is not strictly linked to the release cycle of the CD. So I'll try to push Wubi as an official stand-alone installer on the main Ubuntu download page well before Hardy. We'll see what happens...

You can expected a reasonable 7.10 alpha this weekend, that will not be publicized on the website and will only be available in: [http://wubi-installer.org/devel/minefields/](http://wubi-installer.org/devel/minefields/) 

The 7.10 beta release will depend on the bug reports, hopefully it will be 1 week from now. That will hit our website and will replace the current version. If the feedback is good we might even remove the "beta" badge...

---

### Post by MSchenker on 2007-10-18
You are doing amazing work on Wubi!  I'm now joining the Ubuntu/Kubuntu community in a major way, and it is all because of Wubi.

I might give the 7.10 Wubi a try.

Should I wait until early next week, or do you think the current version is good enough?  At this point, I'd just be interested in giving it a try, not for full production use.

I'm really hoping to see Wubi as a standard install feature in Ubuntu/Kubuntu.

Thanks for all the hard work!

---

### Post by akb on 2007-10-18
MSchenker, for me wubi worked quite well for gutsy already a few revisions ago. Tested it last week or so and it worked almost out of the box. The only issue I found was that I had to edit the path to wubis root hdd, as I installed it onto my second hard disk. But this was just editing a oneliner within Windows to point to (hd1,0) instead of (hd0,0).

I did not find any other wubi related issues, so if you're going to test outside a productive system anyway, I think you'll be fine with trying right now. Afaik the worst case scenario would be having a wubi installation that's not working, but I wouldn't care about that, since it doesn't affect your system and you can simply remove it after that again.

---

### Post by MSchenker on 2007-10-18
akb,
Thanks for jumping in with an answer!  I'm still fairly new at the whole Linux world, so I move slowly!

OK, should I uninstall the old Wubi 7.04 installation before running the Wubi 7.10 alpha?

---

### Post by akb on 2007-10-18
if you're not quite familiar with linux i'd uninstall the old installation to get a clean one that does not require you to edit the menu.lst or something like that. well, you may nevertheless have to do that if you run into problems like if its not booting, but you can minimize the risk for it by uninstalling the old one.

if you'd like to save the installation, do so, you should be able to reproduce the current state with some file copy and paste.

---

### Post by asbjornu on 2007-10-18
I just tried Wubi 7.10 Alpha and got the following error message:
```

Assertion failed!

Program: C:\WINDOWS\DESKTOP\UBUNTU-7.10-ALPHA.EXE
File: /build/buildd/mingw32-3.4.5.20060227.2.dfsg/build...
Line: 247

Expressioin: w32_sharedptr->size == sizeof(W32_EH_SHARED)

```
I'm trying to run it from a Windows 98SE installation without a CD-ROM or floppy drive (which is why I would like to use Wubi; it's hard to boot from a CD without a CD-ROM :)).

---

### Post by Ljorring on 2007-10-19
I tried to use Wubi installer for 7.10, and after the reboot and boot into the ubuntu installer, I ended up in a screen like this:

**
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7)....
Enter 'help' for at list of built.in commands

(initramfs) _
**

I can write several linux commands and browse my linux directories from there... Am I doing something wrong?

---

### Post by ago on 2007-10-19
> **Ljorring said:**
> I tried to use Wubi installer for 7.10, and after the reboot and boot into the ubuntu installer, I ended up in a screen like this:

Is this during installation or after installation? I mean do you see the chocolate screen? Does that finish ok?

---

### Post by asbjornu on 2007-10-19
Is [the error I encountered](http://ubuntuforums.org/showthread.php?t=447764&page=9#post_message_3563178) caused by something in my environment or a bug in Wubi? I'd love to innstall Xubuntu with Wubi on my Compaq Armada M300, but can't right now because there's no floppy disk or CD-ROM drive on it plus no way (that I know of) to virtually mount the Xubuntu ISO image in Windows 98 and innstall it via Live CD. Not even sure that would work after reboot (I guess you need to be able to boot off the CD or at least have it available after boot, which I won't).

If this is a bug in Wubi, do you have any ETA on when it will be fixed so I can try a new version then and help with the alpha/beta testing?

---

### Post by ago on 2007-10-19
It's probably on our side, I need to check how we compile the software to make it compatible with windows 98.

---

### Post by asbjornu on 2007-10-19
I gave Wubi 7.10 Alpha another try, and here's more information about the error I get:
```

UBUNTU-7 caused an exception 03H in the module MSVCRT.DLL at 0167:7800e34d.

Registry:
EAX=00000004 CS=0167 EIP=7800e34d EFLGS=00000246
EBX=00fb09d0 SS=016f ESP=011cf36c EBP=011cf690
ECX=80004980 DS=016f ESI=0000002c FS=5697
EDX=80008718 ES=016f EDI=011cf758 GS=0000

Byte at CS:EIP:
5e c9 c3 83 f8 05 74 f8 e9 29 c4 ff ff 66 f7 05 

Stack trace:
00000000 575c3a43 4f444e49 535c5357 5649524b 524f4245 42555c44 55544e55 312e372d 4c412d30 2e414850 00455845 0e67a8c1 02020e9f 803e52e9 bfdf1020
```
If I press "Ignore", I get the following error:
```

Assertion failed!

Program: C:\WINDOWS\DESKTOP\UBUNTU-7.10-ALPHA.EXE
File: /build/buildd/mingw32-3.4.5.20060117.1.dfsg/build...
Line: 241

Expressioin: GetAtomName (atom, s, sizeof(s)) != 0
```
With the following debug information:
```

UBUNTU-7 caused an exception 03H in the module MSVCRT.DLL at 0167:7800e34d.

Registry:
EAX=00000004 CS=0167 EIP=7800e34d EFLGS=00000246
EBX=00fb09d0 SS=016f ESP=011cf35c EBP=011cf680
ECX=80008718 DS=016f ESI=00000026 FS=5697
EDX=80004980 ES=016f EDI=011cf758 GS=0000

Byte at CS:EIP:
5e c9 c3 83 f8 05 74 f8 e9 29 c4 ff ff 66 f7 05 

Stack trace:
00000000 575c3a43 4f444e49 535c5357 5649524b 524f4245 42555c44 55544e55 312e372d 4c412d30 2e414850 00455845 312e372d 4c412d30 2e414850 00455845 
```
Please just let me know if this information is completely useless and if so, how I should submit bug reports and what information you're interested in! :)

---

### Post by Planets on 2007-10-20
Trying to install Ubuntu with Wubi, I get a black screen after selecting "Ubuntu-Linux" from the boot menu. Running Windows Vista.

---

### Post by PGHammer on 2007-10-25
We have a successful install of 7.10 (Gutsy Gibbon) from Vista Ultimate!

Install used Wubi-alpha-368.exe and the Ubuntu-desktop-7.10-i386.iso I downloaded separately via torrent.

It picked up the nine updates since 7.10's launch, then went one step further and offered to install the accelerated drivers for ATI cards (I have an X1650PRO AGP).  Though they were an option for 7.04 (Feisty Fawn), that version did *not* offer to install them (I had to install them manually via apt-get).  Advantage: Gutsy Gibbon.

Like 7.04, my Audigy 2 ZS was detected without prompting.

Also, like every other Linux (or UNIX) distribution I've ever bare-metal tested since I've owned the printer, it picked up my HP DeskJet 940C automagically (and it's connected via USB).  CUPS (AKA Plug and Print) strikes again.

Looks like we have a winner here, folks....

---

### Post by ago on 2007-10-25
I am unsticking this post, the summary of what happened and what might happen is here:

[http://ubuntuforums.org/showpost.php?p=3557352&postcount=83](http://ubuntuforums.org/showpost.php?p=3557352&postcount=83)

Wubi 7.10 Alpha is getting there...

---

