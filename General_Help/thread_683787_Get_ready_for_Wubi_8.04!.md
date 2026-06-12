---
title: "Get ready for Wubi 8.04!"
date: 2008-01-31
forum: General Help
---

### Post by ago on 2008-01-31
Wubi now ships with Ubuntu 8.04.  Alpha5!!! 

I am particularly pleased about this for two reasons:

1) This is the first release within the 8.04 Ubuntu cycle
2) Even if still an alpha, this can probably be considered the first "official" Wubi release with the Ubuntu stamp on it!!! 

Many, many thanks to Evan D'Andrea and Colin J Watson that made it possible to incorporate Wubi/Lupin code within Ubuntu.

The latest Wubi alpha version (testers only) is available here: [http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)

Gotchas:[list]
[*]Wubi 8.04 requires the Hardy Desktop Alpha5 ISO or later daily build/release. Old hardy ISOs are not supported, if you have an old hardy-desktop ISO laying around, please remove that to make sure that the newer Alpha5 ISO is used instead.  
[*] Wubi will download the (Ubuntu) ISO for you, if you prefer to download it yourself (Wubi downloader can be slow at times), place the ISO in the same folder where you have wubi.exe:
* Daily ISO for 32bit machines: [http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.iso](http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.iso)
* Daily ISO for 64bit machines: [http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-amd64.iso)
[*] If you have problems booting, try first to run "chkdsk /r" in Windows within the same drive where you installed Wubi.
[*] If you still have problems booting, press ESC when you see a countdown after selecting Ubuntu, and try the available options
[*] If you want to keep your previous 7.10 installation, backup the /ubuntu/disks directory (note that the /ubuntu folder will be deleted and regenerated).
[*] Suspend and hibernation do not work in Wubi 8.04.
[*] The version of Ubuntu which is installed is also an Alpha, this has two implications: 1) it may contain bugs, 2) once installed you can expect that several packages will be upgraded on a daily basis (far more often than in a final release).
[/list]

---

### Post by EXCiD3 on 2008-01-31
When is alpha 4 being released? I cant wait! I'm running alpha 3 right now and it works great. Can i get all the updates through the update manager to make mine essentailly alpha 4?

---

### Post by flamelab on 2008-01-31
Thanks ago !!:guitar::guitar::guitar:


But .... the links don''t work ! 

On the Ubuntu server there is no Hardy 4 ...

---

### Post by rw2007 on 2008-01-31
Would you recommend a newbie like me installing it or just wait until it comes out on beta?  BTW when will beta be released?

---

