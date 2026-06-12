---
title: "Vista and Ubuntu"
date: 2007-05-29
forum: General Help
---

### Post by sheine on 2007-05-29
I read somewhere on the internet that if you set up a dual boot with Vista and Ubuntu the automatic updates of Vista will make Ubuntu inaccessible. Is this true? If so, it make it senseless to set up dual booting and leaves one with a Vista or linux choice. Unfortunately new computers come with Vista.

---

### Post by kuja on 2007-05-29
> **sheine said:**
> I read somewhere on the internet that if you set up a dual boot with Vista and Ubuntu the automatic updates of Vista will make Ubuntu inaccessible. Is this true? If so, it make it senseless to set up dual booting and leaves one with a Vista or linux choice. Unfortunately new computers come with Vista.
Not all of them, for example, as of about a week ago, you can get a computer with Ubuntu from Dell :popcorn:

---

### Post by LaRoza on 2007-05-29
If that is true, which it might, it is another reason to get rid of Vista.

Personally, I have already overwritten Vista Home Premium and have my other computer with two hard drives set up with Ubuntu on the first drive and Vista on the second, where it can't do any harm.

[http://www.vistaboard.org/windows_vista_forum/124-vista_testimonial.html#post247](http://www.vistaboard.org/windows_vista_forum/124-vista_testimonial.html#post247)

Interestingly, I just posted the above, before responding to this. 

If you want Vista, I think you can turn the automatic updates off, or you can get another version of Windows, like XP preinstalled.

---

### Post by sheine on 2007-05-29
The only reason that I would have any form of Windows on my computer is that some web sites insist on Windows. Wine does not work for everything. Up to now, Windows is also better than linux for wireless.

Although it is heresy in my political circles, I prefer to buy computers at Wal-Mart. They take things back without a hassle.

I looked up LaRosa's other posting and agree.

---

### Post by gdoermann on 2007-05-29
> **LaRoza said:**
> If that is true, which it might, it is another reason to get rid of Vista.

Personally, I have already overwritten Vista Home Premium and have my other computer with two hard drives set up with Ubuntu on the first drive and Vista on the second, where it can't do any harm.

[http://www.vistaboard.org/windows_vista_forum/124-vista_testimonial.html#post247](http://www.vistaboard.org/windows_vista_forum/124-vista_testimonial.html#post247)

Interestingly, I just posted the above, before responding to this. 

If you want Vista, I think you can turn the automatic updates off, or you can get another version of Windows, like XP preinstalled.

So does Vista only affect the boot sequence if it is on the first partition of the first drive?

---

### Post by WiFi Ed on 2007-05-29
I dual boot Vista and Ubuntu on my Dell E520. Vista lives on the first hd and Ubuntu on the second one. Grub resides on hd0, the Vista hd.

Vista has installed several updates since this cohabitation began (in February) and has never broken grub or my ability to boot Ubuntu. It looks like the concerns expressed about this are untrue.

Of course, it may all burst into flames tomorrow, but so far no problems...

---

### Post by sheine on 2007-05-29
My new computer has one hard drive. Therefore some of the two drive experience might not be appropriate.

---

### Post by WiFi Ed on 2007-05-29
> **sheine said:**
> My new computer has one hard drive. Therefore some of the two drive experience might not be appropriate.

Possibly. I had Ubuntu and XP on one hd at first with no problems but added a second drive when I upgraded to Vista, giving each OS it's own drive. 

One thing you have to be careful about is not using the disk partition tool that comes with Ubuntu to resize your Vista partition. Vista will probably not boot after doing so and repairing it can be difficult. Use a Vista-compatible partitioning tool to make room first. Acronis makes a good one and I'm sure there are others available.

---

### Post by prankst3r on 2007-05-29
> **sheine said:**
> The only reason that I would have any form of Windows on my computer is that some web sites insist on Windows. Wine does not work for everything.

Take a look at [ies4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") - it allows an IE6 install and IMO ies4linux works better than IE in Wine.

---

### Post by Delkster on 2007-05-30
> **WiFi Ed said:**
> One thing you have to be careful about is not using the disk partition tool that comes with Ubuntu to resize your Vista partition. Vista will probably not boot after doing so and repairing it can be difficult. Use a Vista-compatible partitioning tool to make room first. Acronis makes a good one and I'm sure there are others available.

Is this true, and if it is, are there any reliable and free (as in free of charge, preferably also free software) alternatives? I have a work laptop with Vista that I'd like to install Ubuntu on (with dual-boot) but this is my greatest concern. Having used mostly Linux for personal use since 2002 or so, I have little experience with any recent versions of Windows and have almost never even touched NTFS partitions so I'm a little scared.

---

### Post by loathsome on 2007-05-30
I'm sure everything will be fine if you set up Ubuntu on a seperate partition. I've never experienced any problems with dual booting, and I've had like 10 operating systems going on at the same time ;)

---

### Post by Delkster on 2007-05-30
> **loathsome said:**
> I'm sure everything will be fine if you set up Ubuntu on a seperate partition. I've never experienced any problems with dual booting, and I've had like 10 operating systems going on at the same time ;)

It's exactly the resizing of the Windows partition (in order to make room for a Linux one) that I'm worried about. I know that it has been done succesfully with other Windows operating systems but I don't know much about Vista and haven't seen many reports about that either.

---

### Post by loathsome on 2007-05-30
> **Delkster said:**
> It's exactly the resizing of the Windows partition (in order to make room for a Linux one) that I'm worried about. I know that it has been done succesfully with other Windows operating systems but I don't know much about Vista and haven't seen many reports about that either.
I resized my (previous) Vista partition using **gparted** without any problems at all.

---

### Post by Delkster on 2007-05-30
According to an [APC Magazine article](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first), Vista (or at least one of the gazillion different editions) seems to have its own disk manager that can also shrink partitions. I'm genuinely surprised. I may need to take a look at that.

---

### Post by WiFi Ed on 2007-05-30
Vista itself has a partitioning tool that can resize your NTFS partition, but I've never used it so I don't know how well it works. Here's a link to a how-to:

[http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/]("http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/")

Here's another one that might be useful:

[http://www.partition-manager.com/]("http://www.partition-manager.com/")

As for using gparted to resize Vista partitions, I tried it and it hosed my Vista install. Maybe that was my fault (perhaps I chose the wrong options or something) but I'm not the only one it's happened to. There are more than a few posts in this forum about it.

---

### Post by flat4 on 2007-05-30
> **loathsome said:**
> I resized my (previous) Vista partition using **gparted** without any problems at all.

I tried using the live cd and gparted but when it tried to partition it would failed. I have the latest updates for vista. Someone told me to use the alternative cd install but i have not tried yet.

---

### Post by wpeteroy on 2007-05-31
Ok all - take a look here - [http://5363.blogspot.com/2007/05/adding-feisty-to-your-vista-fast-and.html](http://5363.blogspot.com/2007/05/adding-feisty-to-your-vista-fast-and.html)

I just put it together yesterday - I haven't tried it all from a clean install but I'm guessing that if you just use gparted from the start with two separate drives and make sure to install Vista first you should be in like flint -

Grub will detect the windows boot loader and just start that normally and then your windows won't mess with your ubuntu and your ubuntu won't mess with your Vista.

Hope that helps

---

### Post by WiFi Ed on 2007-05-31
> **wpeteroy said:**
> Ok all - take a look here - [http://5363.blogspot.com/2007/05/adding-feisty-to-your-vista-fast-and.html](http://5363.blogspot.com/2007/05/adding-feisty-to-your-vista-fast-and.html)

I just put it together yesterday - I haven't tried it all from a clean install but I'm guessing that if you just use gparted from the start with two separate drives and make sure to install Vista first you should be in like flint -

Grub will detect the windows boot loader and just start that normally and then your windows won't mess with your ubuntu and your ubuntu won't mess with your Vista.

Hope that helps

Yes, that does work very well, it's how I'm doing it now. The OP's concern is that he wants to dual boot using only one hard drive, with Vista already installed and occupying the whole disk. The touchy part is re-sizing the Vista partition to free up room for Ubuntu, but it can be done safely if a Vista-compatible partition tool is used.

---

### Post by wpeteroy on 2007-05-31
Read the How-to - it's directly for a computer with 1 hard drive with vista occupying the whole thing. You can just use the latest gparted livecd - i did it all last Friday.

Yeah gparted "breaks" vista as in it changes the MBR so that its not recognizable to vista but that's easily repaired...

---

### Post by flat4 on 2007-05-31
I went ahead a reformatted my drive and went this way. install Ubuntu first.

then vista and then followed this instructions.
[here]("http://apcmag.com/5045/how_to_dual_boot_vista_with_linux")


Now i need help in another form, I install Ubuntu set a password but now I can boot into linux but forgot my password. How do you reset it using the live cd?  :o:o:o:o

---

### Post by esavato on 2007-06-02
I would suggest using Vista's own disk resize utility, to avoid all of the problems with the MBR becoming corrupted,  which is under the Control Panel --> System Maintenance.  You can take your vista partition and resize it on the fly, creating a / and swap partition.  I actually split off about 35G of space, quickly set it up as NTFS with no drive label so that I could resize it again into a / .. /home and swap.  I then used the live cd installer to change them to ext3 and swap.  

Grub was able to find the Vista/Longhorn boot manager and everything went off without a hitch..

---

### Post by sheine on 2007-06-04
> **esavato said:**
> I would suggest using Vista's own disk resize utility, to avoid all of the problems with the MBR becoming corrupted,  which is under the Control Panel --> System Maintenance.  You can take your vista partition and resize it on the fly, creating a / and swap partition.  I actually split off about 35G of space, quickly set it up as NTFS with no drive label so that I could resize it again into a / .. /home and swap.  I then used the live cd installer to change them to ext3 and swap.  

Grub was able to find the Vista/Longhorn boot manager and everything went off without a hitch..

I think that I did this butgGrub did not find Vista for me.
I also used the method that always worked with WindowsXP. I used gparted to reduce the size of Vista and then put linux in the freed space. Grub booted linux but not Vista.

In both methods when I chose Vista from grub, I got Vista's repair site. Standard didn't repair anything and full gave me Vista on the whole harddrive.

Vista is nothing but trouble as far as I am concerned.

---

