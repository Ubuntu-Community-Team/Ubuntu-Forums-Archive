---
title: "Booting from an empty partion, require help"
date: 2008-01-19
forum: General Help
---

### Post by Smush on 2008-01-19
[SIZE="2"][SIZE="3"]Hi I have Windows XP as my main operating system but wanting to try Ubuntu I got my self Partition Magic 8.0 and made a partition for it using their "Install another operating system" wizard, except it has gone wrong (I am currently on the internet via live CD) what I did was in the partition magic there is a tool called boot manager or something similar and it came up in a windows-like command prompt asking which partition to boot from so I selected the Linux one thinking it will now let me install Ubuntu on it but I was terribly wrong because the partition is empty it is not booting anything. I just looked at the install wizard on this live CD and in the manual partition step it shows all current partitions. If i delete the empty linux partition will I be able to get back to windows? Or are there any other solutions?

I have 4 partitions so far:
1 = Windows operating system files
2 = all my data
3 = the linux swap partition that partition magic asked me to create
4 = the space I partitioned with the intention of putting Ubuntu on

EDIT: I'm not abandoning ubuntu just want to get back to default desktop so I can give it another go 
Thank you[/SIZE][/SIZE]

---

### Post by erginemr on 2008-01-19
Hi,

If you have Windows XP install CD, you can recover Windows bootloader by using the XP Install CD, boot into recovery mode and use the command: "fixmbr" from the recovery console.

You should search google for "fixmbr" first, get your Windows back, and when everything is back in order, use your Ubuntu Live CD to install Linux into the newly created partition. 

But be careful with the partitioning phase of the Ubuntu Installation. You should manually select your new Linux drives and indicate the mount points as:

* Main Linux Drive -> format it to "ext3" file system -> mount point as "/" which means the linux root.

* Swap partition -> format it to "swap" file system -> mount point as "swap" which means RAM to hard disk memory swap space.

Good Luck!

---

### Post by Smush on 2008-01-19
Thanks so much for the reply but I tried fixmbr already before posting and it says successful I type exit into the console, PC reboots and I get the same message as before Error Loading or something like that any ideas on what I do next?

Thanks again.

---

### Post by databoy2k on 2008-01-19
What error is Windows giving you exactly? Is it looking for a file that cannot be found?
--Databoy2k

---

### Post by mister_pink on 2008-01-19
If its trying to boot from an empty partion then I suggest you put something on that partion to boot! You're on the live CD, so click install! I imagine ubuntu will set things up right for you then

---

### Post by Smush on 2008-01-19
The message I get when I boot up PC is "Error loading operating system"

---

### Post by erginemr on 2008-01-19
> **Smush said:**
> Thanks so much for the reply but I tried fixmbr already before posting and it says successful I type exit into the console, PC reboots and I get the same message as before Error Loading or something like that any ideas on what I do next?

Thanks again.

I assume a similar recovery console command "fixboot" didn't work, either.

