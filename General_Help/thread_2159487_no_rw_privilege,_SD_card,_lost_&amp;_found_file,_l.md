---
title: "no r/w privilege, SD card, lost &amp; found file, live ubuntu, ext4"
date: 2013-07-03
forum: General Help
---

### Post by greatsirkain on 2013-07-03
Yes I've tried the switch on the side haha, even after formatting it over and over again, changing the file system, taking ownership of it - I can't get rid of the lost and found file (when I put write protect on with the switch on the side of the card ubuntu wont even mount the first partition [with the lost & found folder]).

I had previously used startup disk creator to put lubuntu live on it but at boot it just told me to 'insert bootable media then press any key' so I decided to start again.

Just read that linux reserves a % of the drive for use by root as a lost and found file? - (lost & found is over 600mb)
it's partitioned: 
1st: 7gb ext4 for ubuntu live (some folks said not to use ext4 as a boot partition but then others said with it being an sd card it would actually be better? - had used fat32 previously)
2nd: 7gb fat32 for storage 
3rd: swap partition

I'm not used to all this hastle, I usually use a usb stick and things go smoothly (for the most part), reason I want a live sd card is because it's faster than disk + I can still use the dvd drive and I don't want a usb stick hanging out the side of the laptop

---

### Post by tgalati4 on 2013-07-03
First, the "lost&found" is a directory not a file.  Inside "lost&found" will be a bunch of randomly numbered files that represent recovered files and bits and pieces of files that were recovered during a file system check.  It's possible that your SD card is having problems and thus won't mount or boot properly.  The fact that you have 600 MB of files in "lost&found" means you have a lot of files and file fragments during your previous file system check and recovery.

Running any operating system from SD card or USB stick, you run the risk of disk corruption because of the nature of how flash memory is used and how the "wear-leveling" algorithms interfere with the disk access required by the OS.  So although your reasons for using an SD card are sound, the reality is that SD cards are not suited for long-term operating system use.  How long was your system stable before the problems?

---

### Post by greatsirkain on 2013-07-03
the card was brand new, never been used, tried to install lubuntu live on the primary partition, it wouldn't boot so I formatted it and started again, that's when I had the 600mb+ lost & found problem.

I've got a few bootable live usb sticks (the oldest will only boot 1 out of 5 times so I presume it's failing [even then it will only boot from a specific usb port] but it is a good 5 years old and actually an mp3 player)

Edit: This is the usual time I would begrudgingly head downstairs and fire up the naughty box but windows 7 wont even recognise it, by design too - according to the m$ webite.

Edit 2: sudo rmdir  /media/lubuntu/lost+found got rid of it, there was a hidden .999-trash file there too that I deleted & it says there's nothing there at all but it still shows that 600mb+ as being used in properties

---

### Post by varunendra on 2013-07-03
> **greatsirkain said:**
> the card was brand new, never been used, tried to install lubuntu live on the primary partition, it wouldn't boot so I formatted it and started again, that's when I had the 600mb+ lost & found problem.
The "lost & found" directory is not a problem, it is an inherent part of the Linux file-systems (ext2/3/4). It gets created in every partition formatted as ext2/3/4. By default it is owned by root and normal users don't have even read permission to it, so you can't actually determine the space occupied by it. You can change the permission with "chown" command to see what's in and how much space it has occupied. Unless there was a problem and some files were recovered, it'll be empty occupying no additional space.

The 600 MB you noticed must have been the reserved space. It is by default 5% of the partition size, if the partition is ext2/3/4. You can change this %age, for example on partition /dev/sdb1, with -
```
sudo tune2fs -m 0 /dev/sdb1
```
0 is the percentage. For partition that contains the operation system or is bootable one, it is recommended to reserve at least 100 MB or more space to avoid crashes. Even for data partitions, it is recommended to reserve at least 2% or 200 MB to avoid excessive fragmentation.

That being explained, how are you trying to make it live??

As far as I know, it is mandatory to have the partition formatted as FAT or FAT32 if you want to install a "Live" system on it. This is because "syslinux" - the boot loader that boots a live os - is only compatible with FAT/32, it has been designed as such for a good reason.

Also, I think all the tools that create a Live USB specifically look for partitions that are formatted as FAT/32. They won't/can't use a partition if it is formatted as an ext file-system.

By your current partitioning scheme, it seems you are attempting a full installation, which is okay, but will significantly reduce the life of the card.

---

### Post by tgalati4 on 2013-07-03
5% of a 7GB OS partition would be around 350MB of reserved space.  It's possible that there was a write error when initially installing to the SD card.  That is consistent with non-boot behavior.  Reformatting the partition will not fix such an error because it is either a bad memory location or the SD drive controller (electronics) is having a problem with large, sustained writes.

