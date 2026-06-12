---
title: "Kernel panic: Attempted to kill init!"
date: 2004-11-17
forum: General Help
---

### Post by xinelo on 2004-11-17
Hi the list!

I've got the following problem. After having installed Ubuntu in a dual-bootable laptop, checked that everything works fine, configured some features and visited this page and the forums, I've rebooted the system and logged into Windows. 

In windows everything worked more or less fine, as usual. The only thing that didn't work was Partition Magic. Before installing Ubuntu, PM showed hda as a long yellow bar and display an error message (maybe Error 15, but I'm not sure). However, after installing Ubuntu and rebooting in Windows, PM wouldn't start at all (and the ptnmgc.exe -or sth like that- was at 100%, not collapsing the system though). 

That was yesterday. This morning, I rebooted to log into Ubuntu and there began the trouble. Ubuntu's loading process (the black screen with the upgoing white letters ;) says: 
[B][COLOR=Red][COLOR=Navy]
pivot_root: No such file or directory
/sbin/init: 429: Cannot open dev/console: No such file
Kernel panic: Attempted to kill init!
[/COLOR][/COLOR][/B]
of which I only understand "panic" and "kill", so that seems bad. Bad, in fact. 

I've found no answers in this forum or Google ([http://www.google.es/search?hl=es&q=pivot_root+%22%2Fsbin%2Finit%22+429+%22kernel+panic%22+%22attempted+*+kill+init%22&btnG=B%C3%BAsqueda+en+Google&meta=](http://www.google.es/search?hl=es&q=pivot_root+%22%2Fsbin%2Finit%22+429+%22kernel+panic%22+%22attempted+*+kill+init%22&btnG=B%C3%BAsqueda+en+Google&meta=)) but at least I've seen that quite many others have this same problem.

I should also mention that Windows don't boot now either (so I'm getting nervous...). It thinks it over and over and then a blue screen appears that says: 

[COLOR=Blue]*** STOP: 0x0000007B (0xF8955640, 0xC0000034, 0x00000000, x0000000)[/COLOR]

and suggests me to do CHKDSK /K and some other things I can't do without loggin into the system. 

I should also mention, in case it's related (although I don't think so) that lately, when rebooting, a message appeared sometimes that said that the system was too hot and that I should contact DELL with the error #M1004.

My system's characteristics are:
[COLOR=Blue]
DELL Inspiron 8500
Mobile Pentium 4: 2.20 GHz / 1.20 GHz
CPU speed: 1.20 GHz
Level 2 cache: 512 KB
System memory: 512 MB
Video controller: ATI Radeon 9000
Video memory: 32 MB
Panel type: 15.4" wide XVA
Audio controller: Sigmatel 9750[/COLOR]

I've seen quite many people with this problem but with no replies offering a good solution. Has somebody found the solution recently? Should just we wait? Could I sort it out maybe just installing another distribution? I don't dare touch anything just in case I make it worse. Is it serious?

Someone has suggested using some program to repair partitions... but I don't know any. 

Btw, now I'm using Knoppix (blessed may be it).

I'd be really grateful if anyone could help.

Cheers, Manuel

PS It's confusing to see that such a good distribution (excellent, actually) as Ubuntu causes such a trouble.

---

### Post by TravisNewman on 2004-11-17
OK I can tell you from personal experience that when Partition Magic has that yellow bar and gives you errors, it's time to back stuff up, wipe the drive, and start all over. Just to be safe. The partition tables are screwed, basically, and when you partitioned for Ubuntu, it may have made things worse. THEN when you opened Partition Magic again, it may have tried to "fix" some errors, resulting in even more corruption, that may have messed up the partition table on your Ubuntu partition.

In short, if you'd been isntalling Fedora or SuSE, the same thing probably would have happened, and you see people with this problem in all the linux forums. It's not really Ubuntu's fault ;)

If you have more things in Windows that you care about, I'd suggest booting off your Windows CD and using the recovery console to run chkdsk /K.

---

### Post by xinelo on 2004-11-17
[QUOTE=panickedthumb]OK I can tell you from personal experience that when Partition Magic has that yellow bar and gives you errors, it's time to back stuff up, wipe the drive, and start all over. Just to be safe. The partition tables are screwed, basically, and when you partitioned for Ubuntu, it may have made things worse. THEN when you opened Partition Magic again, it may have tried to "fix" some errors, resulting in even more corruption, that may have messed up the partition table on your Ubuntu partition.

