---
title: "How do I uninstall Ubuntu?"
date: 2008-01-03
forum: General Help
---

### Post by trail0r on 2008-01-03
Hey

I am going to set my laptop back to how it was when I first bought it, because I am going to sell it.

One time I simply formatted the hard disk Ubuntu was installed on, and this totally screwed up my computer because grub was trying to load but it crashed because it wasn't there. So I couldn't boot any OS. To fix this I had to install Ubuntu all over again and it worked just fine. This time I don't want Ubuntu back at all so I want to know how I remove Grub/Ubuntu so the computer is like it was when I got it.

I haven't found any thread about exactly what I want, so if someone could post how to do it or post a link to another thread that I didn't find it would be awesome.

Just to be clear; I want to totally remove Ubuntu from my computer.

Thanks

---

### Post by shad0w_walker on 2008-01-03
Just reinstall windows. I am assuming this is how your laptop came. I have encountered very few laptops that come with no OS installed. But in the off chance you did get it with out windows on then do a google search for one of the many ways to zero fill your hard drive.

---

### Post by evil316 on 2008-01-03
Ubuntu is an operating system, you don't uninstall operating systems.  Just install Windows over it.  If the boot sector is a problem with grub then use the live CD and format your hard drive.

---

### Post by ogcub on 2008-01-03
Hi,
You should clear things a little: if you want uninstall Ubuntu and leave hard drive empty, you  should use hard-drive manufacturer utility and zerofill your drive. That way you will ensure nobody will recover any your data.

Assuming you have Windows XP on it you should remove grub and Linux partitions. Boot to windows recovery console and run fixboot. It should fix your boot sector. At that time windows should be able to boot. If not then boot to some Ubuntu livecd and check wherever windows partition is set to active. If not set it. Then using windows drive manager remove linux partitions and add windows ones(you might then use some data shredding utility on those new partitions to get rid of important data, if any)

---

### Post by trail0r on 2008-01-03
Hey

The laptop came with windows, but no CD. It has a "setback" function on the menu, but I've read a bit about it and fount out that it only sets back the station windows is installed on. Windows is on C: and Ubuntu is on D:. Actually C: and D: are 2 different hard disks. Is this a problem? Because last time I just formatted D:(Ubuntu) it got screwed up, but maybe it will work if I reinstall Windows after this so I get the windows original boot "thing". Sorry I am a newbie and I don't know what I am doing.
Those replies came really fast by the way, wish windows had the same support ;|

---

### Post by trail0r on 2008-01-03
> **ogcub said:**
> Hi,
You should clear things a little: if you want uninstall Ubuntu and leave hard drive empty, you  should use hard-drive manufacturer utility and zerofill your drive. That way you will ensure nobody will recover any your data.

Assuming you have Windows XP on it you should remove grub and Linux partitions. Boot to windows recovery console and run fixboot. It should fix your boot sector. At that time windows should be able to boot. If not then boot to some Ubuntu livecd and check wherever windows partition is set to active. If not set it. Then using windows drive manager remove linux partitions and add windows ones(you might then use some data shredding utility on those new partitions to get rid of important data, if any)


I have Windows and Ubuntu on different Hard Disks(NOT partitions) so I guess this zerofill thing you are talking about will work out perfectly? Can you explain how I do this and/or where I can get it?

Thanks for great answers! really helpful!

---

### Post by joe.turion64x2 on 2008-01-03
Can you still boot into Windows? From there you can use its Disk Management Utility to destroy your Ubuntu partition. If you were able to create your OEM's restore disks you could even reformat the drive altogether.

Joe.

---

### Post by ogcub on 2008-01-03
> **trail0r said:**
> I have Windows and Ubuntu on different Hard Disks(NOT partitions) so I guess this zerofill thing you are talking about will work out perfectly? Can you explain how I do this and/or where I can get it?

Thanks for great answers! really helpful!

2 hard disks on laptop? That rare :)
Go to manufacturer's website and search for some disk maitenance tool. Or you could use some Ubuntu livecd, and do the same thing from command line.

---

### Post by Kzin on 2008-01-03
If you still have windows on it, and it is dual booting, sell it with both installed.  You may get more money for it based on the fact that its a "Dual boot linux/windows workstation for optimum productivity".

Let the buyer deal with restoring the full windows partition.

---

### Post by PeterJS on 2008-01-03
You could just DBan the disk and sell it as a laptop with no OS.