I'm running 12.10 and there are no files in lost+found.  I'm not sure where the reserved disk space is kept, but I can't see it in my lost+found.

---

### Post by varunendra on 2013-07-03
> **tgalati4 said:**
> 5% of a 7GB OS partition would be around 350MB of reserved space.  It's possible that there was a write error when initially installing to the SD card.  That is consistent with non-boot behavior.  Reformatting the partition will not fix such an error because it is either a bad memory location or the SD drive controller (electronics) is having a problem with large, sustained writes.

That's ^ right.

@greatsirkain,
Why are you trying a live system on an ext partition? The swap partition does make some sense, but the rest of the complexity is not worth it. I'd suggest to remove all the partitions (even better - simply re-write a fresh msdos partition table) using gparted and create a single fat32 partition on tha card, as is expected on it. If you have access to a windows machine, you may try formatting the card on it (with fat32 of course) as sometimes it has been reported to make the difference when formatting on Linux doesn't work. If formatting on gparted, make sure to put the "boot" flag on the partition.

If the live system boots by doing this, you may consider shrinking the partition and creating an additional swap partition (although not recommended for a flash media).

As for the mysterious 600+ MB usage, the default file browser may get confused sometimes. Just unplug > re-plug the card, and check the property again. Or show us the output of -
```
df -h
```

---

