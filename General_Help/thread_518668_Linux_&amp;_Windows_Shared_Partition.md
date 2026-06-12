---
title: "Linux &amp; Windows Shared Partition"
date: 2007-08-06
forum: General Help
---

### Post by Naatan on 2007-08-06
Hi, I'm thinking of setting up a shared partition for my windows and linux OS, so that I basically have 3 partitions, one with the linux OS, one with the windows OS and one shared, which will contain all program files and what not.

This shared partition would probably be NTFS or FAT32 (tips are welcome..)

However, in Windows it's quite easy to simply install all additional software to a different partition, but in Linux I can't 'choose' where everything is installed, it's all pre-configured..

So is there some way I can configure where all software is installed? Both by deb files and from source installations (./configure - make - make install).

Also, what type of partition would you recommend using as the shared partition, keeping in mind all additional software will be running from this partition ?

And last but not least, what size should I use for the Ubuntu partition, keeping in mind that it will contain purely the system files.

So to sum it all up..

[LIST=1]
[*]Can I configure a different partition as the default target for application setups?
[*]What type of partition would you recommend to use as the shared partition between Win and Linux
[*]What partition size should I reserve for the Ubuntu installation purely the OS)
[/LIST]

Thanks a lot in advance..

---

### Post by DeusEx on 2007-08-06
1. why would you want to do that? I don't think I would like windows to be able to access my linux files.
2. FAT32 works fine with both OS's, NTFS is a bit sh*tty IMHO
3. at least 5GB, though 10GB saves a lot of headaches.

Note: you'll need a swap partition to.

---

### Post by Naatan on 2007-08-06
I 'need' that because I only have a 40gb hard disk in my laptop and I prefer keeping ALL my files in one central position

---

### Post by Naatan on 2007-08-06
bump

---

### Post by LaRoza on 2007-08-06
> Can I configure a different partition as the default target for application setups?
What type of partition would you recommend to use as the shared partition between Win and Linux
What partition size should I reserve for the Ubuntu installation purely the OS

0. Probably, but don't. Linux and Windows apps are different and should be kept seperate.
1. FAT32
2. 5-10 GB.

You should install apps to the default locations most of the time. Just make a little extra room in each OS partition for future installs.

---

### Post by Naatan on 2007-08-06
I know linux and windows apps are different, I am not looking to install them to the same directory or anything, just the same partition, I appreciate your opinions but I'd really like to know if it is possible to install applications to a non-default location and if so.. how?

---

### Post by jespdj on 2007-08-06
Why would you want your Windows and Linux *programs* on one partition? It's strange and not very useful to mix programs for two different operating systems on the same disk.

More logical would be if you have one Windows partition for your Windows programs, one Linux partition for your Linux programs and one FAT32 partition for your *data* that you want to share between Windows and Linux.

If you're doing this because your laptop harddrive is so small (40 GB), consider buying and installing a new, bigger harddrive for your laptop. Harddrives are not so expensive these days (&#8364; 50 for 80 GB or so) and installing a new one isn't that hard. Your laptop probably has a lid on the bottom that you can open with a screwdriver to install it - you won't have to screw the whole laptop open.

---

### Post by Naatan on 2007-08-06
The laptop is from my work therefore I cannot simply buy a new hard disk, the reason I want them on a shared partition is because I test a lot of software so it takes a lot of disk space, if I would have two seperate partitions I could for example have one of the hard disks full while the other still has 5gigs left, now if they were shared, then I would have 5 gig left on both OS'es rather than just the one I dont need it at.

Long story short, that's just the way I need/want it :p And the question remains (simply) can it be done?

---

### Post by por100pre1 on 2007-08-06
Use FAT32 for that partition.

---

### Post by pointone on 2007-08-06
You might consider using only one partition and simply using a virual machine.

---

### Post by Naatan on 2007-08-06
I have concidered that but a Virtual Machine slows down both OS'es and does not have 3d acceleration.

---

### Post by Naatan on 2007-08-07
bump, question 1 is still unresolved :)

---

### Post by merlinus on 2007-08-07
Linux uses a completely different filesystem from windows.  So although various drivers will allow each OS to read-and-write to-and-from data partitions, the native filesystems are required for applications.

In other words, linux apps will not run on fat or ntfs, and windows apps will not run on ext2, ext3, reiserfs, etc.

-merlin

---

### Post by el Arm on 2008-04-14
[LIST=1]
[*]My best guess would be to mount /usr/local as your third partition.
[*]Either NTFS or ext3.  NTFS-3G is now stable for writing, and there exists [this driver]("http://www.fs-driver.org") for ext2/3 under Windows.
[*]5-10Gb
[/LIST]

(I know this is an old thread, just thought I'd update it with current info)

---