---

### Post by trail0r on 2008-01-03
The last replies weren't really helpful =( I already got a buyer(friend of mine) and he wants the computer as it was :< And for you who said I could just delete ubuntu from the partition that doesnt work for sure, because then I get the grub problem and wont be able to boot windows or any other OS I may have on the computer.

---

### Post by evil316 on 2008-01-03
I think you are saying you had a C and D drive.  It's actually one physical hard drive.  C and D are partitions.  D would have been your Windows restore partition.  If you put Ubuntu on that partition and you didn't create recovery CD's from your Windows OS before messing with Ubuntu then you are probably out of luck for putting Windows back on it without getting a new copy of Windows from the laptop company and they'll likely charge you $20 for it.

---

### Post by trail0r on 2008-01-03
> **ogcub said:**
> Assuming you have Windows XP on it you should remove grub and Linux partitions.

I have done this before and the result was I couldn't boot any OS at all. :(

Sorry for loads of meaningless double-triple-post's, but I haven't really found what I was looking for.

> I think you are saying you had a C and D drive. It's actually one physical hard drive. C and D are partitions. No they are actually 2 different disk's with 2 different file system's. NTFS on C: and FAT32 on D:.

---

### Post by joe.turion64x2 on 2008-01-03
Which brand the laptop is? In case it is an Acer then the above statement does not apply because Acer's have the recovery partition at the beginning of the drive, it is hidden and not very large. 

Edit: And the restore utility can be used from BIOS.

Joe.

---

### Post by Kzin on 2008-01-03
> **trail0r said:**
> The last replies weren't really helpful =( I already got a buyer(friend of mine) and he wants the computer as it was :< And for you who said I could just delete ubuntu from the partition that doesnt work for sure, because then I get the grub problem and wont be able to boot windows or any other OS I may have on the computer.

In that case we will need more info about the laptop.  If the 2nd part. was supposed to be a restore partition and has been deleted we could be in trouble.  Sometimes, when they don't come with a CD, they come with the relevant files on a small partition at the beginning of the drive...

What is the computer model?

---

### Post by trail0r on 2008-01-03
The laptop is a HP Pavilion 9000 series.

Like I said earlier I am a newbie, and I need a newbie explanation on this :S sorry ^^

---

### Post by joe.turion64x2 on 2008-01-03
Have you tried to run the HP restore utility? I mean, just try it to see if it can find the relevant files.

---

### Post by trail0r on 2008-01-03
> **joe.turion64x2 said:**
> Have you tried to run the HP restore utility? I mean, just try it to see if it can find the relevant files.

Yeah ok I will try that. I was just afraid that it would screw up the boot thing I had problems with earlier. But I'll give it a shot.

---

### Post by trail0r on 2008-01-03
I tried it and found out that it couldn't find the restore partition=(

I guess I have fked it all up now.. I haven't made any restore CD's either.

I there any other way?

---

### Post by erfahren on 2008-01-03
look at the link in this forum member's signature to fix the MBR
[http://ubuntuforums.org/showpost.php?p=4030157&postcount=6](http://ubuntuforums.org/showpost.php?p=4030157&postcount=6)

also if you do have windows you can use MBRfix [http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

---

### Post by erfahren on 2008-01-03
if that recovery partition is still there you might be able to add an entry to GRUB to boot into it.

you're right as far as it not restoring the MBR though, so if you were able to do that (restore Windows) you wouldn't be able to boot into it after restoring. You'd need to have a SuperGRUB CD on hand to fix the MBR (I think that Fix MBR link will lead to that - if not, that info is on hermanzone's site).

just for reference, the GRUB entry for my recovery partition is:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Acer Recovery
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by trail0r on 2008-01-03
Sorry I didn't understand that :(

If I may ask; if I zerofill the disk Ubuntu is on, will I still have a problem with booting windows because of Grub? Because the MBR somehow is linked to the windows disk? I don't know what im talking about, am I?

---

### Post by joe.turion64x2 on 2008-01-03
> **trail0r said:**
> Sorry I didn't understand that :(

If I may ask; if I zerofill the disk Ubuntu is on, will I still have a problem with booting windows because of Grub? Because the MBR somehow is linked to the windows disk? I don't know what im talking about, am I?
Your concern makes sense because the file where the GRUB menu is stored resides in that partition. If you still have the Ubuntu LiveCD I think you can reinstall GRUB in one of the remaining partitions, it is quite easy in fact. Don't know if GRUB supports NTFS partitions though.

Joe.

---

### Post by erfahren on 2008-01-03
Can You Still Boot Into Windows?

---

### Post by trail0r on 2008-01-03
Uhm, why would I want to reinstall grub? ;O I want to remove it completely :<

By the way, what if I zerofill BOTH hard disks, so all disks are totally empty, then install Windows again?

---

### Post by trail0r on 2008-01-03
> **erfahren said:**
> Can You Still Boot Into Windows?

Yes

---

### Post by evil316 on 2008-01-03
> **trail0r said:**
> Yes


Then you need to create a windows recovery CD before you do anything else.

---

### Post by trail0r on 2008-01-03
Hmmmmmm

If I zerofill both harddisks and install windows on it again, will it look for grub, and not be able to boot because it wont find it? Or will grub disappear along with everything else on the computer? :S

---

### Post by erfahren on 2008-01-03
dang, I wish people will stop posting in useless answers ("DBan the disk") - slow down! ....

trail0r -
1) you may think you have two disks, but I don't think you do, you just have C: and "D:" partitions.

