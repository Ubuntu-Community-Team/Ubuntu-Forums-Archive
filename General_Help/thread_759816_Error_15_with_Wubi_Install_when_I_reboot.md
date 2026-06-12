---
title: "Error 15 with Wubi Install when I reboot"
date: 2008-04-19
forum: General Help
---

### Post by Linux Kelley on 2008-04-19
Hello,

I just installed Ubuntu using Wubi on Drive D:

When I reboot, and select ubuntu, I get the following error:

[B]find --set-root --ignore -floppies /ubuntu/boot/grub/menu.1st

Error 15: File not found[/B]

 I looked and the file is on drive D in the directory indicated.

Any ideas?

Thanks!

Kelley

---

### Post by ago on 2008-04-19
Is this 8.04? If not I would recommend uninstalling and using 8.04

---

### Post by Linux Kelley on 2008-04-19
> **ago said:**
> Is this 8.04? If not I would recommend uninstalling and using 8.04

Yes, this is 8.04

---

### Post by ago on 2008-04-19
is that

find --set-root --ignore -floppies /ubuntu/**install/**boot/grub/menu.1st?

---

### Post by Linux Kelley on 2008-04-19
> **ago said:**
> is that

find --set-root --ignore -floppies /ubuntu/**install/**boot/grub/menu.1st?

**Yes it is!**

Wupps, I left the install out of my original message!

Sorry.

---

### Post by ago on 2008-04-20
It might be that grub cannot see your disk at boot to begin with
Is your drive/partition any special?

Press insert rapidly after selecting ubuntu

Or press c to enter commands manually

you can type:

cat (hd

then [TAB] (don't press <enter>), this will show all recognized hard disks. Then,

cat (hd0,

then [TAB], this will show all the partitions in (hd0)

keep expanding using [TAB], until you get to /ubuntu/install/boot/grub/menu.lst

---

### Post by Linux Kelley on 2008-04-20
> **ago said:**
> It might be that grub cannot see your disk at boot to begin with
Is your drive/partition any special?

Press insert rapidly after selecting ubuntu

Or press c to enter commands manually

you can type:

cat (hd

then [TAB] (don't press <enter>), this will show all recognized hard disks. Then,

cat (hd0,

then [TAB], this will show all the partitions in (hd0)

keep expanding using [TAB], until you get to /ubuntu/install/boot/grub/menu.lst

Nothing special about my drive D. Just a standard NTFS local disk.

I'll give your for manual commands a try and let you know what happens.

Thanks!

---

### Post by Linux Kelley on 2008-04-20
> **ago said:**
> It might be that grub cannot see your disk at boot to begin with
Is your drive/partition any special?

Press insert rapidly after selecting ubuntu

Or press c to enter commands manually

you can type:

cat (hd

then [TAB] (don't press <enter>), this will show all recognized hard disks. Then,

cat (hd0,

then [TAB], this will show all the partitions in (hd0)

keep expanding using [TAB], until you get to /ubuntu/install/boot/grub/menu.lst

No go. Here's what happened:

**cat (hd**

**then [TAB] (don't press <enter>), this will show all recognized hard disks. Then,**
[COLOR="Red"]Possible disks are: hd0 hd1[/COLOR]

**cat (hd0,**

**then [TAB], this will show all the partitions in (hd0)**
[COLOR="Red"]grub> cat (hd0,0)[/COLOR]
also tried
[COLOR="Red"]grub> cat (hd1,0)[/COLOR]

**keep expanding using [TAB], until you get to /ubuntu/install/boot/grub/menu.lst**
[COLOR="Red"]expanding TAB never went any further than showing (hd0,0) or (hd1,0) no matter how many times I pressed tab[/COLOR]

I tried [COLOR="Red"](hd0,0) /ubuntu/install/boot/grub/menu.1st[/COLOR]
and
[COLOR="Red"](hd1,0) /ubuntu/install/boot/grub/menu.1st[/COLOR]
directly, but no go.

---

### Post by ago on 2008-04-20
Basically the first number is the disk number -1, the second number is the partition -1

It could well be that /ubuntu is on a partition greater than the first 

(hd0,2) for instance

---

### Post by Linux Kelley on 2008-04-20
> **ago said:**
> Basically the first number is the disk number -1, the second number is the partition -1

It could well be that /ubuntu is on a partition greater than the first 

(hd0,2) for instance

When I try any of the following and press TAB nothing happens:

(hda0,0) (hda0,1) (hda0,2) (hda0,3) 
(hda1,0) (hda1,1) (hda1,2) (hda1,3)  

If I hit enter for the following I get a [COLOR="Blue"]No such partition[/COLOR] error.

 (hda0,1) (hda0,2) (hda0,3) 
 (hda1,1) (hda1,2) (hda1,3)  

All this is on an XP Pro PC with ubuntu installed on NTFS local Disk Drive D (not an external drive)

Thanks

---

### Post by ago on 2008-04-20
hmm it's hd not hd**a**
do not hit enter, keep hitting tab to get a list of possible options, you have to exhaust all possibilities

---

### Post by Linux Kelley on 2008-04-20
> **ago said:**
> hmm it's hd not hd**a**
do not hit enter, keep hitting tab to get a list of possible options, you have to exhaust all possibilities

Sorry, the A was a typo in my message.
Here's what I meant to write:

[COLOR="Blue"]When I try any of the following and press TAB nothing happens:

(hd0,0) (hd0,1) (hd0,2) (hd0,3)
(hd1,0) (hd1,1) (hd1,2) (hd1,3)[/COLOR]

If I hit enter for the following I get a No such partition error.

(hd0,1) (hd0,2) (hd0,3)
(hd1,1) (hd1,2) (hd1,3)

[COLOR="Blue"]All this is on an XP Pro PC with ubuntu installed on NTFS local Disk Drive D (not an external drive)[/COLOR]

Thanks

---

### Post by ago on 2008-04-20
and that is with "**cat** (hdX,Y)[TAB]"?

---

### Post by Linux Kelley on 2008-04-20
> **ago said:**
> and that is with "**cat** (hdX,Y)[TAB]"?

Yes it is.

Plus I have tried deleting ubuntu and reloading it, which didn't work.

I also totally deleted it, including the backup and reloaded it, which didn't work.

Should I try down loading ubuntu-8.04-rc-desktop-i386.iso from one of the mirrors and put it in the ubuntu-backup folder and after checking the md5sum install with that?

Thanks

---

### Post by ago on 2008-04-20
no need that will make no difference to grub4dos, I will ask grub4dos devs.

---

### Post by Linux Kelley on 2008-04-20
> **ago said:**
> no need that will make no difference to grub4dos.

So are the problems because I am using drive D instead of C?

Drive D is internal and not an external drive.

Thanks.

---

### Post by Linux Kelley on 2008-04-20
> **ago said:**
> no need that will make no difference to grub4dos, I will ask grub4dos devs.

Thanks!

---

### Post by bean123 on 2008-04-22
you can type

cat (hd0,

then [tab], this will show you the available partitions for hd0. then for a partition such as 0, type

cat (hd0,0)/

and [tab] (remember to add / ), this will show you the files in root directory of (hd0,0).

---

### Post by Linux Kelley on 2008-04-22
> **bean123 said:**
> you can type

cat (hd0,

then [tab], this will show you the available partitions for hd0. then for a partition such as 0, type

cat (hd0,0)/

and [tab] (remember to add / ), this will show you the files in root directory of (hd0,0).

With your suggestion I've been able to make some progress.
I now know that cat is only seeing my C drive and my USB drive. 
It doesn't see my D drive.

---

### Post by bean123 on 2008-04-23
> **Linux Kelley said:**
> With your suggestion I've been able to make some progress.
I now know that cat is only seeing my C drive and my USB drive. 
It doesn't see my D drive.

where is your D drive, is it in the same hard disk as C ?

---

### Post by Linux Kelley on 2008-04-23
> **bean123 said:**
> where is your D drive, is it in the same hard disk as C ?

It is a separate internal NTFS drive.

---

### Post by twigusa on 2008-04-24
Hi,

I'm also getting this issue with Ubuntu 8.04 final version (i386). I have one internal IDE, one internal SATA and one External USB.

I've installed to the SATA disk using wubi which initially had problems until I turned off plug and play OS in my bios.

I'll report any successes here.

Twig.

---

### Post by twigusa on 2008-04-24
Hi,

I managed to get ubuntu to boot by switching my external usb drive off and amending grub to point to hd0 instead of hd1. 

Not sure what the issue is here but I do know it will not boot with the usb drive switched on at boot.

Twig.

---

### Post by Linux Kelley on 2008-04-24
> **twigusa said:**
> Hi,

I managed to get ubuntu to boot by switching my external usb drive off and amending grub to point to hd0 instead of hd1. 

Not sure what the issue is here but I do know it will not boot with the usb drive switched on at boot.

Twig.

I turned off my USB drive and when that is done it only shows hd0, Drive C.
Grub doesn't see my drive D at all.

Both of my internal drives are EIDE drives. No Sata.

---

### Post by projectshave on 2008-04-24
I had the same problem and fixed it just now. I ran chkdsk in Windows on the drive with Ubuntu. When I rebooted, I then got Error 21. (Actually, when I rebooted again I got Error 15, so maybe chkdsk doesn't help)

It looks like grub (the program that loads Ubuntu) couldn't find Ubuntu because it's looking at the wrong disk. So I went to the grub menu and edited the first line. I replaced hd3 with hd2 and it worked for me. You may have to try different numbers there to get yours to work.

My machine has 3 drives, 1 SATA (main, partitioned into C & D) and 2 IDE (F & G). I installed Ubuntu on my G: drive, which is the 2nd IDE drive. Perhaps grub was confused because it looks like 4 drives in Windows, but it's really 3 drives. 

Hope that helps. Now I've got to figure out how to get multiple monitors to work. :)

---

### Post by Linux Kelley on 2008-04-24
> **projectshave said:**
> 
It looks like grub (the program that loads Ubuntu) couldn't find Ubuntu because it's looking at the wrong disk. So I went to the grub menu and edited the first line. I replaced hd3 with hd2 and it worked for me. You may have to try different numbers there to get yours to work.

My machine has 3 drives, 1 SATA (main, partitioned into C & D) and 2 IDE (F & G). I installed Ubuntu on my G: drive, which is the 2nd IDE drive. Perhaps grub was confused because it looks like 4 drives in Windows, but it's really 3 drives. 

Hope that helps. Now I've got to figure out how to get multiple monitors to work. :)

I'm not sure why this would work when grub cannot see drive D at all, and I have a simple drive setup. 3 drives, one partition each. Nothing fancy.

So how does one edit the 1st line in grub?

---

### Post by Linux Kelley on 2008-04-24
Never mind. I'm tossing in the towel.

I got it to boot up when I installed it on drive C instead of D.

However, it does the exact same thing the live CD's do. It comes up with an unreadable scrambled mess on my Monitor. With 8.04 this makes three versions where this happens.
See [http://ubuntuforums.org/showthread.php?t=576449](http://ubuntuforums.org/showthread.php?t=576449)

So I guess I'm stuck with XP even though I want to switch to Ubuntu.

Thank you all for the help you were willing to give me.

Kelley

---

### Post by tinybit on 2008-04-25
> **Linux Kelley said:**
> I'm not sure why this would work when grub cannot see drive D at all.


Obviously your BIOS cannot see your drive D. Nor can GRUB. This shows a bug with your BIOS, not with GRUB.

---

### Post by blug on 2008-04-25
> **ago said:**
> It might be that grub cannot see your disk at boot to begin with
Is your drive/partition any special?

Press insert rapidly after selecting ubuntu

Or press c to enter commands manually

you can type:

cat (hd

then [TAB] (don't press <enter>), this will show all recognized hard disks. Then,

cat (hd0,

then [TAB], this will show all the partitions in (hd0)

keep expanding using [TAB], until you get to /ubuntu/install/boot/grub/menu.lst


Thx guys

I had a symilar problem with Grub pointing to hd0 in stead of hd1. This solved my problems.

Blug

---

### Post by saman_pfdo on 2008-04-25
repartion your disk

---

### Post by Linux Kelley on 2008-04-25
> **tinybit said:**
> Obviously your BIOS cannot see your drive D. Nor can GRUB. This shows a bug with your BIOS, not with GRUB.

Then why does windows see drive D?

---

### Post by Linux Kelley on 2008-04-25
> **blug said:**
> Thx guys

I had a symilar problem with Grub pointing to hd0 in stead of hd1. This solved my problems.

Blug

In my case this would just move it to drive C.
I got it to work on drive C except I get scrambled video just like I get with the live CD.
See [http://ubuntuforums.org/showthread.php?t=576449](http://ubuntuforums.org/showthread.php?t=576449)

---

### Post by tinybit on 2008-04-25
> **Linux Kelley said:**
> Then why does windows see drive D?

Cause Windows won't use BIOS. Windows has its own harddisk driver for drive D, actually for any drive. So Windows needn't call BIOS to access data on the drive.

@Ago,

Crucial boot files such as wubildr, wubildr.mbr, menu.lst, vmlinuz , initrd, etc. should all be placed on a primary partition(usually C:) which also contain NTLDR or BOOTMGR.

---

### Post by ago on 2008-04-25
> **tinybit said:**
> Crucial boot files such as wubildr, wubildr.mbr, menu.lst, vmlinuz , initrd, etc. should all be placed on a primary partition(usually C:) which also contain NTLDR or BOOTMGR.

hmm it should put them in any reasonable place:

    strcpy $str $WINDIR 3
    ${If} ${FileExists} "$9ntldr"
    ${OrIf} ${FileExists} "$9boot.ini"
    ${OrIf} ${FileExists} "$9config.sys"
    ${OrIf} "$9" == "c:\"
    ${OrIf} "$9" == $str
    ${OrIf} "$9" == "$InstallationDrive\"
    ${OrIf} "$9" == "$OldInstallationDrive\"
        strcpy $drive "$9" 2 ; 1st two letters.
        call editBootDrive
    ${EndIf}

---

### Post by tinybit on 2008-04-25
In fact I know little about Windows. If I recall correctly the safe place for boot files should be in the "system boot" drive. It is usually C: but not always. It is, for sure then, a primary partition, and with NTLDR/BOOTMGR in it.

---

### Post by flizebogen on 2008-04-26
I got the same message after using wubi for the first time with ubuntu 8.04.

This is my disc layout:

HDD 1 (Partition C | Partition F)
HDD 2 (Partition E | Partition G)
HDD 3 (Partition D | Partition H)

I selected drive f and ubuntu was installed fine. But the menu.lst was completely wrong. Instead of (hd0,1) the entries were (hd2,1)

Also the Entry for Windows XP was messed up (hd2,0) instead of (hd0,0).

I corrected this on windows and now ubuntu boots fine.

I found the files "wubildr." and "wubildr.mbr" in both drives F:\ and C:\

I used wubi.exe Rev 501.

By the way: The installer asks for admin privilegues, why can i execute "Uninstall-Ubuntu.exe" as normal user?

---

### Post by ago on 2008-04-26
Yes there is a known bug about disk ordering ([https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230](https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230)) we will have a workaround soon and temporary app fix

---

### Post by tinybit on 2008-04-26
This situation is far not as simple as just about the disk ordering.

Buggy BIOSes(unfortunately there are many!) might have no access to hard drive 0x81, 0x82,...... They only have the ability to access the first drive, i.e., 0x80.

So 'find --set-root' would not solve the problem totally and utterly.

For maximum compatibility we must place all crucial boot files in C: as explained above. Thus we can avoid so many problems as reported by the users.

---

### Post by ago on 2008-04-26
> **tinybit said:**
> For maximum compatibility we must place all crucial boot files in C: as explained above. Thus we can avoid so many problems as reported by the users.

If you go through the algorithm that places wubildr & co in ALL drivers where:

There is ntldr
OR boot.ini
OR config.sys
OR C:
OR %WINDIR%
OR InstallationDrive
OR OldInstallationDrive

Not sure how I would miss that.

---

### Post by tinybit on 2008-04-26
Oh, sorry. I just cannot understand the scripting language in floor #34.

Thanks, ago.

---

### Post by bean123 on 2008-04-26
The grldr in the attachment contains the extension for find --set-root as discussed in irc, for example:

find --set-root --relative=/boot /boot/grub/menu.lst

suppose (hd0,0) is the right partition, the effect is:

root (hd0,0)/boot

It also avoid calling int 15/ah=88 as suggested by tinybit, please check if it fixes the upper memory problem.

---

### Post by tinybit on 2008-04-26
@bean123:

This new syntax:

```

find   --set-root   --relative=/boot   /boot/grub/menu.lst

```

seems equivalent to the old command pair of:

```

find   --set-root   /boot/grub/menu.lst
root   ()/boot

```

where the device "()" stands for the current root device.

So the new option --relative is not a must.

---

### Post by ago on 2008-04-26
Bean123 the upper memory issue is in fact gate A20, my fault if the error message was confusing. Sorry for the trouble there. You can revert the relevant code. As for the relpath patch, please push the changes to svn.

I didn't know about the root () trick! That can then be used immediately!

All, if you have problems booting and have more than 1 harddisk please do the following:

Edit c:\ubuntu\disks\boot\grub\menu.ls t
Replace "(hdX,Y)" with "()"
Before each line that starts with "root" add a new line: 
"find --set-root /ubuntu/disks/boot/vmlinuz"

Note that the operation might have to be repeated after kernel upgrades. A proper fix will be available soon.

---

### Post by tinybit on 2008-04-26
@bean123

2008-04-22 has not yet been patched with your crontab-like feature. you may patch it and commit to svn.

The --relative and get_memsize issues can be ignored thou.

The changelog may say something like: new command crontab(sorry I forget the name), bugfixes on int vector probing and others.

please remember to change the changelog file.

If you do want the --relative feature for the FIND command, I feel it would be better if you use syntax in this way:

```

find   --set-root=/boot   /boot/grub/menu.lst

```

@ago

the device "()" and the find option of "--set-root" can only be recognized by grub4dos. these are extensions to gnu grub 0.97.

---

### Post by darkenedsoul on 2008-04-27
I have a pair of SATA II 640Gb's in a RAID 1 configuration. The installation went fine for Wubi for 8.04 except on reboot where it got the error 15 can't find /ubuntu/install/boot/grub/menu.lst file. I looked in that directory and it is not there. There is a menu.lst file in winboot directory but that gets me a repeating message on the black screen (starting (something)/getting (something)) when I copied it into the directory path above. It has a bunch of find and config* on a line in it. I'll remove it and wait to see what the response is to this. This shouldn't be such a big deal by now with SATA/RAID configurations....

E8400 CPU, 2Gb Crucial Ballistix Tracer DDR2-800, SATA Optical, XFX 8800GT 512Mb Extreme edition video card. That's pretty much all in the system. An external USB for backups which is disconnected (will be after current imaging is done). Abit IP35 Pro w/latest official BIOS release. Windows XP Pro SP2 installed and works fine.

Suggestions?

Thanks in advance,

Mike

---

### Post by ago on 2008-04-27
software raid is not supported at the moment (note that some "hardware" raid are actually software raids).

---

### Post by r0tor on 2008-04-27
I spent the better part of yesterday uninstalling 7.10 and reinstalling 8.04 and got it all setup and running perfectly.  Today I accidently hit the hibernate button and the computer froze trying to shutdown.  I rebooted and got the error 15...

I defragged my harddrive and ran chkdsk /r... still have the problem

... i just booted in windows and checked the ubuntu\install\boot\grub folder and its empty!  

What can I do? ...I don't feel like spending another 4+ hours wiping out ubuntu and doing a clean reinstall along with all the other programs i was using.

---

### Post by ago on 2008-04-27
Ntfs corrupted files and directories are sometimes renamed as "found.000" but the files are hidden. Make sure you can see hidden files in the folder options, and look if you see such files in C:\ubuntu. If so there are recovery tools to restore them.

---

### Post by r0tor on 2008-04-27
I have the hidden files visible but don't see any files in the grub folder... nor do i see any .000 type files in c:/ubuntu

---

### Post by ago on 2008-04-27
See if you can access c:\ubuntu\disks\root.disk from within the LiveCD 
[https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7)

---

### Post by darkenedsoul on 2008-04-27
> **ago said:**
> software raid is not supported at the moment (note that some "hardware" raid are actually software raids).

So when is it going to be supported? I find it hard to believe that it hasn't been incorporated yet into this OS. It means I am just going to install VMware and run Fedora Core 7 then since they are lacking this support. I'll find out if Fedora runs under VMware probably tomorrow night. I liked what I saw previously when I had this running on a regular IDE HDD. I've since updated my systems to be running P35 mobos and C2D CPU's running RAID 0 (other desktop) and RAID 1. It should have been built into it by now.....but that's just my opinion. I wasn't lucky with 7.xx so I stopped messing with it. Then I saw they had 8.04 out and I thought it said SATA support so I figured I'd try it again. Oh well, so much for wasting half my day today on trying to get this running.

---

### Post by ago on 2008-04-27
You will have to keep an eye on fakeraid and dmraid announcements.

You can use them [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) but they are not loaded by default at the moment (hence not in Wubi). Probably it was decided that the drivers were not mature enough for an LTS. Please note that this does not depend on Wubi itself.

---

### Post by r0tor on 2008-04-27
> **ago said:**
> See if you can access c:\ubuntu\disks\root.disk from within the LiveCD 
[https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7)


tried...

ubuntu@ubuntu:~$ sudo mkdir /win
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /win
ubuntu@ubuntu:~$ sudo mkdir /vdisk
ubuntu@ubuntu:~$ sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
/win/ubuntu/disks/root.disk: No such file or directory

---

### Post by r0tor on 2008-04-27
I just noticed on my c:\ there is a "found.000" folder with my root disk in and grub files.... ect ect..

what do i do with them?

---

### Post by ago on 2008-04-28
There are recovery tools to handle them, but I do not have any suggestion in this regard.

---

### Post by darkenedsoul on 2008-04-28
> **ago said:**
> You will have to keep an eye on fakeraid and dmraid announcements.

You can use them [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) but they are not loaded by default at the moment (hence not in Wubi). Probably it was decided that the drivers were not mature enough for an LTS. Please note that this does not depend on Wubi itself.

Ok, What about this as an option? I have a 300Gb IDE HDD that I am going to be putting in as a data disk soon (should have done it this weekend when I had the case open....). Would this allow Wubi to install and set up ok within the boot loader for windows? I can work with that instead of putting it on the main RAID 1 configuration.

Mike

---

### Post by ago on 2008-04-28
Should be fine! Most disks not on raid and not encrypted will work. Note that with multiple disks you might have to edit menu.lst after installation (see error 21 in wubiguide), but other than that it should work

---

### Post by darkenedsoul on 2008-04-28
Well perhaps I'll shutdown the system, install the IDE HDD and bring it back up and see if all goes well, format it then deinstall Ubuntu and reinstall it to the new drive. What happened with all the other desktop options in Wubi too? There used to be at least 5-6 options, now it seems kind of pared down.

---

### Post by ago on 2008-04-28
If a physical CD is used only 1 option is shown.

---

### Post by darkenedsoul on 2008-04-30
Well I put the EIDE drive in which came up as drive D:. I deinstalled then reinstalled to the D: drive and on boot it bitched about needing to run chkdsk /r on the drive. I had done that already on my C: drive last night which took quite awhile for some reason so I wasn't going to waste time on it and figured it was complaining about drive D:. So I ran it this morning which took around an hour to complete and then tried booting it again and it bitched again. Guess what,  until this works better I am not wasting my time with it. I'll install VMware and run Fedora Core 7 instead which I know works just fine in VMware. I'll get Core 9 when it's out in a couple of weeks and update to that. I can't believe Ubuntu is this much of a pain with newer hardware....

---

### Post by dartdog on 2008-05-02
Well. HAte to chime in here but it looks like someone is paying attention. I aheve a fairly vanilla dell with 2 internal Hard disks (NTFS) and a bunch of external logical disks.

I went through the newest Hardy ISO install and chose the install without making changes to windows option on my newly formatted drive "F" Chosen from the menu choice. So from my other attempts over several days, to reslove this via the main message board I got directed here so I guess I've got a Wubi prob. 

I see the installation on "F" but grub does not. I get Error 15 then the grub menu. I've tried "Find" and get nothing. It seems that someone here has an idea, but I can't follow.

I searched my "c" drive for some file to modify, but don't see an obvious canidate. The "E" drive has several Menu1st file but no disk adresses in any, and I'd figure if it was getting to there The "F' Dive, that it should find the rest of the system on "F".

---

