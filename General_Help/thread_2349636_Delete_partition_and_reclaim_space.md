---
title: "Delete partition and reclaim space"
date: 2017-01-16
forum: General Help
---

### Post by RobGoss on 2017-01-16
Hello all, I was wondering how do I reclaim partition space that I deleted from my multi system. I know how to achieve this with Windows but Linux is a bit different 

I have one of my machine that have about three OS's on it I wanted to clean it up and only have a dual boot, I was able to delete one of the partition that had **Manjaro **but it's now unallocated and I would like to reclaim back that space to my **Ubuntu 16.04** partition

Ubuntu is my primary OS on this machine I don't want to loose that space it's abot a **160-GB** of disk space and I would like to merge it if possible 

And this machine is not running Windows also


Thanks so much for any help

---

### Post by Dennis N on 2017-01-16
Depends on if they are adjacent. If the unallocated space is adjacent to and after the Ubuntu root partition, just expand the Ubuntu partition into the unallocated space.

---

### Post by RobGoss on 2017-01-16
> **Dennis N said:**
> Depends on if they are adjacent. If the unallocated space is adjacent to and after the Ubuntu root partition, just expand the Ubuntu partition into the unallocated space.

Hi Dennis can I do this with GParted?


Thanks so much

---

### Post by Bucky Ball on 2017-01-16
Yes, you can do it with Gparted, but not while you are running the system. As you are wanting to expand / into the free space (if the partition is next to it) you will need to boot to a 'live' session from USB or DVD, 'Try Ubuntu' and take it from there.

Right click the / partition in Gparted and 'Resize'. Be aware that before doing anything like this you should have reliable backups of valuable data, but you already have them and knew that, right? :)

Good luck.

---

### Post by sudodus on 2017-01-17
If you want help with the details in order to avoid mistakes, please attach a screenshot of gparted, when it is displaying this drive, and explain which partition is the Ubuntu root partition.

I'll repeat what Dennis N wrote, "If the unallocated space is adjacent to and after the Ubuntu root partition, just expand the Ubuntu partition into the unallocated space." ***I would add if they are adjacent to and the unallocated space is before the Ubuntu root partition, things are more complicated***. You can expand the Ubuntu root partition to use the unallocated space, but you must also re-install the bootloader, grub, because it should point to the head end of the partition. Exception: If you have a separate boot partition, the bootloader points to the head end of that partition instead.

-o-

It is also possible to ***create a data partition*** (from the unallocated drive space), where you store your personal files (instead of using the default directories in your home directory, Documents, Downloads, Music, Video). I use a data partition and have a line for it in /etc/fstab to get it mounted automatically. It makes it easy to back up my personal files separately from the operating system.

---

### Post by HermanAB on 2017-01-17
First get a big mug of coffee, a chocolate bar and a large capacity USB memory thingy.  Make a backup of all your data.  Now reboot with a Linux live install disk and run gparted.  Carefully note the size and filesystems of all partitions. Think about it for a minute while swilling your coffee and munching the chocky.  Be sure to format the correct partition, then remove the USB thingy and reboot.

---

### Post by RobGoss on 2017-01-17
>    Right click the / partition in Gparted and 'Resize 

Are you referring to my primary partition that has Ubuntu on it is that the one that needs to be resized?

Yes I don't keep tons of data on any of my machines so I think it all good there

Thanks Bucky

---

### Post by RobGoss on 2017-01-17
> **sudodus said:**
> If you want help with the details in order to avoid mistakes, please attach a screenshot of gparted, when it is displaying this drive, and explain which partition is the Ubuntu root partition.

I'll repeat what Dennis N wrote, "If the unallocated space is adjacent to and after the Ubuntu root partition, just expand the Ubuntu partition into the unallocated space." ***I would add if they are adjacent to and the unallocated space is before the Ubuntu root partition, things are more complicated***. You can expand the Ubuntu root partition to use the unallocated space, but you must also re-install the bootloader, grub, because it should point to the head end of the partition. Exception: If you have a separate boot partition, the bootloader points to the head end of that partition instead.

-o-

It is also possible to ***create a data partition*** (from the unallocated drive space), where you store your personal files (instead of using the default directories in your home directory, Documents, Downloads, Music, Video). I use a data partition and have a line for it in /etc/fstab to get it mounted automatically. It makes it easy to back up my personal files separately from the operating system.