### Post by greatsirkain on 2013-07-04
I tried the fat32 live version first, when that failed I just wanted to try & make it bootable and have the full OS installed to the ext2 partition, neither would boot on the windows desktop downstairs or this laptop.

 
This laptops hard drive wont boot after I formatted it to get rid of windows 7 and put Ubuntu on it so I formatted it again and just use it as storage (booting from USB).
 

  I looked at the bios of both machines and they looked normal & didn't mention UEFI anywhere but then I noticed bitlocker on the desktop bios so maybe there's some pre UEFI windows TPM voodoo going on (I seem to have lost touch with current computing through using old hardware) which might explain the desktop but the only thing I was unsure of on the laptop bios was 'execute-disable bit' which looks harmless enough, basic anti-virus-y-thingy?

 

 Without me wanting to confuse things further talking about the desktop anymore (SD card's only for use with the laptop anyway) or looking at alternative bootloaders  – I'll redo the partition table then make the single fat32 as varunendra suggested

...Can't redo it with windows because windows refuses to recognise the card and the timer just runs continuoulsy as soon as I plug it in until I remove it - on purpose, another example of microsoft locking out hardware it can't control & taking over things it can (another possibility is that the card reader on the desktop is just too old to recognise this card).

---

### Post by varunendra on 2013-07-04
> **greatsirkain said:**
> ...Can't redo it with windows because **windows refuses to recognise the card and the timer just runs continuoulsy** as soon as I plug it in until I remove it - on purpose, another example of microsoft locking out hardware it can't control & taking over things it can (another possibility is that the card reader on the desktop is just too old to recognise this card).
..yet another possibility could be that there is really something seriously wrong with the card itself, like tgalati4 pointed out earlier :(

The partitioning scheme you currently have is okay for a full installation. The single fat partition advice was for Live system, a full installation will need an ext partition anyway.

---

### Post by Bashing-om on 2013-07-04
greatsirkain;
Recon that card has a lock on it from not being "safely removed" causing problem ? Just a thought, sure others can advise better.

---

### Post by greatsirkain on 2013-07-04
well if I haven't messed up the file system... *shrugs*
the card  works fine when reading/writing there's no problems there now, Ubuntu  seems to have installed to it fine, I can mount and un-mount it from  within Ubuntu ok, it just doesn't get recognised at boot...I'll check it  with other distros and maybe try it in winxp with hbcd.
I checked  the file system of each partition with fsck, each one came back clean  and there were no errors reported in gparted...*shrugs again*...I  thought if there were actual damage one of them would hint at it?

*goes for power nap*

---

### Post by Bashing-om on 2013-07-04
greatsirkain; Hey, all that is great news... lookin better alla the time.

Ok booting: Are you certain that grub (GRand Unified Bootloader) was installed to the MBR of the SD card ? And Just touching the obvious --bios is set to boot from usb, no ?

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by greatsirkain on 2013-07-08
yup pretty sure grub installed ok and boot from usb is enabled in bios (I have to boot from a usb because bios doesn't recognise the hard drive :P )

---

### Post by Bashing-om on 2013-07-08
greatsirkain; Hey ..

Try'n to hang with you...Let's define 1 single issue as the predominate one taking priority over any other.
So I understand that you have ubuntu installed onto a external SD card and can not boot from that external device ?

Boot that external device is what we are working toward ???

[INDENT][INDENT]I be try'n to help
[/INDENT][/INDENT]

---

### Post by greatsirkain on 2013-07-11
Yup, the 16GB san disk ultra SD card I installed Ubuntu to.
I installed GrUB to the main device (/dev/mmcblk0) then Ubuntu to the first partition (/dev/mmcblk0p1).
It's an Advent Quantum Q200 laptop and it's all set up to boot from USB.
Ubuntu has no problems mounting/reading/writing to any partition on the card, all partitions checked and OK.

---

### Post by Bashing-om on 2013-07-11
greatsirkain; Hey.

Quite frankly I am not following the assignment " main device (/dev/mmcblk0) then Ubuntu to the first partition (/dev/mmcblk0p1)"
Standard install I would expect an assignment such as "/dev/sdc"

Raid and or raid/LVM ???.. Taking time to re-read the thread and see again where you are coming from.

[INDENT][INDENT]later
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-11
greatsirkain; Hey,

Looking about and find that sometimes there are issues of RAID as Intel SRT uses RAID for the SSD.

What results form terminal command :
```
sudo blkid
```

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by greatsirkain on 2013-07-12
Hi Bashing-om, the mmc thing has been bothering me too
found this > Setting up two partitions which are the boot image (FAT 16) and root file system (ext4). The SD card plugged in through USB card reader found as /dev/sdb in this example (**we&#8217;re formatting be sure of this!**). If you plug MMC card to laptop slot, it may be found as /dev/mmcblk0. here [http://lakm.us/logit/2013/03/duplicate-restore-arm-linux-image-mmc-sd-card-beagleboard-devkit-board/](http://lakm.us/logit/2013/03/duplicate-restore-arm-linux-image-mmc-sd-card-beagleboard-devkit-board/)
Don't think it's really relevant to me but it did put me onto Das U-Boot bootloader that seems to be able to do things syslinux can't...If you compile your own kernel? Maybe it's because I haven't had my coffee yet and I still have crusty eyes but this is starting to look too complex for a Friday morning

```
sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="B178-B232" TYPE="vfat" 
/dev/sda2: LABEL="b127 laptop" UUID="5984-2E44" TYPE="vfat" 
/dev/sdb: LABEL="SARDU" UUID="20CA-4D11" TYPE="vfat" 
/dev/sr0: LABEL="Lubuntu 12.04 i386" TYPE="iso9660" 
/dev/mmcblk0p1: LABEL="ubuntuboot" UUID="ddbd9593-1744-4fcd-b4ef-593d0dae12cd" TYPE="ext2" 
/dev/mmcblk0p2: LABEL="dump" UUID="4343-AB0D" TYPE="vfat" 
/dev/mmcblk0p3: UUID="fb2c9e61-8ad5-4195-aa06-13669b3b8d44" TYPE="swap" 
/dev/sdc1: LABEL="SARDU" UUID="A8CF-6C55" TYPE="vfat" 


```

Thanks for the help you three, this is annoying me. The card cost 17 quid and hasn't done anything useful yet

Edit: also this [https://bbs.archlinux.org/viewtopic.php?id=97207](https://bbs.archlinux.org/viewtopic.php?id=97207) which seems to be exatly what I'm looking for but still by using a custom kernel

Edit 2: I'm trying to learn about RAID now too and reading ( here: [http://www.geeks.com/techtips/2005/techtips-020305.htm](http://www.geeks.com/techtips/2005/techtips-020305.htm) [although it was written in 2005] ) that a MMC is not an SD card although many, many other, newer, sites I've read define them as the same thing & say you can definitely boot from a MMC >.<

---

### Post by varunendra on 2013-07-12
> **greatsirkain said:**
> Edit 2: I'm trying to learn about RAID now too and reading ( here: [http://www.geeks.com/techtips/2005/techtips-020305.htm](http://www.geeks.com/techtips/2005/techtips-020305.htm) [although it was written in 2005] ) that a MMC is not an SD card although many, many other, newer, sites I've read define them as the same thing & say you can definitely boot from a MMC >.<

I believe that any storage media that can appear in BIOS and its boot menu should also be able to boot. The only chance when it is logically questionable is when it does not appear in the BIOS.

---

### Post by Bashing-om on 2013-07-12
greatsirkain;

I am known as Bashing-om ....but to be frank -> I do not know !
1. ARM is a different architecture and so - out of the picture;
2. Compiling the kernel from source not to be thought of as ubuntu prides itself on the kernel's ability to recognize hardware out of the box;

3. It blows me away how the SSD is partitioned, formatted and a file system installed onto it with such an "unorthodox" partition table " /dev/mmcblk0p1:" ;
4, That sure makes me hesitant to "sic" dmraid tools on that device as was my former intention.
Maybe all that needs doing is to make a small "/boot" partition ? to make the other partitons format properly ?
Make the partition(s) for ubuntu formats as "ext4" ?

So what I am going to do .. is seek the guidance of oldfred and his contacts and see what he/and others make of this sloppyation.

[INDENT][INDENT]3 heads are better than 2[/INDENT][/INDENT]

---

### Post by oldfred on 2013-07-12
I have never installed to a memory card, just USB flash drives. 
But it looks like it uses a different driver than hard drives or USB flash drives, and is then mounted at /dev/mmcxxxx?

---

### Post by oldfred on 2013-07-12
Just booted my 6 year old laptop. It will not boot from Memory Card, I think, never created bootable MMC card.

Only used memory card a couple of times. Originally did not even notice it had a tiny slot at front that was for MMC cards.
Plugged in a MMC card and it mounted at /dev/mmcblk0p1 on /media/FC30-3DEA9 which is UUID of partition. And it did not add an icon on my desktop like my flash drives do. Using 12.04 with fallback or gnome panel.

---

### Post by sstefann90 on 2013-08-01
I'm new to the forums and figured i'ld reply to this post since I seem to be in the same sticky situation.I'm running 
OS= Ubuntu 12.04LTS on Windows 7 64-bit Lenovo V570 (for what its worth).
GCC = 4.7.2
ELDK = 5.3 
U-boot = 2013.04
cross compiler = arm-linux-gnueabi
arch = arm 
board = Freescale mx53evk
SD card = Patriot Memory MicroSD adapter 8gb

when i go through the make process in u-boot
```
export BUILD_DIR=/tmp/build
make distclean
unset LDFLAGS
make mx53evk_config
make all
```
to successfully build it, i get the u-boot.imx image, and when i try burning it to the SD card i get the same result of just the lost+found folder, if i use format FAT32, refreshing gparted yields filesystem as 'unknown'. I've had the problem where I need the sd card in my sd card slot of my laptop upon bootup if i want my computer to recognize the sd card (and i can't have any cd's/ext usb drives in too, apparently a 12.04 64-bit os problem)
my sd card set-up is as follows:
heads: 255
sectors: 63
cylinders: 968 (based on 7969.../255/63/512 = roughly 968)
when i 'dd' i do the two variations, the internet told me to always specify the 512 to use 0x400 slot (from what i remember)
```
dd if=u-boot.imx of=/dev/sdb
dd if=u-boot.imx of=/dev/sdb bs=512 seek=2
```
I'm following this thread hoping something works lol, I'm about to go officespace on my laptop, freescale community forums is difficult

---

### Post by greatsirkain on 2013-08-26
I'm still on trying with this btw, when life doesn't get in the way....Or the forum getting messed up and needing me to make another account :P
nice to see more folks trying to solve this too :)

nothing  really to report from me, just trying different programs in winxp 
still  trying to avoid kernel compiling but I am liking the idea of  building my own pre 2.6 kernal before the NSA did stuff to it...Don't  know what they did but I don't want it in my house....Looking at me, like peeping toms in long raincoats with nothing underneath

---

### Post by Bashing-om on 2013-08-26
greatsirkain; Hey ...

I have not forget either !
Look; QcQccbM has one solution. Looks tough to implement .. but he advises he has got it working:

[http://ubuntuforums.org/showthread.php?t=2165125&highlight=mmcblk0p1](http://ubuntuforums.org/showthread.php?t=2165125&highlight=mmcblk0p1)

beyond my comprehension ->

[INDENT][INDENT]I know a little about some things and less about others
[/INDENT][/INDENT]

---

### Post by greatsirkain on 2013-08-27
well that's raised some new questions and cleared up some.
seems I have to set up a virtual floppy disk containing the boot loader on the card then the rest of the card gets treated like a seperate hard drive with the OS etc on it, given me a rash of new ideas on how to go about things. 
I'll test it with xp live to avoid messing with the casper workaround.

....later at least, I'm on puppy atm and I'm too tired go get my ubuntu/xp drives until I've had a sleep but as usual I'm not tired enough to sleep. By the time I get this sorted out there'll be new computers out that fit in your eyeball and use your brain for memory/processing with near instant information exchange, watch a 3 hour movie in under a second etc........and don't be stealing that it already in my book! :P

---

### Post by Bashing-om on 2013-08-27
@greatsirkain; Haw & har Har..

off topic:
One thing for sure, we will never know all we need to know about this operating system ... just learn what we need to know to do what we want to do !
But as always;
[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

