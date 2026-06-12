---
title: "Windows ON Ubuntu Help/advice/Suggestions"
date: 2007-09-07
forum: General Help
---

### Post by Corbin on 2007-09-07
Hey, While i HAVE to continue running xp. But prefer ubuntu. I was wondering if anyone could fill me in/give me some advice as to my set up weather i should stick to dual booting or run windows ON ubuntu.

Currently i have XP and Ubuntu installed in as a duel boot. While my XP partition is a NTSF and ubuntu is a fat32.  and So i was doing some research and read that it is better to just use FAT32 all around for xp AND Ubuntu. That way Ubuntu can communicate better with the "LOCAL DISK" drive. (is this true? Will XP install on a fat32 partition). 

Ive also been doing some research to set up windows ON Ubuntu, and found there to be many many many many programs to do it. And so i was wondering if anyone could suggest a particular program to do it. 

So i am deciding to either 

Completely wipe my hard drive (ubuntu and all) and change the file type to fat32 and install windows ON ubuntu. 

OR

To Format my hard drive to FAT32 and partition it into 3 drive. One for windows and Ubuntu and then a "Downloads" partition "for all my downloads.. DUH!.  
(which is basically what i have now... other then my "downloads" partition and "local Disk" partition are both NTSF

So all in all. I was looking for some advice as to whether i should change my set up to the first one. Or keep it (and change my windows over to FAT32). The reason why i would like to run windows ON Ubuntu is that it allows me to (run them both at the same time) and not have to shut down and boot the other... The reason why i ask is because i am not sure sure how windows runs ON Ubuntu. Whether is it glitchy and slow etc. because Photoshop, premier pro will be used allot on windows... and windows needs to run pretty good... 

So if you guys think running windows on ubuntu is a good idea what programs do you suggest and why. 


Sorry this message turned out longer then i though... 

-Thanks

---

### Post by bogdan_5844 on 2007-09-07
i suggest to run Windows XP in a virtual machine(try InnoTek VirtualBox,never failed me)but you need RAM(at least 512) and processing power(at least 1 GHz)to do that,but only try it if you are prepared to deal with problems sharing files between the 2 os,internet problems,and if you wanna play games on XP,forget it,VirtualBox emulates an old Graphics Card and it won't work for many things...if you want to go simple,dual boot is the solution.
i have dual boot on my laptop(using xp solely for Photoshop and games):popcorn:

---

### Post by Corbin on 2007-09-07
yea Photoshop, After Effects, Premier pro, and a few other programs are heavelily used on my comp... so i need it to run good.

---

### Post by bogdan_5844 on 2007-09-08
then dual-boot is the way to go ;-)

---

### Post by strabes on 2007-09-08
Definitely do NOT use fat32 as your filesystem for windows OR ubuntu (I didn't know the latter was even possible...)

If your harddrive is >100gb, you should set it up like this:

20gb: NTFS Windows
10-15gb: ext3 ubuntu 
2gb: swap
Rest of HDD: ext3 Data/downloads partition

Use the driver from fs-driver.org to read and write to ext3 from windows and install ntfs-3g and ntfs-config to read and write to NTFS from ubuntu.

---

### Post by brickbat on 2007-09-08
Strabes is right. ext3 is the best file system of the 3 but unless you have 4gb ram 2gb swap is excessive.  1/2 your ram is the general rule.

I run xp in a vm and i swear it is faster than native with an antivirus.  i only use it an hour or 2 a week for apps i cant find in linux.  usb doesnt always work. in virtualbox.

---

### Post by Corbin on 2007-09-08
Yea etx3 is what i ment...... i have no idea why i said fat32.......... (OOPS) 

But no... sadly enough my laptop does not have 100 gigs (got it 5ISH years ago) 
But im running 

40 gig hard drive... I Know it sucks
Pen. 4 (2.4 GHz)
768 MB RAM
64mb Nvidia Gforce 4 440 GO

So you all suggest duel booting?

---

### Post by strabes on 2007-09-08
With that amount of ram, probably. I don't know where you'll store all your files though. Probably on the ubuntu partition because ubuntu doesn't need as much space as windows.

---