I had issues with Manjaro the os have some kind of Panic error I tried fixing it but felt it wasn't worth the headache if you know what I mean. I have to many OS's to worry about just one that I hardly ever use

I'll keep your suggestions in mind as well thanks so much

---

### Post by RobGoss on 2017-01-17
> **HermanAB said:**
> First get a big mug of coffee, a chocolate bar and a large capacity USB memory thingy.  Make a backup of all your data.  Now reboot with a Linux live install disk and run gparted.  Carefully note the size and filesystems of all partitions. Think about it for a minute while swilling your coffee and munching the chocky.  Be sure to format the correct partition, then remove the USB thingy and reboot.

Coffee is always a good start:)

Backup is already done, You mentioned formatting the partition in question then rebooting, then what?

---

### Post by RobGoss on 2017-01-17
I have three partitions on this machines now because I deleted one, Let's just say I didn't want the other partitions and just wanted to do a clean installation of Ubuntu 16.04 the process is still the same use the entire disk correct? This would give me back all my disk space right

The reason I'm asking is because I got a few more machines and I don't see the point of having dual boot machines as much now. I have to total of 6 machines

This is just me speaking out load

I hope I'm not confusing my topic if so I  apologize in advance. I was just curious. 16.04 is running so well I would hate to reinstall anything

---

### Post by HermanAB on 2017-01-17
I won't risk resizing a partition while there is anything that is in active use on a machine.  I'd suggest formatting the empty space with ext4 or btrfs and mounting it somewhere in your main Linux file system instead.  Doing that is almost risk free.

---

### Post by sudodus on 2017-01-17
> **HermanAB said:**
> I won't risk resizing a partition while there is anything that is in active use on a machine.  I'd suggest formatting the empty space with ext4 or btrfs and mounting it somewhere in your main Linux file system instead.  Doing that is almost risk free.

This is another way of saying what I meant by a **data** partition and I think it is a good idea.

---

### Post by RobGoss on 2017-01-19
Here's an update on my partition situation, so I managed to delete two of the four partitions I have on this machine 

I was able to expand my Xubuntu partition so that leaves me with only one unallocated partition which for some reason I'm unable to extend it to my primary Ubuntu 16.04 partition

I notice that a small section of my two active remaining partitions are a yellow color, I'm not sure if it really matters and something to do with me not being able to extend my primary Ubuntu 16.04 partition. The unallocated space is on the left side of the Ubuntu partition 

Also I don't know if the partition need to be in a certain position in order to combine them or maybe I'm not using the correct format


I'll have to try it again as soon as I get to my destop

Thanks so much

---

### Post by Dennis N on 2017-01-19
In gparted, the yellow shading inside the partition rectangles at the top represents the size of the used space.

If you care to post it, a screenshot of the gparted window would help others understand where all the partitions and unallocated spaces are, and get a more definite answer.

---

### Post by Bucky Ball on 2017-01-19
If you're wanting to expand you primary Ubuntu partition to the space these partition are occupying, you obviously don't want what's on the partitions so why not just delete them and expand your partition into the free space? You can't expand a partition into another one. You need to get rid of one of them and leave free space. 

You may also be having issues trying to expand a partition that is not part of an extended partition into an extended partition.

[QUOTE=Dennis N]If you care to post it, a screenshot of the gparted window would help others understand where all the partitions and unallocated spaces are, and get a more definite answer. [/QUOTE]

And this. Take a screenshot and attach it to a post rather than inserting it into the text. ;)

---

### Post by RobGoss on 2017-01-19
>    f you're wanting to expand you primary Ubuntu partition to the space these partition are occupying, you obviously don't want what's on the partitions so why not just delete them and expand your partition into the free space? You can't expand a partition into another one. You need to get rid of one of them and leave free space.    


That's exactly what I did with the first partition after deleting it and I was able to expand my Xubuntu partition

So I tried repeating the same process with the last unallocated partition but was not able to. I'll post a screen shot as soon as I get to my desktop

---

### Post by RobGoss on 2017-01-19
Ok guys here's a screen shot, I was able to add that unallocated space to the Xubuntu partition but my main partition is **Ubuntu 16.04, **so I would like to resize the Xubuntu partition to about **100-GB** and give the remaining space to Ubuntu 16.04 partition seeing this is my primary desktop

For some reason I can't extend my primary partition the 147-GB to use up the 200-GB unallocated space but if I try to add that space back to the Xubuntu partition I can do so..


Thanks so much for all the help

---