### Post by ago on 2008-02-01
Official ISOs are not out yet, but you can try  Wubi-8.04-rev395.exe ( [http://wubi-installer.org/devel/minefield/Wubi-8.04-alpha-rev395.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04-alpha-rev395.exe) ) with the latest daily build

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It's almost the same as the alpha4, grab the iso that is appropriate for you and put it in the same folder as wubi.

---

### Post by ago on 2008-02-01
> **rw2007 said:**
> Would you recommend a newbie like me installing it or just wait until it comes out on beta?  BTW when will beta be released?

If you are open minded and keep expectations low (alpha software is buggy), why not? You can always uninstall. In the worst case you will have to run chkdsk /r from windows. If you want a smooth ride, then you are better off waiting.

[https://wiki.ubuntu.com/HardyReleaseSchedule](https://wiki.ubuntu.com/HardyReleaseSchedule)

---

### Post by ago on 2008-02-01
Alpha4 is out, you can now play with Wubi 8.04!
Feedback welcome.

---

### Post by slayer666 on 2008-02-02
I installed alpha4, but it wont boot.
Look at the attached picture to see the error message.

---

### Post by ago on 2008-02-02
press esc at the countdown then "e" to edit the menu entry and the kernel line

make it so that it reads

root=/dev/sda1

where a=disk number, 1=partition number pointing at the ubuntu installation.
Then press enter to confirm, and "b" to boot using the modified entry.

---

### Post by flamelab on 2008-02-02
I guess Hardy Alpha 4 has a serious bug ...

Check the image from my mobile phone

[ATTACH]58361[/ATTACH]

It also takes too long to load squashfs ...

---

### Post by slayer666 on 2008-02-02
> **ago said:**
> press esc at the countdown then "e" to edit the menu entry and the kernel line

make it so that it reads

root=/dev/sda1

where a=disk number, 1=partition number pointing at the ubuntu installation.
Then press enter to confirm, and "b" to boot using the modified entry.

Ok, it worked, but I have to do this every time I boot ubuntu.
How can I make it stick?

---

### Post by ago on 2008-02-02
You can change kopt in /boot/grub/menu.lst and run update-grub
I am interested in knowing why the specified deviced is not booting though. Can you check what is the UUID of the correct device? And what is the device with UUID=549EE...?


Use: sudo vol_id /dev/sda1

---

### Post by ago on 2008-02-02
> **flamelab said:**
> I guess Hardy Alpha 4 has a serious bug ...

Check the image from my mobile phone

[ATTACH]58361[/ATTACH]

It also takes too long to load squashfs ...
at the countdown try to select safe graphic mode

---

### Post by flamelab on 2008-02-02
Already done ...

Nothing .

Ubuntu tries to show the desktop , but that error shows only the console ...:confused::confused:

---

### Post by slayer666 on 2008-02-02
> **ago said:**
> You can change kopt in /boot/grub/menu.lst and run update-grub
I am interested in knowing why the specified deviced is not booting though. Can you check what is the UUID of the correct device? And what is the device with UUID=549EE...?


Use: sudo vol_id /dev/sda1

Shall I do this in commandline before booting ubuntu or in terminal inside ubuntu?
My ubuntu installation is located on (hd0,1)
Is this the right command "sudo vol_id /dev/sda1" ? or shall I alter it?

---

### Post by ago on 2008-02-02
> **slayer666 said:**
> Shall I do this in commandline before booting ubuntu or in terminal inside ubuntu?
My ubuntu installation is located on (hd0,1)
Is this the right command "sudo vol_id /dev/sda1" ? or shall I alter it?

inside ubuntu

hd0,0 <-> /dev/sda1
hd0,1 <-> /dev/sda2

I'd need to know whether menu.lst ended up pointing to the wrong device and in case which one. So you may want to run vol_id on each of your devices (you can get a full list with cat /proc/partitions).

---

### Post by slayer666 on 2008-02-02
ok, here"s what i got running vol_id:

sda1:
ID_FS_USAGE=filesystem
ID_FS_TYPE=ntfs
ID_FS_VERSION=3.1
ID_FS_UUID=CCAADC8EAADC7704
ID_FS_UUID_ENC=CCAADC8EAADC7704
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

sda2:
ID_FS_USAGE=filesystem
ID_FS_TYPE=ntfs
ID_FS_VERSION=3.1
ID_FS_UUID=549EE1859EE15FCA
ID_FS_UUID_ENC=549EE1859EE15FCA
ID_FS_LABEL=samsung500
ID_FS_LABEL_ENC=samsung500
ID_FS_LABEL_SAFE=samsung500

sdb1:
ID_FS_USAGE=filesystem
ID_FS_TYPE=ntfs
ID_FS_VERSION=3.1
ID_FS_UUID=3AEC214BEC2102AD
ID_FS_UUID_ENC=3AEC214BEC2102AD
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

sdb2:
ID_FS_USAGE=filesystem
ID_FS_TYPE=ntfs
ID_FS_VERSION=3.1
ID_FS_UUID=C6366EC6366EB6D9
ID_FS_UUID_ENC=C6366EC6366EB6D9
ID_FS_LABEL=Internet Downloads
ID_FS_LABEL_ENC=Internet\x20Downloads
ID_FS_LABEL_SAFE=Internet_Downloads

sdc1:
ID_FS_USAGE=filesystem
ID_FS_TYPE=ntfs
ID_FS_VERSION=3.1
ID_FS_UUID=4AA0E90DA0E90075
ID_FS_UUID_ENC=4AA0E90DA0E90075
ID_FS_LABEL=Fotografier_Dokument
ID_FS_LABEL_ENC=Fotografier_Dokument
ID_FS_LABEL_SAFE=Fotografier_Dokument

---

### Post by ago on 2008-02-02
Are you sure that Wubi is in sda2? What did you put in menu.lst to boot? Your sda2 has UUID=549EE1859EE15FCA which is what you had in menu.lst to begin with...

---

### Post by ago on 2008-02-02
> **flamelab said:**
> Already done ...

Nothing .

Ubuntu tries to show the desktop , but that error shows only the console ...:confused::confused:
Your issue is that X does not start, that's more likely a generic Ubuntu issue. Can you try to boot from CD?

---

### Post by slayer666 on 2008-02-02
> **ago said:**
> Are you sure that Wubi is in sda2? What did you put in menu.lst to boot? Your sda2 has UUID=549EE1859EE15FCA which is what you had in menu.lst to begin with...

I got it working.
I had to edit /ubuntu/disks/boot/grub/menu.1st

I scrolled to the end of the file and edited every (hd0,0) to (hd0,1) and then saved it and rebooted.

Thank you for the swift help!!
:guitar:

---

### Post by ago on 2008-02-02
> **slayer666 said:**
> I got it working.
I had to edit /ubuntu/disks/boot/grub/menu.1st

I scrolled to the end of the file and edited every (hd0,0) to (hd0,1) and then saved it and rebooted.

Thank you for the swift help!!
:guitar:

You have to edit groot then update-grub

---

### Post by slayer666 on 2008-02-02
> **ago said:**
> You have to edit groot then update-grub

edit what??!?
:confused:

---

### Post by ago on 2008-02-02
in /boot/grub/menu.lst look for a line such as

# groot (hd0,0)/ubuntu/disks

That's where you need to edit, since the menu items are generated from that and you will lose your changes the next time you run update-grub

---

### Post by slayer666 on 2008-02-02
> **ago said:**
> in /boot/grub/menu.lst look for a line such as

# groot (hd0,0)/ubuntu/disks

That's where you need to edit, since the menu items are generated from that and you will lose your changes the next time you run update-grub

Done! :)

thanx

---

### Post by Wesley on 2008-02-02
got the busybox messages with black background


used the installer from the first post. ubuntu on laptop Pm 2.0ghz, 1GB ddr2, ata 60GB hard drive, 7800GTX 256mb. older wubi version worked fine

pls help thanks

---

### Post by ago on 2008-02-02
what message exactly?

---

### Post by Wesley on 2008-02-03
nothing really, just "type help" for more details, cant remember exactly

---

### Post by Wesley on 2008-02-03
just took photo of busy box

---

### Post by ago on 2008-02-03
There should be logs in /*.log and /tmp/*.log
You can reed them using "more" command
Or get a list of errors with

grep -i err /*log /tmp/*log

---

### Post by Wesley on 2008-02-03
hi

just did grep -i err /*log /tmp/*log

it cames back with 

/casper.log:Failed to mount '/dev/sda12: Input/output error
grep: /emp/*log: no such file or directory

thanks

---

### Post by Wesley on 2008-02-03
ago? :(

---

### Post by ago on 2008-02-03
what partition did you install wubi into? check for messages relating to that.
if you run cat /proc/mounts you can see all partitions mounted.

Did you use an old hardy iso by any chance?

---

### Post by mikedep333 on 2008-02-03
How about some good news.
I ran into a couple of small problems. During the first boot I had to select the acpi workarounds option from the GRUB menu. Also, I installed Wubi to (hd0,4) but the installed GRUB attempted to find it at (hd0,0). Other than that Wubi worked for me.
My system is an HP TX1000z tablet PC.

---

### Post by Sockerdrickan on 2008-02-04
I get busy box and sometimes stops at squash

---

### Post by ago on 2008-02-04
> **mikedep333 said:**
> How about some good news.
Always like those :D

---

### Post by ago on 2008-02-04
> **Tux0r said:**
> I get busy box and sometimes stops at squash

Press esc at the countdown, select verbose mode, then look at the logs in /*log /tmp/*log
with the "grep" (search for word) or "more" commands. You scroll with shift pgup/pgdown, exit with q.

Ideally you can try to mount your windows partition and copy the logs there

mkdir -p /tmpmnt
mount -t ntfs /dev/sda1 /tmpmnt
mkdir -p /tmpmnt/wubilogs
cp *log* /tmp/*log* /tmpmnt/wubilogs


Replace sda1 with the appropriate partition where you have windows (a=disk number, 1=partition number). You should see the logs in C:\wubilogs. Post them here.

---

### Post by Sockerdrickan on 2008-02-04
```
cp *log* /tmp/*log* /tmpmnt/wubilogs
```
how does 3 arguments work?

---

### Post by Wesley on 2008-02-04
> **ago said:**
> what partition did you install wubi into? check for messages relating to that.
if you run cat /proc/mounts you can see all partitions mounted.

Did you use an old hardy iso by any chance?

did cat /proc/mounts, 

rootfs /rootfs rw 00
none /sys sysfs rw, nosuid,nodev,noexec 0 0
none /proc proc rw, nosuid, nodev,noexec 0 0
udev /dev tmpfs rw 00
fusect1 /sys/fuse/connections fusect1 rw 0 0

installed wubi on XP's partition drive C:, using the ISO downloaded when installed the wubi

thanks

---

### Post by ago on 2008-02-04
> **Tux0r said:**
> ```
cp *log* /tmp/*log* /tmpmnt/wubilogs
```
how does 3 arguments work?

copy can take a list of source files and a single target dir: cp src src src target
In any case the meaning of the above is to copy over any log file you see.

---

### Post by ago on 2008-02-04
Wesley see the instructions above to get the logs in windows

---

### Post by Wesley on 2008-02-04
> **ago said:**
> Wesley see the instructions above to get the logs in windows

got error message

see the photo:

i tried sda0 and sda2, they came out with no such file or directory so i guessed sda1 is correct but if i carry on to cp: /tmp /*log*/ tmpmnt/wubilogs, its come up no such file or directory message

thanks

---

### Post by ago on 2008-02-04
Is your windows partition the first partition of the firts harddisk? DO you have any raid in place? Are you sure it is ntfs?

If the ntfs partition is sda1 and there is no raid, try to run "chkdsk /r" from windows first.

---

### Post by Wesley on 2008-02-04
yes, windows partition is primary (1st) of the hard drove, non RAID, just single 60GB 2.5" 7200rpm laptop hard drive

doing the chkdsk /r on next reboot now

thanks

---

### Post by Wesley on 2008-02-04
Hi

posting from KDE4 :) all working now

chkdsk /r went fine, reboot and installed ubuntu 8.04 without any problem, downloaded and installed KDE4, all working now

thank you :)

