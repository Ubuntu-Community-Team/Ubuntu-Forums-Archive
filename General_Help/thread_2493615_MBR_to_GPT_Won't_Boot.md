---
title: "MBR to GPT Won't Boot"
date: 2023-12-19
forum: General Help
---

### Post by mikegreen8 on 2023-12-19
Hi.

I'm trying to copy from a SATA Ubuntu EXT4 partition using an MBR partitioning scheme to an ESATA EXT4 partition using a GUID partitioning scheme. The end result is that I cannot boot the target ESATA. 

To try and fix this, I tried the following steps:
1. Delete all partitions on the ESATA, and format to GPT using Gparted.

2. Allocate a 500mb FAT32 EFI partition using Gparted.

3. Allocate a 100gb EXT4 partition using Gparted.

4. Boot an Ubuntu USB ISO and install ubuntu onto the ESATA EXT4 partition.

5. Boot the ESATA and copy the first 2048 blocks to a file:
    sudo dd if=/dev/sda of=GPTESATA bs=512 count=2048

6. Note the UUID of the ESATA EXT4 partition.

7. Booting from a Gparted USB, copy/paste the SATA Ubuntu EXT4 partition to the ESATA EXT4 Partition.

8. Restore 1st 2048 blocks on the ESATA
    sudo dd if=GPTESATA of=/dev/sda 

9. Change the UUID of the ESATA EXT4 partition back to the one created by the ISO build:
    sudo tune2fs -U a015ff09-0e6f-48ba-8899-f57941694d44 /dev/sda2

The ESATA will NOT boot! All I get is a flashing cursor.

So what am I doing wrong?

Is there any way to copy (clone) an Ubuntu partition with MBR scheme to another drive
with a GPT scheme ?

Thanks,
M...

---

### Post by MAFoElffen on 2023-12-19
I usually do that from disks that are not mounted.

I do about at least 5 installs a day, when it is a slow day, but about half of those are vai debootstrap, rsync or other methods... I have a bit of experience with this, but let's see if I can explain it.

I think your UUID for the vfat EFI filesystem in the fstab may be off...

I rsync from one efi partition to the other on the disk... Then I chroot into the installed system on that disk, remount everything as it should be, and update the UUID of the filesystem of it's EFI partition to the fstab file of that. reinstall grub, then update the intramfs images, so that everything in the RAM disk on boot is current, and everything it pointing to the right things....

---

### Post by oldfred on 2023-12-19
Do not use dd from MBR to gpt for anything.

With gpt you also have GUIDs that must match in primary partition table, backup partition table & each partition.

Best to just create gpt partitioning, create desired gpt partitions, typically ESP is first. And do full install to drive using Something Else to choose / (root) and /home, if you have it.
Restore from backups which at minimum must include /home, list of installed apps, and any server type apps installed in /. 

You cannot have any duplicate UUIDs or GUIDs if keeping both drives plugged in on reboot.

---

### Post by MAFoElffen on 2023-12-20
> **oldfred said:**
> Do not use dd from MBR to gpt for anything.
+1 -- 

This is why I create my partition table, partitions, format, use rsync to sync the data between, then update the fstab with the UUID's of the existing filsystems...

---

### Post by mikegreen8 on 2023-12-20
So it appears that rsync File-Level Cloning is what I want.

 After the ISO USB Build, I will boot with the ISO USB and:

Live (Active) Ubuntu Partition: /media/ubuntu/Ubu_Live       (Source)
ESATA Ubuntu Partition:         /media/ubuntu/Ubu_New       (Target)


My proposed 'Clone' command:
```
rsync -axHAXS  --info=progress2 /media/ubuntu/Ubu_Live/ /media/ubuntu/Ubu_New
```

1. Does this make sense ? I prefer doing the whole partition. I do realize that a clean install is best, but I will be upgrading to 24:04 in April.

2. Should I use "--exclude=PATTERN etc/fstab" to avoid having to edit fstab later?

3. The Target SSD will be on /dev/sdb. Will boot-repair allow me to select 'sdb' ? Does anything have to be done after boot-repair re booting ? 

Notes:
Target SSD will have 500mb Fat32 EFI and 100gb EXT4 partitions.
I will note the Target UUID after the ISO build and  "tune2fs" it back after rsync.
If I don't use the --exclude for etc/fstab, I will manually update fstab. (Or maybe make a copy of fstab and uuid to a usb.)

Thanks for your rapid and informative responses

Happy Holidays,
M.....

---

### Post by oldfred on 2023-12-20
So are you wanting to just have the live installer on the drive, not a full install?
If that is what you want, no need to create flash drive. Just extract ISO into FAT32 partition on drive with esp,boot flags & it will boot from drive.  But that is just a live install, not a full system. And it really cannot be edited.

