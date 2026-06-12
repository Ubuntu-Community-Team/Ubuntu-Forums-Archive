---
title: "Using Aptik as a backup method"
date: 2015-09-16
forum: General Help
---

### Post by Cavsfan on 2015-09-16
Something else I've noticed which sort of just came with experience it that if you back your stuff up to a Linux partition when needed, it is much better.

I've backed my files on my ntfs USB drive and when putting them back after re-installing the file permissions and other stuff were all messed up.

Like the entire contents of the Documents folder had the executable bit set and asked me if I wanted to execute every document I opened. 

Just a thought. :lolflag:

---

### Post by QDR06VV9 on 2015-09-16
> **Cavsfan said:**
> Something else I've noticed which sort of just came with experience it that if you back your stuff up to a Linux partition when needed, it is much better.

I've backed my files on my ntfs USB drive and when putting them back after re-installing the file permissions and other stuff were all messed up.

Like the entire contents of the Documents folder had the executable bit set and asked me if I wanted to execute every document I opened. 

Just a thought. :lolflag:
Oh heavens yes. The last time I had to reinstall about a year or even longer ago.
I had a clone-like  of my original OS in less than 20 mins after Install.
I use [Aptik]("http://www.tecmint.com/aptik-a-tool-to-backuprestore-your-favourite-ppas-and-apps-in-ubuntu/") Restores everything from themes, Settings, Installed Drivers and Apps.
All my conky's the exact way they were compiz and emerald Etc Etc
With no fighting with what you are going through.(Permissions)
Kind Regards

---

### Post by Cavsfan on 2015-09-16
Cool! Thanks for that I bookmarked it.

---

### Post by Cavsfan on 2015-09-17
While I was redoing my partitions and getting rid of 3 or 4 I believe, I set the swap file to be 1MB. :p

Having 4GB memory or more I believe causes no need for a swap file unless you plan on hibernating instead of suspending.

But, making it that small definitely caused the hibernate option to be grayed out, which Cavsfan likey. :p

I initially had an 8GB swap file back in like 2009 and it never used 1% of it so 1MB will do nicely.

---

### Post by Cavsfan on 2015-09-17
> **runrickus said:**
> Oh heavens yes. The last time I had to reinstall about a year or even longer ago.
I had a clone-like  of my original OS in less than 20 mins after Install.
I use [Aptik]("http://www.tecmint.com/aptik-a-tool-to-backuprestore-your-favourite-ppas-and-apps-in-ubuntu/") Restores everything from themes, Settings, Installed Drivers and Apps.
All my conky's the exact way they were compiz and emerald Etc Etc
With no fighting with what you are going through.(Permissions)
Kind Regards

Runrickus, how much space does Aptik use to backup? Just curious. And you can backup to another ext4 partition too right?

---

### Post by QDR06VV9 on 2015-09-17
You know I don't know for sure if you can back-up to ext4 as I have always used my Western Digital My Book(2TB cap) (Fortmat Fat32)
Don't see why not just can't say for sure. With a lot of Bloat My current Back-up is 80 items, totalling 971.1 MB for the whole Kit and Kaboodle.
Hope that was useful.:D

---

### Post by Cavsfan on 2015-09-17
> **runrickus said:**
> You know I don't know for sure if you can back-up to ext4 as I have always used my Western Digital My Book(2TB cap) (Fortmat Fat32)
Don't see why not just can't say for sure. With a lot of Bloat My current Back-up is 80 items, totalling 971.1 MB for the whole Kit and Kaboodle.
Hope that was useful.:D

Thanks! :D

I'll add it to Wily for future use. Plus see what type files system it supports. I was trying to see if there was any way to use it on Arch but don't think so.
Plus I don't think I'll ever need to back that beast up. :p

I'm down to Arch, Wily and Windows 10 finally! I got tired of updating 5-6 systems all the time. Plus I have a spare 10GB partition just in case I need to install something for any reason.

Cheers!

---