---

### Post by ago on 2008-02-07
The new daily build ISO + wubi 398+ should now work on partitions other than the first without requiring manual fixes. Please try it out and let me know if it works for you.

---

### Post by slayer666 on 2008-02-07
Is Kubuntu 8.04 available yet?

---

### Post by ago on 2008-02-07
There used to be some issues in 8.04 alpha-4 (it would always start in desktop mode skipping automatic installation and in some case would freeze at the end of the installation), not sure whether they have been patched, you can always try.

---

### Post by ago on 2008-02-07
Kubuntu has not been fixed yet, as for Ubuntu, the patches to fix menu.lst in installations on non-first partition are not in yet. So no rush.

---

### Post by shinji257 on 2008-02-10
> **ago said:**
> in /boot/grub/menu.lst look for a line such as

# groot (hd0,0)/ubuntu/disks

That's where you need to edit, since the menu items are generated from that and you will lose your changes the next time you run update-grub

Just so you know I had to do this too.  It came up file not found and I found out it was trying to load up the first partition of my hard drive.  I changed it to 0,1 instead of just 0,0 and it loaded up fine.  I edited menu.lst and update-grub once I got into Ubuntu.  Great job but just so you know I did not have this issue with 7.04!

System: Dell Inspirion E1705
Hard drive layout:
Partition 1 (approx 30MB) - Dell Diagnostics Partition
Partition 2 (net remainder of drive) - Main Windows XP System Partition

---

### Post by ago on 2008-02-11
> **shinji257 said:**
> Just so you know I had to do this too.  It came up file not found and I found out it was trying to load up the first partition of my hard drive.  I changed it to 0,1 instead of just 0,0 and it loaded up fine.  I edited menu.lst and update-grub once I got into Ubuntu.  Great job but just so you know I did not have this issue with 7.04!

System: Dell Inspirion E1705
Hard drive layout:
Partition 1 (approx 30MB) - Dell Diagnostics Partition
Partition 2 (net remainder of drive) - Main Windows XP System Partition

I have already patched that a few days ago', but the fix hasn't reached the ISO yet (should be in from tomorrow).

---

### Post by shinji257 on 2008-02-11
That's fine.  If my install breaks then I will be sure to download a new iso image then.  In the meantime I have been doing quite well with the copy I have now.  BTW, did you notice that both the hibernate and standby buttons were showing up again?  If you have fixed it already then fine but a way to disable them would be useful.

Thanks.

---

### Post by ago on 2008-02-11
Yes, feel free to add to the bug report:

