---
title: "1st time using Ubuntu. Ran 7.04 Live CD. Now can not boot Windows XP :("
date: 2007-04-17
forum: General Help
---

### Post by enthusaroo on 2007-04-17
ELP!

That's all I have to say at this point.

First off, I ran Ubuntu "Fiesty" 7.04 Beta off a Live CD today in order to test Ubuntu before I make the full install. I LOVE Ubuntu. Once this mess is sorted out, I DO want to make it my main operating system for this computer.

I have a Lenovo/IBM Thinkpad R60e that I bought just a few weeks ago. One of the Intel video driver files under Windows XP Home became corrupt. I went through hell trying to reinstall the video drivers with no luck. Even the Thinkpad technical support place in Hong Kong was unable to fix it. But this is a whole 'nother story. Finally, I decided "enough is enough" and decided to download Ubuntu today. I know the final release of 7.04 comes out on the 19th, so I decided just to make a live CD of the beta tonight to test it.

Actually, my plan was to use IBM's Recovery and Rescue program to "restore Windows to it's factory state". I wanted to restore Windows XP Home to it's original "just left the factory" state and then find a way to duel book my computer to have both Ubuntu and Windows XP.

I did not get that far. In fact, I have not gotten anywhere.

I booted the Ubuntu 7.04 Beta live CD. Everything with Ubuntu works like a dream! I love it. Linux is everything I expected and more.

THE PROBLEM is when I try to restart my system, I should expect it to automatically try to boot into Windows XP as usual, right? WRONG.......

IF I have the Ubuntu live CD in the CD/DVD ROM drive then it will boot Ubuntu. However, if I DON'T have the live CD in the CD/DVD ROM drive then it simply will boot into IBM's Rescue and Recovery program. There seems to be no way to get it to boot into Windows XP or find an option to boot into Windows XP.

ACTUALLY, the main problem is I simply want to restore my system and Windows XP back to it's "original factory condition" with all of the original files. However, when I try to do this in the Rescue and Recovery program I get the following error message: "Product Recovery failed to restore your system". I figure it has something to do with the fact that I can't even boot up Windows! This problem began three hours ago after I first booted the Ubuntu live CD. Therefore, I'm assuming that perhaps Ubuntu changed something related to the "boot loader". After searching Google for an hour, I came up with some results. It turns out there should be a file located here: /file system/boot/grub/menu.1st.... However, in this beta of 7.04.... this file seems to not exist.

I'm at a lost. I don't know what to do. This is my first time using Linux/Ubuntu. I simply want to find a way to restore my system back to it's original factory state using Rescue and Recovery and also be able to boot-up Windows XP.

