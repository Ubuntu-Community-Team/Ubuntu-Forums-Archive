---
title: "extended partition?"
date: 2006-09-18
forum: General Help
---

### Post by Schalken on 2006-09-18
I was prepared to install 3 OS on my computer (SUSE, Ubuntu & Windows), plus the linux-swap and home partition, making 5 partitions total. To my suprise it appears I can only have 4 partitions max and if I wanted more I should make one of those extended to contain others.

What are the ramifications of creating an extended partition to contain mutliple OSs, and how does it affect GRUB and the OS's ability to read and write file systems within and without the extended partition?

---

### Post by kidders on 2006-09-18
Hi there,

The effects are not very dramatic. Years ago, Bill Gates decreed that four partitions were as many as anyone would ever need. Of course, if you don't agree with him, you could always switch to Apple's partitioning scheme, or someone else's :-P

Anyhow, the only thing that might get upset about living in an extended partition is Windows ... nothing else really cares. Very, very frequently-accessed partitions (such as swap) can underperform if they're thrown into an extended partition though, because of the increased number of lookups an OS must perform to find the partition's allocation table.

Afaik, there's nothing else you need to be aware of. Technically, an extended partition group is viewed as being a single primary partition, so if you create two primaries, and an extended with two more partitions inside it, the device naming scheme might go something like this:

Device: /dev/sda
[LIST=1]
[*]Primary 1 - /dev/sda1
[*]Primary 2 - /dev/sda2
[*]Extended group - /dev/sda3
[*]Extended 1 - /dev/sda4
[*]Extended 2 - /dev/sda5
[/LIST]

So, you'll always wind up with a /dev entry that doesn't point to anything immediately useful (/dev/sda3 in my example).

---

### Post by Schalken on 2006-09-18
Okay, thanks for your help!

I think SUSE's and Ubuntu's system partitions would be best to be put in the extended. ;)

Once more question, is there any limit on the number of partitions that can go into the extended partition?

I hope GRUB behaves with my now elaborate partitioning scheme.

---

### Post by kidders on 2006-09-18
Off the top of my head, I don't think there's a limit. Well ... there must be _*some*_ limit (hehe) but it's probably astronomical!

The use of extended partitions is extremely commonplace on Windows, Linux and other systems, so you have nothing to worry about :-)

---

### Post by Schalken on 2006-09-19
Awesome. Ubuntu is obediently living in a logical partition right now. Once it's downloaded, SUSE should do likewise.

Thanks again.

---

### Post by geezerone on 2006-09-20
Hi

I read this thread with interest because I am trying to install Dapper on to some free space on my primary hard disk (sda) but coming acropper saying only allowed 4 primary partitions but am unable to create a logical partition unless using the extended partition created under Windows for a second logical drive (NTFS)

The disk layout is as follows:

/dev/sda1      -  NTFS
    /dev/sda2  -  Extended
/dev/sda3      -  NTFS

If I try and add partitions using the Ubuntu drive partitioner I am only allowed to create primary partitions which doesn't allow me to create a '/home' directory just '/' and 'swap'. I am allowed to add logical partition under the Extended option but this is NTFS and will lose data on it.

Any ideas?

Thanks :)

---

### Post by kidders on 2006-09-20
Hi there,

I'm afraid I don't completely understand your question. If there is some unallocated space on your disk, you should be able to allocate it to an extended partition, depending on where it is. Maybe something like ...

[LIST]
[*]/dev/sda1 - Primary 1 (NTFS)
[*]/dev/sda2 - Extended --------
[*]/dev/sda3 - Extended 1 (NTFS)
[*]/dev/sda4 - Extended 2 (New partition)
[/LIST]

That way, you'd only have two "real" partitions on your disk (sda1 & sda2), which would work fine.

---

### Post by geezerone on 2006-09-20
I went to add primary partitions for root and swap but unable to add more than 4 primary partitions. I tried to add extended logical partition but the option is greyed out for all except the 'extended' one. If I try and create a logical here (if i remember correctly) the data stored here doesn't appear (stored on the NTFS extended partition) and don't want to lose this.