[https://bugs.launchpad.net/wubi/+bug/187463](https://bugs.launchpad.net/wubi/+bug/187463)

---

### Post by slayer666 on 2008-02-14
The first reboot after wubi installation does not work with my usb keyboard as I need to press esc to get to the grub menu. The usb keyboard doesn't respond after I pressed enter in the vista/ubuntu bootmenu. I had to plug in my ooold ps2 keyboard to be able to finish the installation. Anyone else had this problem? Also the 415 version of wubi gave me a rescources error during the windows installation so I used the 410 version instead.

---

### Post by ago on 2008-02-14
415 is bad, use 417
re keyboard: that probably is a bios/ntldr issue (could also be a grub4dos problem though) , you can set the menu not to be hidden by commenting out hidemenu in menu.lst.

---

### Post by kupaka on 2008-02-14
just to check... which version should we be using?:confused:

---

### Post by slayer666 on 2008-02-15
Is Kubuntu supported yet?
I tried to install it last night with version 420 but it didn't get installed, only booted to livecd mode even though I chose 30gb install size.

Another problem.. I've never been able to boot on the amd64 versions at all.
Everything looks fine untill the first reboot after ubuntu-linux is chosen from the menu,
after that the monitor goes black and I can hear my computer working on something and I can see that my usb soundcard power up.
After that - nothing..

I have:
Asus P5K motherboard
Intel Q6600 Core2Quad CPU 2.4GHz
4gb DDR2 Ram
XFX Nvidia 8800 GTS 320Mb graphics card

---

### Post by slayer666 on 2008-02-15
I got the busybox with 420 and Ubuntu8.04  i386 (latest daily)
It gets stuck like in a loop on the last post for a minute or so before the busybox appears.
I can hear something going on with my harddrives 1 at a time in a loop.

The last 3 wubi installers generates the same error. Installation still is kinda smooth with 410.

---

### Post by ago on 2008-02-15
The new wubi versions requires a patched ISO, but the ISO releases have been blocked by other packages since the 9th of Feb. For a workaround see:

[http://ubuntuforums.org/showpost.php?p=4334951&postcount=7](http://ubuntuforums.org/showpost.php?p=4334951&postcount=7)

---

### Post by slayer666 on 2008-02-15
ok, but why can't I install 64bit versions?

And what about Kubuntu? It loads like a livecd now after I edited menu.1st from iso-scan to find iso as described in [http://ubuntuforums.org/showpost.php?p=4334951&postcount=7](http://ubuntuforums.org/showpost.php?p=4334951&postcount=7)
I really wanna try KDE4, but I have no clue of how to install it on Ubuntu. I managed to install the kubuntu package, but then what ?? ;)

---

### Post by ago on 2008-02-15
That used to be an issue in alpha4, I believe it was fixed, but it might be that the patches did not reach the ISO yet.

Anyway workaround is to run the following once you have booted into the live environment:

ctrl + alt+ f2
sudo /etc/init.d/kdm stop
sudo /etc/init.d/ubiquity start

Other workaround is to install Ubuntu and then the kde desktop package

---

### Post by w3stfa11 on 2008-02-17
Was wondering if a great number of people have actually gotten this to work. All I read in this thread was a bunch of people having problems.

I'd like to give this a try, but I don't want it creating any booting problems for Vista.

---

### Post by slayer666 on 2008-02-17
I've got this working several times, with help from ago.
I've never had any problems booting vista. The problems I had mainly involve the installer and my hardware. I can't promise it will work for you but I think you should try it.
If you don't like it, reboot to vista and uninstall wubi from add/remove programs in the controlpanel.

---

### Post by w3stfa11 on 2008-02-17
slayer666: Thanks for the response.

I did give this a try and I ended up with a terminal screen with busybox loaded and initramfs>. I think I might've gotten the wrong Wubi version (rev420) or wrong Ubuntu iso (Alpha 4) or maybe it didn't work because I installed it on a partition on my second hard drive. I don't want to mess with any boot configs so I think I'll just wait until Alpha 5 comes out in a week or so. I read it'll be integrated by then with all the needed patches and such.

I was pleasantly surprised at the ease of installation and uninstallation. It was very quick and easy.

---

### Post by slayer666 on 2008-02-18
> **w3stfa11 said:**
> slayer666: Thanks for the response.

I did give this a try and I ended up with a terminal screen with busybox loaded and initramfs>. I think I might've gotten the wrong Wubi version (rev420) or wrong Ubuntu iso (Alpha 4) or maybe it didn't work because I installed it on a partition on my second hard drive. I don't want to mess with any boot configs so I think I'll just wait until Alpha 5 comes out in a week or so. I read it'll be integrated by then with all the needed patches and such.

I was pleasantly surprised at the ease of installation and uninstallation. It was very quick and easy.

You got the same error I had.

Just do as it says in this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4334951&postcount=7").
Read it, install with wubi 420 and the latest daily iso, edit /ubuntu/install/boot/grub/menu.lst and then reboot.

---

### Post by Christian Johansson on 2008-02-18
I'm looking forward to a stable 8.04 release. I would like to install Wubi on a computer I have but right now there is nothing good to install I think. If I install 7.04, there is no working upgrade path. 7.10 is unstable and will never be made stable. 8.04 might become an official installer but is currently in alpha stage.

---

### Post by w3stfa11 on 2008-02-18
> **slayer666 said:**
> You got the same error I had.

Just do as it says in this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4334951&postcount=7").
Read it, install with wubi 420 and the latest daily iso, edit /ubuntu/install/boot/grub/menu.lst and then reboot.

Thanks, I got it to work now. I had some trouble figuring out what to change the grub boot command. I couldn't which number was needed for (hd0,0). I forgot that I installed it on a [logical partition]("http://wiki.wolvix.org/Partitioning") (rather than primary) which meant it was (hd0,4) and not hd0, 1 as I was originally doing it. 

Wubi has now finished installing Ubuntu and it's awesome! Since it's Ubuntu alpha 5, I ran into some problems, but that's Ubuntu related and not Wubi. Great job!

---

### Post by ago on 2008-02-19
> **Christian Johansson said:**
> I'm looking forward to a stable 8.04 release. I would like to install Wubi on a computer I have but right now there is nothing good to install I think. If I install 7.04, there is no working upgrade path. 7.10 is unstable and will never be made stable. 8.04 might become an official installer but is currently in alpha stage.

8.04 will stabilize soon. We are already in feature freeze, and all major bugs should have been dealt with. There are a few upstream patches pending though. With today's ISO the "find_iso" hack should no longer be required, but it may stills necessary to modify root in ubuntu/disks/boot/grub/menu.lst after installation.

---

### Post by Termy58 on 2008-02-20
> **ago said:**
> but it may stills necessary to modify root in ubuntu/disks/boot/grub/menu.lst after installation.

Please try to fix that :(

---

### Post by ago on 2008-02-21
I fixed that long ago', but the CD updates have been frozen for weeks.

Anyway latest daily build should contain all the patches!!!

But... at the moment I am experiencing kernel related issues (probably not related to wubi) which result in a complete system freeze on boot. Might very well be linked to my particular hardware.

---

### Post by bobap1950 on 2008-03-05
I installed KVM in Ubuntu 8.04 and I keep getting the error message as follows:

Could not initialize KVM, will disable KVM support
Ubuntu does not support running KVM without hardware acceleration. Sorry.

My CPU supports Virtualization so I am not sure what it means by "harware acceleration.

Any ideas?

Bob

---

### Post by ago on 2008-03-05
> **bobap1950 said:**
> I installed KVM in Ubuntu 8.04 and I keep getting the error message as follows:

Could not initialize KVM, will disable KVM support
Ubuntu does not support running KVM without hardware acceleration. Sorry.

My CPU supports Virtualization so I am not sure what it means by "harware acceleration.

Any ideas?

Bob
Some machines do not enable VT extensions even if the CPU supports it. In same case you can activate via bios in some you can't. Google for your make and mode. My laptop for instance (samsung q45) has a CPU that supports VT but cannot be used... Nothing to do with ubuntu/linux.

---

### Post by bobap1950 on 2008-03-05
Virtualization has been enabled in the BIOS and it is definately a AMD AM2 CPU with Virtualization.  Maybe it is a bug in 8.04?

Thanks for your help.

Bob

---

### Post by ago on 2008-03-06
It might be a bug, but it's unlikely to be related to Wubi, you might want to post that on launchpad after doublechecking the forums.

---

### Post by heinz57g on 2008-03-13
when WUBI starts downloading UBUNTU, it shows 35+ hours (hours. not minutes!) as the
anticipated download time. is there anything wrong with the servers? or just overload?

any particular time a day it might be (considerably, pls) better?

my connection with any other board or download location is fine, roughly 40-50 times faster.

am i doing somthing wrong?

i have now just interrupted it. should i delete the files and folders already downloaded and
set up, or leave them and the download/install will pickup where it left?

greetings         - heinz -

---

### Post by ago on 2008-03-13
Things should be better with 8.04
In any case you can download the appropriate ISO manually (NOTE: 7.04 requires the ALTERNATE 7.04 ISO, while 8.04 requires the DESKTOP ISO) using the download manager of your choice (including bt) and place the ISO in the same folder as wubi.

---

### Post by heinz57g on 2008-03-13
as a total newcomer, i tried the standard version as decribed: downloading WUBI 8.04 first, 
then installing it, and it looks for the right UNBUNTU files itself.

i am a bit afraid using any other method and then mixing something not quite compatible.

is the alternate method you suggest described somewhere step-by-step? for a willing-and-
interested-but-still-stupid-LINUX-idiot?

and where could these extreme low DL speeds come from? am i the only one?

many greetings        - heinz -

---

### Post by ago on 2008-03-13
> **heinz57g said:**
> as a total newcomer, i tried the standard version as decribed: downloading WUBI 8.04 first, 
then installing it, and it looks for the right UNBUNTU files itself.

i am a bit afraid using any other method and then mixing something not quite compatible.

is the alternate method you suggest described somewhere step-by-step? for a willing-and-
interested-but-still-stupid-LINUX-idiot?

and where could these extreme low DL speeds come from? am i the only one?

many greetings        - heinz -

Download this alpha-6 image here (as daily builds may be corrupted at the moment):
[http://cdimage.ubuntu.com/releases/8.04/alpha-6/hardy-desktop-i386.iso](http://cdimage.ubuntu.com/releases/8.04/alpha-6/hardy-desktop-i386.iso)


And the latest wubi 8.04 here: [http://www.wubi-installer.org/devel/minefield](http://www.wubi-installer.org/devel/minefield)

Put both in the same folder and run wubi.

---

### Post by heinz57g on 2008-03-13
that makes more sense, says 45 min to download.

putting both in the same folder make WUBI recognize the ISO file and use it to built the actual file structure and content?

assume you are busy, but cld y keep yr fingers crossed for me?

greetings     - heinz -

and: do i first remove the old files structures and few files that the initial attempt had put there?

---

### Post by ago on 2008-03-13
> **heinz57g said:**
> that makes more sense, says 45 min to download.

putting both in the same folder make WUBI recognize the ISO file and use it to built the actual file structure and content?

assume you are busy, but cld y keep yr fingers crossed for me?

greetings     - heinz -

and: do i first remove the old files structures and few files that the initial attempt had put there?

Yes uninstall the old files without backing up.

---

### Post by heinz57g on 2008-03-13
sorry? uninstall? there is nothing to unstall, i could just remove (erase) them.

and what backup are you talking about? i had the original version just running some <5 minutes, and broke off when the time indicator stayed at 35 hrs.

by that time, it had not even reached 1% of all files, and basically only built the files structure and empty folders.

there is no WUBI entry in the WIN SOFTWARE listing, either.

greetings      - heinz -

PS: OK, found it, there is an UNINSTALL EXE in the the new ubuntu folder, which now erased everything in that folder (but left the actual folder there, empty) and possibly ( ? ) also changed something in WIN (registry ?).

the boot (INI) file with the choice WIN-UNBUNTU had not been touched yet, as the computer booted still straight into WIN.

last question (before that cup of coffee): is there a way to either leave out the login / password sequence in ubuntu? or to overide it later somehow with a script or similar?

i am the only one ever touching this particular machine, so i would prefer an automatic non-stop login, both into WIN (as it is now), and by choice into unbutu too.

---

### Post by ago on 2008-03-13
> **heinz57g said:**
> sorry? uninstall? there is nothing to unstall, i could just remove (erase) them.

There should be an entry in add/remove programs in the control panel. Anyway erasing will do to...
When you uninstall you are offered the option to back up downloaded ISO files, you do not want that since you will provide your own ISO.

> and what backup are you talking about? i had the original version just running some <5 minutes, and broke off when the time indicator stayed at 35 hrs.
It might well be that there were problems with the download server. In fact today was a bit hectic with some libraries breaking down in the daily build (the alpha-6 linnk above is fine), it might be that they had to update the files on the server/stop downloads to correct that

---

### Post by heinz57g on 2008-03-13
got it, well, part of it. see my later add-ons in my last post, crossed your mssg (thought i was faster, beaten). 

there was NO entry i the WIN ADD/REMOVE SOFTWARE section, for sure, but the EXE file in the new ubuntu folder did the trick.

greetings      - heinz -

---

### Post by heinz57g on 2008-03-13
still to scared to install right now, doing a mirror backup, entire disk, right now (using CASPER, just perfect for this).

but once this is done, off we go.

somehow i feel you are sitting on a mine. if WUBI/unbuntu does what it is advertised to do, and as solid as unbuntu is
known for, this will explode: it is just what WIN users have been waiting for.

and once it works on remote media (SD's, USB sticks, similar), without really needing ANY ( ! ) interaction with the host
computer, similar to those PORTABLE progs, and not leaving anything behind, WOW ...

i see people are working on all this, too, still with plenty of hickups, but it really seems to be going forward.

greetings       - heinz -

---

### Post by heinz57g on 2008-03-13
well, i got somehwere - you tell me where.

installation went fine. the ISO image was actually copied over to the ubuntu install folder, do i now still have to keep it there? saving 800k would help.

and: UBUNTU comes up, asks for user [ENTER] and password [ENTER], then goes blank, and starts again, asking for user [ENTER] and password [ENTER], then goes blank, and starts again, asking for user [ENTER] and password [ENTER], then goes blank, and starts again, asking for user [ENTER] and password [ENTER], then goes blank, and starts again, asking ...

i was trying to be descritive, did i make my point?

where do we go from here?

greetings      - heinz -

PS: WIN XP works fine, no obvious effect here (yet).

---

### Post by ago on 2008-03-13
> **heinz57g said:**
> installation went fine. the ISO image was actually copied over to the ubuntu install folder, do i now still have to keep it there? saving 800k would help.
Yes you can delete the ISO and all the /ubuntu/install folder for what matters.

> and: UBUNTU comes up, asks for user [ENTER] and password [ENTER], then goes blank, and starts again, asking for user [ENTER] and password [ENTER], then goes blank, and starts again, asking for user [ENTER] and password [ENTER], then goes blank, and starts again, asking for user [ENTER] and password [ENTER], then goes blank, and starts again, asking ...

Did that happen after a second reboot and lots of progressbars on a screen with a bird?
Do you see any message about username/pwd not being correct? 
Otherwise it looks like the video driver is failing
Assuming the linux-side installation went well press

ctrl+alt+f2
login and run:
sudo dpkg-recofigure xserver-xorg
select vesa driver and leave the other options at default
then reboot

---

### Post by heinz57g on 2008-03-13
>> Did that happen after a second reboot

yes

 >>  and lots of progressbars on a screen with a bird?

only the standard UBUNTU progress bar, then the user/passw request, then the bird (THATS what it is!) on an
otherwise completely empty screen, not even an icon, then blank/black and reboot.

 >> Do you see any message about username/pwd not being correct?

no, and i dont think they are, as i use rather simple ones for testing.

 >> sudo dpkg-recofigure xserver-xorg

results in a lot of explantion and possible error codes, but no real reaction. more like
a HELP page.

question: 

 - are there spaces before/after the two ' - 's above?

 - is it recofigure or reconfigure ? 

if i use 'sudo dpkg-reconfigure xserver-xorg' with no spaces before/after but an 'n' in recoNfigure it get into a few pages about keyboard language adjustments and versions, nothing about a VESA driver or similar.

greetings      - heinz -

PS: if this helps ...

 - UB7.10 from a live CD works just fine

 - UB8.04 made into a live CD from above ISO file starts fine, then says 'loging in user ubuntu', then without a password request, gets to the bird screen,
   then blank and reboot

---

### Post by ago on 2008-03-13
I will need the log files
Press ctrl+alt+f2

sudo cp -rf /var/log /host/wubi-logs || sudo cp -rf /var/log /isodevice/wubi-logs

You should now be able to see wubi-logs inside windows,
pls zip it and attach it here.

---

### Post by heinz57g on 2008-03-14
ago, how about the spelling questions in my post just above?

and: 

 - sudo cp -rf /var/log /host/wubi-logs

worked but no visible reaction

 - sudo cp -rf /var/log /isodevice/wubi-logs

did not work, comes back with an error 'cannot create /isodevice/wubi-logs ... no such file or directory'

trying to ZIP the entire wubi-logs folder gives an error for 5 files named :0.log1 through 4, as windows
cannot read files starting with :

the rest was zipped, and is attched here.

greetings      - heinz -

---

### Post by ago on 2008-03-14
> **heinz57g said:**
> ago, how about the spelling questions in my post just above?

sudo dpkg-reconfigure xserver-xorg

> 

 - sudo cp -rf /var/log /host/wubi-logs

worked but no visible reaction

 - sudo cp -rf /var/log /isodevice/wubi-logs

Depending on what stage the error occurs either /host or /isodevice will be available, but not both. 

Thanks

---

### Post by ago on 2008-03-14
Did you use the alpha-6 ISO or the one downloaded by wubi?
Yesterday the ISO were not good.

---

### Post by heinz57g on 2008-03-14
downloads - only the ones you suggested and provided links for (post #77),
so it must have been the alpha 6.

greetings     - heinz -

PS: a personal question - do you ever sleep?

---

### Post by ago on 2008-03-14
It is possible that an upgrade imported the wrong files. 

I would suggest reinstalling using today's daily ISO

---

### Post by heinz57g on 2008-03-14
reinstalling, no problem.

just to make sure i make no mistakes:

 - use the uninstall.exe in the UBUNTU folder rather than the WIN PROG INST/REM

 - this corrects the WIN boot (BIN) file and empties out the UBUNTU folder

correct so far?

 - no need to download the WUBI file again, that one is OK ? << JUST SAW THERE IS A NEWER ONE 452 LATE YESTERDAY >>

 - download the latest ISO (to be sure: which one? where? link?) << CANNOT TELL FROM NUMBERING WHICH REALLY IS LATEST - HOW ABOUT V6 AS 'hardy-desktop-i386.iso' ?? >>

 - put both in one folder, run WUBI

 - enjoy

have i gotten it? i am getting the feeling ** I **am becoming the addict ...

greetings       - heinz -

---

### Post by plus on 2008-03-16
wubi installer 8.04 alpha-rev453 wont run,why?

---

### Post by heinz57g on 2008-03-27
AGO seems to have vanished, or is on holiday. or he got so frustrated with our requests,
that he needed a time-out.

last option: he is working so hard on a final and really working version that he has no time 
for anything else.

greetings      - heinz -

---

### Post by ago on 2008-03-27
plus please try wubi beta on the website, if it does not work post the logs in %temp%

---

### Post by heinz57g on 2008-03-27
ago, you are back!

there are so many supposedly latest versions of WUBI and UBUNTU &#304;SO floating around, that
i plainly cannot tell anymore which one to try - can you pls point out the really solid ones?

greeti&#305;ngs     - heinz-

---

### Post by ago on 2008-03-27
All the versions from rev 449 onward should be considered stable, in the sense that from now on it is feature freeze and only bugs and translations will be addressed. All major bugs should have been dealt with. You can see the open bugs in:

[https://bugs.launchpad.net/wubi](https://bugs.launchpad.net/wubi)

If none of the bugs regards you, then current version will be no different in your case. If you think you are affected by some of the bugs reported, you can help by attaching as much information as possible to help pin it down.

Last release is rev457 (available as main download on wubi-installer.org). The beta Ubuntu ISO contains Wubi rev449.

---

### Post by plus on 2008-03-31
[http://wubi-installer.org/](http://wubi-installer.org/)
i have downloaded the beta from this website but it would not run or i would get a message :   error launching installer
the temp file-i believe that is what you are referring to(i dont know much about computers so i searched the internet)
[http://knowledge.macrovision.com/selfservice/viewContent.do?externalId=Q108334&sliceId=1](http://knowledge.macrovision.com/selfservice/viewContent.do?externalId=Q108334&sliceId=1)

---

### Post by plus on 2008-03-31
[http://wubi-installer.org/](http://wubi-installer.org/)
i have downloaded the beta from this website but it would not run or i would get a message :   error launching installer
the temp file-i believe that is what you are referring to(i dont know much about computers so i searched the internet)
[http://knowledge.macrovision.com/selfservice/viewContent.do?externalId=Q108334&sliceId=1](http://knowledge.macrovision.com/selfservice/viewContent.do?externalId=Q108334&sliceId=1)
if the picture is not redable please tell me what to do-i followed the instructions about browsing a picture from the computer
before continuing -thanks for your time and effort to help me

---

### Post by ago on 2008-03-31
Type "%temp%" in the bar of windows explorer.
Then open Wubi-8.04-rev*.log in notepad.
Copy everything and post it here.

---

### Post by plus on 2008-04-01
sorry for the double post

here are the contents of wubi-8.04-beta-rev467-notepad

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Owner\LOCALS~1\Temp\nst280.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Owner\&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;\Wubi-8.04-beta-rev467.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
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
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843060; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843072; Volume Serial # -260583365; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1700; Volume name My Book; Max #/chars in vol name 1843076; Volume Serial # 924308016; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive H: has valid filesystem FAT32
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in F: is 116285
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder H:\
GMT=3
Country=SA
Locale=el_GR.UTF-8
TimeZone=Asia/Riyadh
Domain=localdomain
HostName=user-5c29df0e3d
ComputerName=USER-5C29DF0E3D
EnvUsername=Owner
UserDomain=USER-5C29DF0E3D
UserInfoName=Owner
UserProfileFolder=C:\Documents and Settings\Owner
UserProfileName=Owner 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Owner\LOCALS~1\Temp\nss282.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Owner\&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;\Wubi-8.04-beta-rev467.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
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
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843060; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843072; Volume Serial # -260583365; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1700; Volume name My Book; Max #/chars in vol name 1843076; Volume Serial # 924308016; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive H: has valid filesystem FAT32
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in F: is 116285
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder H:\
GMT=3
Country=SA
Locale=el_GR.UTF-8
TimeZone=Asia/Riyadh
Domain=localdomain
HostName=user-5c29df0e3d
ComputerName=USER-5C29DF0E3D
EnvUsername=Owner
UserDomain=USER-5C29DF0E3D
UserInfoName=Owner
UserProfileFolder=C:\Documents and Settings\Owner
UserProfileName=Owner 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Owner\LOCALS~1\Temp\nsp284.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Owner\&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;\Wubi-8.04-beta-rev467.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
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
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843060; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843072; Volume Serial # -260583365; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1700; Volume name My Book; Max #/chars in vol name 1843076; Volume Serial # 924308016; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive H: has valid filesystem FAT32
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in F: is 116285
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder H:\
GMT=3
Country=SA
Locale=el_GR.UTF-8
TimeZone=Asia/Riyadh
Domain=localdomain
HostName=user-5c29df0e3d
ComputerName=USER-5C29DF0E3D
EnvUsername=Owner
UserDomain=USER-5C29DF0E3D
UserInfoName=Owner
UserProfileFolder=C:\Documents and Settings\Owner
UserProfileName=Owner 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Owner\LOCALS~1\Temp\nss287.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Owner\&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;\Wubi-8.04-beta-rev467.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
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
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843060; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843072; Volume Serial # -260583365; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1700; Volume name My Book; Max #/chars in vol name 1843076; Volume Serial # 924308016; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive H: has valid filesystem FAT32
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in F: is 116285
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder H:\
GMT=3
Country=SA
Locale=el_GR.UTF-8
TimeZone=Asia/Riyadh
Domain=localdomain
HostName=user-5c29df0e3d
ComputerName=USER-5C29DF0E3D
EnvUsername=Owner
UserDomain=USER-5C29DF0E3D
UserInfoName=Owner
UserProfileFolder=C:\Documents and Settings\Owner
UserProfileName=Owner 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Owner\LOCALS~1\Temp\nsv289.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Owner\&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;\Wubi-8.04-beta-rev467.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
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
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843060; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843072; Volume Serial # -260583365; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1700; Volume name My Book; Max #/chars in vol name 1843076; Volume Serial # 924308016; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive H: has valid filesystem FAT32
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in F: is 116285
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder H:\
GMT=3
Country=SA
Locale=el_GR.UTF-8
TimeZone=Asia/Riyadh
Domain=localdomain
HostName=user-5c29df0e3d
ComputerName=USER-5C29DF0E3D
EnvUsername=Owner
UserDomain=USER-5C29DF0E3D
UserInfoName=Owner
UserProfileFolder=C:\Documents and Settings\Owner
UserProfileName=Owner 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Owner\LOCALS~1\Temp\nsh28B.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Owner\&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;\Wubi-8.04-beta-rev467.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
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
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843060; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843072; Volume Serial # -260583365; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1700; Volume name My Book; Max #/chars in vol name 1843076; Volume Serial # 924308016; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive H: has valid filesystem FAT32
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in F: is 116285
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder H:\
GMT=3
Country=SA
Locale=el_GR.UTF-8
TimeZone=Asia/Riyadh
Domain=localdomain
HostName=user-5c29df0e3d
ComputerName=USER-5C29DF0E3D
EnvUsername=Owner
UserDomain=USER-5C29DF0E3D
UserInfoName=Owner
UserProfileFolder=C:\Documents and Settings\Owner
UserProfileName=Owner 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Owner\LOCALS~1\Temp\nsh28D.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Owner\&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;\Wubi-8.04-beta-rev467.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
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
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843060; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843072; Volume Serial # -260583365; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1700; Volume name My Book; Max #/chars in vol name 1843076; Volume Serial # 924308016; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive H: has valid filesystem FAT32
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in F: is 116285
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder H:\
GMT=3
Country=SA
Locale=el_GR.UTF-8
TimeZone=Asia/Riyadh
Domain=localdomain
HostName=user-5c29df0e3d
ComputerName=USER-5C29DF0E3D
EnvUsername=Owner
UserDomain=USER-5C29DF0E3D
UserInfoName=Owner
UserProfileFolder=C:\Documents and Settings\Owner
UserProfileName=Owner 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Owner\LOCALS~1\Temp\nsv23E.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Owner\&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;\Wubi-8.04-beta-rev467.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
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
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843060; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843072; Volume Serial # -260583365; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1700; Volume name My Book; Max #/chars in vol name 1843076; Volume Serial # 924308016; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive H: has valid filesystem FAT32
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in F: is 116285
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder H:\
GMT=3
Country=SA
Locale=el_GR.UTF-8
TimeZone=Asia/Riyadh
Domain=localdomain
HostName=user-5c29df0e3d
ComputerName=USER-5C29DF0E3D
EnvUsername=Owner
UserDomain=USER-5C29DF0E3D
UserInfoName=Owner
UserProfileFolder=C:\Documents and Settings\Owner
UserProfileName=Owner 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Owner\LOCALS~1\Temp\nsq241.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Owner\&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;\Wubi-8.04-beta-rev467.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
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
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843060; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843072; Volume Serial # -260583365; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1700; Volume name My Book; Max #/chars in vol name 1843076; Volume Serial # 924308016; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive H: has valid filesystem FAT32
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in F: is 116285
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder H:\
GMT=3
Country=SA
Locale=el_GR.UTF-8
TimeZone=Asia/Riyadh
Domain=localdomain
HostName=user-5c29df0e3d
ComputerName=USER-5C29DF0E3D
EnvUsername=Owner
UserDomain=USER-5C29DF0E3D
UserInfoName=Owner
UserProfileFolder=C:\Documents and Settings\Owner
UserProfileName=Owner 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Owner\LOCALS~1\Temp\nsv238.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Owner\&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;\Wubi-8.04-beta-rev467.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
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
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843060; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843072; Volume Serial # -260583365; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1700; Volume name My Book; Max #/chars in vol name 1843076; Volume Serial # 924308016; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive H: has valid filesystem FAT32
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in F: is 116285
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder H:\
GMT=3
Country=SA
Locale=el_GR.UTF-8
TimeZone=Asia/Riyadh
Domain=localdomain
HostName=user-5c29df0e3d
ComputerName=USER-5C29DF0E3D
EnvUsername=Owner
UserDomain=USER-5C29DF0E3D
UserInfoName=Owner
UserProfileFolder=C:\Documents and Settings\Owner
UserProfileName=Owner 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Owner\LOCALS~1\Temp\nsk23A.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Owner\&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;\Wubi-8.04-beta-rev467.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
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
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843060; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843072; Volume Serial # -260583365; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1700; Volume name My Book; Max #/chars in vol name 1843076; Volume Serial # 924308016; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive H: has valid filesystem FAT32
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in F: is 116285
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder H:\
GMT=3
Country=SA
Locale=el_GR.UTF-8
TimeZone=Asia/Riyadh
Domain=localdomain
HostName=user-5c29df0e3d
ComputerName=USER-5C29DF0E3D
EnvUsername=Owner
UserDomain=USER-5C29DF0E3D
UserInfoName=Owner
UserProfileFolder=C:\Documents and Settings\Owner
UserProfileName=Owner 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Owner\LOCALS~1\Temp\nsd23C.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Owner\&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;\Wubi-8.04-beta-rev467.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
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
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843060; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Drive & Path name 1700; Volume name ; Max #/chars in vol name 1843072; Volume Serial # -260583365; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive F: has valid filesystem NTFS
Drive & Path name 1700; Volume name My Book; Max #/chars in vol name 1843076; Volume Serial # 924308016; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive H: has valid filesystem FAT32
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -50854609; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
FreeSpace in F: is 116285
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder F:\
IsBackupFolder H:\
GMT=3
Country=SA
Locale=el_GR.UTF-8
TimeZone=Asia/Riyadh
Domain=localdomain
HostName=user-5c29df0e3d
ComputerName=USER-5C29DF0E3D
EnvUsername=Owner
UserDomain=USER-5C29DF0E3D
UserInfoName=Owner
UserProfileFolder=C:\Documents and Settings\Owner
UserProfileName=Owner 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.

---

### Post by plus on 2008-04-01
i am afraid the temp file contained many things so since the maximum upload is 5 images i have to post 5 more posts,if i am doing something wrong after reading them please delete them and sorry for the incovenience

---

### Post by plus on 2008-04-01
5 more

---

### Post by plus on 2008-04-01
more screenshots...

---

### Post by plus on 2008-04-01
one more to go

---

### Post by ago on 2008-04-01
Delete C:\ubuntu
Download the new wubi (474)
And try again

---

### Post by plus on 2008-04-01
the last set of them sorry for the many images ,again if it is too much of them  after reading them please delete them and excuse me :(

---

### Post by ago on 2008-04-01
All those images weren't really needed, only the log...

---

### Post by plus on 2008-04-01
guess i misunderstood,sorry  for the trouble, i will try what you suggested.
again, thank you for the help

---

### Post by TimJBart on 2008-04-16
Is there a way of gettin ubuntu installed with wubi to see my other existing NTFS partitions?

Cheers.

---

### Post by ago on 2008-04-16
Other partitions will be accessible via:

/host
/media/*

---

