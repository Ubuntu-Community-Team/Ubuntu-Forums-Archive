---
title: "I want to install Ubuntu x 64 via wubi on windows 8"
date: 2012-12-31
forum: General Help
---

### Post by aviramof on 2012-12-31
I want to install Ubuntu x 64 via wubi on windows 8 but no luck so far why is that?
 
10x in Advance.

---

### Post by Cheesemill on 2012-12-31
If Windows 8 was installed on your computer when you bought it then you're out of luck.

Wubi wont work on a computer that uses UEFI and GPT disks (which is all machines with Windows 8 preinstalled).

---

### Post by aviramof on 2012-12-31
Its a desktop computer with ssd drive and I personally installed everything including dual boot between my ssd drive and my hdd drive so It should work.
 
I'm trying to run it via virtual drive meaning poweriso mount option and all it said is to restart the computer and use cdrom.

---

### Post by aviramof on 2013-01-01
I Guess I will have to wait for the next version of Ubuntu x64 to support windows 8 with working wubi.

---

### Post by Cheesemill on 2013-01-01
The only things that don't work with Wubi are UEFI and GPT partitioning. If you aren't using either of these then Wubi should work fine.

---

### Post by aviramof on 2013-01-01
Unfortunally it doesn't it just say restart the computer and nothing happen.
 
I used wubi before but on windows 7 32 bit and an old sata 1 160gb hdd not 
 
on my brand new expensive computer with windows 8 pro so I really don't 
 
know what is the problem.
[http://imageshack.us/photo/my-images/834/56758156.jpg/](http://imageshack.us/photo/my-images/834/56758156.jpg/)
 
[[IMG]http://img834.imageshack.us/img834/7104/56758156.jpg[/IMG]]("http://imageshack.us/photo/my-images/834/56758156.jpg/")
Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by oldfred on 2013-01-01
With multiple drives it should not be difficult to allocate the 25GB you would have for wubi to a Linux partition instead. Then you have a full partitioned install that does not depend on Windows.

       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    
       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by Paddy Landau on 2013-01-01
> **oldfred said:**
> With multiple drives it should not be difficult to allocate the 25GB you would have for wubi to a Linux partition instead.
+1. As Agostino said, WUBI is not suitable for long-term use. In my experience (and many other posts that I have read), it tends to be less stable, and can fail fatally..

If you intend doing more than just test-driving Ubuntu, go for a proper installation. I believe that 12.10 already supports UEFI, with the next point-release of 12.04 (due February) scheduled to do so.

---

### Post by aviramof on 2013-01-01
I know how to install Ubuntu long term I have done it in the past but I don't want to install grub on my very fast new computer and mess up my windows 8 boot loader and that about it.
 
it could could a lot of problems that I don't want to fix later like removing grub with windows disk and the commands bootre.exe/fixboot and bootrec.exe/fixmbr on two seperete 
drives meaning that I would have to do it twice and change the drives in the bios everytime.
 
I have done it in the past on my old computer but here I really don't want to do it period.:)
 
now I have ssd drive and 1TB HDD not one ide drive and one 160GB sata1 drive and that makes a big difference for me.:)
 
There I had nothing here I have 140GB of high end games to loose if my bootloader would cause problem I want be able to fix.
 
thanks in advance.

---

### Post by oldfred on 2013-01-01
With multiple drives I really like to keep each drive separate. If not sure and as many suggest just disconnect the Windows drive and install Ubuntu. That way grub will not accidentally get installed to the Windows drive. Be sure to keep Windows as sda. You can use one time boot key or usually the chain load entry from grub will boot Windows. Some have had issues when Windows 8 is hibernated, so then one time boot key is no that difficult to use.

Always have a repairCD or flash drive for every system you have installed. Best to make one for Windows and if installing Ubuntu have the Ubuntu liveCD and possibly several other repair ISO on DVDs, CDs or flash drives. Boot-Repair and Supergrub are always good to have.

---

### Post by aviramof on 2013-01-01
I have two drives one ssd one hdd on both I have windows 8 install with it's own bootmgr partition and I have dual boot  for both OS and the reason for it is because I didn't have an 
 
ssd drive when I bought the computer it's a later upgrade so now I use one as the
 
main windows 8 on my ssd with all the games and the other with just softwares so it is a big mass to install grub here and etc no matter what I do.
 
and that is why I want and need a good working wubi I know it's not perferct but it's the best I can do under those circumstances or how you write it.:)
 