Hope this is a bit clearer, I know it isn't the easiest of queries.

---

### Post by kidders on 2006-09-20
> the data stored here doesn't appear

You mean your partition editor is misreporting your drive layout? Hmm... that's very odd. Are you certain your disk is laid out the way you think it is, and not how your partition editor says it is?

---

### Post by geezerone on 2006-09-20
When I go to change the layout of the extended partition there is about 2.7GB of data which is no longer shown when attempting to change/add logical partitions if that makes sense?

---

### Post by kidders on 2006-09-20
This is sounding like a bug in your partition editor ... have you tried another? :confused:

---

### Post by geezerone on 2006-09-21
Just the partitioner on the Ubuntu live CD i386. I did try Qtparted but not convinced it is working ok, do you have a link to a known working .iso?

---

### Post by kidders on 2006-09-21
I'm afraid not ... I'm very text-based, I'm afraid :-( I always rely on "cfdisk" to repartition things.

I'm still a little fuzzy on exactly what's gone wrong for you though. Is it that apparently unallocated space is there one minute and seems to disappear when you try to do anything with it?

---

### Post by geezerone on 2006-09-21
No, there is approx 16GB unallocated space at the end of the drive. I have a Windows NTFS primary partition, then have a data NTFS extended partition and that is all. If I want to install Ubuntu with a / and swap partition (both primary) all would be ok. I do, however, want to have a /home directory and am unable to add this (cannot add /home as primary and extended option isn't there) without potentially wiping the 3GB of data off the second NTFS data partition.

---

### Post by kidders on 2006-09-21
Hey again,

> I do, however, want to have a /home directory and am unable to add this without potentially wiping the 3GB of data off the second NTFS data partition. I don't really follow why you would have to delete this data. Are those 16GB not enough for your Ubuntu install?

**Edit:** You can add as many logical partitions to your extended partition as you like, you know.

---

### Post by geezerone on 2006-09-21
I don't wish to delete the data and perhaps it won't be, but when trying to change the extended partition setup the 3GB isn't there anymore.

The 16GB is fine and would be ok for the three partitions I need but the editor won't allow me to add another logical partition in the 'free space' available, i.e. 16GB - just primary which has a limit of 4 per disk. 

I will try the centos live cd to see if this sheds any more light on this.

---

### Post by kidders on 2006-09-21
Without actually trying it, I can't be sure, but can't you either stretch your extended partition to the end of the disk or simply add another?

Adding primary/logical partitions to disks is *supposed* to be easy! I think I see what you're doing wrong though ... your extended partition is only as big as the one logical partition it contains.

---

### Post by coffeecat on 2006-09-22
Word of explanation. As I understand it an extended partition is simply a container for one or a number of logical partitions. There is a limit to the number of logical partitions, but I can't rememer what this is. Well over 10 anyway.

In Gparted and Qtparted, you have to create an extended partition using the unallocated space first. (You can create more than one but then you'd have the potential to create an enormous number of logical ones.) That's why the logical option is greyed out until after you create an extended partition. Once you have an extended partition (which will be numbered between 1 and 4) you can then create logical partitions (which will be numbered 5 and upwards).

---

### Post by geezerone on 2006-09-22
> **coffeecat said:**
> In Gparted and Qtparted, you have to create an extended partition using the unallocated space first. (You can create more than one but then you'd have the potential to create an enormous number of logical ones.) That's why the logical option is greyed out until after you create an extended partition. Once you have an extended partition (which will be numbered between 1 and 4) you can then create logical partitions (which will be numbered 5 and upwards).

I have an Extended partition with one logical partition in it (NTFS data for windows created before windows install). The option to create another extended partition is 'greyed out' so only able to add primary partitions (x2).

---

### Post by kidders on 2006-09-22
Hi again,

Since creating a second extended partition, or extending the first one, seem to be giving you so much grief, perhaps it would be simpler to move your logical NTFS partition into a primary one and create a fresh extended partition from scratch? A bit silly maybe ... just a thought.

---

### Post by NeutrinoX on 2006-09-23
Don't know if this goes too much off-topic, but since this thread is about extended partitions... I'm having problems to manage an extended partition on QtParted, basically what I want to do is to resize it in order to take advantage of the empty space now my HDD has since I deleted my Windows NTFS partition I used to have (Part of the switch-completely-to-Linux-for-daily-use-and-forget-Windows plan I had)... but seems that's not possible. The only thing I can do is to resize the partition to the right side (The free space is allocated on the left side, before the extended partition). I think I heard somewhere it's kinda tricky to resize these partitions, is this true? Any suggestions?

EDIT: Attached a screenshot of QtParted for reference purposes:

[[IMG]http://img116.imageshack.us/img116/3158/screenshotqtpartedlu1.th.png[/IMG]](http://img116.imageshack.us/my.php?image=screenshotqtpartedlu1.png)

---

### Post by kidders on 2006-09-24
Hmm... 17 hours without any help :-(

You could always resort to the long-winded solution ... [here]("http://ubuntuforums.org/showthread.php?t=263416&highlight=reflect+change"), from one of my other posts, but only as a last resort!

---

### Post by geezerone on 2006-09-24
> **kidders said:**
> Hi again,

Since creating a second extended partition, or extending the first one, seem to be giving you so much grief, perhaps it would be simpler to move your logical NTFS partition into a primary one and create a fresh extended partition from scratch? A bit silly maybe ... just a thought.

Thanks for your perseverance Kidders. I managed to increase the extended partition into some free space at end of drive and then setup a logical partition for /home directory (ext3). I then created a /swap primary and then a primary / drive. 

All looked to go ok and installed Ubuntu but after reboot (and Windows checking the extended resize which went ok) it doesn't give an option for Grub to run Ubuntu but instead always boots windows? I reinstalled but still the same.

I have a primary windows part, then extended part (containing NTFS data and ext3 /home), then primary swap and then primary / directory.

The install did show 'setting up Grub' info just before it finished so puzzled as to why it doesn't show boot options. :(

---

### Post by kidders on 2006-09-24
Great news :-)

> I reinstalled but still the same.I assume you didn't reinstall your entire operating system!! Are you sure grub is being installed on the correct disk drive?

---

### Post by geezerone on 2006-09-25
> **kidders said:**
> Great news :-)

I assume you didn't reinstall your entire operating system!! Are you sure grub is being installed on the correct disk drive?

:)  No just reinstalled Ubuntu but not picking up grub. I have a SATAII hard disk with XP and Ubuntu installed and two more SATAI and two more IDE disks. I opened a terminal and grub menu.lst is on hd2,3 and the hard disks in the system according to grub menu is hd0 1 2 3 4. Don't know for sure how my SATA disk correlates to these hd numbers as during install the disk was sda and root partition was 4 , so sda4.

When i carried out 'root (hd2,3)' command the response is = Filesystem type is ext2fs, partition type 0x83 ? I did format as ext3 so unsure of ext2fs?

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+15 p (hd2,3)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

After trying to install grub for hd2,3 the above msg displayed. 

I now get grub menu loading but when i select option for Ubuntu it says partition doesn't exist (i think) and NOW windows doesn't boot (NTLDR missing - tried fixmbr and now boots windows ok (no grub option) but loathe to mess with Grub until i am sure it will work.

---

### Post by kidders on 2006-09-26
> No just reinstalled UbuntuUbuntu *is* your operating system! Oh dear.

I imagine you already tried assuming /dev/sda was hd0, /dev/sdb was hd1, and so on. 

In that case, the surest way to identify your disk numbers is to do it from the grub menu itself, during boot. Grub's silly hard disk numbering system is annoying, but at least it provides a nice terminal-style interface at boot-time to let you play around. It has a pretty handy command autocompletion feature that you can abuse to get it to tell you which disk is which. Once you have found which drives correspond to disk numbers 1-4, and which settings let you boot the way you want to, tweaking menu.lst will be easier.

I imagine your Windows stopped booting because you just happened to pick the one MBR you shouldn't have, at random. Unlucky :-(

It's a pretty safe bet the Ubuntu's installer will have tried to install Grub on the MBR that's logically "first" on your list. To keep things simple, I suppose your BIOS's boot sequence should reflect the disk you want to do the booting with.

**Edit:** If you're finding Grub too hard to use, bear in mind that it's not the only bootloader in the world :-)

---

### Post by geezerone on 2006-09-26
Hi

No, XP is still the 'king' so to speak and boots ok now. I saw a thread here to enquire at terminal as to what grub thinks is the Ubuntu installation and then boot (hd2,3) into it and install grub on that disks MBR. I did this and it mucked up the XP MBR. If you know the autocompletion feature i would be grateful but used tab to ask 'grub' the disk layout and just said hd0 - hd4. I did examine the partition formats but only hd2,3 and hd2,4 (i think) showed as ext2fs partition x83 and other partitions on other disks were unknown or wrong type.

I wonder if i should try the ALT cd instead to install on my SATAII disk (which is shown as the 5th disk in the BIOS table BTW and is IDE mode).

Thanks again!  :)

---

### Post by geezerone on 2006-09-26
Just thought I would post an update.

I had a brainstorm ;) and decided to remove all disks apart from my SATAII drive and installed over the existing partitions (dev/sda 3 [swap],4 [/ ] and logical 6 [/home]. After rebooting Grub 1.5 loads and so do the options to choose between XP and Ubuntu. I booted into both OS's successfully and amended the 'menu.lst' file in grub to set default as XP and changed timeout to 3 secs.

I suspect that grub was writing to my master IDE drive mbr record but this way there was no way it could write to any disk as only one there!

So thanks for the help guys (esp Kidders =D> )

Just need to find out some more now! :mrgreen:

---

### Post by Ocxic on 2006-09-26
> **kidders said:**
> Years ago, Bill Gates decreed that four partitions were as many as anyone would ever need. Of course, if you don't agree with him, you could always switch to Apple's partitioning scheme, or someone else's

not to sidetrack this threab but how do i go about learning about something like this, and more importantly if i can run ubuntu on such a different schem???

---

### Post by kidders on 2006-09-27
Hi there,

In terms of whether you can run Ubuntu off non-Microsoft disk partitions, the general answer is that you can run Linux under almost any conditions you can dream up. Microsoft systems are the fussy ones!

Learning about the technical stuff underlying partition layout schemas takes a fair bit of reading, but there's plenty of help out there ... I'm pretty sure google, wikipedia or other common information sources can help you out. If you have a specific question though, I'd be happy to try to answer it.

---

### Post by Ocxic on 2006-09-27
could you point me in a good direction to start, I googled for an hour and came up with nothin???

---

### Post by Schalken on 2006-09-28
What's your motive for trying to use another partitioning scheme anyway? It really is getting down and dirty with your hard drive, and isn't necessary since you can just create an extended partition to contain logical partitions if you want more than 4.

Just keep in mind that the extended partition itself counts towards your 4 primary partition limit, while the logicals inside it don't.

---

### Post by kidders on 2006-09-28
That's a worthwhile point ... there is no particular advantage in choosing one schema over another.

---

### Post by Ocxic on 2006-09-28
the simple fact that i can use something different intregues me, thats what brought me to ubuntu, plus i like figuring stuff like this out, it fun.

---

### Post by kidders on 2006-09-29
Oh heck... we forgot to actually answer your question!!

Well, if you're curious about what partition schemes Linux supports, check out [http://lwn.net/2000/0525/kernel-symbols.php3](http://lwn.net/2000/0525/kernel-symbols.php3). It's really a table of things that have to do with reconfiguring the Linux kernel, but it contains a list of the names of supported partition types. Search for the phrase "Advanced partition selection".

Now, should you happen to want to actually try any of them, you'll need to find a disk partitioner that speaks the right language. "pdisk" and "mac-fdisk" are examples of Apple partition managers.

One thing to bear in mind, of course, is that choosing any non-Microsoft partitioning scheme will render the affected disk completely unreadable in Windows, which will try to persuade you to completely wipe it. How helpful.

I hope that helps.

---