2) if you can still boot into Windows then all you need is that MBRfix.exe - run it from within Windows

3) many notebooks come (from the manufacturer) with a D: partition to make backups onto - if that is what Ubuntu is on then all you really need to do is fix the MBR and reformat the partition.

---

### Post by trail0r on 2008-01-03
> **evil316 said:**
> Then you need to create a windows recovery CD before you do anything else.

but like I said, the windows recovery doesnt recover the entire computer, it only recovers the windows hard disk.

---

### Post by trail0r on 2008-01-03
> **erfahren said:**
> dang, I wish people will stop posting in useless answers ("DBan the disk") - slow down! ....

trail0r -
1) you may think you have two disks, but I don't think you do, you just have C: and "D:" partitions.

2) if you can still boot into Windows then all you need is that MBRfix.exe - run it from within Windows

3) many notebooks come (from the manufacturer) with a D: partition to make backups onto - if that is what Ubuntu is on then all you really need to do is fix the MBR and reformat the partition.

Ah this sounds really like what I am looking for, now the question is where do I find MBRfix.exe? :P Yes im a noob for the zillion't time !!!!! ;((

and actually you are probably right, there are probably 2 partitions, but because they have different file systems I thought they were different disks.

---

### Post by joe.turion64x2 on 2008-01-03
_If you have a WIndows XP install CD_ then you can completely reformat your drive from there with no hassle. Just make sure you grab the drivers for your hardware before formatting. GRUB won't be an issue either.

Zeroing the Ubuntu partition makes sense if you had important data (finantial) there.

Joe.

---

### Post by evil316 on 2008-01-03
I would do as Erfahren suggests but I'd also create a Windows recovery CD.  If you ever have to reinstall Windows you already said you don't have any Windows CD's and if you don't make your own you'll likely have to pay for one.

---

### Post by trail0r on 2008-01-03
I can just dl and burn out a windows CD, no problem, but I think I will try Erfahren's suggestion first.

Where do I find MBRfix.exe and what exactly is it that it do? ^^ google.com?

---

### Post by erfahren on 2008-01-03
> **trail0r said:**
> Ah this sounds really like what I am looking for, now the question is where do I find MBRfix.exe? :P Yes im a noob for the zillion't time !!!!! ;((

and actually you are probably right, there are probably 2 partitions, but because they have different file systems I thought they were different disks.
I linked to it here:

