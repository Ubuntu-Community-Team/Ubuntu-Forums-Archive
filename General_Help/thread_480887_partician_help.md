---
title: "partician help?"
date: 2007-06-21
forum: General Help
---

### Post by nate22 on 2007-06-21
ok so ive found out that best fay to some hat foolproof your self is to partician you hard drive. this part im good at 

i want to be able to asure my self that most of my programs will work on ubuntu b4 i make the complete switch over to it..which i wana do ASAP and join the many ubuntu users


before i even start to partician i have some question to ask


numero UNO and my BIGGEST one:
WILL my files be deleted in the process? 

2- if so any way to prevent that other than saving em all into a cd drive or sumthin? i have some 7gb-8gb files (games)

3- would it be possible to buy a external hardrive and have ubuntu run on it?



k thnx in advance

---

### Post by mikewhatever on 2007-06-21
Every partition you format will loose all data on it. I do not know if you are planning to format the hdd, so can't tell whether you'll loose your files. In my case, I've only resized the existing Windows partition and created the ones for Ubuntu, loosing nothing at all. Here is a good guide 
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

Yes, you can run Ubuntu from an external hdd.

---

### Post by nate22 on 2007-06-22
wut do you think is my better option?

by a hdd and run ubuntu on that OR buy a new computer to run ubuntu?

---

### Post by mikewhatever on 2007-06-22
Buying a new computer to run Ubuntu sounds very unjustified. Why would you consider that? You can have Ubuntu installed on the same hdd with Windows, provided there is enough space, or on the external hdd.
The guide in my post above shows the first option. Have you looked at it?

---

### Post by nate22 on 2007-06-22
well i have alot and i do mean ALOT of valuable files that i need
WOW
guild wars 
unreal tournament
antrix

are just a few

and most of those files are 8gb+

i would be real happy to just install ubuntu altogether..but idk if these programs would work on em

next option is to partician...which i heard deletes the files:(

---

### Post by theonlyalterego on 2007-06-22
If you are considering switching from a Windows Gaming environment to a Linux Gaming  environment you should be aware there are considerable differences. Many of the games you mentioned: WOW, unreal tournament you'll have to see if there's a linux client. You most likely won't be able to install them the same as you did on windows.

linky -> [How-to for World of Warcraft on Ubuntu]("https://help.ubuntu.com/community/WorldofWarcraft")

linky -> [Unreal Tournament 2004 on Ubuntu]("https://help.ubuntu.com/community/Games/Native/UnrealTournament2004?highlight=%28Tournament%29%7C%28Unreal%29")

There are a number of how-to's on the web about installing wine to run windows games, you should look into these before making your switch.

EDIT: If you want to switch to a 100% ubuntu enviroment, or a dual boot I would consider one of two options (these options assume you cannot resize the existing windows disk, or don't have enough space for ubuntu and windows):
Option 1:
Buy a new hard drive to install ubuntu on, and mount your windows drive as 'additional storage'. If I were to do this I'd get a decent size hard disk like 100gb-250gb in case I wanted to move it to a different pc later. This way you don't lose your existing data, and can run a dual boot similar to this example:
linky -> [dual boot ubuntu and xp on two drives]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=%28dual%29%7C%28boot%29%7C%28windows%29%7C%28ubuntu%29%7C%28and%29")

Option 2:
Buy a small hard disk, say around 20-30gb and install a dual boot of windows and ubuntu on the new disk. Then mount your existing HDD as storage, and remove windows from it. This way you're booting from a 'clean' disk with only your OS stuff on it, and you can store stuff on the windows disk.


I'm sure some more experienced people will chime in with better ideas, but that's my ¢2

---

### Post by bigboy_pdb on 2007-06-22
If you've repartitioned your hard drive when installing Windows then you shouldn't have too many problems with getting used to creating and deleting partitions using the software on the Ubuntu Live CD. However, I'd recommend that you read up on setting up partitions in Ubuntu (or for Linux in general) especially if you intend on manually setting up the sizes of partitions for root, tmp, home, usr, & var yourself.

For some information on partitions you can read:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[http://tldp.org/HOWTO/Partition/](http://tldp.org/HOWTO/Partition/)

To answer your questions:

1) Will my files be deleted?

The simplest response to this is:
If you delete/reformat a partition, your files will be gone.

Although technically, the information for your files will not be gone until those areas of the hard drive disk are overwritten, but without a file index to show how that data should be interpreted you cannot do much with it. However, you can use a recovery program to get information back if you don't write over it (although to be safe you should assume that this might not be an option).

2)  Can I keep my files using some method other than backing them up?

Yes.

You can buy another internal hard drive to install Linux on. You can either install the hard drive into your computer yourself or you can get someone else to do it, but I would recommend setting your first hard drive (which has Windows on it) as the master and setting the second one which will have Linux as the slave. If reinstalling all of your Windows software would be a tedious task or if you aren't going to back up your Windows files (for some unknown reason) then I'd recommend this option.

Also, there are partitioning programs that allow you to resize your partitions without losing the data on the partitions. I know that 'Symantec's' 'Parition Magic' does this, though it's proprietary software, meaning you'd have to pay for it. I'm not certain as to which other programs that are free alternatives do this well. Here is a list and perhaps somebody else can post free alternative to 'Partition Magic':
[http://en.wikipedia.org/wiki/List_of_partition_utilities](http://en.wikipedia.org/wiki/List_of_partition_utilities)

Although, I think you should back up the files that you want to keep regardless of what approach you take in the end. It's always a good idea to make backups at any point when you're going to make major or significant changes to your computer.

3) Can I run Ubuntu from an external hard drive?

I was considering doing this myself, but I don't think this is a good idea because most of the external hard drives seem to get hot pretty quickly due to their enclosures.

I've read some information on it (although I can't find it now) so I'll state what I can remember. You are able to install Ubuntu to the hard drive by booting using the Live CD and then connecting the hard drive and installing Linux to the device and partition where the hard drive is present (from what I read, it is supposed to show up in the menu). In other words, you use the regular installation process. However, in order to boot Ubuntu from the hard drive when the computer starts up, you'll need to change some of the files on the hard drive (and I cannot remember which ones they are).