Two other problems related to fixing this issue that I should note.
1) I bought this Thinkpad brand new. However, as it turns out, when I bought this computer it did not come with any Windows XP disk. Therefore, I have no sort of back-up of Windows or way of reinstalling. My only hope is the IBM Rescue and Recovery program, which is suppose to be able to reinstall Windows by itself; but in my case I got the following error:
"Product Recovery failed to restore your system"
2) I am currently on work assignment in China (I'm originally from the U.S), so it's impossible for me to get to an IBM service center to have them assist with me with these errors. My only hope is that I may be able to get some advice on here to try to resolve the issues all by myself.

---

### Post by UbuntuniX on 2007-04-17
...Have you ever thought of simply removing the disc while booting?

If you can't figure that out, you can always change your BIOS settings to boot the hard drive before the disc drive.

---

### Post by notwen on 2007-04-17
> ACTUALLY, the main problem is I simply want to restore my system and Windows XP back to it's "original factory condition" with all of the original files. However, when I try to do this in the Rescue and Recovery program I get the following error message: "Product Recovery failed to restore your system". I figure it has something to do with the fact that I can't even boot up Windows! This problem began three hours ago after I first booted the Ubuntu live CD. Therefore, I'm assuming that perhaps Ubuntu changed something related to the "boot loader". After searching Google for an hour, I came up with some results. It turns out there should be a file located here: /file system/boot/grub/menu.1st.... However, in this beta of 7.04.... this file seems to not exist.


If you booted Ubuntu from the LiveCD, your HDD was not touched by Ubuntu.  Hope you're able to figure this out. =]

---

### Post by enthusaroo on 2007-04-17
> **UbuntuniX said:**
> ...Have you ever thought of simply removing the disc while booting?

If you can't figure that out, you can always change your BIOS settings to boot the hard drive before the disc drive.

I said in my original post:
> 
IF I have the Ubuntu live CD in the CD/DVD ROM drive then it will boot Ubuntu. However, if I DON'T have the live CD in the CD/DVD ROM drive then it simply will boot into IBM's Rescue and Recovery program. There seems to be no way to get it to boot into Windows XP or find an option to boot into Windows XP.


If the disc is removed then it will only boot into the IBM Rescue and Recovery program. It will not try to load Windows XP. I have no option to load Windows XP. Plus, Rescue and Recovery is unable to restore the original files from Windows, which is what I really want to do. 

If all else fails, is there simply any way to just delete ALL of Windows and all data under my Windows installation from within Ubuntu? (I already have back-ups of mp3s, photos, etc..)

---

### Post by teddmeister2 on 2007-04-17
> 
First off, I ran Ubuntu "Fiesty" 7.04 Beta off a Live CD today in order to test Ubuntu before I make the full install. I LOVE Ubuntu. Once this mess is sorted out, I DO want to make it my main operating system for this computer.

Just to verify, could you answer the following:
1) You *didn't* do a full install of feisty, right, you only ran it off of the live cd (the stuff about /boot/grub/menu.lst seems to suggest you installed it)?
2) Did you change any settings in your bios before booting to the cd?
3) Try running gparted from the livecd (don't have the program do anything to your partitions), check the number and types of partitions it lists and post your results here.


I guess we'll go from there.

p.s.  You CAN just repartition your hard drive using gparted through the installer (I'm assuming the feisty installer runs gparted, as I've only used the edgy livecd so far).  If you just want to reformat your NTFS partition, you don't even have to run the installer to use gparted, AFAIK.

---

### Post by notwen on 2007-04-17
If you have all your stuff backed up, then just install Ubuntu using the Install icon on the desktop from the liveCD session.  During the installation you will be prompted to select the HDD/partitions to install Ubuntu to.  Just choose the option to reformat your entire drive and let the installer do the rest.  Hope you're able to get your system up & running.

---

### Post by ajgreeny on 2007-04-17
You are suggesting that the machine boots into the rescue and recovery system even without a CD in the drive and that it then fails to restore the windows setup.  Is that correct?

I don't know the IBM rescue and recovery program, but is it on another CD or on the hard disk?  Generally such things are on a CD, and if that's so, try booting with _that_ CD, not the ubuntu live CD, in the drive and then try the restore system again.

Apologies if the recovery system runs only from the hard drive and not a CD, but nevertheless I thought it worth just mentioning this point; sometimes the obvious is not quite so obvious for a variety of reasons.
Finally, GOOD LUCK!

---

### Post by Neobuntu on 2007-04-17
Why are you making a beta your main system?

Did you change the boot flag (via Gparted on the live CD) to a hidden restore partition?

As stated, just running live CD will not keep Windows from booting. There are great measures to insure that one would have to purposely install AND instruct the installer to take the whole drive before OPTIONALLY erasing Windows. (or even rewriting the MBR which is easy and fast to fix.)

Just in case someone comes across this post and thinks it's easy to harm Windows or that one HAS to replace Windows, it's not and you don't.

I recommend new users start with Kubuntu and Dapper. It's the LTS version, most smoothed and is best able to handle anything off the beaten path.

---

### Post by Neobuntu on 2007-04-17
Never, I repeat never, restore anything (old) to it's factory state. The insecure nature and build up required is horrendous.

The current reality is any Internet using system needs the most current upgrades. With Windows you get security upgrades (that are a joke) but with open software you get real security (comparatively) AND newer programs and features.

Don't fail to understand the difference between using and testing a total system. The current reality is you don't want testing for everyday use and you do want testing to participate and make things better.Therefore, keep them separate.

So if you're starting, go with tried and true release tiers (keep upgraded not dist-upgraded) first.

I wish *ubuntu were less confusing; about this but new users should start with Dapper; still. I think is it very confusing that Edgy has been out a while and is largely stabilized but in reality, it is a sudo-testing version (and NOT LTS they will tell you) and not for all but the lightest usage (and depends on your hardware set).

You can and may chose anything you like. Even geeks shouldn't use betas for everyday use.

Your main system had best be a one that has been out a great while and certainly not one just due next week.

Also, a clean install is still the overall best and time saving method of jumping to new releases(when they are NOT new and they are improved, unless you are doing SEPARATE testing).

---

### Post by Bodomity on 2007-04-17
==================
:restart
:run bios
:turn off Hdd with XP OS
:restart
:run bios
:turn on Hdd with XP, turn off Hdd with Ubuntu
:restart
:run bios
:turn both Hdd on
:restart
==================


Make Sure that both Hdd are master.. If You have 1 Hdd with two partitions, then i guess you must format drive  with GNOME partition Editior, and make all partitions with boot flag..

---

### Post by Sunflower1970 on 2007-04-17
You might want to check over at [www.thinkpads.com](www.thinkpads.com) (link to forum [http://forum.thinkpads.com/](http://forum.thinkpads.com/)) and ask the question...I found this link: [http://forum.thinkpads.com/viewtopic.php?p=159336&sid=3774f844a3287b92edb6ab34b235d569](http://forum.thinkpads.com/viewtopic.php?p=159336&sid=3774f844a3287b92edb6ab34b235d569)  A similar problem to yours. Someone suggested it could be a problem with RAM which won't let you do a clean install of Windows. Also could be another type of hardware problem (motherboard, or even the CD/DVD drive). 

If you do a google search for "Product Recovery failed to restore your system" you get a lot of results. Hopefully one of them will have an answer for you. :)

---

### Post by Neobuntu on 2007-04-17
It may be important to note that computer distributors have a bad habit of stuffing what was a reinstall CD into an odd partition on your hard drive space (Usually FAT) instead. What's worse is they play games with it's position and naming standard. This adds to the confusion and is only useful (worth it) when the system is still very new.

In order for your (all parts seen or not) drive to register as "C:" sometimes the first partition is hidden, skipped and may not be the one flagged as "boot" (which Windows requires).

Note that this is largely one of the lock-in tricks you get with closed software. Why? Because after any amount of time passes, you are much better served with a newer version of Windows that has updates rolled in. That's not legally free but if you don't pay to be "legal", you will pay in MUCH more time "updating" Windows. Then more build up is heck, comparatively! Ask me how I know!

I recommend (optionally) keeping the Windows you got and installing Kubuntu Dapper in an easy to do "dual boot". Then only use Windows for comparison testing and NOT on-line. First, it takes far more time to scan for mal-ware. Second, Windows can not be fully secured compared to Open software and what it CAN do (not talking about human error such as phishing).

---

### Post by dannyboy79 on 2007-04-17
hey there, it sounds as though somehow your bot sector may have been messed up. If you want to restore your brand new laptop to it's factory state, follow the instructions here.
[http://www-307.ibm.com/pc/support/site.wss/MIGR-54483.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-54483.html)

you'll need to use the .exe on another computer which will create a bootable floppy that you can then use to fix your bootsector and what not so that then you can do a system restore. they refer to also being able to use an iso to boot and fix your bootsector but I don't see the downloadable iso anywhere on that page. this would be the first thing to try if you really want to get your original laptop back and then do a dual boot.

Neobuntu states, "Never, I repeat never, restore anything (old) to it's factory state. The insecure nature and build up required is horrendous."

I have to completely agree with this. Once he restores to factory state, he'll then do the windows updates and what not. He has no other choice based on what he has told us, he doesn't have a windows install disk, all he has is a restore partition which dell has been doing for awhile now. I have no idea how his hard drive got messed up but it has, so we should inform him how to fix it so he can move on and dual boot and enjoy linux. If all else fails and the link above doesn't help you to restore your system to factory state, you can purchase a cd or dvd to boot to from them. here's the link for that: [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4M7HWZ#purchase](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4M7HWZ#purchase)

I would say to be on the safe side to go with a dual boot at first until you get more familar with linux, this way you can experiement and get used to it, if you come across something you can't figure out and we don't help you fast enough, then you'll at least be able to shutdown and bootup into windows. good luck and let us know how it goes. 

we also need to figure out how this happened? did you go on the internet and or mount a parititon while using your live cd? what did you all do exactly while using the live cd.


I read into the link that the person above posted. here is the most promising solution IF YOU CHANGED ANYTHING. NOTE: if you didn't change anything while in the live cd, than I would call this a hardware issue as it's imposible for Ubuntu Live CD to change anything unless you mounted any drives while playing in the live cd!!!


[I]I received exactly this same error yesterday on a T60. Now, this particular T60 had had Linux installed on it for a while, and for various reasons I needed the machine back to running Windows (lets not get into the religious war. I describe these things in terms of preferences like Myers Briggs; I have a strong preference for Linux but that doesn't mean that I don't use Windows under stress). 

First of all, I had to get the RR partition to boot. The Linux I had been using was Fedora Core 5, and Grub had been installed on the Master Boot Record, so my "F11" option had vanished. I booted the machine into the Grub command line, and looked at the disk using the 'geometry' option. The first partition on the disk (hd0,0) was of type 0x83 (linux ext3), and the second partition (hd0,1) was of type 0x07 ("compaq rescue"), so I figured I need to boot into the second one. I typed: 


unhide (hd0,1) 
rootnoverify (hd0,1) 
chainloader +1 
boot 


and woo woo, the RR console loaded. So, I went to restore, it said "do you want to wipe all the other partitions on the disk or just the C: partition", I told it to wipe them all, and boom - after 25 seconds I got the error message described in this post, "IBM Product Recovery failed to restore your system". Arrrrgh. 

So I played with it for a while, and no matter what I did I couldn't get it to work. I tried setting the disk up to its original factory settings, by creating a single NTFS partition (also tried FAT), even went to the extent of creating a file system on the partition, and nothing - every single time I got the same message, just a frustrating failure and nothing more. Oh dear. 

Finally I tried to use the 'root (hd0,1)' instead of rootnoverify in the grub command line, and it came back and told me that it can't mount the partition as it is an unknown type. That gave me a clue - so I tried to boot by tweaking the partition type using grub: 


rootnoverify (hd0,1) 
parttype (hd0,1) 0x0b 
chainloader +1 
boot 


And this time, boom - the restore worked just fine! 0x0b is the partition type for Windows 98 FAT, which is what the file system on the RR partition is. I restored Windows to factory settings, fixed the MBR to boot the RR partition correctly and tried again - and once again it gave me the "IBM Product Recovery failed to restore your system" error! So then I used linux fdisk (via a knoppix CD) to switch the partition type to 0x0b, tried again and boom it worked just fine. 

So the moral of this story is, check the partition type that the RR partition is being created as. If it's a 0x07 partition type, change it to 0x0b and hopefully the problem will go away. 

Oh, finally a word about changing the MBR. Not being Windows inclined, I don't own a Windows CD, so I couldn't use the Windows recovery console to fix the Master Boot Record. After a lot of searching, I found mbrfix.exe (download from [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx)) and mbrfixgui.exe (download from [http://www.autoitscript.com/fileman/users/public/Triton/mbrfixgui.exe)](http://www.autoitscript.com/fileman/users/public/Triton/mbrfixgui.exe)). The two of these together fixed my MBR without even having to reboot the machine. 

Hope that's of use to someone. [/I]

---

### Post by Neobuntu on 2007-04-17
OK, good point about hardware failure but assuming that's not the coincidental problem, mangling of partitions and the MBR can be easily fixed (if you didn't erase and then write over things you can't live without and should have backed up anyway.) That is, if that's what you did.

Full discloser is in order, if you want an easy fix.

Now, I'm into fast time saving solutions AND I don't know what you need and want specifically. But based on what you said, perhaps it's time to step back and think about your overall goals.

No religious war here, run what you want but what do you need?

The big question in my mind is, do you have data stored on your Windows partition that you can't live without. Is it backed up. Backup from that partition FIRST and you can use the live CD to do this.

In fact, don't do ANYTHING to change your system until you fully understand what happened and where you want to be (and have a backup of what you can't live without).

The question is, do you feel that you still need Windows at all. Perhaps you need to ask about what you need before proceeding.

I would agree that if it can't be done with Linux, it can't be done. I will also tell you that your life will be simpler with One install to babysit. This one (or your main) install should definitely be DAPPER (and my preference is to start with Kubuntu and stay with it. The  "ubuntu-desktop" is a fine choice too. this is not a critical choice, Dapper is.) You could run the live CD of each Kubuntu and ubuntu  and decide that way. Of course you can run both but with more stuff to upgrade. Note: You can still use any program (KDE or Gnome/GTK), that doesn't matter. You just have to set your theme/style preference for each.

The next big choice is whether you want to go Kubuntu Dapper only, or dual boot Windows. Having Windows does give an excellent hardware comparison and of course lets you best use Windows only programs titles. It will eat up your time though. You may find the Kubuntu way of getting the job done is preferred. It depends on what is an important computer task; to you.

The only (main) reason not to use Dapper(compared to some other distro IMHO) is odd hardware and odd hardware is better replaced, if possible. Babysitting a "Windows only" device every time the core kernel updates, gets old and tiresome quick.

It was said you have no choice but to recover the Windows you have and to reinstall from the recovery partition.  Not good. First of all, you have no "LEGAL" option to install a newer and time saving/updated Windows without paying big bucks. That may be enough reason to kick Windows to the curb, right there! 

Secondly, your Windows install is (probably) still there. (Unless, did you get confused, seeing the recovery partition and tell the installer to erase your Windows partition?)

I would NOT recover with that crappy partition(as they are all or nothing), the only thing it might have of value is odd drivers and they would be old (unless you just bought a new system). Being Lenovo (I think you said) newer Windows drivers would be on-line anyway. Trust me, that's a WHOLE can of worms you don't want to open. You'll be building your Windows system back-up for hours and hours (so days or months). With Dapper comparatively, it comes with drivers/modules and they are automatic (given decent hardware). Dapper can be done in about 20 minutes.

If you must have Windows, fix your Windows First (unless you wrote over you whole XP partition) and go from there. If you have ALL your stuff backed up (for sure) and prefer to save time, get a (Kubuntu) Dapper live CD (Alternate CD if less than 192MB RAM and 128MB or more), boot it, run the easy installer and simply tell it to use the whole drive. You could always revisit Windows later or even start all over with a clean install, later. Windows likes to be First (it's stupid that way) and it's simpler to install Windows First. A Dapper install is easy and quick. Your choice. 

A clean install always wins but if you are not going to be using Windows much anyway, fix the boot to Windows, and install Dapper.

Summary: Backup and Save time by fixing your Windows install or just give the drive to Kubuntu Dapper. Then just see the forums about any "codecs" and plug-ins you might want to add and you'll have the best system, bar none. 

Do testing and new releases SEPARATELY; on another partition or simply on another drive.

Hope that helps. 

Please give more info as to what you did (if you want Windows) and what you want to accomplish.

---

### Post by Neobuntu on 2007-04-18
Many possibilities come to mind without further info.

Is there a BIOS upgrade for that notebook?

Perhaps you did install over the XP/NTFS partition and the recovery partition needs to see a blank formated NTFS partition to work. The live CD can make this with gtparted (or qtparted with Kubuntu).

It may be that the recovery partition is made to boot first in any case and then boot XP if it is in good order.

The "recovery" partition may require install or verification files on the other XP partition.

Did you install "GRUB" from the installer. Did you know that, normally one would resize  the XP partition (This will refuse; if there are errors on your XP drive that need to be checked in Windows). Resizing NTFS or FAT is easy with gparted. Just split it 50/50  to make some room (and then let the install use the free space to create the root and swap partitions for Kubuntu automatically). 

Did you try to reinstall GRUB manually. The following should NEVER be anything but "setup hd(0)" (not two numbers) which selects the MBR(Master Boot Record), and only after you designate the "root" partition (like Ubuntu such as: "root hd(0,1)" meaning partition two; where "menu.lst" and stage 2 lives.). This when manually reinstalling GRUB. Otherwise you'll trash the first part of your miss-selected partition, instead of the desired MBR (It's before ALL other partitions). Just stay with guided GRUB installs, if this seems hard.

Maybe the "makeactive" command needs to be used with GRUB, due to funky partitioning.

:confused: What did you do after, booting the live CD?

---

### Post by enthusaroo on 2007-04-18
THANK YOU SO MUCH to everyone who replied this me attempting my first usage of Linux/Ubuntu last night. 

First to clear up something. Almost all of my problems last night were in regards to Windows XP and the IBM Rescue and Recovery program. As I said in my original post, I love Ubuntu and as soon as 4.04 is released today, I plan to make a real install of Ubuntu to use as my main operating system. 

I only played with Linux for about a day, but what I love is knowing that it's a lot more flexible than Windows. I may not know a lot about operating systems, but I've been working with web applications like Drupal on a daily basis for more than two years - so "open" and "flexible" is good for me. I know it will take time to learn Linux, but that's just like anything.

Here is what happened last night. Actually, it's one of those strange seemingly unexplainable technical things. 

I mentioned in my first post that my main trouble was that IBM's Rescue and Recovery program was not working properly due to the fact that I was unable to restore Windows XP back to the original factory settings like I wanted. Oddly, I tried restoring it THREE MORE TIMES through Rescue and Recovery actually ended up working like it should. Therefore, I got it to reinstall Windows XP / reformat the drive and thereby fix my Intel video driver issues that were otherwise unresolvable. 

To the person who suggested that I should 'never restore to factory set-up'. The fact is that I tried everything to get the video drivers to work or install. Even the technicians at the IBM/Lenovo office in Hong Kong were unable to fix the issue three weeks ago when I brought it into their office. Either way it was necessary to restore Windows XP back to it's original factory condition. 

Everything in Windows XP works fine now. I have everything I need reinstalled and I copied all my important files over from DVD today. It was very time-consuming, but hey it was necessary. 

Tomorrow I will wake up - download the officially release of Feisty - and then install it.

---

### Post by dannyboy79 on 2007-04-18
glad to hear you got it working. If you're going to dual boot, I would suggest the Alternate Install CD as you have much more control over the Partitioning process. It's also text based so you should have any graphics issues which many have with ATI cards as I did myself. If you only have 1 hard drive (versus dual booting with 2 hard drives)  I would suggest using the Live CD that you already tried and then use Gnome Partition Editor to "shrink" your NTFS (windows) partition. 

******NOTE****** you'll most likely see other partitions in there, probably your restore partition and or restore program, leave them alone if you want to be able to restore to factory defaults in case you want to sell it in the future. OR you could try Norton Ghost or something that can backup an entire hard drive or at  the partition level but they'll most likely hidden from windows so you'd have to boot to the ghost cd. I have tried to use Partimage to backup and restore my NTFS partition (developers of Partimage warned that it was still experiemental but I wanted to find out) and it did NOT work so be caustious if your recovery partitions are NTFS, free Partimage may work with FAT though. I would boot to a live cd and back up your mbr for sure as it may be a  special MBR due to the f11 key or whatever you hit to activate the restore program. I've seen this with Dells, the MBR CAN'T just be restored by using fdisk /mbr or even Fixmbr. You can back up your current MBR from a linux live cd by using this command in a terminal

dd if=/dev/hda of=MBR-backup bs=512 count=1
(note: hda is the first hard drive in your system)

or use the link i provided earlier which makes a bootable floppy to be able to utlize your restore partitions.

Make sure you shrink the correct partition (the one with windows install on it)
Obviously everyone will tell you something different but based on an 80 gb hard drive my suggestion is to leave a little pad for windows (maybe 500mb to 1.5gb) and leave about 10gb for "main system" and then the remaining for your "home" partition, then of course 1.5 times the amount of your actual RAM for a swap partition. BUT leave this space unallocated so that the installer will format it and chose the correct mount points (yes I know that the Alt install cd can chose existing partitions for mount points etc etc). 

As an FYI, I have had SUCCESS with shrinking my Windows 2000 Pro  NTFS partition using the latest Gparted Live CD. I can't speak for the Ubuntu installer but I am sure it can shrink it successfully during the partitioning process just as easily. Then when it asks you where you want to install grub to, YOU HAVE 2 OPTIONS, READ BOTH BEFORE MAKING CHOICE:

pick (hd0) as this will install grub to your MBR which could affect the way your restore program works. but since you backed it up you're ok in case you ever want to sell it as I was saying earlier. this will present you with either Ubuntu or Windows choices immediately after the bios is done.

OR

you can install grub to the same partition that you're installing Ubuntu to NOTE: due to your restore partitions, this may be something like (hd0,4). Notice how we have a number after the (hd0,X) the x represents the partition where you want to install grub to. it'll basically install it to the bootsector of that partition. then you'll have to follow this guide for booting grub using NTLDR. (guide is similar here: [http://www.andrejciho.com/linux/mbrsafe-dual-boot/](http://www.andrejciho.com/linux/mbrsafe-dual-boot/))

E4: To use Windows Ntldr to boot a chainlaodable Linux in partition hda4.
Note : The file boot_hda4.lnx is the first 512 bytes of Linux boot loader in partition hda4. It has to be copied into the partition where XP/Win2k is booted.
In Linux :- Copy the first 512 bytes into a file

dd if=/dev/hda4 of=boot_hda4.lnx bs=512 count=1

then copy the file boot_hda4.lnx into "C" drive of Windows

In Windows

cd \
attrib -r -s -h boot.ini
edit boot.ini

then add "C:\boot_hda4.lnx "Ubuntu" to boot.ini
save the file boot.ini

attrib +r +s +h boot.ini

and then after your bios is done, you'll NTLDR with a list of choices being either Ubuntu or Windows. Then if you want to change how NTLDR acts (timeouts, default system to boot etc) then go to Control Panel, then Advanced, then Startup and Recovery and they you can modify how NTLDR acts.

Good luck and let us know how it goes.

---

### Post by pwhite on 2007-04-19
> **notwen said:**
> If you booted Ubuntu from the LiveCD, your HDD was not touched by Ubuntu.  Hope you're able to figure this out. =]


That's the way it **should** work - however, I wasn't able to boot back to Edgy after rebooting from a 7.04 Live DVD test drive. After removing the DVD and rebooting, I am greeted with the following error:

Disk Error
Press any key to restart

This problem may be hit or miss - I used the same DVD to test drive 7.04 on my laptop, without problems, before trying the same thing on my desktop...

---

### Post by pwhite on 2007-04-19
You can disregard my last post - it was a case of pilot error. I had left my USB flash drive in my computer while test driving 7.04. For whatever reason, it seems to have pushed my hard drive off the boot device list in my bios (I had checked, but not consciously changed any bios settings). I'm back in business after removing my USB flash drive...

---

### Post by dannyboy79 on 2007-04-19
> **pwhite said:**
> You can disregard my last post - it was a case of pilot error. I had left my USB flash drive in my computer while test driving 7.04. For whatever reason, it seems to have pushed my hard drive off the boot device list in my bios (I had checked, but not consciously changed any bios settings). I'm back in business after removing my USB flash drive...

you should really edit the previous post to this one because some may read it and not read the next one. it's always a good idea to just "edit" instead of create a new post when replying about the same issue. glad you're ubuntu/computer is alright

---

### Post by FrancoNero on 2007-04-19
btw, installing grub into the MBR always messes up the ability to boot from IBM's (hidden) recovery partition. request recovery CDs from IBM, you'll get those for free, and then get rid of that hidden partition, which might already be messed up. that's what happened to me. damn those recovery partitions, why don't manufacturers just ship windows CDs.... assholes in my book

---

### Post by dannyboy79 on 2007-04-19
hence why I informed him to back up his mbr just in case as well as install grub to partition instead of mbr. You know, you could even get away with not even installing grub. Just make a boot floppy or boot cd. install grub to that, create a menu.lst just like normal and you just boot to that and chose your os. he he he. Here's a great guide for making a grub boot floppy: [http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

---

### Post by pwhite on 2007-04-19
> **FrancoNero said:**
> ...request recovery CDs from IBM, you'll get those for free...

If I'm not mistaken, the thinkpad help system documents how to create the recovery CDs from the hidden partition. Of course, no one creates those CDs before it's too late. Last July IBM charged me $50 USD for a set of recovery CDs after I had blown my MBR away and was unable to recover my system...

---

### Post by Lieter on 2007-04-19
I had the same thing, i had a breezy partition, but i replaced the MBR with the windows MBR(shame on me) and when i popped in a feisty cd and rebooted after looking at it(just browsing the web) i suddenly had GRUB to boor breezy of WinXP, it wasodd but made me decide to completely switch anyway, and i'm happy i did :D

---

### Post by dannyboy79 on 2007-04-20
> **Lieter said:**
> I had the same thing, i had a breezy partition, but i replaced the MBR with the windows MBR(shame on me) and when i popped in a feisty cd and rebooted after looking at it(just browsing the web) i suddenly had GRUB to boor breezy of WinXP, it wasodd but made me decide to completely switch anyway, and i'm happy i did :D

not sure what you're saying here but you should really clarify as this will definitely scare away potential new users. If you already had grub installed in your mbr for booting breezy, then overwrote it with a windows mbr, then popped in the fiesty live cd and only surfed the web, it's completely impossible that grub overwrote the windows mbr. i repeat, this is IMPOSSIBLE, you're either not telling us something or some1 did something when you weren't looking or whatever. the drive doesn't get mounted when using a live cd and even if it did you'd have to tell grub to install itself to the mbr, it doesn't have a mind of it's own. 

Please clarify for other new users.

---

### Post by Aiown on 2007-04-24
> **dannyboy79 said:**
> not sure what you're saying here but you should really clarify as this will definitely scare away potential new users. If you already had grub installed in your mbr for booting breezy, then overwrote it with a windows mbr, then popped in the fiesty live cd and only surfed the web, it's completely impossible that grub overwrote the windows mbr. i repeat, this is IMPOSSIBLE, you're either not telling us something or some1 did something when you weren't looking or whatever. the drive doesn't get mounted when using a live cd and even if it did you'd have to tell grub to install itself to the mbr, it doesn't have a mind of it's own. 

Please clarify for other new users.

I also had problems with Ubuntu installing grub to the MBR by default, no question asked. Here is my scenario.

I use [[COLOR="DarkRed"]Symon[/COLOR]]("http://symon.da.ru") for partition and boot manager. It sits in the first sector with its configuration, it doesn't require a separate partition, and has true partition hiding.

Now here comes Ubuntu, dumps grub to the MBR overwriting everything, even the Symon config is lost. If you didn't write down the partition table on a piece of paper beforehand you can forget about all the partitions beside what was prepared for Linux. Your Windows is gone for good because Symon hid it from Ubuntu.

So by trying to be too easy Ubuntu is actually very destructive in certain situations. It caused me many days of pain trying to recover the lost partitions and re-instanning another distro. 

This is why I don't use Ubuntu. It takes away choices. A few years ago I asked why Ubuntu gives no choices during installation. Why it doesn't ask if you wanted sudo by default or you wanted to activate the root account. Why it doesn't ask if you wanted to install grub to the MBR or the Linux boot partition. Simply there is no advanced install option. Ubuntu treats everyone as a beginner who has no idea what the MBR is.

I know there was an earlier version that had an advanced install option, but I could not figure out how to do it with the last two. So I gave Ubuntu a chance, every time swearing never to do it again. This time I have downloaded 7.04 just to find out that if I wanted to install grub to the boot partition I need the "alternative" ISO. Why the hell is it not built into the same CD? Most people don't read the whole website to figure out that the main download CD is not good for them. I wasn't even aware there was an alternative ISO that gave me a choice of how to install Ubuntu. And don't forget that in many countries internet connections are slow and there is a strict download limit. Mistakenly downloading a CD then re-downloading another is not an option for many. The free CD offered on the website arrive 4-6 weeks later.

so I have the 7.04 CD but I will not give it a try unless I am certain it will not blow away my partitions. And the constant sudo-ing drives me nuts. I know I can enable the root account, but when I tried it in the past many applications started from the menu (I use KDE) that expected sudo-ing simply no longer worked.

I wish Canonical takes these into consideration in the next 10-20 years and comes up with a distro that gives choices. :-(

---

### Post by dannyboy79 on 2007-04-25
> **Aiown said:**
> I also had problems with Ubuntu installing grub to the MBR by default, no question asked. Here is my scenario.

I use [[COLOR="DarkRed"]Symon[/COLOR]]("http://symon.da.ru") for partition and boot manager. It sits in the first sector with its configuration, it doesn't require a separate partition, and has true partition hiding.

Now here comes Ubuntu, dumps grub to the MBR overwriting everything, even the Symon config is lost. If you didn't write down the partition table on a piece of paper beforehand you can forget about all the partitions beside what was prepared for Linux. Your Windows is gone for good because Symon hid it from Ubuntu.

So by trying to be too easy Ubuntu is actually very destructive in certain situations. It caused me many days of pain trying to recover the lost partitions and re-instanning another distro. 

This is why I don't use Ubuntu. It takes away choices. A few years ago I asked why Ubuntu gives no choices during installation. Why it doesn't ask if you wanted sudo by default or you wanted to activate the root account. Why it doesn't ask if you wanted to install grub to the MBR or the Linux boot partition. Simply there is no advanced install option. Ubuntu treats everyone as a beginner who has no idea what the MBR is.

I know there was an earlier version that had an advanced install option, but I could not figure out how to do it with the last two. So I gave Ubuntu a chance, every time swearing never to do it again. This time I have downloaded 7.04 just to find out that if I wanted to install grub to the boot partition I need the "alternative" ISO. Why the hell is it not built into the same CD? Most people don't read the whole website to figure out that the main download CD is not good for them. I wasn't even aware there was an alternative ISO that gave me a choice of how to install Ubuntu. And don't forget that in many countries internet connections are slow and there is a strict download limit. Mistakenly downloading a CD then re-downloading another is not an option for many. The free CD offered on the website arrive 4-6 weeks later.

so I have the 7.04 CD but I will not give it a try unless I am certain it will not blow away my partitions. And the constant sudo-ing drives me nuts. I know I can enable the root account, but when I tried it in the past many applications started from the menu (I use KDE) that expected sudo-ing simply no longer worked.

I wish Canonical takes these into consideration in the next 10-20 years and comes up with a distro that gives choices. :-(


OK, hold on here. Grub was NOT installed onto your MBR when you ran the LivdCD I can guarentee that. Also, if you used the Desktop LiveCD to install Ubuntu then I can't say for sure but I believe by default it will install Grub to the mbr of the disk unless you chose something different BUT I can't say for sure as I never install using that disk. I always use the Alternate CD as it's way more versatile (allows you to upgrade from previous version, allows you to install grub where ever you want and other great stuff)

So again, please don't go spouting off that running the LiceCD ruined your Windows Install. You should have read up on Dual Booting before you decided to do it. Before you replace an engine, do you just dig right in and not understang what's going to occur when you do that. Also, like I said, I can't agree or disagree with you as I am not sure that the installer didn't ask you where you wanted to put grub and you just didn't know so you chose the default which is what many newbies do.

---

### Post by dannyboy79 on 2007-04-25
> **Aiown said:**
> I also had problems with Ubuntu installing grub to the MBR by default, no question asked. Here is my scenario.

I use [[COLOR="DarkRed"]Symon[/COLOR]]("http://symon.da.ru") for partition and boot manager. It sits in the first sector with its configuration, it doesn't require a separate partition, and has true partition hiding.

Now here comes Ubuntu, dumps grub to the MBR overwriting everything, even the Symon config is lost. If you didn't write down the partition table on a piece of paper beforehand you can forget about all the partitions beside what was prepared for Linux. Your Windows is gone for good because Symon hid it from Ubuntu.

So by trying to be too easy Ubuntu is actually very destructive in certain situations. It caused me many days of pain trying to recover the lost partitions and re-instanning another distro. 

This is why I don't use Ubuntu. It takes away choices. A few years ago I asked why Ubuntu gives no choices during installation. Why it doesn't ask if you wanted sudo by default or you wanted to activate the root account. Why it doesn't ask if you wanted to install grub to the MBR or the Linux boot partition. Simply there is no advanced install option. Ubuntu treats everyone as a beginner who has no idea what the MBR is.

I know there was an earlier version that had an advanced install option, but I could not figure out how to do it with the last two. So I gave Ubuntu a chance, every time swearing never to do it again. This time I have downloaded 7.04 just to find out that if I wanted to install grub to the boot partition I need the "alternative" ISO. Why the hell is it not built into the same CD? Most people don't read the whole website to figure out that the main download CD is not good for them. I wasn't even aware there was an alternative ISO that gave me a choice of how to install Ubuntu. And don't forget that in many countries internet connections are slow and there is a strict download limit. Mistakenly downloading a CD then re-downloading another is not an option for many. The free CD offered on the website arrive 4-6 weeks later.

so I have the 7.04 CD but I will not give it a try unless I am certain it will not blow away my partitions. And the constant sudo-ing drives me nuts. I know I can enable the root account, but when I tried it in the past many applications started from the menu (I use KDE) that expected sudo-ing simply no longer worked.

I wish Canonical takes these into consideration in the next 10-20 years and comes up with a distro that gives choices. :-(

Ok, my previous post was hastly written when I saw that you like others are trying to inform people about what Ubuntu does from the livecd and what you're conveying is a complete falicy!!

I started to read the rest of your post after I posted my first response and and am just flaburgasted at your ignorance. Ubuntu only erased your partition table because you probably instructed it to. It doesn't just go and do that on it's on,  you actually think the installer would do this? There is an option to manually edit the partition table which would have saved your previous partitions, exiting data and partition table!!

Next issue is grub being installed to your mbr. Again, just because it did this (i can't say for sure if you just didn't see the option of installing it elsewell) does not mean that you couldnt have booted a livecd and fixed windows from being hidden. So again, it sounds like your ignorance really deleted your ubuntu and windows stuff because all you would have had to do was access the disk from any live cd and copy your stuff off at a minimum but I am also sure you could have unhid your windows partition using Super Grub Disk or Ultimate Recovery CD. 

So please don't spread such ignorant comments about Ubuntu and if you do, don't put them in relation to the Livecd when you acually attempted the install which is a completely different story as you're the one that told the installer to start. You should learn what you're doing before you do it, FYI.

---

### Post by Aiown on 2007-04-26
> **dannyboy79 said:**
> OK, hold on here. Grub was NOT installed onto your MBR when you ran the LivdCD I can guarentee that. Also, if you used the Desktop LiveCD to install Ubuntu then I can't say for sure but I believe by default it will install Grub to the mbr of the disk unless you chose something different BUT I can't say for sure as I never install using that disk. I always use the Alternate CD as it's way more versatile (allows you to upgrade from previous version, allows you to install grub where ever you want and other great stuff)

So again, please don't go spouting off that running the LiceCD ruined your Windows Install. You should have read up on Dual Booting before you decided to do it. Before you replace an engine, do you just dig right in and not understang what's going to occur when you do that. Also, like I said, I can't agree or disagree with you as I am not sure that the installer didn't ask you where you wanted to put grub and you just didn't know so you chose the default which is what many newbies do.

Did I mention running the live CD? No. I installed Ubuntu from it as I am installing 7.04 to a blank disk right now. While this time I know about the alternate CD, don't forget that magazines only have the other one. 

And no, Ubuntu doesn't ask you whether you want GRUB on the MBR or elsewhere. It recommended an over 9GB partition. This time I ticked to use the whole disk then the install went on. Don't forget, if I had Symon on the disk it would have worked the same way as Symon has true partition hiding. Ubuntu cannot see the Windows partition on a Symon disk, so Ubuntu installs GRUB to the MBR destroying the Symon config for the whole disk.

---

### Post by Aiown on 2007-04-26
> **dannyboy79 said:**
> Ok, my previous post was hastly written when I saw that you like others are trying to inform people about what Ubuntu does from the livecd and what you're conveying is a complete falicy!!

I started to read the rest of your post after I posted my first response and and am just flaburgasted at your ignorance. Ubuntu only erased your partition table because you probably instructed it to. It doesn't just go and do that on it's on,  you actually think the installer would do this? There is an option to manually edit the partition table which would have saved your previous partitions, exiting data and partition table!!

Next issue is grub being installed to your mbr. Again, just because it did this (i can't say for sure if you just didn't see the option of installing it elsewell) does not mean that you couldnt have booted a livecd and fixed windows from being hidden. So again, it sounds like your ignorance really deleted your ubuntu and windows stuff because all you would have had to do was access the disk from any live cd and copy your stuff off at a minimum but I am also sure you could have unhid your windows partition using Super Grub Disk or Ultimate Recovery CD. 

So please don't spread such ignorant comments about Ubuntu and if you do, don't put them in relation to the Livecd when you acually attempted the install which is a completely different story as you're the one that told the installer to start. You should learn what you're doing before you do it, FYI.

Before calling each other by name let me put forward that I am a long time Linux user. I tried at least ten if not more different distros. I mainly use Fedora or CentOS. So I am not inexperienced when it comes to installing Linux.

I think you are talking about the alternate CD. I am talking about the normal live CD. I did not say Ubuntu destroyed the partition table, but the Symon config that is stored in the first sector of the HDD. When it writes to the MBR the config is over-written for good, so all information about the partition table (and there can be dozens of them created in Symon) is lost unless one has the values on paper so that they can be manually entered afterwards. Only the partitions assigned to Ubuntu remain intact, all others are lost because the configuration is destroyed.

I ALWAYS pre-create the partitions for Linux before install. I did NOT instruct Ubuntu to write to the MBR and I purposely left the Windows partitions hidden. I don't want the various O/Ss to see each other. Ubuntu did NOT ask where I wanted GRUB to be installed. This is a big turn-off for me when it comes to Ubuntu. Why is it so hard to build advanced install options into the normal CD rather than issuing another, alternate one? Magazines don't distribute the alternate CD and many people don't have the time to hunt around websites to find information they didn't know they had to look for.

All you need is a plain vanilla check box called "advanced" displayed at the beginning of the install process. Then both the newbie and the advanced can use the very same CD.

---

### Post by dannyboy79 on 2007-04-26
> **Aiown said:**
>  Did I mention running the live CD? No.  
Look at the title of where you posted your comments. People will come here and read your comments and think that running a live cd did this to your computer, that's what we don't want to happen.


> **Aiown said:**
>  And no, Ubuntu doesn't ask you whether you want GRUB on the MBR or elsewhere. It recommended an over 9GB partition. This time I ticked to use the whole disk then the install went on. Don't forget, if I had Symon on the disk it would have worked the same way as Symon has true partition hiding. Ubuntu cannot see the Windows partition on a Symon disk, so Ubuntu installs GRUB to the MBR destroying the Symon config for the whole disk. 
Why would you tell Ubuntu to use the whole disk if you had other partitions on it that you wanted to still use? Do you mean to say that you told it to use a certain hard drive and use the remaing space for your install? If so, then yeah, that's your mistake, based on that the installer makes a lot of assumptions like to install grub to your mbr whereas I believe if you chose to manually edit the partition table it would have asked you were you wanted to install grub but like I said I can't say that for sure as I only use hte alt cd due to the more versatility during the install. You did state that it wiped out your partition table, in fact you stated those exact words. Here's what you wrote, "If you didn't write down the partition table on a piece of paper beforehand you can forget about all the partitions beside what was prepared for Linux. Your Windows is gone for good because Symon hid it from Ubuntu." Yeah, since you chose to perform the install the way you did, it overwrote your mbr with Grub which you're right, it would've erased Symon from the mbr but that didn't mean that you couldn't have fixed it. the partition is NOT hidden from the bios, it's hidden from other os's therefore like I said, you could have reinstalled symon to the mbr after you booted into windows and fixed this issue. all you would have had to do was boot to your windows cd, go into the recovery console and typed in FIX /MBR (or whatever the command is but whether it's FIX MBR or FIX /MBR I am not sure as I don't feel like googling it right not) and your computer would have booted up windows just fine. then you wouldv'e installed symon, then you would've added ubuntu  to symon. Wala, that's fixed.

---

### Post by dannyboy79 on 2007-04-26
I don't disagree with this at all, you're totally corrrect but one would think that before performing a dual boot setup you would know what the installer "COULD" do to your computer. The Desktop CD is aimed at new beginners setting up 1 machine. If you read almost every Ubuntu Dual Boot guide, everyone states the fact that the installer will install grub to the mbr. I am sorry this happened to you and i agree with you completely, I merely wanted to make sure other readers understood that you chose to install it and told it to use the "entire" drive which makes no sence to me when you knew you had other stuff on you hard drive that  you wanted to save/use. Symon does NOT hide partitions from a live cd. (please correct me byt symon was installed in the hard drive therefore if you booted to the CD than there was no way that Symon would've even come into effect therefore now that you infomed me that you chose to "Erase the Entire" disk, YEAH, ALL YOU STUFF WAS DELETED CAUSE YOU TOLD IT TO.

---

### Post by Aiown on 2007-04-28
> **dannyboy79 said:**
> Look at the title of where you posted your comments. People will come here and read your comments and think that running a live cd did this to your computer, that's what we don't want to happen.

You are right, I should have made it clear that I was not talking about simply running the live CD, but installing Ubuntu from it. I focused on what installing Ubuntu did and ignored the title.


> **dannyboy79 said:**
> Why would you tell Ubuntu to use the whole disk if you had other partitions on it that you wanted to still use? Do you mean to say that you told it to use a certain hard drive and use the remaing space for your install? If so, then yeah, that's your mistake, based on that the installer makes a lot of assumptions like to install grub to your mbr whereas I believe if you chose to manually edit the partition table it would have asked you were you wanted to install grub but like I said I can't say that for sure as I only use hte alt cd due to the more versatility during the install. You did state that it wiped out your partition table, in fact you stated those exact words. Here's what you wrote, "If you didn't write down the partition table on a piece of paper beforehand you can forget about all the partitions beside what was prepared for Linux. Your Windows is gone for good because Symon hid it from Ubuntu." Yeah, since you chose to perform the install the way you did, it overwrote your mbr with Grub which you're right, it would've erased Symon from the mbr but that didn't mean that you couldn't have fixed it. the partition is NOT hidden from the bios, it's hidden from other os's therefore like I said, you could have reinstalled symon to the mbr after you booted into windows and fixed this issue. all you would have had to do was boot to your windows cd, go into the recovery console and typed in FIX /MBR (or whatever the command is but whether it's FIX MBR or FIX /MBR I am not sure as I don't feel like googling it right not) and your computer would have booted up windows just fine. then you wouldv'e installed symon, then you would've added ubuntu  to symon. Wala, that's fixed.

May I suggest that you get a copy of Symon and play around with it? I don't mean to be rude, but Symon works differently than you think. The partitions created by Symon cannot be seen by the BIOS. Briefly, Symon is able to create 32 primary partitions on your hard drive, and out of four of these it recreates the MBR at boot time. So when you setup Symon you can only specify up to 4 partitions for a particular O/S. The remaining partitions stay invisible to the O/S you boot into, they appear as unused space. Now if in the meantime grub corrupts the Symon config (that contains the information to all "partitions") then only those partitions will be visible to the BIOS that were used the last time. The BIOS knows nothing about the rest. So it is not the partition table, but the Symon config about the - shall I call them - "virtual partitions" that are destroyed, and thus, the pointers to those "partitions" are lost.

Now when XP overwrites the MBR it only removes Symon, but leaves the config intact, therefore, reintalling Symon will bring back the system. Grub, however, destroyed both Symon and its config.

Today I conducted an experiment. I downloaded the alternate CD hoping that it will give me the option to select where grub would be installed. I chose the text-based install and it really gave me a lot of options how to setup the partitions, etc. However, it silently installed grub to the MBR again, no question asked. This is what I call destructive. Symon along with its config was totally wiped out. Luckily, I had the config (partition head, sector numbers, etc) written down and I could bring the Windows partitions back to life.

So, if you ask, I had given Ubuntu plenty of time despite not having a lot of time. I have to say, I am not impressed with Ubuntu not asking where I wanted to install grub and whether I wanted to enable the root account or not. All other distros I tried had given me these vital choices. Ubuntu didn't.

---

### Post by Aiown on 2007-04-28
> **dannyboy79 said:**
> I don't disagree with this at all, you're totally corrrect but one would think that before performing a dual boot setup you would know what the installer "COULD" do to your computer. The Desktop CD is aimed at new beginners setting up 1 machine. If you read almost every Ubuntu Dual Boot guide, everyone states the fact that the installer will install grub to the mbr. I am sorry this happened to you and i agree with you completely, I merely wanted to make sure other readers understood that you chose to install it and told it to use the "entire" drive which makes no sence to me when you knew you had other stuff on you hard drive that  you wanted to save/use. Symon does NOT hide partitions from a live cd. (please correct me byt symon was installed in the hard drive therefore if you booted to the CD than there was no way that Symon would've even come into effect therefore now that you infomed me that you chose to "Erase the Entire" disk, YEAH, ALL YOU STUFF WAS DELETED CAUSE YOU TOLD IT TO.

I see you do not understand the problem I stated. Contrary to the above, I never tell the Linux installer to take over the whole disk. I always pre-create the partitions for Linux to be installed on. I would like the readers to understand that Symon doesn't create REAL partitions. The BIOS can only see up to 4 primary partitions. If you want multiple partitions you need to create extended partitions with logical drives. Symon uses its own "exotic" technology to mark out up to 32 primary "partitions" and keep records of where they are. The config is stored in the first sector of the hard drive beside the MBR. They are not "real" partitions in the sense of what you create with fdisk, but a smart hack to bypass the limitations of an old technology.

You assign four of these partitions to a particular O/S. I usually assign 3 primary and an extended, and withing the extended partition I have a number of logical drives. Symon recreates the MBR out of these partitions when you boot into the O/S (or pretend to boot into it before it is installed by hitting enter when the O/S is highlighted on the menu). This way the chosen partitions become available for the O/S to use (or for installing the O/S to them). The other partitions don't exist as far as the O/S is concerned, they appear as unused space. It is only Symon that keeps record of where they are.

Now Windows only installs the standard MBR, and since the Symon config is stored beside the MBR in the first sector, it remains intact, however, grub is fat and it needs a lot more space than MBR and wipes out the Symon config. This is the problem. Since the partitions created are only recorded in the config, once it is destroyed, the info about all the other partitions are lost. Reinstalling Symon will not bring them back. Sometimes Symon can successfully recover them (it has a partition scanning tool), but not always.

All I suggest is to give users the advanced install option in the same CD. One should be able to choose how to install it. If Ubuntu is aimed at the newbie why is vi installed? Vi is not for newbies. Why do you get to install server software once you boot into the O/S? All advanced stuff should be removed and disabled by default.

Ubuntu has the same sickness as Gnome. It is taking choices away. It is making decisions for the user even when they are capable to decide for themselves. If Ubuntu gave these choices it would indeed be a great distro.

Check out the VLC preferences window. There is a checkbox "advanced options". Have a look at Xine's setup window. One can select the experience level from a drop-down list. These determine what options are available to you. This is what I am talking about. The option to go advanced and not be treated as a little child.

---

### Post by dannyboy79 on 2007-04-30
> **Aiown said:**
>   I never tell the Linux installer to take over the whole disk. I always pre-create the partitions for Linux to be installed on.    
This is not what you have already stated in your previous message. You stated and I quote, "This time I ticked to use the whole disk then the install went on."

> **Aiown said:**
>  May I suggest that you get a copy of Symon and play around with it? I don't mean to be rude, but Symon works differently than you think. 
It sounds like a versatile tool for booting tons of os's although since I am familar with grub I would merely use grub to do what you're suggesting and then some. Here's a example of booting 100plus operating systems using grub.  [http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)

> **Aiown said:**
>  However, it silently installed grub to the MBR again, no question asked. This is what I call destructive. Symon along with its config was totally wiped out.  Well I am sorry but I have no idea how or what you're chosing or what installer you're using because the installer definitely asks you where you want to install grub to without a doubt. I just did the edgy install using the Alternate Install less than 2 weeks ago onto a dual boot setup running windows xp and the person I was doing it for wanted to use NTLDR as his boot loader so no mbr was overwritten as I chose to install grub into the edgy partition.

> **Aiown said:**
>  All I suggest is to give users the advanced install option in the same CD. One should be able to choose how to install it. If Ubuntu is aimed at the newbie why is vi installed? Vi is not for newbies. Why do you get to install server software once you boot into the O/S? All advanced stuff should be removed and disabled by default. 
I can't agree with you more. VI is installed but not the default editor, at least not in my experience. I think your questions about why people get to install server software after isntalling Ubuntu is just obsurd, why wouldn't you??? Linux has long been great for the server market and if Ubuntu is going to release a distro trying to gain Desktop OS marketshares, why would they remove the ability to install server software?? If someone is smart enough in ubuntu to want to install it, then they're going to be smart enough to configure it or at least learn to configure it properly. Ubuntu does NOT come with any ports listening by default so it's very secure, so it's not like you install ubuntu and by default you have all this server stuff running.

---