so please make sure that your next Ubuntu version will work fine with wubi and windows 8 or it want be much use for me at all.
 
thanks in advance.

---

### Post by Cheesemill on 2013-01-01
You haven't actually told us what happens when you try and install Ubuntu using Wubi. All you have said so far is 'It doesn't work'.

What point does the installation get to? What errors do you get? Have you looked at the Wubi log file to see what it says?

---

### Post by mJayk on 2013-01-01
Is it still possible to install ubuntu along side, say, a laptop preinstalled with win 8 via the usual boot from usb and then install method?


Cheers

Matt

---

### Post by oldfred on 2013-01-01
You have to use the 64 bit version of 12.10 as that has grub2 2.00 that has added support for UEFI with secure boot. But to install you have to turn secure boot off and some systems must have quick boot off or you cannot get back into UEFI menu with quick boot on. 
And you have to Boot usb flash drive from UEFI menu in UEFI mode. It should also offer legacy/BIOS/AHCI mode also, but do not use it.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by aviramof on 2013-01-02
As I beleive I said instead of the usual wubi options that I know to choose drive and etc all it says is restart the computer as you can see in this pictures and that it.
 
[http://imageshack.us/photo/my-images/441/57893884.jpg/](http://imageshack.us/photo/my-images/441/57893884.jpg/)
[http://imageshack.us/photo/my-images/856/35687607.jpg/](http://imageshack.us/photo/my-images/856/35687607.jpg/)

---

### Post by aviramof on 2013-01-03
So I hope that now you understand my problem and would try to fix it on your next release.

---

### Post by Paddy Landau on 2013-01-03
> **aviramof said:**
> So I hope that now you understand my problem and would try to fix it on your next release.
The people on this forum are volunteers (people just like you!), and are not involved in the development.

I suggest that you raise a bug report on [Launchpad]("https://bugs.launchpad.net/ubuntu").

However, the suggestion has twice been given to avoid WUBI and go for a native installation. I know that you are concerned about losing your bootloader; but you do realise, don't you, that installing WUBI affects your bootloader anyway?

Therefore, here is what I would do in your place:

[LIST=1]
[*]Ensure that you have uninstalled WUBI. Reboot.
[*]Backup up your **entire** disk using either [CloneZilla]("http://www.clonezilla.org/") or [RedoBackup]("http://redobackup.org/") (RedoBackup is the easier option, but does not work on all computers). This way, if your Ubuntu installation turns out to be a complete mess, you can restore your entire disk (both Windows and bootloader) easily.
[*]Of course, also do you usual daily backup.
[*]Using the built-in Windows Disk Management utility, free up space for Ubuntu. I recommend 20Gb + enough space for all the data that you intend to store. You'd probably want to do this on your second 1Tb drive. Create two *empty* partitions in this space: 8Gb (for your Linux swap) and the rest for your Ubuntu.
[*]Install Ubuntu 12.04 64-bit using the two newly-created partitions.
[*]If you have problems with your bootloader, post back here so that you can solve the problem.
[/LIST]
If it is really a mess, and we can't help you solve your bootloader problem (assuming there is one), you can restore the entire disk with CloneZilla or RedoBackup.

---

### Post by aviramof on 2013-01-03
WUBI use the boot loader of windows grub however is a different bootloader completely and 
backing up my entire disk is 304GB on my E partition another 54GB on my D partition and 
another 39GB on my drive c which is the ssd so 
it's not so practicall after call.
 
the only thing I can of beside live cd is if the installer from the disk will let me use windows bootloader and not grub.

---

### Post by Paddy Landau on 2013-01-03
> **aviramof said:**
> … backing up my entire disk is 304GB on my E partition another 54GB on my D partition and another 39GB on my drive c which is the ssd so 
it's not so practicall after call.
You only need to back up the bootable drive, which would be your C: drive. You don't have to back up your other data disks, as the installation of Ubuntu won't touch that data (provided you take care to install as per my instructions).

Incidentally, your screen-shot shows your SSD as 120GB and your other  drive as a full 1,000Gb. So, you have plenty of spare space — you can  back up your SSD onto your E: drive. That's not a bad idea, anyway, because if you get bad malware (virus, etc.), you can simply restore instead of having to reinstall Windows.
 
> **aviramof said:**
>  the only thing I can of beside live cd is if the installer from the disk will let me use windows bootloader and not grub.
You have one more option. You can install to a drive other than your SDD, and tell the installer (in the advanced option) to install the bootloader onto that drive. When you boot your computer, you have to press a key (generally F12 or something like that) to tell your BIOS from which drive to boot. If you choose the SSD, Windows will boot. If you choose the other drive, Ubuntu will offer you a choice of Windows and Ubuntu.

You can use an external hard drive as the other drive, but your internal drive would do just as well.

---

### Post by aviramof on 2013-01-03
Well thanks any way i'll think about it but I still prefer wubi.

---

### Post by aviramof on 2013-01-05
I have decided to wait sorry guys but full install is not for me right now.

---

### Post by Paddy Landau on 2013-01-05
OK, no problem.

---

### Post by aviramof on 2013-01-07
Ubuntu ultimate-edition-3.5-x64 does work with wubi and windows 8 so I trust you to pass it along to the developers:)
 
[http://ultimateedition.info/](http://ultimateedition.info/)
 
I don't have the energy to do it my self for now.:)

---

### Post by Paddy Landau on 2013-01-07
> **aviramof said:**
> … I trust you to pass it along to the developers
Aviramof, we are all just people like you, who chip in to the forum now and then to help, out of the goodness of our hearts.

I certainly don't have the energy — I have my own problems and health issues to deal with.

You are best placed to pass it to the developers, as you have the problem. I don't even have Windows 8, and if I did, I wouldn't be interested; as I have advised you, WUBI is a poor long-term solution.

If you don't pass it along, it won't be passed along.

---

### Post by aviramof on 2013-01-07
an updated wubi does work the one in the Ubuntu disk is probobbly old.

---

### Post by Paddy Landau on 2013-01-07
> **aviramof said:**
> an updated wubi does work the one in the Ubuntu disk is probobbly old.
You may be right. Getting the latest release of a version often helps.

I'm pleased that you've managed to find the solution. It looks as though the developers had it in hand after all.

Please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so that others with the same problem can find it.

---

### Post by oldfred on 2013-01-07
@   	aviramof
Is your install of Windows 8, your own install in MBR partitioning?

 The issue with wubi and Windows 8 is that pre-installed copies of Windows 8 are UEFI and UEFI uses gpt partitions. It is that wubi does not work with gpt partitions.

---

### Post by aviramof on 2013-01-07
Everything is all right for now thanks for all your help.

---

### Post by Calinou on 2013-01-07
> **aviramof said:**
> 
on my brand new expensive computer with windows 8 pro so I really don't 

Next time be smart -- install Ubuntu directly, don't buy WIndows which is useless today.

---

### Post by Paddy Landau on 2013-01-08
> **Calinou said:**
> Next time be smart -- install Ubuntu directly, don't buy WIndows which is useless today.
Calinou, that's an interesting viewpoint but not helpful to the OP, who wants to keep (and, presumably, use) his Windows installation.

---

### Post by aviramof on 2013-01-08
> **Calinou said:**
> Next time be smart -- install Ubuntu directly, don't buy WIndows which is useless today.
 
Who buys windows?):P
 
 
And Ubuntu is a nice OS but not so usable and usefull in the end because I can't really install anything on it not games not heavy famous softwares and not new windows "anadroid style" applications.

---

### Post by Paddy Landau on 2013-01-08
> **aviramof said:**
> I can't really install anything on it not games not heavy famous softwares and not new windows "anadroid style" applications.
If you are talking games, for the time being Windows is the platform to use. For office use, Linux tends to be excellent. For graphics, people usually want Mac. For smartphones, of course, Linux (Android) is the big one.

Steam has arrived on Linux, albeit still in Beta, so it won't be long before some great games are available on Linux.

---

### Post by aviramof on 2013-01-09
For the time being I still have problems with auto arrange on Linux on desktop not to 
mention the automatic log off when I try to use firefox or Ubuntu tweak so
I seriously doubts that Ubuntu Linux or any other Linux edition would ever 
be as usefull and usable as windows 7/8 and beyond.
 
For the time being all I hear are exuses from Ubuntu developers that they have problems developing there own operating system.
 
and I can't even find an option or an addond in pidgin to start automaticly with windows or with Ubuntu via the software itself 
so I have to use other ways to do it.
 
and according to my experience this something that is very basic on 95 percent of other windows softwares that I ever used before.
 
So basically Ubuntu have many problems and windows virtually none so I don't see my self use Ubuntu full time for the near future.

---

### Post by Paddy Landau on 2013-01-09
Aviramof, you may need to start separate threads for your problems, but I'll briefly discuss them here.

> **aviramof said:**
> For the time being I still have problems with auto arrange on Linux on desktop
I don't know what you mean by that, sorry.

> **aviramof said:**
> the automatic log off when I try to use firefox or Ubuntu tweak
Start a new thread. You obviously have some problem that needs fixing. This is neither normal nor expected. It is possible that you have a driver problem. It is also possible that a native installation of Ubuntu (not WUBI) would fix this — have you tried a Live CD? A Live CD will let you test these things without changing your computer at all. If it works in a Live CD, it will work in a native installation.

> **aviramof said:**
> so I seriously doubts that Ubuntu Linux or any other Linux edition would ever be as usefull and usable as windows 7/8 and beyond.
Well, you're basing that comment on a couple of odd problems that you have while using WUBI, which is not recommended. In fact, Linux has shown itself to be extremely useful, with entire government departments, police departments, and large corporations changing over to Ubuntu or Red Hat.
 
> **aviramof said:**
> or the time being all I hear are exuses from Ubuntu developers that they have problems developing there own operating system.
I haven't heard those excuses, and if you've heard them, I'd like to know where. Do you know that there is a formal place in which to report bugs?
 
> **aviramof said:**
> I can't even find an option or an addond in pidgin to start automaticly with windows or with Ubuntu via the software itself
Well, that's a problem to bring up with Pidgin, not with Windows or Linux. But did you know that Pidgin is built into Ubuntu and automatically started? Look at the top right-hand corner where the envelope symbol is. It is better in 12.10 than in 12.04, but you can add on-line accounts, incorporated into Ubuntu.

> **aviramof said:**
> So basically Ubuntu have many problems and windows virtually none so I don't see my self use Ubuntu full time for the near future.
Ubuntu has problems for you; that's OK, just use Windows. If you want to solve your problems, do raise new threads, but I'd really recommend that you move away from WUBI. Think of it the other way: imagine running Windows under Ubuntu (you can do that, incidentally, using Wine and PlayOnLinux) — the problems are immense, far greater than running Ubuntu under Windows.

But if you're happy with Windows, I suggest that you just stick with it.

Please don't judge Ubuntu by a couple of problems in WUBI. It needs to be judged by the same standards as any other operating system: running on appropriate hardware in a native installation, just as Windows and Mac are. (If you compare like-to-like, i.e. Ubuntu running under Windows to Windows running under Ubuntu, you'll see that Ubuntu comes out significantly better.

---

### Post by aviramof on 2013-01-09
1.there is no auto arrange on desktop meaning icons often piles up one on top of the other and you need to do arrange by name manually.
 
2.i don't believe I have a driver problem.
 
3.have you seen my beans? there was a time that have invested nuemerus hours here trying to find solutions to all Ubuntu problems but with not much luck and I did not used wubi at that time and I have reported bugs before check your bugs site for my nickname.
 
basically I am not a new user to Ubuntu and other Linux releases so I still don't belive that the problems that I have encountered in the past and reported will ever be fixed or at least not in the next 10 years:)
 
[http://ubuntuforums.org/search.php?searchid=88824050](http://ubuntuforums.org/search.php?searchid=88824050)

---

### Post by Paddy Landau on 2013-01-09
OK, it seems that you have been unfortunate in your experience.

I think that you may be happier using Windows.

When the time comes to purchase another computer, if you still want to use Ubuntu, get one that has been certified for Ubuntu, and then you won't have all these problems. (But stay away from WUBI.)

Until then, good luck!

---

### Post by aviramof on 2013-01-10
Yeah well with the computer I currently have that might take about 20 years:):):)
 
I hope it would be enaf time for Ubuntu developers to fix all 
the bugs in there operating system):P
 
and good luck to you too:)

---

### Post by Paddy Landau on 2013-01-10
> **aviramof said:**
> Yeah well with the computer I currently have that might take about 20 years:):):)
LOL, you'll have an [Ubuntu Phone]("http://www.ubuntu.com/devices/phone") before then!
 
> **aviramof said:**
>  I hope it would be enaf time for Ubuntu developers to fix all the bugs in there operating system):P
Wouldn't that be nice! But no modern operating system on earth has all the bugs fixed.
 
> **aviramof said:**
> and good luck to you too:)
:)

---