---

### Post by mikegreen8 on 2023-12-20
Hi oldfred.

I already have the USB ISO ubuntu. I will do the install on the ESATA merely for the purpose of being able to boot it. 

Then comes the rsync to xfer my desktop ubuntu onto the ESATA.

I will keep you posted.

Thanks for all your help and have a happy holiday season.
M...

---

### Post by mikegreen8 on 2023-12-21
Hi.

The rsync command worked like a charm. 71gb transferred to ESATA. 

I fixed etc/fstab to reflect ESATA UUID.

Now I'm trying to work on getting ESATA to boot using boot-repair.

I created an ISO boot-repair usb using Balena-Etcher, and booted it with the ESATA plugged in. Note that it  saaid 'bios-session' when it was scanning the system - doesn't sound right to me. It also said 64bit system which is good.

It tells me that a GPT was detected and to create a bios-boot partition with a bios-grub flag. I do not understand why, but I did.

After booting the ISO boot-repair usb again, it wanted me to execute 3 chroot commands, which I did. They appeared to work, including the last one which was a 'purge' command.

Then it asked if I want to have Grub 2 files removed. I wasn't sure what to do here, but the TAB key didn't work in order for me to say "no". I hit the ENTER key and it said 'grub is still present'. Then it cancelled the entire operation.

What should I do now ?

Thanks,

M...

---

### Post by MAFoElffen on 2023-12-21
Dang...

It does that if it was booted as BIOS Legacy Boot mode, instead of UEFI, and recognized that the Partition table is GPT.

Create the LiveUSB in Rufus as GPT and UEFI boot only...

---

### Post by dragonfly41 on 2023-12-21
If you are at an experimental stage you could try installing rEFInd in your new SSD - alongside Grub - to see if you can boot in using rEFInd which you should be able to select in BIOS at boot up - F2.