-----

What I would recommend doing is the following:

Try the Ubuntu Live CD to see how many of your hardware devices (such as sound card, graphics card, networking hardware, printers, scanners, and other etceteras) are detected.

Buy an external hard drive and back up everything that you want on it. The advantage to this is that you can use it to regularly back up your files and you'll worry less about losing your files if you only plug in and/or turn on your hard drive when you need to copy something to your computer or copy something to the hard drive.

Either, do one of the things that I mentioned for 2) or delete the Windows partition (if there's no available space for Linux) and partition the disk so there's space for both Window and  Linux, and install both of them on separate partitions on the same hard disk.

---

### Post by bigboy_pdb on 2007-06-22
I forgot to mention that if you like playing games, the support for games that were released for Windows under Linux isn't too great.

For the Windows programs that you want to run in Linux, you could always try running a program like WINE or another program for running Windows software in Linux. Generally, expect that some (or a good amount) of your Windows software won't run in Linux (depending on what program you use to run it). You'll be able to find open source alternatives for some of it  that will be close enough to the original software with respect to general functionality (meaning most of the important things that you'll need to have done can be done) but for others you either won't be able to find something that is as close as you'll want it to be or you might not find anything similar. There are some people that will agree with me on these issues and others that will say I'm wrong. Whether or not you agree is a matter of perception and is dependent on what you define as being close enough to your programs. 

I'm not saying this to deter you from using Linux. I know that since birth you've been a long time Windows user (because you mentioned this in one of your other posts) and I too have been a long time Windows user. I personally prefer Linux to Windows. However, it's important that you realize that your experience with Linux won't be like using Windows. That's why if you're attempting to make the move to Linux. It's a good idea to have a dual boot system (a system that boots both Linux and Windows). This way you don't regret your decision and you can appreciate what both operating systems can offer you. If (in time) you really like using Linux, you might even stop using Windows.

By the way, welcome to the community.

---