### Post by ajgreeny on 2017-01-19
I can not see a 200GB unallocated space on your disk so I'm confused, still, about what you want to do.

You have sda5 and sda10 which are both ext4 partitions, but which is Xubuntu and which Ubuntu? I think sda10 is probably Xubuntu, and I suspect you may be showing the screenshot from that OS not a live system, as sda8 (swap) and sda10 (ext4) are both locked, usually meaning they're mounted and in use.
The Ubuntu sda5 is not locked as you are not using that OS which is why you can work on that partition.

As others have said, you should use a live system when using gparted as you can't do anything to partitions that are mounted and in use, and even when doing that you may need to right click on the swap partition and choose swapoff, as swap will be found and used by a live Linux OS.

---

### Post by RobGoss on 2017-01-19
Sorry about that here you go, **sda10 **is my Ubuntu 16.04 and **sda5** is Xubuntu

---

### Post by yancek on 2017-01-19
You already have a 100GB+ partition for Ubuntu.  You would have to install an awful lot of software to use up that much space.  It would seem simpler and less risky to just create a data partition from the unallocated space for Ubuntu.  You could also access it from Xubuntu if you wanted.

If you want to move Ubuntu/sda10, you would need to use GParted from an iso, turn off swap, delete swap and resize moving sda10 to the left.  Make sure you leave room for a new swap.  The problems with moving a system partition to the left is that you are moving all your boot files to a new location and may be unable to boot that system.  You will likely get a warning to that effect after clicking Apply in GParted.

---

### Post by Bucky Ball on 2017-01-19
> **yancek said:**
> You already have a 100GB+ partition for Ubuntu.  You would have to install an awful lot of software to use up that much space.  It would seem simpler and less risky to just create a data partition from the unallocated space for Ubuntu.  You could also access it from Xubuntu if you wanted.

+1. Personally, I'd be shrinking both Xubuntu and Ubuntu to about 20Gb and 25Gb respectively, creating a /data partition with the free space and putting all my personal data there to be accessed by both OSs. No redundancy and confusion.

Just a note. Is that first partition, Windows RE, Windows recovery tools? I can't see Windows on that list. There are NTFS partitions but none of them big enough for a Win install. Perhaps that partition needs to be there to use EFI. Not familiar enough with Win anymore, or EFI, to know either way.

---

### Post by sudodus on 2017-01-20
Please consider what I wrote before, and what several other people have written:  create a **data** partition from the unallocated space and put all your personal data there to be accessed by both OSs. It will also make it ***easy to back up your personal data*** separately from the operating systems.

-o-

Otherwise it should be easy to expand /dev/sda5 to use the unallocated drive space, but difficult to expand /dev/sda10 to use the unallocated drive space.

If you want a clean system, you should also consider a completely fresh installation, or a fresh installation, where you keep /home as a separate home partition.

---

### Post by HermanAB on 2017-01-20
The thing to bear in mind is that if you faf around with the partitioning long enough then you machine will eventually be rendered unbootable.  

So, if there is nothing important on the machine, by all means go ahead an play.  Otherwise - STOP.

---

### Post by Bucky Ball on 2017-01-20
> **HermanAB said:**
> The thing to bear in mind is that if you faf around with the partitioning long enough then you machine will eventually be rendered unbootable.  

So, if there is nothing important on the machine, by all means go ahead an play.  Otherwise - STOP.

Good advice. Back up what you don't want to lose, delete the partitions you don't want and then you have a clear view and can go for it. Be prepared to reinstall if you keep fiddling.

I always advise sitting with a beverage of choice, pen and paper and making a clear, hardcopy plan prior to diving into anything like this or going anywhere near the computer (except perhaps to confirm what partitions are already on there). Appears you are playing this 'on the fly'. You know you want to merge this with that but have no clear path for how to get there. 

Time to draw that mud-map of how you want your *whole* drive to look when you're finished then get to work making that happen. ;)

What we're suggesting, and my plan would be, something like this:

/OS1 - 20Gb
/OS2 - 20Gb
/Data (or whatever you want to call it) - the rest of the drive except for
/swap - 2Gb

The swap can be used by both, or more, Linux OSs. Good luck. ;)

---

### Post by RobGoss on 2017-01-20
I was able to expand the Ubuntu partition by moving it to the left everything seems to be OK so far I'll mark this as solved.

Thanks everyone for your help it's much appreciated

---

### Post by sudodus on 2017-01-20
Congratulations and thanks for sharing your solution :-)

---

