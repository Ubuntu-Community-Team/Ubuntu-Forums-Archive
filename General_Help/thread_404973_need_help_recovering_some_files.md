---
title: "need help recovering some files"
date: 2007-04-09
forum: General Help
---

### Post by MichaëlVD on 2007-04-09
The situation: 250GB harddrive, of which about 116 is used by OS X. The OS X disk utility also sees a 5GB linux swap partition. Everything else (= my Ubuntu files) seem to be gone.

However, using a program called 'testdisk', I was able to browse the directories of my Ubuntu install. I hope this means that there is a way to recover those files. The log of the testdisk program is attached to this message.

I can also mount /dev/sda3 with a live cd. However, the /home directory of that partition only contains an /ubuntu directory, and not the /michael directory that I need. 

You can do me a huge favor by helping me with this. I've been in this situation for two months now, and I don't see a way out. Thanks a lot!

---

### Post by Herman on 2007-04-10
> However, using a program called 'testdisk', I was able to browse the directories of my Ubuntu install. I hope this means that there is a way to recover those files. The log of the testdisk program is attached to this message.
Hello MichaëlVD, that should mean you can recover your operating system along with its files.
What do you think might have caused this partition to disappear like this, or what do you think the main problem is?
 
When you are running the Ubuntu Live CD, what is the output from 'sudo fdisk -l' please? ```
sudo fdisk -l
```

---

### Post by MichaëlVD on 2007-04-10
fdisk -l gives:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2   *          26       15169   121634816   af  Unknown
/dev/sda3           15169       29777   117343750+  ef  EFI (FAT-12/16/32)
/dev/sda4           29777       30402     5015181   82  Linux swap / Solaris
```

The cause of the problem is probably that the setup I used to have was to complicated for me to understand: I used rEFIT to be able to boot either Ubuntu or Mac OSX, but at some point (maybe after an upgrade, I don't remember), this did not work anymore, and instead of the usual pinguin, I saw a generic icon in the rEFIT boot screen. I have not been able to access that partition since.

Thanks for your help

---

### Post by Herman on 2007-04-11
Well MichaëlVD, 
TestDisk is great software. I used it recently to recover some partitions and it worked well for me. I found I just needed a little practice to get used to using TestDisk first. An old hard disk is ideal for practicing on before using testDisk on the real rescue mission.

Your fdisk output looked quite unusual to me at first. 
You have a very small partition to begin with, sda1 is about 0.2 GB 'EFI GPT', [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Then you have sda2, 125 GB or so according to my calculations I presume that's your OSx partition.

sda3 will be your Linux partition, that looks like about 120 GB to me, but why does fdisk seem to see it as a FAT file system, not ext3?  :confused:

Then you have your swap area, which does look like 5 GB. It doesn't really matter, but that's far more then you probably need for a swap area. ! GB would be plenty.

Unfortunately I don't know what advice I can give you. I'm not familiar with EFI or Mac or OSx stuff at all. Here is a link to the Official Ubuntu Wiki guide to installing Ubuntu in a MacBook in case that has any information in it that might be useful.  _[how to install Ubuntu 6.10 "Edgy Eft" on a MacBook]("https://wiki.ubuntu.com/MacBook")_
It looks like they use something called '[Boot Camp]("http://www.apple.com/macosx/bootcamp/publicbeta.html")' to partition the drives and then you install Ubuntu and select 'Windows' to boot Ubuntu? I wonder why that could be? Does Grub see Ubuntu as a Windows OS when it's installed in a Mac? How bizarre! :confused: I wonder if there's any connection between that strange peculiarity and the way fdisk shows your ext3 filesystem as FAT-12/16/32?  I hate to disappoint you, but I think I had better leave this to someone else. I don't want to give you bad information and I'm realizing this could be a lot more complicated than I first thought.

I don't think you need TestDisk though, because your partition is showing in fdisk, so I don't think it's a partition table problem. Your partition is there alright. It seems to me to look like a file system problem of some kind. 
Another thing that's weird is the way you say you mounted the filesystem in the live cd but you found the /home directory with a username directory named /ubuntu. Did you mount ubuntu in /media or in /mnt in the livecd? And if so did you access it through /media or /mnt? I can only image a /home/username directory named /ubuntu as being the /home/usernam directory of the live cd rather than thehard disk installed /home/username (michael) directory. Hmmm. :confused: Lot of things here don't make any sense to me.

If this was a normal installation I would try to see what's wrong with the filesystem with Linux commands like sudo dumpe2fs -h /dev/sda3. I guess you could try that and se what we can find out anyway, that won't hurt anything and it might help, you never know, ```
sudo dumpe2fs -h /dev/sda3
``` If you could post that output here please it might help someone help you, I'm not sure. Well we can keep trying I guess, and hope it turns out to be something relatively simple and easy to fix. 

That's all for now, Regards Herman

---

### Post by MichaëlVD on 2007-04-11
Progress! I mounted the partition I need using the live cd. Apparently, the difference between /mnt and /media is crucial. I think we better forget about all this complicated stuff, and just find a way for me to recover the data that I can now access... I suppose it is not possible to burn cds (or dvds) when using the live cd? I do have 2 GB of ram, so that may help.

At least now I'm sure that everything is still there, thanks!

---

### Post by Herman on 2007-04-11
Hey, that is progress! :D Wonderful!
If you can 'see' all your files now then that means there's probably nothing wrong with the fiesystems either, or at least nothing too serious wrong with it. 
Okay, now you only have a booting problem, which is something I'm better at helping with. 
You can probably even get your Ubuntu to boot now, with a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") usb, cd or floppy. [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") (documentation). Since you say this problem started right after an update, possibly your menu.lst file has a glitch in it so it's not booting the kernel, have you had any error messages when you tried to boot up? If so, can you tell me what error messages you get when you try to boot this time pplease?[LIST=1]
[*]boot your SGD floppy disk, USB disk or CD-ROM
[*]English Super Grub Disk
[*]Gnu/Linux
[*]Boot Gnu/Linux Directly[/LIST]Okay, you can try that,  but it's still a good idea to make a backup of all those files too. The easiest way is to get a usb external hard drive from somewhere. I find it cheaper and best to buy the USB2 empty hard drive case and then put any old hard drive inside it myself, and partition it with [GParted -- LiveCD]("http://gparted.sourceforge.net/")
 If you buy one with the hard dirve already  in it they are usually already partitiioned for dumb  Windows users  and they have some extra sofware that Linux users don't need so they charge double the price at least.  An external USB2 drive is the fastest and simplest, and it's a good investment in the long run. 
The  next option is if you have another computer with some hard drive space to spare, even if a friend who can help you has a laptop and can bring it to visit you. You can connect the two with an ethernet crossover cable or two ordinary ethernet cables and a hub or a router. You can use any kind of networking you like, but I like [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm")ing it's probably the simplest and in my opinion it's also the best.
If you find that the ony wway to rescue your files is to copy them to CDs or DVDs, and you have 2 GB of RAM (over 800 MB), and you have a Knoppix disk, you can get Knoppix to load into the RAM and run in the RAM. Look at the boot options. Then you can eject the Knoppix disk to free up your CD/DVD drive and use it for burning data CDs or DVDs. 
Puppy Linux is an even easier distro to use for doing that. Puppy Linux is only a small operating system that will load into even a moderate RAM, and can mount your filesystem and make DVDs or CDs for you with your files on them.

If you tell me what you decide to do and if you need a little more exact help, just let me know.
Regards, Herman :D

---

