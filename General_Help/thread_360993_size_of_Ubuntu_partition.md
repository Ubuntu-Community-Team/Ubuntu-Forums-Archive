---
title: "size of Ubuntu partition"
date: 2007-02-13
forum: General Help
---

### Post by mikawber on 2007-02-13
I decided to wipe my hard drive and install and daul boot Ubuntu Dapper Drake and Windows Vista. I have an 80GB hard drive on my laptop so I made a / partition of 20GB and a swap 1.5GB. This left me roughly 60GB for my Vista partition. However, in the past 3 weeks since I installed I have only used Windows for a total of like 3 days. I still need windows for a few applications and such so I don't want to get rid of it. But will 20GB of space be enough for a new user like me or should I resize it? Also, is just the / partition enough or should I seperate it into other partitions? Thanks for any help!

---

### Post by CowboyCoffee on 2007-02-13
When I installed, I set up a /windows partition, a swap partition, a small / partition (10 GB), and a much larger /home partition to store all my documents. This way if I ever upgrade or reinstall Ubuntu (or any other Linux flavor I think), I will still have my files and settings. anything you have in the Windows partition should also be available to you while in Ubuntu, so you may want to keep that in mind if you don't want to resize anything.

---

### Post by 3rdalbum on 2007-02-13
Just having a / and a swap partition is good enough. 20 gigabytes is well enough for Ubuntu, although I'm using just over 20 gigs on mine (I have a lot of clutter and a fair few disc images of other distros!).

Your swap is a bit big though - you don't need more than 512 megabytes of swap. (mine is 600 megabytes, and since I've got over a gig of RAM only 17 megabytes of the swap ever gets used - cursing!)

---

### Post by Imsati on 2007-02-13
>you don't need more than 512 megabytes of swap

Really? I have 2 gig set aside for mine. Overkill? Root is 10 Gig and Home is 25 Gig.

---

### Post by mikawber on 2007-02-14
well I really had no idea what a swap partition was before so I just picked an amount lol. I also have an external hard drive that I store a lot of my information on so I'm not worried about having enough space for my personal items. I was more concerned with having enough space for program installations etc.

---

### Post by nalioth on 2007-02-14
> **Imsati said:**
> >you don't need more than 512 megabytes of swap

Really? I have 2 gig set aside for mine. Overkill? Root is 10 Gig and Home is 25 Gig.
I go by 3x your physical ram, but no more than 768mb.  If you have 2gb plus of physical ram, it's not gonna need anywhere near 768mb of swap file.  There are exceptions to the rule, but if you live one of those exceptions, you know who you are.

I have not used Windows since the year 2000, but i keep a windows install on a laptop for friends who stop by to check their mail and such.  

Windows has 4gb
swap is ~512mb
/ is 4gb 
/home is the rest of the disc

I also install my Windows using the 'fat file system' which makes things lots easier when I run clamav on the windows partition from linux.

---

### Post by Imsati on 2007-02-15
Ahhh. I was under the assumption it was 2x physical memory. I've currently 512 mb, but am looking to jump up to 1 GB in the near future, hence the 2GB swap. Eh--oh well. Not desperate for HDD space, so I'll leave it be I suppose.

--Jay

---

### Post by dcstar on 2007-02-15
I hate threads like this - there is no "rule" for Swap space!

Swap is just an extension of your physical memory, and the overall amount of **Virtual Memory** is basically determined by the total demands of all the processes you will ever be running simultaneously on your system.

If you have 1G of RAM and don't run extra-ordinarily memory intensive applications like video editing, then you probably can live without a Swap partition and suffer no adverse effect at all.

The so-called "Rule" for allocating Swap space for a Unix/Linux system may have had some merit 15 years ago when RAM was far more expensive that it is now, but unless you are building an under-resourced PC for the job you actually need it to do, this is a non-issue.

The kernel will try and use Swap space to move rarely used data areas out of main memory to the slower swap space to free up the faster memory for more (potentially) productive uses, but if you still have more than enough free RAM for the jobs you are doing then this ends up being redundant (and may even slow things down overall as it unnecessarily uses disk I/O).

Bottom line: If you are going to use your Ubuntu system for "normal" things - Web browsing, e-mail etc. etc. - and have at least 512 MB RAM, then use about that for you swap space. Chances are you'll never see it get close to filling it up.

---

### Post by Artemis3 on 2007-02-15
Oh, linux is smart enough to not use it if its not needed, even if you allocate a lot of swap space.

There is nothing to worry, you can check the swap usage all the time. I have 1GiB ram and the automatic partition from dapper allocated 2.9GiB... i currently have 17MiB of swap file used, with around 582MiB of physical, typical gnome with firefox, bunch of other windows, azureus with many days running, etc.

I would advise to have around 1GiB of swap regardless of memory. with the gparted livecd, you can always later resize. If you have many hard drives, and they use different pata cables (or they are sata / scsi) it is good to have small swap partitions on each hard disk.

---