In short, if you'd been isntalling Fedora or SuSE, the same thing probably would have happened, and you see people with this problem in all the linux forums. It's not really Ubuntu's fault ;)

If you have more things in Windows that you care about, I'd suggest booting off your Windows CD and using the recovery console to run chkdsk /K.[/QUOTE]
 Thanks a lot, panickedthumb

I hadn't thought about rebooting from the Windows CD, I'll try that. Otherwise, your explanation is quite convincing, so I might reinstall everything... :- (((((

Only may I ask, do you or anyone know why this could have happened? 

Thanks again. Fingers and toes crossed... 
xinelo

---

### Post by TravisNewman on 2004-11-17
I've never known why it happened, Its only happened a couple times, but it has always happened when I'm repartitioning a lot.

I also think that Partition Magic and the Linux fdisk use somewhat different methods that don't always agree with each other, because it's also only happened when I've used both concurrently.

The other day I booted off of a Partition Magic rescue disk to resize my ext3 partition and delete my Windows partition (MS Free baby!) and when I rebooted, grub flat out didn't work, so I booted off of a Gentoo livecd and checked out the partitions, and I had an ext3 partition as hda1, which I wanted. The only thing is, it had all the files from my windows partition on it, and none of my files from Linux!! So my suggestion is to pretty much never use Partition Magic when changing any Linux filesystem. It seems to work fine for windows partitions, but in my experience, not Linux. I've heard good things about Acronis Partition Expert, but I've never tried it personally.

---

### Post by jdong on 2004-11-17
It sounds like you lost all files in /dev.

Boot up from Knoppix, then issue **mount /mnt/hda1; cp -rfvp /dev /mnt/hda1; umount /mnt/hda1** to attempt to salvage!

---

### Post by xinelo on 2004-11-17
Well, this is getting exciting! Thanks for your reply, jdong. 

I've done as you said, but also with hda5 (which is where all my data is / was? :(( ) instead of hda1. 

[B]# mount /mnt/hda1
# cp -rfvp /dev /mnt/hda1
# umount /mnt/hda1[/B]

The result is

[B]root@ttyp0[~#] cd /mnt/hda5 
root@ttyp0[hda5]# ls
System.map-2.6.8.1-3-386  grub                      memtest86+.bin
config-2.6.8.1-3-386      initrd.img-2.6.8.1-3-386  vmlinuz-2.6.8.1-3-386
dev                       lost+found
root@ttyp0[hda5]# cd dev[/B]
(I get an endless list of files/directories, some of which are the **hda** series... 
[B]root@ttyp0[dev]# cd hda5
bash: cd: hda5: Not a directory [/B]

From the Knoqueror file manager, If I click on **hda5**, the message is **You do not have enough permissions to read file:/mnt/hda5/dev/hda5**

I think this is silly of me to be trying to do that, but I don't know what else I could do...

However, now this is somewhat different:
[B]root@ttyp0[hda5]# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/root             3.0M  1.2M  1.8M  39% /
/dev/scd0             690M  690M     0 100% /cdrom
/dev/cloop            1.9G  1.9G     0 100% /KNOPPIX
/ramdisk              396M  7.4M  389M   2% /ramdisk
/dev/hda5              37M   11M   25M  30% /mnt/hda5
/dev/hda1              47M  5.1M   42M  11% /mnt/hda1[/B]

Before there was no hda5 or hda1. Now there they are, the only problem is that hda5 should have 15 GB, not 37MB... 

Btw, I tried to boot from the WIndows XP CD so as to try to repair the partitions or do a CHKDSK, but it wouldn't boot at all. Ugly ugly. 

Please help... And thanks again. 
xinelo

---

### Post by jdong on 2004-11-17
the drive /dev/hda5 seems just to have /boot's files, not /. Are you sure that's your / , not your /boot???

---

### Post by xinelo on 2004-11-17
hI panickedthumb, 

i didn't see your reply before. thanks a lot. 

i agree it might have sth to do with using PM and the fdisk one after the other one. I've been trying to install Gentoo, Mandrake and Ubuntu in two days, so that makes a lot of partitioning (or formatting of already existing partitions).

regarding PM's rescue disks: I haven't tried them, because I've moved recently and left them behind in the other house, far away, so I can't use them. If they could be of any use to recover my data, do you think I could create them in another computer having installed PM in it? Or are they unique to the computer in which PM is installed? Or would they be useless to this effect? 

In the future, I'll try to avoid using PM, as it seems that is the problem. 

Thanks again!
xinelo

[QUOTE=paickedthumb]I've never known why it happened, Its only happened a couple times, but it has always happened when I'm repartitioning a lot.

I also think that Partition Magic and the Linux fdisk use somewhat different methods that don't always agree with each other, because it's also only happened when I've used both concurrently.

The other day I booted off of a Partition Magic rescue disk to resize my ext3 partition and delete my Windows partition (MS Free baby!) and when I rebooted, grub flat out didn't work, so I booted off of a Gentoo livecd and checked out the partitions, and I had an ext3 partition as hda1, which I wanted. The only thing is, it had all the files from my windows partition on it, and none of my files from Linux!! So my suggestion is to pretty much never use Partition Magic when changing any Linux filesystem. It seems to work fine for windows partitions, but in my experience, not Linux. I've heard good things about Acronis Partition Expert, but I've never tried it personally.[/QUOTE]

---

### Post by xinelo on 2004-11-17
[QUOTE=jdong]the drive /dev/hda5 seems just to have /boot's files, not /. Are you sure that's your / , not your /boot???[/QUOTE]
 I thought i had explained this, but I didn't, so here it goes:

hda1: (DELL partition... a few megas)
hda2: NTFS (SO WinXP)
hda3: extended, contains (contained? :_(
__hda5: FAT32 (data, several gigas)
__hda6: boot
__hda7: swap
__hda8: /

So that means taht hda5 had my data (FAT32) but wasn't my / 

But now they're sth like this:

root@ttyp0[hda5]# fdisk -l

Disk /dev/sda: 164.6 GB, 164696556032 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20023   160834716    6  FAT16
Warning: deleting partitions after 60

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           6       48163+  de  Dell Utility
/dev/hda2   *           7        2114    16932510    7  HPFS/NTFS
/dev/hda3            2115        4864    22089375    f  W95 Ext'd (LBA)
/dev/hda5   *        2115        2119       40131   83  Linux
/dev/hda6   *        2115        2119       40131   83  Linux
/dev/hda7   *        2115        2119       40131   83  Linux
/dev/hda8   *        2115        2119       40131   83  Linux
/dev/hda9   *        2115        2119       40131   83  Linux
/dev/hda10  *        2115        2119       40131   83  Linux
/dev/hda11  *        2115        2119       40131   83  Linux
/dev/hda12  *        2115        2119       40131   83  Linux
/dev/hda13  *        2115        2119       40131   83  Linux
/dev/hda14  *        2115        2119       40131   83  Linux
/dev/hda15  *        2115        2119       40131   83  Linux
/dev/hda16  *        2115        2119       40131   83  Linux
/dev/hda17  *        2115        2119       40131   83  Linux
/dev/hda18  *        2115        2119       40131   83  Linux
/dev/hda19  *        2115        2119       40131   83  Linux
/dev/hda20  *        2115        2119       40131   83  Linux
/dev/hda21  *        2115        2119       40131   83  Linux
/dev/hda22  *        2115        2119       40131   83  Linux
/dev/hda23  *        2115        2119       40131   83  Linux
/dev/hda24  *        2115        2119       40131   83  Linux
/dev/hda25  *        2115        2119       40131   83  Linux
/dev/hda26  *        2115        2119       40131   83  Linux
/dev/hda27  *        2115        2119       40131   83  Linux
/dev/hda28  *        2115        2119       40131   83  Linux
/dev/hda29  *        2115        2119       40131   83  Linux
/dev/hda30  *        2115        2119       40131   83  Linux
/dev/hda31  *        2115        2119       40131   83  Linux
/dev/hda32  *        2115        2119       40131   83  Linux
/dev/hda33  *        2115        2119       40131   83  Linux
/dev/hda34  *        2115        2119       40131   83  Linux
/dev/hda35  *        2115        2119       40131   83  Linux
/dev/hda36  *        2115        2119       40131   83  Linux
/dev/hda37  *        2115        2119       40131   83  Linux
/dev/hda38  *        2115        2119       40131   83  Linux
/dev/hda39  *        2115        2119       40131   83  Linux
/dev/hda40  *        2115        2119       40131   83  Linux
/dev/hda41  *        2115        2119       40131   83  Linux
/dev/hda42  *        2115        2119       40131   83  Linux
/dev/hda43  *        2115        2119       40131   83  Linux
/dev/hda44  *        2115        2119       40131   83  Linux
/dev/hda45  *        2115        2119       40131   83  Linux
/dev/hda46  *        2115        2119       40131   83  Linux
/dev/hda47  *        2115        2119       40131   83  Linux
/dev/hda48  *        2115        2119       40131   83  Linux
/dev/hda49  *        2115        2119       40131   83  Linux
/dev/hda50  *        2115        2119       40131   83  Linux
/dev/hda51  *        2115        2119       40131   83  Linux
/dev/hda52  *        2115        2119       40131   83  Linux
/dev/hda53  *        2115        2119       40131   83  Linux
/dev/hda54  *        2115        2119       40131   83  Linux
/dev/hda55  *        2115        2119       40131   83  Linux
/dev/hda56  *        2115        2119       40131   83  Linux
/dev/hda57  *        2115        2119       40131   83  Linux
/dev/hda58  *        2115        2119       40131   83  Linux
/dev/hda59  *        2115        2119       40131   83  Linux
/dev/hda60  *        2115        2119       40131   83  Linux

Any interpretations? Should I bear any hope?

Thanks again, a lot
xinelo

---

### Post by xinelo on 2004-11-17
[QUOTE=jdong]the drive /dev/hda5 seems just to have /boot's files, not /. Are you sure that's your / , not your /boot???[/QUOTE]
 Sorry, jdong

I've just thought there may have been a misunderstanding between us. When you said:

# mount /mnt/hda1
# cp -rfvp /dev /mnt/hda1
# umount /mnt/hda1

did you mean hda1 = / ? If yes, I should try with **hda8** instead of **hda1**? Could I try again? Or is it too late?

---

### Post by TravisNewman on 2004-11-17
Wait, does that thing say you have 60 partitions???? Maybe I missed something, but fdisk -l has never returned anything like that for me.

---

### Post by jdong on 2004-11-17
My steps were how to fix your Linux partition. Use /dev/hda8.


P.s. that fdisk output is _VERY_ concerning... it's physically impossible to have 60 partitions

---

### Post by TravisNewman on 2004-11-17
It also says it's skipping all partitions over 60, so who knows how many partitions it THINKS are there

---

### Post by FLeiXiuS on 2004-11-17
[QUOTE=panickedthumb]It also says it's skipping all partitions over 60, so who knows how many partitions it THINKS are there[/QUOTE]


Very tricky eh, I've had this happen turned out that my motherboard didn't like the distro I installed..So I just booted back into Ubuntu and everything was solved.

---

### Post by xinelo on 2004-11-17
> **FLeiXiuS]Very tricky eh, I've had this happen turned out that my motherboard didn't like the distro I installed..So I just booted back into Ubuntu and everything was solved.[/QUOTE]
 jdong, 

# mount /mnt/hda8
# cp -rfvp /dev /mnt/hda8
cp: overwrite `/mnt/hda8/dev/cloop'?

I don't dare say yes. Should I? 

Btw, could you tell me briefly what that does?

> P.s. that fdisk output is _VERY_ concerning...
This is basically why I am _SO_ concerned  said:**
> ..So I just booted back into Ubuntu and everything was solved.
Well, thanks for your comment, but I remind you that I can't do that at all. If I boot into Ubuntu it says "the kernel is panicking because init nearly got killed" or something like that...

---

### Post by xinelo on 2004-11-18
I'd like to add some new data, just in case it clarifies something so we can all devote our dear neuronal activity to other more important affaires ;)

I've tried to run Ubuntu's installation CD, not that I wanted to reinstall it (I prefer to wait and see if I can save any data) but just to see what showed. Anyway, I can't do anything else apart from booting with Knoppix...

When it gets to the [!!] Disk Partitioning section, this is what it shows:

[COLOR=Navy]IDE1 Master (hda) - 40 GB HITACHI...
scsi1 (0,0,0) (sda) - 164 GB ... (this is my external HD)
.......... # Primary 164 GB fat32 [/COLOR]

See that it jsut shows hda and not the eight partitions that were there before (two primary, one extended and fore logical). It seems as hda is empty. Does this means all partitions are screwed? If yes, does that mean that all data is unrecoverable? 

Thanks a lot again!
xinelo

---

### Post by jdong on 2004-11-18
Under Knoppix when you mount /dev/hda*, can you read what's inside?


If so, I highly recommend that at this point you back everything up! Do you have another system on your network, an external hard drive, DVD/CD's for smaller sets of data, etc?

---

### Post by xinelo on 2004-11-18
[QUOTE=jdong]Under Knoppix when you mount /dev/hda*, can you read what's inside?


If so, I highly recommend that at this point you back everything up! Do you have another system on your network, an external hard drive, DVD/CD's for smaller sets of data, etc?[/QUOTE]
 Hi jdong, 

Answer to the 2nd question: yes, I've got an external HDD. Nearly everything was backed up but not some important files I've worked with lately. 

Answer to the 1st question: I don't know if I can read what's inside. 

Under knoppix, there's already a /mnt/hda5 (that used to be the partition with data, sniff), so I don't need to mount it. **ls /mnt/hda5** outputs nothing, so either I can access it or it's empty. 

So I try and create another partition and mount /dev/hda5 to it, and the result is that I can access what is inside:

[B]# mkdir /mnt/data
# mount /dev/hda5 /mnt/hda5
# ls /mnt/data
System.map-2.6.8.1-3-386  grub/                      memtest86+.bin
config-2.6.8.1-3-386      initrd.img-2.6.8.1-3-386  vmlinuz-2.6.8.1-3-386
dev/                       lost+found/[/B]

and that's the same contents if I create a /mnt/data1 directory and mount, say, /dev/hda8 into it, and I suspect thats the contents of any /dev/hda* partition... 

Any more ideas?
Cheers, Manuel

---

### Post by jdong on 2004-11-18
yeah, that does look pretty bad... Your partition tables are seriously messed.  The only possible fix is to rewrite that partition table. I don't really want to suggest anything at this point; modifying the partition table could lead to permanent loss of data.

Sorry

---

### Post by xinelo on 2004-11-18
[QUOTE=jdong]yeah, that does look pretty bad... Your partition tables are seriously messed.  The only possible fix is to rewrite that partition table. I don't really want to suggest anything at this point; modifying the partition table could lead to permanent loss of data.

Sorry[/QUOTE]
 I've managed to boot from the Partition Magic rescue disks and I get PM's GUI showing the yellow bar and error #3. I can't do anything but reformat (which would erase the data). 

A MS-DOS rescue floppy was useless.

Well, thanks for trying. I appreciate it. I'll wait some days to see if I get any other suggestion before trying to reinstall Linux or format hda with the rescue disks.

:(((((((((((((((((((((
Manuel

---

### Post by xinelo on 2004-11-19
[QUOTE=xinelo]I've managed to boot from the Partition Magic rescue disks and I get PM's GUI showing the yellow bar and error #3. I can't do anything but reformat (which would erase the data). 

A MS-DOS rescue floppy was useless.

Well, thanks for trying. I appreciate it. I'll wait some days to see if I get any other suggestion before trying to reinstall Linux or format hda with the rescue disks.

:(((((((((((((((((((((
Manuel[/QUOTE]
 Hi all, 

I resist to giving up. So I tried another CD live Linux distro, called Famelix 1.0. This distro has a tool called **Testdisk**, which I hadn't seen on the other distros. 

Well, the good thing is that this tool shows the partitions structure just as it was before when everything worked, which might mean that the partitions are still there. And not only that! I can also see the files and directories that I'd like to save (in hda5), but I can't save them, I just can see them (with these tool, that is).

There are another 2 tools, called KDE Information Center and KDiskFree, which show both the structure: partition mnt, auto, cdrom, hd, **hda1** (46,9 MB vfat), hda10, hda11, hda12, hda13, hda14, hda15, hda16, hda17, hda18, hda19, **hda2** (16.1 GB NTFS),  hda20, hda5, hda6, hda7, hda8, hda9, pts, sda1, test and floppy, which all have the same size and fs (36,7 MB and ext3) except the exceptions that I've indicated between parens (only hda2 and hda1).  

I remind that hda1 and hda2 are the windows partitions (DELL and Windows XP's OS). I can actually access, browse and edit the files in these 2 partitions but I can't copy them to my external HD, because it says I (CORRECTION: ) can't  write to it: 

**chmod: changing permissions of "/mnt/sda1/home': Read-only file system** (any suggestions as to how to overcome this will be welcome as I'm also interested in saving some files from hda2)

nor can I burn a CD with K3b, because Famelix Live CD is on the drive and it doesn't come out (at least I don't know how to take it out!). 

---

Some other things that I've tried, although they might be less light-shedding, are:

-Run qtparted /dev/hda: Critical error during ped_disk_new!

-Booting into the Partition Magic's rescue disks. PM shows the message "Partition table error #3 found" (I haven't found relevant info on this error on the internet). After that I am in DOS (A:\>) but I can't move around as my commands do nothing (neither C: nor C:\ nor C:/ nor cd C:*...). 

---

So at least I know the contents of hda1 and hda2 are there. And if those are there, why should hda5's not be? But just for clarification, hda5's contents are still the ones that used to be: 

System.map-2.6.8.1-3-386 grub/ memtest86+.bin
config-2.6.8.1-3-386 initrd.img-2.6.8.1-3-386 vmlinuz-2.6.8.1-3-386
dev/ lost+found/

So it seems that the previous /dev/hda5 (that I used to use) is not the same as current /dev/hda5, so its current contents aren't either my data (neither accessing self-mounted /mnt/hda5 nor creating a new /mnt/data partition and mouting /dev/hda5 to it: **mount /dev/hda5 /mnt/data**

Still with me? Still wanting to help me out? I know you do, I just hope you can. 
Cheers, Manuel

---

### Post by TravisNewman on 2004-11-19
OK you can't get NTFS partitions read/write because the ntfs support in the kernel is pretty poor at the moment. There's a program called Bart's PE builder which basically takes you into a Windows Live CD, if you need to write to an NTFS. You'll need a functioning machine to make it though. In a Linux LiveCD, As long as your external drive isn't NTFS you should be able to back up anything you can mount, whether it's read-only or not.

---

### Post by xinelo on 2004-11-20
[QUOTE=panickedthumb]In a Linux LiveCD, as long as your external drive isn't NTFS you should be able to back up anything you can mount, whether it's read-only or not.[/QUOTE]
 Yes, that's what I thought (my external HDD is vfat), but that's not the case.  I've tried again, see by yourself.

# mount -t vfat /dev/sda1 /mnt/sda1
# ls /mnt/sda1 (to check it's properly mounted)
...
# mount /dev/hda2 /mnt/hda2
# ls /mnt/hda2 (checking again)
# cp /mnt/hda2/directoryx/   /mnt/sda1/
**cp: omitting `directoryx'**
# chmod 777 /mnt/hda2 (just in case it's a problem of permissions)
**chmod: changing permissions of `/mnt/hda2': Read-only file system**

Maybe I should customise more my commands?

Thank you so much for the patience!
cheers, xinelo

---

### Post by TravisNewman on 2004-11-20
you may need to throw some options in, such as user, rw, umask=0000

Try:
mount -t vfat -o user,rw,umask=0000 /dev/sda1 /mnt/sda1

---

### Post by xinelo on 2004-11-20
[QUOTE=panickedthumb]you may need to throw some options in, such as user, rw, umask=0000

Try:
mount -t vfat -o user,rw,umask=0000 /dev/sda1 /mnt/sda1[/QUOTE]
 Thanks a lot, panickedthumb

I tried it again with the options you've suggested, but the outcome is just the same: 

cp: omitting directory `/mnt/hda2/directoryx/' 

:(( 

Thanks for trying. xinelo

---

### Post by xinelo on 2004-11-20
[QUOTE=xinelo]Thanks a lot, panickedthumb

I tried it again with the options you've suggested, but the outcome is just the same: 

cp: omitting directory `/mnt/hda2/directoryx/' 

:(( 

Thanks for trying. xinelo[/QUOTE]
 Well, I'd like to thank everyone for your help. However dark it seemed one day ago, I've managed to sort it out. 

What I've done is make the WIndows hda2 partition bootable. That still didn't sort the problem, still I got a grub error, so I overwrote the MBR. I did this with TestDisk, which finally was also included in Knoppix. It can be downloaded from [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

Now I've got Windows working properly and don't know what happened to the other linux partitions. I'll check it later. Now I can save my data and repartition (not with PM!) to start it over again. 

Thanks again! xinelo

---

### Post by TravisNewman on 2004-11-20
Dude, I'm SO glad you got everthing fixed. Try to find something that will completely zero the drive so that you don't have any partition structure hanging around(even the "empty" partition structure, if it's messed up, can cause problems with new ones in my experience). If you got a floppy or cd with your hard drive, it'll probably contain utilities to do this.

---