[https://installati.one/install-refind-ubuntu-20-04/](https://installati.one/install-refind-ubuntu-20-04/)

I am reorganising three SSD's and I have just done that installation on one SSD until Grub chaos can be sorted out. You can install rEFInd on any EFI drive.  And multiple drives.

[https://installati.one/install-refind-ubuntu-20-04/](https://installati.one/install-refind-ubuntu-20-04/)


It is installed in /boot/efi/EFI/refind/refind_x64.efi and you can hack refind.conf in same location.

---

### Post by mikegreen8 on 2023-12-22
Isn't rufus a windows product - how can I make 'boot-repair' usb boot in uefi ? I flash the iso using balena-etcher. 

If it matters, secure boot is enabled in my bios which does work well in my dual boot win8/ubuntu system.

Thanks,
M...

---

### Post by oldfred on 2023-12-22
The Boot-Repair ISO is based on Lubuntu and you create it as bootable the same way you create any Linux live installer.
But with Boot-Repair it also has its ppa, second option in instructions. The ppa is updated more often so usually better to use ppa with your Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

You should always have an Ubuntu live installer for current version installed, and a Windows repair/recovery flash drive, in addition to good backups.

---

### Post by mikegreen8 on 2023-12-23
> Create the LiveUSB in Rufus as GPT and UEFI boot only.

Isn't Rufus a Windows program ?

 I flashed the  LiveUSB using Balena-Etcher booted from my UEFI mbr desktop. I ran the live install to a GPT ESATA with an efi partition. 

The ESATA then boots. But after the rsync, it won't boot.

 I then try to fix boot problem with iso USB boot-repair, but that doesn't complete as per my #8 post above.

It seems that the boot-repair usb is not working for my scenario. I download the latest boot-repair iso, and flash to usb using balena-etcher on my UEFI **MBR** desktop. Is that my problem? Should I be creating the boot-repair on the GPT ESATA after the live iso usb install?

Thanks,
M....

---

### Post by mikegreen8 on 2023-12-23
refind looks like it may be the ticket, but I don't understand how to get it on the ESP partition on the ESATA.  

I'm booting with my active Desktop, and try to install refind. The ESATA that won't boot is mounted.

The install process says I must install refind on an ESP partion. The ESP partition is on the mounted ESATA drive. If I allow the refind installation to install refind, will it install it on the ESP of the mounted ESATA ?  I'm afraid it may wipe out my active desktop.

It also says: If you want refind to control the boot process, you can do so by runing:

dpkg-reconfigure refind

Again, on what system do I run this on ?

Do I install refind  on the EFI partition right after the ESATA ubuntu live install, but BEFORE the rsync? After rsync I can't boot the ESATA, but if I have refind on the ESATA EFI partition, will that resolve my problem ?

Sorry for all my confusion.
M...

---

### Post by MAFoElffen on 2023-12-23
I'm not one of the persons recommending rEFInd. But...

If I am worried about a boot loader installing to the wrong drive in a very complex system, Then I will remove/disconnect all drives except that target drive, boot from from a LiveUSB, and install the boot-loader to that "only" other drive... Whatever that Boot-loader might be.

Doesn't that sound like a bit more fool proof?

Just saying, some things just make sense when you cut the variables down.

---

### Post by tea for one on 2023-12-24
> **MAFoElffen said:**
> I'm not one of the persons recommending rEFInd. But...
Conversely, I like the additional functions offered by rEFInd.
To name but three:-

(a) You do not have to install it to a disk - USB flash drive image [https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)
(b) There are options to boot the kernel directly.
(c) If your UEFI settings do not allow you to boot an EFI shell, rEFInd will offer an option.

---

### Post by #&amp;thj^% on 2023-12-24
I'm one that also uses a USB install for rEFInd, it has saved my bacon a time or two.

I think MAFoElffen is *right* though advising to install grub the proper way.

With rEFInd on a USB Drive your covered with an extra go to.
That way there is no guess work on where to install rEFInd, it's just there on the USB Drive when needed.
And Leave Grub intact.

---

### Post by oldfred on 2023-12-24
+1 to 1fallen's comments.

I had an old flash drive that was too small for just about anything anymore.
But rEFInd fit. And it also has saved me a couple of times.

---

### Post by dragonfly41 on 2023-12-24
+1 to all comments

On the argument about disabling SSD's and HDD's .. yes .. that is an option. you can also disable power feeds (including an internal HDD).
But the unique selling point of [rEFInd]("https://ubuntuforums.org/ROOT--REFIND--rEFInd_839.html") .. to me .. it is a nice GUI and can be customised.
I also think about how in an emergency an unfamiliar user might pickup the threads of booting into a complex setup. And how to explain "look for my LiveUSB".
It is easier to explain .. &#8220;power up and hit the third orange button from left seen in the window&#8221;.


[https://wiki.archlinux.org/title/REFInd#Manual_installation](https://wiki.archlinux.org/title/REFInd#Manual_installation)


You can install [rEFInd]("https://ubuntuforums.org/ROOT--REFIND--rEFInd_839.html") in your host OS (or Live USB) then you have the option of *copying* from /usr/share/refind ...  manually or gsync into the target ESATA


[https://wiki.archlinux.org/title/REFInd](https://wiki.archlinux.org/title/REFInd)
[https://wiki.archlinux.org/title/REFInd#Manual_installation](https://wiki.archlinux.org/title/REFInd#Manual_installation)


Do read here.
[https://rodsbooks.com/refind/configfile.html](https://rodsbooks.com/refind/configfile.html)
Hiding and displaying EFI boot loaders


Finally there is efibootmgr to install.
Here is a peek at my output ..
$ efibootmgr 
BootCurrent: 0004 
Timeout: 0 seconds 
BootOrder: 0004,0003,0001,0002,0000,0011,0007,0010,0009,000A,000D 
Boot0000* Windows Boot Manager 
Boot0001* ubuntu 
Boot0002  Ubuntu-SATA-HD 
Boot0003* ubuntu 
Boot0004* rEFInd Boot Manager 
Boot0007  Diskette Drive 
Boot0009* USB Storage Device 
Boot000A  CD/DVD/CD-RW Drive 
Boot000B  Onboard NIC 
Boot000D* Onboard NIC 
Boot0010* CT1000MX500SSD1 
Boot0011* UEFI: ASMT ASM1156 
the current priority is Boot0004* rEFInd boot manager

And when installed run efibootmgr --help
to view options ...

Above Boot0009 is a LiveUSB since I have a Startech powered USB port (10) expander hub.


Another rEFInd pro is the provenance - RodBooks.

[P.S.] Some examples of custom themes.

[https://github.com/topics/refind-theme](https://github.com/topics/refind-theme)

---

### Post by mikegreen8 on 2023-12-24
Thanks for all the advice. I will start to attempt to fix my "won't boot' issue shortly.

I do have a question - I don't have the basic understanding of why I can't Boot the ESATA.

First I do the Ubuntu Live USB Install.  ESATA Boots like a champ.

Then I rsync from Root on my Desktop  to  the ESATA ubuntu Partition created by the Live USB Install. NO Boot - just a blinking cursor.

I would assume that rsync would not 'touch' anything outside the Target Partition - so what's going on here ??

My guess is that there is an address pointer (LBA ??) in the Boot Bock that points to a FILE on the ESATA ubuntu Partition, and that FILE is relocated by rsync ???  

Does this make any sense ? And if so, what is the name of that FILE - /boot/grub/ ??

And what exactly does boot-repair do ?? Does it find the address of the elusive FILE on the EXT4 partition and set it properly in the Boot Block ?

Does this mean my problem has Nothing to do with the fact that I'm going from an MBR SATA to a GPT ESATA ?

I thank you all for your patience. I'll work away at the problem and keep you posted.

Happy Holidays,
M.....

---

### Post by MAFoElffen on 2023-12-24
VERY IMPORTANT POINT *** ---> So it is booting fine "before the rsync"... But fails to boot after the rsync.

The bootloader and boot loader type is not the question there (specifically). There seems to be a problem with the "what" is being copied over to the eSATA drive...

I think to debug that, we need to see the exact rsync commands you are using, so we can see which partitions and data you are copying over from the source to the target...

---

### Post by dragonfly41 on 2023-12-24
Have you tried installing efibootmgr to review boot order as in post #19?

---

### Post by mikegreen8 on 2023-12-24
My rsync command copies the entire Source (/) to the Taget (/) and so I now believe that is the problem.

Please read my Post #20.

Thanks,
M...

---

### Post by mikegreen8 on 2023-12-24
I will be installing rEFind shortly.
M...

---

### Post by #&amp;thj^% on 2023-12-24
> **mikegreen8 said:**
> My rsync command copies the entire Source (/) to the Taget (/) and so I now believe that is the problem.
M...
I second that belief.

---

### Post by MAFoElffen on 2023-12-24
The very first (obvious) problem with that is that destroys the working /etc/fstab by copying over the fstab file from another installation... So then tries to use it's filesystem mounts... LOL

That is just the start of the problems with that...

---

### Post by mikegreen8 on 2023-12-24
And here I am again. I'm spinning my wheels.

I tried installing rEFind but it won't work in BIOS mode

In Synaptic, I installed grub-efi & booted to NO avail.

```
sudo [ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```
    BIOS
and to confirm not efi
```
/sys/firmware/efi 
```  says no file or directory

4 Questions:

1. In my ASUS BIOS, Secure Boot is ON AND CSM is Enabled. If I try to DISable CSM, my Desktop won't boot - BIOS takes me back into the Boot options so I can Enable CSM. Is this preventing me from Booting into EFI mode ?

2. I read somewhere that boot-repair will get me from BIOS mode to EFI mode on a GPT system. Is this true ? If it is true, that would help on my ESATA which is GPT.

3. However, my Desktop is MBR. How can I boot into EFI mode as opposed to BIOS mode on my Desktop ?

4. It seems that converting from MBR to GPT is no easy task. Is this true ?

Thanks,
M...

---

### Post by mikegreen8 on 2023-12-24
"*....destroys the working /etc/fstab by copying over the fstab file from another installation*"

BEFORE the Rsync command, I make a copy of the ESATA fstab to usb. 
AFTER the Rsync, I re-instate fstab from the USB to the ESATA. The UUID checks out.

M...

---

### Post by MAFoElffen on 2023-12-24
Okay...

So what happens if you mount the eSATA's filesystem from a LiveUSB? Does the system look okay and mount as it should? Does the EFI look okay in /boot/efi/EFI/ and /sys/firmware/efi/efivars?

If so, then you next need to rebuild the initramfs and vmlinux images while mounted (because you copied over them)... Then reinstall and update grub2, because you copied over those...

Just saying.

---

### Post by oldfred on 2023-12-25
if you use gparted to convert from MBR to gpt, it totally erases drive. Make sure you have good backups & reinstall.
There is a tool to convert, but best for data only drives as every UUID & gpt changes and you have to update system in every place UUID is used.

I do not think you can have Secure boot on and boot in CSM/BIOS/Legacy mode. That would be broken Secure Boot as BIOS mode has none of the signed files. If you have that setting then UEFI needs update.

---

### Post by VMC on 2023-12-25
> **1fallen said:**
> I'm one that also uses a USB install for rEFInd, it has saved my bacon a time or two....

...With rEFInd on a USB Drive your covered with an extra go to.
That way there is no guess work on where to install rEFInd, it's just there on the USB Drive when needed.
And Leave Grub intact.

Good comment fallen. Thanks! Never occurred to me to use it this way. I'm going to try this and see how it goes.

---

### Post by MAFoElffen on 2023-12-25
Well,adventure has been an education and learning experience... Which I think he has learned that the current method has some problems to migration a system.

If the exercise is for backups and migrations, then a few things need to be adjusted. Foremost is the rsync command used to backup or synchronize hois data from the old install to the new install.

All that needs to be synchronized / backed up is the data, applications, and configurations... If you can tweak it to that, then you can restore and/or migrate your system from one to another.

---

### Post by MAFoElffen on 2023-12-25
I think this is a good exercise of learning to backup, restore and migrate...Learning "what" needs to be backed up, and what needs to be restored, to migrate a system to a new "location".

The other factor here, is whether it replaces or resides next to (coexists) beside the old installation...

This one just happens to replace old installation that was on a  drive with an MS-DOS partition table to a newer drive that is GPT. While converting from Legacy to UEFI boot mode...

There are two ways to do that... Copy just what needs to be copied, or copy fully... Either way, there are some things that need to be unique to the new installation for it to be bootable, and to remain unique.

Just copying everything from one to another fully breaks those things, if that is all you do. (As discussed by both oldfred and myself...)

For me... An easier way, which I often do during installs, is to boot the old installation... From it, write a new partition table and create the partitions you want on the new drive...

From that first foundation, if you want any volume manager, start building those pieces.

Mounting everything at /mnt of the system of how it would piece together as your installed system, but with /mnt as your root... Then do things similar to this, to copy over your system to the new system:
```

rsync -aXHAS --one-file-system / /mnt

```
Then I continue to mount the temporary sysfs, then I chroot into it at /mnt. I create the fstab and mounts with the pieces of that system, reinstall grub2, the rebuild the initransfs images.

I've been doing that since between 16.04 to 18.04... Basically, that is (now) how the new Desktop installer works , from a system image inside the installer, and mounting it to a mount tag named "target" since Lunar 23.04.

Note: As Linux goes, there are many ways to do the same thing. This is just one of many...

_Another way_ is to have a backup strategy that is geared to backup just the essentials of what you need for a migration: data and config files, "plus" a list of user installed applications. Where your backup strategy, routinely backs up interim incremental changes to that, so you can restore to "a point in time". Snapshots from volume managers help with this... 

Then your recovery plan is to do a migration... Where you do a new install, reinstall your applications based on that user installed app list, then restore your data and config files. <-- That makes recovering your system very fast, and to any point of time that you have backups for.

With either of those methods, you can be flexible and adapt to change.

---

### Post by mikegreen8 on 2023-12-25
To recap: 

I did a Live USB Ubuntu (22.04) Install onto an ESATA EXT4 Partition. Boots AOK.

When I make this ESATA the Target of an rsync of an ENTIRE ubuntu partition, the ESATA no longer boots - only a flashing cursor.

The problem appears to be that critical files in /boot (and others??) are moved by the rsync process, and thus an address pointer in the MBR is no longer valid. (Note: I re-instate etc/fstab from prior to the rsync.)

I think I have two options here:

a) Try using rsync with '--exclude /boot/' and any other pertinent Boot directories/files).
    FIRST QUESTION: Which dir/files should be on this Exclude list ?? (This assumes they will remain in place on the Target ESATA.)

b) Or rEFind which I believe will scan the ESATA Ubuntu partition for pertinent Boot files. Seems to be the easiest approach.

The problem here is that  rEFind wants an EFI Boot (as opposed to a BIOS Boot). I don't know how to do an EFI BOOT !!

(The ESATA has NO '/boot/efi/EFI/' and NO '/sys/firmware/efi/efivars'. In fact, '/sys' is empty.) 

I have Disabled Fast Boot in my ASUS BIOS. However, I am forced to Enable 'CSM with Booting from UEFI'. The BIOS will not allow me to DISable CSM.

The SECOND QUESTION: How to get rEFind to work ?

Thanks and Happy Holidays,
M....

---

### Post by dragonfly41 on 2023-12-25
as explained earlier and in RodBooks documents you can _manually _copy rEFInd files into ESTA  /boot/efi/EFI.

Then you have to _manually_ add path to rEFInd to your PC boot options.

That is, although you cannot install eFInd in your source SSD you can unpack it and subject it to rsync as your other files.into a folder/boot/efi/EFI/ etc.  Just be sure of permissions.

---

### Post by dragonfly41 on 2023-12-25
Addendum:
See post #19

[COLOR=#000000]> You can install [/COLOR]> [rEFInd]("https://ubuntuforums.org/ROOT--REFIND--rEFInd_839.html")[COLOR=#000000] in your host OS (or Live USB) then you have the option of [/COLOR]*copying from /usr/share/refind ... manually or gsync into the target ESATA*

---

### Post by MAFoElffen on 2023-12-25
For rsync or rdiff-backup, rather more like --include='/data /etc /usr/local /home' --exclude='/boot /ect/fstab'... but do what you want or fell like...

---

### Post by mikegreen8 on 2023-12-25
> **MAFoElffen said:**
> For rsync or rdiff-backup, rather more like --include='/data /etc /usr/local /home' --exclude='/boot /ect/fstab'... but do what you want or fell like...

Two Questions:

1. What BOOT related files should I Exclude in rsync besides /boot and /etc/fstab ? 

2. How can I boot into efi mode as opposed to BIOS mode (Note: CSM with UEFI Boot is enabled in BIOS) ?

Thanks,
M....

---

### Post by MAFoElffen on 2023-12-26
Going from Legacy Boot to UEFI, you also do not need:
```

/usr/bin/grub*
/usr/lib/grub-legacy/*
/usr/sbin/*grub*
/usr/share/bash-completion/completions/grub*
/usr/share/bug/grub-pc/*
/usr/share/doc/grub-pc
/usr/share/man/man8/grub*
/etc/default/grub
/etc/default/grub.d/*
/etc/grub.d/*
/etc/init.d/grub*
/etc/pm/sleep.d/*grub-common
/lib/systemd/system/grub*
/usr/lib/grub/*
/usr/sbin/grub*
/usr/share/apport/package-hooks/*grub2*
/usr/share/bug/grub-common/*
/usr/share/grub/*
/usr/share/man/man*/grub-*
/usr/share/doc/grub-gfxpayload-lists/*
/usr/share/grub-gfxpayload-lists/*
/usr/share/bug/grub-pc-bin/*
/usr/share/lintian/overrides/grub-pc-bin
/etc/kernel/post*.d/zz-update-grub
/usr/share/bug/grub2-common/*
/usr/share/grub/default/grub*
/usr/share/info/grub*

```

Changing the BIOS Boot mode and which disk you point to. I have no idea what specific options are in your specific BIOS Settings.

---

### Post by mikegreen8 on 2023-12-26
Thanks MAFoElffen
 
I will place this Exclude list (and  /boot & etc/fstab) into a text file that rsync will reference. Then do the Live USB ISO install and the rysnc again and see if it boots.


As far as my Asus Bios is concerned, under the 'Boot' tab, relevant  options are:

CSM is enabled, and under that setting, 'Boot from UEFI storage'. Secure Boot is enabled. Fast Boot is Disabled.

It would sure be nice to Boot into efi mode as opposed to BIOS mode. I have no other way to install refind. 

  
Do you have a procedure to boot into efi mode as opposed to BIOS mode ? Using Synaptic, I have installed 'grub-efi-amd64' to no avail. (I don't even have any efi directory on my system.)

Thanks,
M....

---

### Post by MAFoElffen on 2023-12-26
You have not provided any real basic information on your computer or how it is laid out. You have asked some questions over and over again, even thought they were answered in different ways.... It you do now provide details, then it i shard to answer it detail, and we have to generalize that answer to cover a broad area of the what might be's. Doe sthat make sense?

Let's try to dive into those details for you. To do that, for that to happen, we need more information. If you ran the UbuntuForum 'system-info' script in my signature line, and psoted the URL of where it uploaded to a pastebin, that would provide many needed details. If not, then we are going to have to play 20 questions...

Do not do anything until you answer these basic questions...

What is your brand and model of computer? Is it a laptop or desktop? What CPU and GPU? Does it have a recent updated BIOS version for that computer? Many of these questions and more would be answered by that report...

I can not answer your question in any more details until you provide that information, at the minimum...

---

### Post by dragonfly41 on 2023-12-26
+1 on last observation. 

But to close on ideas for "workarounds" your strategy is to *push* files to your fresh ESATA drive.

I would be inclined to get a standalone external OS working and bootable first. Then and only then pull relevant data from your old MBR drive into your new GPT drive. I am doing that right now with the exception that both SSD's are EFI compatible. I have the advantage of an external StarTech dual docking bay (powered) which makes this easier.

---

### Post by MAFoElffen on 2023-12-26
@dragonfly41 -- He has installed and had it working several times, as UEFI, or at least he said he did... 

Then he would copy or rsync from his old installation, which was Legacy boot. After that, it would "then" fail to boot after that process... because he copied everything, from everywhere, all at once... (like the movie title.)

So you're continued prompting to install rEFInd will still fail, as this is not just a boot-loader problem, but copying over the bootable files from "a different type of boot-mode system" over (what was) a working system makes it unbootable... By making it a non-working system for that Boot Mode. (because there is more involved with that than just the boot-loader, such as the initramsfs images...)

Dang... Hard to reword all that more simply than that. But... That should be an easier summarized "overall assessment" to understand what is going on... He is trying to convert his old MS-DOS partitioned Legacy boot installation from an internal drive, to a GPT partitioned external drive and boot it as a UEFI boot mode... That is it in a nutshell.

---

### Post by #&amp;thj^% on 2023-12-26
> **MAFoElffen said:**
> 
Then he would copy or rsync from his old installation, which was Legacy boot. After that, it would "then" fail to boot after that process... because he copied everything, from everywhere, all at once... (like the movie title.)



+1

---

### Post by dragonfly41 on 2023-12-26
> [COLOR=#000000]because he copied everything, from everywhere, all at once

*I see now* .. that should be .. "copy selectively" .. testing at each data tranche.

And of course changing the various incompatible settings in BIOS. [/COLOR]

---

### Post by MAFoElffen on 2023-12-26
LOL... ++1 --- Yes.

---

### Post by mikegreen8 on 2023-12-26
Sorry if I have broken any rules or appear not to be listening. I did not realize what you wanted. I hope I have supplied it all below.
Be advised that the ESATA in question was not mounted at the time of this report. Currently the ESATA boots fine as I have not yet executed the rsync command.

Here is the system info you wanted: [https://paste.ubuntu.com/p/fCwW7QYD2h/](https://paste.ubuntu.com/p/fCwW7QYD2h/)

I will happily provide anything else that you require.

As per my previous post, I will Exclude all the files you listed as well as /boot & /etc/fstab in my rsync command. Hopefully that will solve the boot issue.

However, as a precaution, it would be nice to have refind installed on the ESATA efi partition. Currently that  is not possible for me as I am unable to figure out how to boot efi as opposed to BIOS. Any help with this will be greatly appreciated.

Thanks for your patience. Please also remember that I am not any where close to your level of expertise, so things have to be spelled out for me - sort of like Ubuntu for dummies :).

M...

---

### Post by MAFoElffen on 2023-12-26
You did nothing wrong. Just trying to clarify things and shorten this up with some concise instructions, instead of generalizations.

*** There is a hole in your plan, which you need to be aware of. Or if you are aware of it, then there will be more work involve with what was known previously...

What version of Windows is installed?

You know that (your Windows installation) will no longer boot if you toggle the BIOS over to boot as UEFI boot mode right? To make that bootable, you would have to either convert it, reinstall it, or have to change the Boot mode every time you wanted to use that...

---

### Post by mikegreen8 on 2023-12-27
Windows 8.

I haven't booted into windows for years now so I'm not concerned about losing that ability. I would clone my entire desktop to another ESATA, and if I required to boot into windows, I would boot that ESATA.

Thanks,
M...

---

### Post by oldfred on 2023-12-27
It looks like my old Asus z97 system was very similar. It died last year, so I cannot compare.
But as I remember the UEFI settings were logically backwards. CSM/Legacy/BIOS is really a sub-set of UEFI, but in my Asus system settings I had to go into CSM/BIOS mode and under that were UEFI settings. 
To turn off UEFI Secure boot, you change from Windows to "Other" in settings. Somewhere it said to use "Other" if installing Windows 7 as it does not support UEFI Secure boot.

That system was only UEFI/gpt as I think I built it in 2014 as my first UEFI system.
Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by mikegreen8 on 2023-12-27
WOW that's a super quick response. 

OKay I'll check out your post after breakfast.

And just a note - I'm not concerned about booting my Desktop into efi, it's just the ESATA that I'm concerned about. It will not be a windows/ubuntu dual boot. 

The only 3 partitions on the ESATA are fat 32 efi, ext4 ubuntu, and ntfs data. The desktop can remain untouched.

Thanks,
M...

---

### Post by MAFoElffen on 2023-12-27
Yes, but you were setting that eSATA up as UEFI mode mode and as GPT... So you will have the change that Boot mode from CSM/Legacy to UEFI...

Wasn't it in that mode (UEFI) when you installed Ubuntu to it?

---

### Post by mikegreen8 on 2023-12-27
A Clarification On Why I'm Doing This:

The purpose of building a bootable ESATA ubuntu which 'looks like' my desktop is to wean my wife off of Windows. Recent malware (which came from Microsoft) wiped out the BIOS on one of her laptops - to the point where it took me a month to recover. 

She likes using my ubuntu desktop, so I'm trying to get a look alike of my ubuntu desktop to boot on her 2 laptops. One will be easy, as I will install the ESATA as SSD2, allowing her to boot either Windows on SSD1, or my 'desktop' as SSD2

The other, which is a brand new ASUS, will be the tricky one, as it will be a dual boot Windows/ubuntu on SSD1. The trick will be to install ubuntu (which will look like my desktop) alongside Windows, WITHOUT wiping out the 'Boot'. If I wipe out her new laptop, I may very well be looking for a place to live lol. (Of course a backup will be done first.)

So I'll do the Live ubuntu ISO USB install, and then try to make the ASUS ubuntu look like my desktop. At this time I am unable to do so on the ESATA attached to my desktop. 

Here is a snapshot of my Desktop BIOS 'Boot'  option. Other than toggling Fast boot to Disabled, it has remained untouched. If I disable CSM, it won't boot:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293251&stc=1[/IMG]

---

### Post by dragonfly41 on 2023-12-27
[COLOR=#000000]> The other, which is a brand new ASUS, will be the tricky one, as it will be a dual boot Windows/ubuntu on SSD1. The trick will be to install ubuntu (which will look like my desktop) alongside Windows, WITHOUT wiping out the 'Boot'. If I wipe out her new laptop, I may very well be looking for a place to live lol. (Of course a backup will be done first.)

Have you considered the option of leaving well alone and instead either building a Ubuntu VM on spouse's Windows laptop, or starting with a Ubuntu VM in the cloud (Azure) security considerations apart?
[/COLOR]

---

### Post by oldfred on 2023-12-27
Please only attach screen shots. Note post in line. Not everyone has high speed Internet.

See my screen shot of the same UEFI screen in post  #50 link. That shows setting as UEFI only.

I use an external USB SSD which has worked for UEFI boot directly and with an old BIOS boot on old system's HDD, it could be directly booted, by passing the UEFI version of grub.

---

### Post by mikegreen8 on 2023-12-27
> *Yes, but you were setting that eSATA up as UEFI mode mode and as GPT...  So you will have the change that Boot mode from CSM/Legacy to UEFI...*

From the Picture of my BIOS Boot Settings in  my Post #53 (next time it will be an attachment) CSM is Enabled, but  'Boot From Storage Devices' is 'UEFI First'. Is that different from  changing the Boot Mode from CSM/Legacy to UEFI ?

---

### Post by mikegreen8 on 2023-12-27
> *[COLOR=#000000]...either building a Ubuntu VM on spouse's Windows  laptop, or starting with a Ubuntu VM in the cloud (Azure) security  considerations apart?[/COLOR]*

I have to think about an ubuntu vm on the ASUS laptop. Absolutely NO cloud for me.

M...

---

### Post by oldfred on 2023-12-27
If I remember right the UEFI first setting did not always work.
But that was 10 years ago. :) and "old" in oldfred not getting any younger.

---

### Post by MAFoElffen on 2023-12-27
I'm going to leave this with oldfred, since he had that motherboard and knows it's BIOS settings. You'll find him a wealth of knowledge who documents "everything"... Especially how his system was and the settings he used on it. I trust him explicitly.

We all help each other, though a lot of cooks at the same time tends to confuse things. I'll let him lead this, and assist if he asks, or I see something struggling. I think that would be better. I'll watch from the sidelines.

Now that we know your goal, and what you are trying to do... I do have some ideas on your plan, that would make this all simpler. If that is okay by oldfred to share. You do not need to copy over things like you are trying to do. You actually need a lot less, to give it just "the look and feel" of your system.

---

### Post by mikegreen8 on 2023-12-28
IT WORKED!

After the Live ISO USB install, I did an rsync from my Desktop/ubuntu to the ESATA/ubuntu  using the '--exclude-from=FILE'  as per MAFoElffen post #39 (I added /boot and /etc/fstab to the list).

There is a problem re wifi networks. The ethernet connection works, however, when I click on the Network icon at the top right of the Desktop screen, only the wired connection is displayed. Even though there are 4 wifi networks available, none are displayed.

sudo lspci shows Network controller: Broadcom Inc. and subsidiaries BCM4352 802.11ac Wireless Network Adapter (rev 03)

sudo rfkill list shows nothing is blocked

nmcli dev wifi lists nothing

I don't understand how making a clone selectively does not display wireless networks. Any Ideas ??

Thanks you all so much for your help. If I can make the wifi work I'm all done.

M....

---

### Post by #&amp;thj^% on 2023-12-28
I am really happy to hear this, Really.
Enjoy

---

### Post by #&amp;thj^% on 2023-12-28
> **mikegreen8 said:**
> I
There is a problem re wifi networks. The ethernet connection works, however, when I click on the Network icon at the top right of the Desktop screen, only the wired connection is displayed. Even though there are 4 wifi networks available, none are displayed.

sudo lspci shows Network controller: Broadcom Inc. and subsidiaries BCM4352 802.11ac Wireless Network Adapter (rev 03)

sudo rfkill list shows nothing is blocked

nmcli dev wifi lists nothing

I don't understand how making a clone selectively does not display wireless networks. Any Ideas ??

Thanks you all so much for your help. If I can make the wifi work I'm all done.

M....
Please start a new Thread for that this one is a bit long in the tooth. :)

---