### Post by QDR06VV9 on 2015-09-17
Pretty sure any Debian Based file system as long as you can install Aptik on it.(Hope that make sense)
See This [http://www.howtogeek.com/206454/how-to-backup-and-restore-your-apps-and-ppas-in-ubuntu-using-aptik/](http://www.howtogeek.com/206454/how-to-backup-and-restore-your-apps-and-ppas-in-ubuntu-using-aptik/)
Also I found this last nite [http://ubuntuforums.org/showthread.php?t=2057342](http://ubuntuforums.org/showthread.php?t=2057342)
Arch is not Apt based which is how ApTik works. So no dice. Sorry:p
Kind Regards

---

### Post by Cavsfan on 2015-09-18
> **runrickus said:**
> Pretty sure any Debian Based file system as long as you can install Aptik on it.(Hope that make sense)
See This [http://www.howtogeek.com/206454/how-to-backup-and-restore-your-apps-and-ppas-in-ubuntu-using-aptik/](http://www.howtogeek.com/206454/how-to-backup-and-restore-your-apps-and-ppas-in-ubuntu-using-aptik/)
Also I found this last nite [http://ubuntuforums.org/showthread.php?t=2057342](http://ubuntuforums.org/showthread.php?t=2057342)
Arch is not Apt based which how ApTik works. So no dice. Sorry:p
Kind Regards

Thanks Bro! I bookmarked them. I already installed Aptik yesterday. :)

Oh, and about the logging in a couple of times to get things working right. :redface:

I had put the wrong file in startup to start the conkys. There was no delay. Once I put the correct file in there with the proper delay everything is working great. 

[[IMG]http://en.zimagez.com/miniature/screenshot2015-09-1810-25-44.png[/IMG]]("http://en.zimagez.com/zimage/screenshot2015-09-1810-25-44.php")

---

### Post by slickymaster on 2015-09-18
Moved all this, from [here]("http://ubuntuforums.org/showthread.php?t=2294686"), to a thread of its own as they're way off topic from the original one.

---

### Post by Cavsfan on 2015-09-29
> **runrickus said:**
> You know I don't know for sure if you can back-up to ext4 as I have always used my Western Digital My Book(2TB cap) (Fortmat Fat32)
Don't see why not just can't say for sure. With a lot of Bloat My current Back-up is 80 items, totalling 971.1 MB for the whole Kit and Kaboodle.
Hope that was useful.:D

Hey Bro, if that will backup to fat32, surely it will backup to ntfs? Me thinks. :P  I'll definitely find out when Wily's final release date comes by.
My son is home from the Army and my Windows 10 partition went from like 112GB free to about 32GB free. :P Steam games.
It's only temporary though as he has a beast on its' way back from Germany. - Full tower, 4 SSD drives, i7 4790k, nvidia 980ti card. He says it boots up in about 2-3 seconds.
One of these days.....

Anyway I was backing up my stuff manually to my other ext4 partition, but I'll give my USB ntfs a go this time when it happens. 

Cheers

---

### Post by QDR06VV9 on 2015-09-29
> **Cavsfan said:**
> Hey Bro, if that will backup to fat32, surely it will backup to ntfs? Me thinks. :P  I'll definitely find out when Wily's final release date comes by.
My son is home from the Army and my Windows 10 partition went from like 112GB free to about 32GB free. :P Steam games.
It's only temporary though as he has a beast on its' way back from Germany. - Full tower, 4 SSD drives, i7 4790k, nvidia 980ti card. He says it boots up in about 2-3 seconds.
One of these days.....

Anyway I was backing up my stuff manually to my other ext4 partition, but I'll give my USB ntfs a go this time when it happens. 

Cheers
Yes it dose work on NTFS, thought you were asking if EXT4 would work and I just don't have first hand knowledge on that.
When your son get's into town i want to hear about that Beast (Full tower, 4 SSD drives, i7 4790k, nvidia 980ti card)
I know Kids these days are so Spoiled Rotten..LOL
Thanks cavsfan
Specs are impressive for the money.
> GTX 980 TI Memory Specs:7.0 GbpsMemory Clock
6 GBStandard Memory Config
GDDR5Memory Interface
384-bitMemory Interface Width
336.5Memory Bandwidth (GB/sec)
GTX 980 TI Technology Support:
Yes (4-way)NVIDIA SLI® Ready
YesNVIDIA G-Sync&#8482;-Ready
YesNVIDIA GameStream&#8482;-Ready
YesGeForce ShadowPlay&#8482;
2.0NVIDIA GPU Boost&#8482;
YesSuper Resolution Technology
YesNVIDIA GameWorks&#8482;
12 API with Feature Level 12.1Microsoft DirectX
4.5OpenGL
YesCUDA
PCI Express 3.0 Bus Support
Windows 8 & 8.1, Windows 7, Windows Vista, Linux, FreeBSD x86
Oh I forgot, check this out [http://ubuntuforums.org/showthread.php?t=2295804&page=3](http://ubuntuforums.org/showthread.php?t=2295804&page=3)  post#23

---

### Post by Cavsfan on 2015-10-01
Ntfs good deal I've got about 300GB free space on my Fantom 1TB USB drive. I'll use that right after Wily is released.

My son is in the Army and he initally had a 780 ti which was better than the Titan at the time. He sold that and with that money and some more got the 980 ti. 
He also has a 2560x1440 monitor. He's a gamer and he's quite good at it. If it weren't for directx 12 he'd probably be into Linux. 

Yeah I seen that the other day LoL! I just didn't want to reply something off topic. :p

Take care dude! :D

---

### Post by Cavsfan on 2015-10-14
If I'd have known yesterday that I would not be able to boot into Wily Xubuntu today, I would have backed the stuff up with Aptik.

I'm getting some odd message saying I'm in recovery mode. It won't let me me login as it says my info is not right. I'll do some more investigating but a backup would've been nice. :)

---

### Post by QDR06VV9 on 2015-10-14
Gosh Cavsfan sorry to hear that, But you should be able to see whats on that Drive booting to another OS with that Drive connected to it, Then moving the important stuff to external Drive. After 5 years in testing I have learned to become Stern with my backup habits, The final lesson for myself was losing 2TB worth of personal and work related data.(years of storage)
You can even do that with a Live CD. What's that Old Saying, Hind-Sight is always 20/20.](*,)
There are days when I have force myself to do my daily backups to prevent that heart breaking occurrence from ever happening again.

---

### Post by Cavsfan on 2015-10-14
> **runrickus said:**
> Gosh Cavsfan sorry to hear that, But you should be able to see whats on that Drive booting to another OS with that Drive connected to it, Then moving the important stuff to external Drive. After 5 years in testing I have learned to become Stern with my backup habits, The final lesson for myself was losing 2TB worth of personal and work related data.(years of storage)
You can even do that with a Live CD. What's that Old Saying, Hind-Sight is always 20/20.](*,)
There are days when I have force myself to do my daily backups to prevent that heart breaking occurrence from ever happening again.

Indeed hind sight is always better lol! I just backed up everything that Aptik would have if I could have gotten to it.
Everything except the PPAs and apps that I installed. But once I install them again, I have the .config folder all backed up. It should be interesting. 

Besides this is a developmental intall so I didn't have much invested in it. I've done this many times. 
I have a spare 10GB ext4 partition that I backed up everything to, so no file permission problems should happen.

So here goes nutten! :) Hopefully I can get a daily ISO to install.

It's always wise to have more than one Linux install!

---

### Post by Cavsfan on 2015-10-14
On second thought I think I'll wait until tomorrow when the RC comes out. 

Heck I may wait until a week from tomorrow when the final release comes out.

---

### Post by QDR06VV9 on 2015-10-14
BTW you can back up apt also, By just grabbing the whole apt file. "etc/apt"
Has to be done as root.
I am sure you already knew that!
Cheers and happy reinstalling.
Best Regards

---

### Post by Cavsfan on 2015-10-14
> **runrickus said:**
> BTW you can back up apt also, By just grabbing the whole apt file. "etc/apt"
Has to be done as root.
I am sure you already knew that!
Cheers and happy reinstalling.
Best Regards

No, I didn't know that. Thanks dude! I will do that. Re-installing developmental versions are part of the way it is though.

They break and you re-install 'em. 

Kind regards

---

### Post by Cavsfan on 2015-10-16
Never try to backup everything from a failed system. :P

I didn't really restore everything but I must have restored whatever caused me to re-install in the first place.

I would say backup when it's good and definitely not when it has failed. I had to re-install twice because I messed up.

Rather than get off topic I'll post anything further in this thread: [http://ubuntuforums.org/showthread.php?t=2294686](http://ubuntuforums.org/showthread.php?t=2294686)

If this were anything other than a developmental install, I'd be worried but I'm not really. Live and learn...

---

### Post by Cavsfan on 2015-10-22
I think I'm going to give this a go - Aptik as I have a nicely working system at this time.

My son's beast of a PC got here a couple of days ago so we upgraded to 150mbps down and 10mpbs up although my network card is 10/100MB and will not handle it.
I still get 89mbps down/11mbps up. 

My son gets 189mpbs down and 11mpbs up. :p Ermahgerd that is fast!! He had 100mbps down in Germany and thought that was fast.

I guess I'll have to reboot first after some updates and then I'll back this puppy up or the werewolf I mean. :p

---