EDIT: Here is a very similar problem, which is not very promising:
[http://forums.fedoraforum.org/archive/index.php/t-91958.html](http://forums.fedoraforum.org/archive/index.php/t-91958.html)

---

### Post by Smush on 2008-01-19
well fixmbr must work because it says "successful" but fixboot doesnt do anything infact it brings up a message saying it couldn't do it

---

### Post by erginemr on 2008-01-19
Unfortunately, the problem seems to be more severe than that. Check out the link in my latest post.

For the details of fixboot & fixmbr: 
[http://pcsupport.about.com/od/termsf/p/fixboot.htm](http://pcsupport.about.com/od/termsf/p/fixboot.htm)
[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)

Also can you please post the output of:
```
sudo fdisk -l
```
from the Live CD environment?

---

### Post by databoy2k on 2008-01-19
You might be in need of an operating system reinstall. There might be a file that's disappeared or something bizarre like that. You won't have to reformat, just go into the windows setup, select to set up windows, and allow it to try to repair... You'll lose updates/settings, but your files will be intact... 
Sorry if i'm giving up too easily, but that was the solution I was just forced to do the other day...
--Databoy2k

---

### Post by Smush on 2008-01-19
So the only way for me to get to windows is to reinstall it? and all my personal files like word documents and the like will remain on my hard drive?

Could someone please shed some more light on how to do this I'm a little confused

Thanks

---

### Post by erginemr on 2008-01-19
No. What databoy2k suggests is to feign a reinstall but have Windows Installer understand that there is already an installed system. So, in the end, the installer will try to repair your active installation.

Meanwhile, could you please post the outcome of 
```
sudo fdisk -l
```
from the Live CD environment?

EDIT: On a side note, can you see your personal files in Windows partition within the Live CD environment?

---

### Post by Smush on 2008-01-19
Wow yes I can see my files didn't expect that maybe there is some light at the end of the tunnel :)

And I dont want to use fdisk, it will format my drive :(

---

### Post by mister_pink on 2008-01-19
fdisk -l (thats an L) lists info about your disks. its safe- but its good to ask. Do "man fdisk" to see the manual that will tell you what the -l does. You can do this for most commands youre not sure about.

---

### Post by GavinZac on 2008-01-19
> **Smush said:**
> Wow yes I can see my files didn't expect that maybe there is some light at the end of the tunnel :)

And I dont want to use fdisk, it will format my drive :(

as long as you don't tell it which drive to format, it wont format a drive.

fdisk -l

just lists the partitions on your computer. Well done for not just blindly entering commands though, its good to know what you are doing.

---

### Post by erginemr on 2008-01-19
Don't worry. That is not the same fdisk as in Windows. The command "sudo fdisk -l" (with lowercase L) as run from the Live CD will just show the current condition of your partitions, so that we shall understand whether your partition table is OK or not. Check out the link:

[http://forums.fedoraforum.org/archive/index.php/t-91958.html](http://forums.fedoraforum.org/archive/index.php/t-91958.html)

where Partition Magic apparently corrupted the partition table of the problem owner's machine.

---

### Post by GavinZac on 2008-01-19
Partition Magic's "Magic" isn't all that wonderful... in future, use gparted :)

---

### Post by Smush on 2008-01-19
Disk /dev/sda: 500.1 GB, 500107862016 bytes
102 heads, 51 sectors/track, 187768 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             196        6498    16394077+  17  Hidden HPFS/NTFS
/dev/sda2            6499      167295   418232997    f  W95 Ext'd (LBA)
/dev/sda3   *      167296      187768    53250273   83  Linux
/dev/sda4               1         195      507169+  82  Linux swap / Solaris
/dev/sda5            6499      167295   418232971+   7  HPFS/NTFS

Partition table entries are not in disk order

*please say its good* :neutral:

---

### Post by erginemr on 2008-01-19
I believe your partition table is OK. The asterisk (*) indicates that the active partition is /dev/sda3, your empty Linux partition. You just need to figure out a way to activate the first partition, which is not my forte. So, any suggestions from other forum users are welcome.

P.S. Just to be on the safe side, I believe it is time for you to back up your important files under Windows, to say, a pen drive.

---

### Post by Smush on 2008-01-19
Heh I just need to figure out how to fit 25GB on to a 2GB USB Pen :lolflag:

---

### Post by GavinZac on 2008-01-19
> **Smush said:**
> Heh I just need to figure out how to fit 25GB on to a 2GB USB Pen :lolflag:

:D you could try gzip'ing them but that would be very optimistic! :D have you got another drive? maybe even DVDs you could burn to?

---

### Post by Smush on 2008-01-19
Probably going to be disks. Quite a few for that matter 4.7GB each DVD stores

So just waiting for someone to help me get back to my Windows partition :-s

---

### Post by erginemr on 2008-01-19
OK, try this:

Run GParted from Main Menu -> System -> Administration.
Find the graphical representation of the partition /dev/sda1.
Right click on it, select manage flags.
Uncheck Hidden and check Boot.
Also make sure that for /dev/sda3, Boot has been unchecked.
Rerun your system w/o Live CD to see if there is any improvement.

Good Luck...

P.S. If you have a spare CD-RW driver (other than the CD/DVD driver where you have been running the Live CD, download the GParted Live CD from: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) and burn it to a CD. This is because the version of GParted from Ubuntu Live CD is somewhat crippled and is missing some functionality. With the a/m GParted CD, you may also check and fix NTFS file systems and partitions.

---

### Post by Smush on 2008-01-20
Ok sorry for the delay, was late and needed sleep :). Anyway I have had a look in System --> Administration and Gparted isn't in the list does it need installing. Also do you still recommend I back up the files I want or is this process safe? 

Thanks

---

### Post by torgrot on 2008-01-20
I think it is actually called Partition Editor so
Administration-> System-> Partition Editor

torgrot

---

### Post by Smush on 2008-01-20
It's Gnome Partition Editor on here. And as mentioned will i still need to back up my data? Because there's quite a bit?

Thanks

---

### Post by torgrot on 2008-01-20
It is always safest to back up things, however if you only change the fllags as mentioned above you should be ok.  Just don't change anything else.

torgrot

---

### Post by Smush on 2008-01-20
Ok, see what I can do. I also have a Linux swap partition that Partition Magic placed on my hard drive before my other partitions do I need worry about that yet?

---

### Post by torgrot on 2008-01-20
To just get back to booting windows no.

torgrot

---

### Post by Smush on 2008-01-20
Horah, Back on windows... well in some ways thats bad :lolflag: 

Took the risk and didn't back up and all worked out.

need to find out how I can get Ubuntu on to the partition I created with partition magic, I will scan the forums first and post a new relevant thread if I need assistance.

All that's left to do for now is give a big thanks to all you guys :)

Edit: Just so I know will I need to delete the swap and or the Linux partition I made originally?

---

### Post by torgrot on 2008-01-20
You should be able to use them with the Ubuntu install.

torgrot

---

### Post by erginemr on 2008-01-20
Well, we are very glad that you solved your problem. Now, you can go for the installation of Ubuntu and use your pre-made partitions for that purpose as togrot said above. 

As the final advices before the actual installation (if you didn't start, that is), I will copy my two posts here from another thread:

> **erginemr said:**
> Hello Matt & Welcome to Ubuntu,

To begin with, you should read the following graphical installation guide thoroughly:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

> **erginemr said:**
> And my humble avdices to you meanwhile are:

- Be extra careful not to overwrite to your Vista partition. It is very easy to be duped by the Ubuntu installer letting it decide on how to partition the hard drives, wiping Windows altogether, resulting in the end with a Linux only system. And there are quite a few sad stories in the forum on this subject. Once you get past the partitioning part, the rest of the installation is piece of cake.

- Before the actual installation, make sure that all your major and peripheral hardware are recognized in Ubuntu Live CD.

- Avoid making radical decisions at this stage. Do not wipe your Windows, let Ubuntu installer work in dual boot mode. Dual boot for some time, all the while learning the ins and outs of your shiny Linux system. Many things can happen, Linux might not work with some of your essential hardware, you might not like it (although I am sure you will love it) and maight want to go back to Windows, you may want to play Windows only games or run Windows only commercial software. So, I would suggest you to have patience and dual boot for some time.

EDIT:

- Due to the Free Software philosophy of Ubuntu Linux, you will not have Flash web pages, mp3 and DVD movie playback support out 
of the box. Do not bother this. It is very easy to add them later on. There are easy to follow guides on the net. Or ask here and we shall do our best to guide you on this.

- Make sure that your network/internet works from within Live CD. Ubuntu without Internet is like a tree without leaves.

- Linux goes along well with NVIDIA cards but is known to have some issues with ATI graphics cards. So, if you have an ATI card, make sure that it will work (Google and Ubuntu Forum search is your friend). Otherwise, you will not be able to use those fancy desktop effects.

---