[http://ubuntuforums.org/showpost.php?p=4066306&postcount=20](http://ubuntuforums.org/showpost.php?p=4066306&postcount=20)

I've done what your doing a couple times...

you do not have two hard drives

you have two partitions

just fix the MBR and reformat D: to FAT32

(Zerofill it :roll: )

---

### Post by trail0r on 2008-01-03
> **erfahren said:**
> I linked to it here:

[http://ubuntuforums.org/showpost.php?p=4066306&postcount=20](http://ubuntuforums.org/showpost.php?p=4066306&postcount=20)

I've done what your doing a couple times...

you do not have two hard drives

you have two partitions

just fix the MBR and reformat D: to FAT32

(Zerofill it :roll: )

reformat to FAT32? I want it to be NTFS unless FAT32 works with windows? ;OOO

---

### Post by trail0r on 2008-01-03
Hehe I already downloaded mbrfix.exe from that site, googled it <3

Thanks for all replies especially Erfahren's, I will try this right now!

---

### Post by insertAlias on 2008-01-03
> **ogcub said:**
> 
Assuming you have Windows XP on it you should remove grub and Linux partitions. Boot to windows recovery console and run fixboot. It should fix your boot sector.

This is definitely the answer you need.  Boot windows into recovery mode.  Fixboot should re-write the default Windows bootloader. Then, once you reboot, grub will be gone and windows should load just fine.

At that point, you can format the linux partitions/drives or whatever you want.

---

### Post by erfahren on 2008-01-03
once you fix the MBR through Windows - go to the Windows Disk Management - it will be in the Administrative Tools (look in the Control Panel) - you can use it to reformat the D: partition to FAT32 or NTFS -

you can then to a recovery on the Windows

BTW: if you have never burned off the Restore CDs you probably still can - look in the All Programs menu for a folder by the manufacturer for the manual - the manual will say how to do that (as well as how to restore Windows)

---

### Post by trail0r on 2008-01-03
I ran MBRfix.exe and formatted the D: partition already. will grub bug now when I reboot? ;o

By the way I have tried to enter the windows recovery console earlier and failed. How do I do it?

---

### Post by insertAlias on 2008-01-03
Grub shouldn't be there anymore.  The windows bootloader should.

---

### Post by trail0r on 2008-01-03
Oh I just found out - there are in fact 2 separate hard disks. When I entered the disk management it said Disk 0 and Disk 1 and listed all the partitions on these Disks. 
And Ubuntu was on another disk than windows.

---

### Post by erfahren on 2008-01-03
what kind of notebook is this?

did you see what I said about burning the Restore CDs? (you can probably still burn them)

---

### Post by trail0r on 2008-01-03
> **erfahren said:**
> what kind of notebook is this?

did you see what I said about burning the Restore CDs? (you can probably still burn them)


Hmmm I didn't find the manual :o

It's a HP Pavilion dv9060

---

### Post by erfahren on 2008-01-03
[look here](http://h20180.www2.hp.com/apps/Lookup?h_lang=en&h_cc=us&cc=us&h_page=hpcom&lang=en&h_client=S-A-R163-1&h_pagetype=s-001&h_query=Pavilion+dv9060&submit.x=6&submit.y=6)

edit -- ok, ok - I guess it does have two hard drives - sorry I didn't believe you - [pretty nice notebook](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00789868&lc=en&cc=us&dlc=en&product=3308939&rule=8120&lang=en)

I'll give you $500(US) for it - you pay shipping (I want it insured) - lol - just kidding

---

### Post by trail0r on 2008-01-03
I'm too afraid to reboot, but after I've tried I will come back and thank you, unless it got screwed up again :p Is that's the case you won't hear from me in the next couple of days =p

---

### Post by trail0r on 2008-01-04
Hi

After I rebooted I got the same stupid problem with grub=(

Error 17 or something.. So I had to install ubuntu again to be able to boot. 

Ah this sux =|

---

### Post by redondo on 2008-01-04
> **joe.turion64x2 said:**
> Can you still boot into Windows? From there you can use its Disk Management Utility to destroy your Ubuntu partition. If you were able to create your OEM's restore disks you could even reformat the drive altogether.

Joe.
And what if I (different person, similar problem) cannot boot into Windows?
rr

---

### Post by joe.turion64x2 on 2008-01-04
> **redondo said:**
> And what if I (different person, similar problem) cannot boot into Windows?
rr
You should explain your problem a bit more. Why can't you boot in to Windows? What do you want to accomplish? What do you have at your disposal?

If you have to (want to) keep that particular Windows install then you'd have to troubleshoot it.

Joe.

---

### Post by erfahren on 2008-01-04
After you used that MBRfix.exe from within Windows you didn't try rebooting before reformatting the Linux partition? 

you can try the SuperGRUB disk - this post gives info on that (a link to Hermanzone's site) and gives info on another way as well. (I actually linked to this earlier).

---

### Post by trail0r on 2008-01-04
Well this time when I installed Ubuntu again, I only gave it a 2.3gb partition. So I think I'll just leave it be.
The only thing this guy i'm selling my pc to wanted was more space(earlier I had 50gb to Ubuntu). I don't wanna screw this up again so I'll just leave it be. 

Thanks for all help everyone!

---

