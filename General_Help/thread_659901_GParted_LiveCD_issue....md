---
title: "GParted LiveCD issue..."
date: 2008-01-06
forum: General Help
---

### Post by LoneWolfUK on 2008-01-06
Hi all.

I would like to dual boot Win XP with Ubuntu 7.10 and I am trying to change and create my partitions using GParted LiveCD.
I have put it onto a CD, booted it, and I load the auto configuation option.

It asks for my language, etc. then I get to a message on the command prompt type screen that says;

> You need graphical enviroment to start GParted.
The graphics enviroment configuration should have been started automatically.
Unfortunetly It did not, since you are back at the bash !

So please run Forcevideo script, and you will be asked for video driver and resolution

Does anyone know why this is happening? and what is "Foricevideo script" ?

I have used Gparted before, about 18 months ago and it worked without problem... :confused:

Any help would be very much appreciated.

EDIT: I found a screenshot from another site of what it looks like - when it gets to this part, it does nothing...

[IMG]http://gparted-livecd.tuxfamily.org/larry/livecd/screenshots_0348/livecd-03.png[/IMG]

---

### Post by erfahren on 2008-01-06
[http://gparted-forum.surf4.info/viewtopic.php?id=1032](http://gparted-forum.surf4.info/viewtopic.php?id=1032)

---

### Post by c0met on 2008-01-06
Hi,

You don' t need to run GParted as a LiveCD. Ubuntu 7.10 already has it available. Simply boot from Ubuntu's LiveCD and look under [COLOR="Purple"]**System >> Administration**[/COLOR].

A few of pieces of advice.

(1) Defrag your hard drive in Windows prior to running the partitioning program.

(2) Backup all your important files just in case the worst happens

(3) I use GParted to create all my partitions and then when I get to the Partion Manager in the install program, I choose "manual" and simply select the partition on which I want to install Ubuntu. You will probably need to choose "Edit" and make the selected partition "/" and choose to format it (ext2 or ext3). 

(4) I have found it a good idea to have a separate "/home" partition. The reason for this is that while the operating system is installed under "/", many of the settings files are stored under "/home". This means that if you reinstall Ubuntu at any time, the settings for many of the programs that you had installed will be maintained.

For some great tips on installing, have a look at...

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

It's worth taking the time to read your way through the above website. 

Good luck!

---

### Post by LoneWolfUK on 2008-01-06
Thanks for the help.

I did try typing "Forcevideo" in the command prompt but it said unknown command or something...

Anyway, it doesn't matter now because I will use the one that came on the LiveCD -- I didn't know that, so thank you c0met.

I have already defragged my HD twice and this is what it looks like;

[IMG]http://img179.imageshack.us/img179/4213/defragwb8.jpg[/IMG]

I was expecting it to be more to the front of the partition -- does it look OK?

The data is all backed up on my external HDD.

How large will the /home partition need to be, roughly?

I think I will read a few more guides before I attempt anything. :popcorn:

Thanks for your help.

---

### Post by erfahren on 2008-01-06
> **c0met said:**
> 
A few of pieces of advice.

(1) Defrag your hard drive in Windows prior to running the partitioning program. ...

It's always a good idea to run scan disk two or three times first (in my experience all the errors may not get fixed the first time around. - the results can be checked through the Administrative Tools > Event Viewer under a "Winlogon".

Some people have actually reported having problems using the Guided Partitioning when they had too many filesystem errors on their Windows partition.

---

### Post by c0met on 2008-01-06
Hi LoneWolfUK,

If you have everything backed up, that's fine. If you wanted to clone your Windows drive rather than simply back it up, I found a Windows freeware program the other day that's excellent. It's XXClone.

I have an 80 GiB disk that I run Ubuntu on. I have set 28 GiB aside for "/", 2 GiB for the Swap File (which some people say is large; I'm not sure as to what is the best). The rest of the space is set to "/home".

I learned the value of having "/home" as a separate partition or drive just a couple of days ago when I had to re-install. You see, when you re-install, Ubuntu reformats "/" and completely cleans it. I was relieved to discover that setting for email, bookmarks, and important settings for other programs that I had installed did not disappear because they were stored on "/home". It was quite a relief and also made reinstalling the programs that much easier.

Good luck! and happy reading :)

---

### Post by erfahren on 2008-01-06
> **LoneWolfUK said:**
> 
How large will the /home partition need to be, roughly?

The size of your /home isn't all that critical, especially when you have plenty of space in the FAT32 partitions to store data on (remember, with Linux, you can natively read/write to partitions formatted to FAT32.) - All I have for my /home(s) is about 10GB each, but also have about a 30GB FAT32 partition to use. 

The size of the root is a little more important, you only need *at the most* about 10GB , but 5GB is enough. Any more than that would be just wasted space.

note: when it comes to mount the FAT32 partition(s) this guide might be helpful: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by LoneWolfUK on 2008-01-06
Thanks for all the help.

I just booted the LiveCD and opened the partition manager. My partitions look very messy! I think it's from the last time I had Ubuntu installed and some of the partitions I believe are to do with Dell, such as the media center, etc. 

I don't really know if I need those extra partitions, so I am thinking of deleting them because I have never used them.

[IMG]http://img134.imageshack.us/img134/7656/96508835sw1.jpg[/IMG]

I can't seem to resize any of the partitions and use up the unallocated space. As you can see in the screenshot, the /dev/sda5 partition is using just 810.30MiB with 5.85GiB unused! I would like to add that un-used space to my Windows partition, but I cannot seem to do this -- I would also like to add that unallocated space to the Windows partition.

How do I do this?

---

### Post by erfahren on 2008-01-06
ok, someone gave a link to hermanzone's site which goes over partitioning rules

real quick here - you can only have 4 primary partitions or 3 primary and one extended partition on a drive (the extended partition counts as a primary)
 - you can have many *logical* partitions within an extended one.

Windows needs to be on a primary - with Linux it doesn't matter, it can be on a logical partition

now that unallocated space (you see it's only a few megs) is used to create the extended

to add (or "grow") that NTFS one (sda2) you could just delete the whole extended partition (sda3) and redo it how you want. - or shrink that sda5 then shrink the extended

(extended partitions work like this: let's say you have a 20GB extended partion - you can then divide that up into, say, two 10GB paritions -
it would show as:
Extended - 20GB
 |--> Logical - 10GB
 |--> Logical - 10GB

(the logicals are within the extended)

---

### Post by LoneWolfUK on 2008-01-06
Thanks erfahren,

I read through one last guide, sorted out my partitions and installed Ubuntu. All is working perfectly so far 8-)

---

### Post by GlennW on 2008-01-08
I've been following this thread with interest and hope that my issue is not completely unrelated. I have a dual boot with XP and Gutsy, on an 80GB HDD. I had partitioned my HDD originally under XP with a C:\ and D:\, with D:\ now empty and taking up space which I wish to add to Gutsy. I'm a complete newb to this whole partition thing. 

I've attached Gparted's assessment of my system and I have no idea what is what except for the drive that I want to add to Gutsy (Work Space, named under XP).

What do I do to add "Work Space" and the unallocated portion as well to Gutsy?

---

### Post by erfahren on 2008-01-08
> **GlennW said:**
> I've been following this thread with interest and hope that my issue is not completely unrelated. I have a dual boot with XP and Gutsy, on an 80GB HDD. I had partitioned my HDD originally under XP with a C:\ and D:\, with D:\ now empty and taking up space which I wish to add to Gutsy. I'm a complete newb to this whole partition thing. 

I've attached Gparted's assessment of my system and I have no idea what is what except for the drive that I want to add to Gutsy (Work Space, named under XP).

What do I do to add "Work Space" and the unallocated portion as well to Gutsy?
you'd want to do that using the GParted LiveCD

once you boot into it just delete the "WorkSpace" partition (/dev/sda2) and then click on your Ubuntu partition (/dev/sda3) and "Edit" - grow it into all of the unallocated space that would now exist before it.

I've resized a existing Ubuntu partition without problems - you shouldn't have any.

(in that screenshot your "WorkSpace" partition isn't empty - I guess you probably realize that.) 


(What font are you using? That looks pretty cool!)

---

### Post by GlennW on 2008-01-09
> **erfahren said:**
> you'd want to do that using the GParted LiveCD

once you boot into it just delete the "WorkSpace" partition (/dev/sda2) and then click on your Ubuntu partition (/dev/sda3) and "Edit" - grow it into all of the unallocated space that would now exist before it.

I've resized a existing Ubuntu partition without problems - you shouldn't have any.

(in that screenshot your "WorkSpace" partition isn't empty - I guess you probably realize that.) 


(What font are you using? That looks pretty cool!)


Thanks erfahren for your response. I went back to XP (which I am so loathe to do now since it seems so clumsy) and formated the drive to the same format as the Ubuntu partition so therefore it's empty.

The font, BTW, is Tork.

---

