---
title: "Re: GParted suddenly not working :-("
date: 2017-12-02
forum: General Help
---

### Post by jakemaverick911 on 2017-12-02
Been having a lot of problems with this new system I'm building for over a week now....but I will try to be brief

New system build...dual boot Windows 7 and Xubuntu. Been trying to transfer all my settings and data from old machine....which I managed, after a fashion. Everything running fine from 500GB HD. This is where it all started to go so wrong....:-(  Physically moved my SSD from old machine, wiped it and been trying to transfer everything from the 500GB HD to the SSD.

Side note problem- it's an HP 8100 desktop system....and in the BIOS for boot order you only have one option to boot from hard drive, the integrated SATA controller on the mummyboard...but no option to specify which drive? I need both drives in this machine ideally....I know it's not an Ubuntu issue but if anybody ever encountered that prob before...?

Anyway cut long story short I have basically wiped the drives and restored backups 20 odd times....:-( REDO was a big disappointment as it turns out it can't migrate the data from a larger drive to a smaller SSD drive...I know everybody saying use Clonezilla, and i've tried that 40 odd times but it keeps failing...so gave up on that!

Partitions got corrupted...anyway what I had to do in the end was use the REDO backup to restore everything back to my500GB HD so back where i was 48 hours ago.... but since then I've been having lots of problems in Xubuntu....had to go through grub rescue, sorted that out....then I seemed to have lost the XFCE environment? no wallpaper, right click context menu wasn't working...fixed that I think, but it came back...fixed again...not rebooted yet!

But now GParted isn't working/ keeps falling over....I've even run it from the liveCD and kept getting same error message.....so i reckon it has got to be something up with my partitions now? i.e. REDO didn't restore it all correctly... I can't copy the text across but it's headed 'Libparted bug' and underneath that it says Assertion (metdata length>0) and a bit more that looks like gibberish to me....I won't type it all out unless it can really help?

thank you for reading anyhoo!

managed to copy the full text "Assertion (metadata_length > 0) at ../../../libparted/labels/dos.c:2313 in function add_logical_part_metadata() failed"

ok, i think i've fixed it.....basically deleted one of my partitions that seemed to be causing the problem and re-created it.....deleted in windows, rebuilt in xubuntu/ gparted....but weird thing is it has to be a primary partition rather than logical (it's just for storage)....i did try setting it back to logical in windows but that just re-created the problem and i had to do it all again ( anybody know if having a logical partition set as primary is going to cause a problem or why/ how it would do that?

actually, i should probably add that this problem partition was originally shaved of my Windows 7 partition in order to get the necessary partitions down to a size that wd fit on my ssd.....plan now is to try and simply copy them all across to my ssd, and hopefully fix it all that way......job for tomorrow now i think, unless somebody can suggest a better way of doing it? ;-)

---

### Post by oldfred on 2017-12-04
If a new system, are you installing Windows 7 in the 35 year old BIOS/MBR configuration. That is default with DVD, but you can copy to flash drive & move/rename a couple of files to make UEFI bootable. You can still then copy your data into data partition(s) from MBR to gpt but cannot image copy a partition from MBR to gpt.
And newer hardware really should be UEFI and then use gpt partitioning. Microsoft originally wanted vendors to not write any drivers for new hardware for Windows 7, only newer Windows. But too many large customs still had Windows 7. But that may not last.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by jakemaverick911 on 2017-12-04
thanks oldfred....um, TBH I didn't even think to think of that on this one....I've always avoided UEFI as it causes so many problems I found....and I did install from dvds....so brain bit frazzled atm, but if i understanding ok i think there shouldn't be any problem with just copying the partitions via gparted (from the live disk) and then just sort the grub out after....? I'm guessing it will go to that grub rescue> thing...I know what I'm doing from there....but i know i do need to sleep first before attempting that ;-)

---

### Post by oldfred on 2017-12-04
UEFI has been an issue, particularly with early UEFI systems.
Most bugs both by vendors & Linux/Ubuntu are resolved.
But HP requires more work arounds than many other vendors. They outright do not follow UEFI standards. But we still have work arounds for HP and similar systems.

Before I had UEFI, I did start converting to gpt partitioning. System was BIOS only.
 You only need MBR on a drive that is for Windows booting in BIOS mode.

So if SSD is Windows and you want BIOS, it must be MBR. But then HDD can be gpt.
I now make all new drives gpt and include both the ESP (FAT32) and bios_grub (unformatted) for BIOS boot. Then easy to later convert from BIOS to UEFI or vice-versa without having to totally backup & redo drive.

But sleep is always a good idea. Helps avoid errors.

---

### Post by jakemaverick911 on 2017-12-05
thanks oldfred

i know, by this time i certainly should have got my head around the whole UEFI thing...shocking when u realise again how quickly time flies these days! and i had no idea on HP being so bad with that....wish i'd known that before i just replaced two of my systems with HPs! :-(
Think i'm ready to boot into live cd now and see if i can just simply copy partitions across....think that should work. but on the HP problem....I still can't get the BIOS to see both hard drives so i can choose which one to boot from.....do u know a workaround for that? all it says is 'hard drive, intergrated sata controller'....and with drives plugged in it only boots from the 500gb :-(

well, that all went to plan! and so surprisingly quick as well....took less than ten minutes! other backup proggies was taking over half an hour...and that way did it qyuickly and simply! must remember that trick for next time....! so wish i had done that first now....but i am now running from the SSD! all i needed to do was sort the grub out after....

couple of things though...Xubuntu did take a very long time to load, longer than the old hd...but i'm guessing that was because it was it's first run andit was 'doing something' expecting to be lot quicker when i reboot.....i also have two entries now for windows 7 on grub, because of that 'system reserved' thing and the actual partition...don't think it matters which one i actually delete from the boot menu? what's the easiest way to edit that out....?

and it wdn't let me copy the swap partition, had to manually re-create that....it's empty anyway...any reason to keep that....or can i delete it and add the space to my xubuntu partition? i dnt see that it does anything after the initial install has been done.....so why does xubuntu keep it?

---

### Post by oldfred on 2017-12-05
Ubuntu from 17.04 uses a swap file. But will use a swap partition if found.

If you redo a swap, you need to double check that UUIDs in fstab are correct. System may then have issues booting and take a long time to time out on missing UUID.

If you ran Boot-Repair it copies bootmgr & BCD files from Windows typical 100MB boot partition into the main partition. Windows uses boot flag, but grub looks for those two files to know what partition is bootable. Boot-Repair copies files as backup as many users do not know about boot partition as it is not normally shown and they delete it. Then they have no boot files. Same users typically do not have backups or a Windows recovery disk, so totally broken Windows.
If you have good backups and repair/recovery disks you only need files in one partition. But probably better to copy one boot stanza into 40_custom and turn off os-prober, so only entry in 40_custom is available.

---

### Post by jakemaverick911 on 2017-12-05
seems i spoke to soon :-( can't boot into windows 7.....so what is the easiest way to copy my MBR across?

---

### Post by oldfred on 2017-12-05
You typically cannot or do not copy MBR. Partitions are different, configuration is different, so it can cause more issues.
Generally very easy to just reinstall a boot loader with Windows repair/recovery disk or install disk using repair console, fixMBR command. Or if just boot loader Boot-Repair can put in syslinux boot loader which will boot Windows. 

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jakemaverick911 on 2017-12-05
this is really doing my nut now....:-(

sorry old fred didn't see that u had replied before my last post here....but after reading that i did run boot repair, from within xubuntu....and that all looked good, until i rebooted then i found grub had gone completely and all i got was the failed to load windows message, so i figured quickest way was to do what i did before, wipe the ssd and put it all back....only thing i changed was i noticed the 'swap off' option...so i did that and it allowed me to copy and paste the swap file this time...i was hoping that would fix the uuid problem....which i had no idea about and don't really understand TBH? how does one manually modify that? but anyway that just bricked my system again....i was expecting it to go to grub rescue again...when i booted from the ssd, but it didn't....just brought up this PXE thing (something to do with my mummyboard i think?) so i had to go back to the 500gb hd to get back online....

and i have 2 windows 7 disks...trouble is trying to do boot repair from either of them, it dnt work....saying neither is the disk i originally installed from, so won't work :-(

i did disable the post to pastebin option on boot repair as i do not like it doing things like that without being able to check exactly what info it is sending before it does it :-( I'm going to go eat before trying anything else with it.....maybe that will get the old brain working again! ;-)

seems u can't use boot repair to re-install grub AND fix mbr at the same time?

---

### Post by oldfred on 2017-12-05
Installing grub and fixing MBR, if BIOS is the same thing.
Or you only have one MBR, and either grub boot loader or Windows boot loader is in MBR.
With newer UEFI system, both are in ESP - efi system partition side by side and you choose from UEFI which to boot.

Really need Summary Report to see your configuration. Otherwise cannot make good suggestions on what to fix.
If you have run report, it also saves copy on your system.

---

### Post by jakemaverick911 on 2017-12-05
thanks old fred...pretty sure it is BIOS, which is why i dnt understand why that happened....my undersatnding was tht grub was working fine....it's just something after that when trying to boot windows was the problem...

all i can do i think atm is try and copy everything back to the ssd again and try replicate to where i was before.....thing is i'm not well at the minute, which might be why i'm making such a pig's ear of it all...and so tired, think i best leave it today and try again tomorrow :-(

thanks for all your help though

this makes no sense whatsoever to me...I did EXACTLY what i did before.....several times now and i just can't make the SSD bootable at all.....what could i have possibly done?

---

### Post by oldfred on 2017-12-06
If you post link from summary report we can at least see if files are in correct places.

---

### Post by jakemaverick911 on 2017-12-06
but i can't make that disk bootable at all now, i swear i did exactly the same thing, it just not working atm....i'll keep playing but no point posting the file from this install as this is all working fine :-(

something changed...i now have ! marks in yellow triangles on my system reserved partition and windows 7 partition......i can post a picture of that from gparted, but i dnt think there is any way to post a pic directly to here?

[https://askubuntu.com/questions/842029/cloning-hard-disk-partition-to-smaller-ssd-on-laptop/842044](https://askubuntu.com/questions/842029/cloning-hard-disk-partition-to-smaller-ssd-on-laptop/842044)

that is what i originally followed, and first time it worked perfectly! just the problem with not being able to boot windows.....but did exactly the same dozen or so times since and just can't get back to that point....that makes no sense to me? nothing changed, at all....:-(

ok this is getting really weird now. I've not done anything with it since I last posted....so whn I booted up today and found all these extra options in my Grub menu, i was tad surprised....I now have multiple entries for both windows and xubuntu and it seems to be referring to both drives..i.e. options to boot from sda or sdb into either....'cept they won't. Whichever option you click they still boot from the 500gb drive. how can grub possibly decide to update itself anyway? it's not just me, this is really quite weird right...?

---

### Post by oldfred on 2017-12-09
If you post summary report we can see what you are seeing.

---

### Post by jakemaverick911 on 2017-12-09
ok, managed to do without re-installing....think this is what you are looking for? LOT bigger than i thought it would be....and second time i just typed this/ tried to paste....system came up with security token error thing before?

yep, too long to cut and paste here....:-(

[https://paste.ubuntu.com/26147902/](https://paste.ubuntu.com/26147902/)

---

### Post by oldfred on 2017-12-09
You have duplicate UUIDs from your cloning.
If you clone a drive, you cannot keep both drives plugged in as duplicate UUIDs are not allowed.
With Ubuntu often easier just to reinstall, not sure with Windows.

```
/dev/sda1        [COLOR=#ff0000]C08E76968E768526 [/COLOR]                      ntfs       System Reserved
/dev/sda2        [COLOR=#0000ff]E0607FF7607FD330[/COLOR]                       ntfs       Windows 7
/dev/sda4        075D70436CED239D                       ntfs       DATA 2
/dev/sda5        4f3630ed-0b71-4e10-bbb8-ab9b5cd4a7a5   swap       
/dev/sda6        [COLOR=#800080]c0cba20c-8a8f-432b-ae1d-c783f62f0e19  [/COLOR] ext4       
/dev/sda7        E9CAA82B09030AF0                       ntfs       DATA
/dev/sdb1        [COLOR=#ff0000]C08E76968E768526[/COLOR]                       ntfs       System Reserved
/dev/sdb2        [COLOR=#0000ff]E0607FF7607FD330[/COLOR]                       ntfs       Windows 7
/dev/sdb3        [COLOR=#800080]c0cba20c-8a8f-432b-ae1d-c783f62f0e19[/COLOR]   ext4       
```

---

### Post by jakemaverick911 on 2017-12-09
ah....figured that might be the prob...how can i change the uuid's? i don't want to re-install from scratch...as i want to keep my system and data how it is, not rebuild everything...it wd also defeat the point of seeting it all up on the 500gb first....idea was to have a backup so when ssd dies without warning, as they have in the past, i can simply switch over....what would be ideal is to keep both copies up to date...like some kind of RAID system, i know that not possible....but in this day and age it really should be ;-)

that can't be the whole problem though as i've had just the kingston plugged in, wnt boot at all? wdn't even get to the grub rescue bit that i know how to deal with...just went str8 to failed windows boot, no grub at all

actually there is an option in gparted to change uuid's...but i just tried that and it failed with no explanation, only tried to do half (which should be enuff?) for the windows/ ntfs drives

thanks dead flowers

seems i cd change all the uuid's 'cept for Windows 7, although 'system reserved' bit did....i have rebooted but sdb options still go back to the sda boot though....i'm half tempted to just boot repair on it, see if that sorts it out?

---

### Post by oldfred on 2017-12-09
Boot-Repair will not change UUIDs.

If you change UUIDs, at least in Ubuntu you have to reinstall grub, and update fstab with new UUIDs. I think there are several other settings also.
I just install another copy of Ubuntu. And have all data in a data partition that I mount with all installs & have backup of, so if drive data is on fails I just copy that back.

Often with Windows better to use an imaging software. Then you can restore image. But that quickly becomes obsolete as you use Windows and update it or add data.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[URL="http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media"]http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media

[/URL]
 Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid 


I have seen where user with duplicate UUIDs, sometimes booted into one drive and sometimes booted into other drive. And then things quickly got messed up on both versions.

---

### Post by jakemaverick911 on 2017-12-09
oldfred
thank you but that all sounds so ridiculously complicated and i understand very little of it :-( i can't even remember what ftsab is right now never mind how to change anything....you only need to know this stuff when u doing jobs like this and TBH i only do it about once a year now.....i'm gonna have to have another sleep and think on this :-(

but surely in this day there must be a simply way to duplicate my OS partitions on one drive and put them on another...? if i had the money i wd buy a 500gb ssd and use less than 20% of it :-( cheaper than the time spent for sure

---

### Post by Ez_Sit on 2017-12-11
> **jakemaverick911 said:**
> oldfred
but surely in this day there must be a simply way to duplicate my OS partitions on one drive and put them on another...? if i had the money i wd buy a 500gb ssd and use less than 20% of it :-( cheaper than the time spent for sure

Like anything else in life, once you know how to do something, it is simple. In order not to learn any of these repair techniques, I keep very good backups of all my data and can restore in under an hour. With good backups, reinstalling an operating system and then restoring your data is trivial. If you can get to your data (booted from another media) and copy your data to a safe location (USB hard drive with enough space), do that and then nuke n' pave. It may seem like the cowards way out, but it always works. Clonezilla has usually worked for me, but I stick to MBR partition layouts on good-ole hard drives with time-tested filesystems like ext3. GPT and UEFI bring nothing to the table for me, and I still have yet to hit any of the filesystem limitations of ext3.

---

### Post by jakemaverick911 on 2017-12-17
Ez_sit  thanks...been tied up a few days and time of year u know...not managed to get back to any of it yet....i keep very good backups to! and that was kind of the point of me trying to do it this way....basically RAID, so if one drive went down i cd immediately switch to the other...but seems just not possible with ssd and a 500gb drive, massively different sizes...i dnt think there is raid function on this mummyboard anyway....and it is a very odd machine, not allowing to choose which HD to boot from....totally agree withya on the partitions....it's not just the data though, custom monitor settings, all your apps, if it was simply copying a directory of data it wd be no problem...and bloody chrimbo! might be a hwile b4 i can get to sort it out proper...but looking like i will have to do that :-( just fresh install and rebuild everything.....just wish i cd figure out a way to make the motherboard bootable from either drive :-( thanks for your input...please leave this thread open for now as i wil come back....just not sure when i'm going to get the time :-(

---

### Post by oldfred on 2017-12-17
If you are using BIOS and do not have duplicate UUID, you can boot from either drive.

I now use UEFI and gpt. And have multiple installs on each drive. But with UEFI they all boot thru the ESP on sda. But I have backup of ESP on an ESP on sdb, so I could boot one of the installs in sdb (with possibly edit as I boot). 
I have backups of /home, but almost all my data in in a /mnt/data partition that I mount in all installs. And I live half time in Fla and bit less in Ill and just copy /mnt/data to flash drive and take back & forth. 
I also export list of installed applications, and then those are all in sync on both systems.

I put ISO on HDD and can install in about 10 min to SSD, with updates. And a small script to do 80% of configuration. Within an hour I have a new install, essentially configured like my old install unless I do want it different to experiment with something.

---

### Post by jakemaverick911 on 2017-12-19
oldfred

it's a problem with this 'new' computer i just bought HP Compaq 8100 Elite....it will only ever boot from the 500gb, it doesn't matter which sata port on the board the cable is plugged into, it just won't see the ssd until after it has booted....it is very weird...only way to make it boot from the ssd is to unplug the 500gb completely, which is what has being doing my nut more than this install :-( if i can fix that, somehow...i can change the UUIDs and i think i can sort the rest out....i want to boot from the ssd, keep the 500gb for storage on this machine...but if the ssd fails i can quickly flick back from the 500gb was the plan, if that makes sense? if u dnt believe me try google the modle number, other people had same problem nobody seems to be able to solve it....it is just so weird/ dnt make any sense to me....but that not an ubuntu related problem

---

### Post by oldfred on 2017-12-19
You cannot have duplicate UUIDs mounted at same time. 
So you can either have second drive connected and usable, but then cannot be a mirror of first drive.


I find just having another install in my second drive (actually several for tests of some sort) separate data partition that is well backed up works for me. And data partition is used for all installs.

---

### Post by jakemaverick911 on 2018-02-24
sorry to disappear for so long.....i really have been having a bad time :-( life in general and numerous probs with my other PCs as well.....but i have found a solution to this one! Acronis True Disk 2018 solved all my problems! it can and does backup up all partitions, linux, windows....everything! interface is a bit clunky but only option i found...it also lets u shrink partitions so they all fit.....so now finally running on the SSD and also managed to get secondary 500gb working as well. so all done, thanks for all your help but i can not recommend Acronis enough!

---

### Post by oldos2er on 2018-02-24
Thanks for posting the solution! Would you please mark the thread "Solved" under Thread Tools at the top of the page?

---

### Post by jakemaverick911 on 2018-03-02
will do, ta ;-)

---

