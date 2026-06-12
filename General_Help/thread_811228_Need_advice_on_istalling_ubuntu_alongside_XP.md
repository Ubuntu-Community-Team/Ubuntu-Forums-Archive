---
title: "Need advice on istalling ubuntu alongside XP"
date: 2008-05-28
forum: General Help
---

### Post by Vladislav Mkrtychev on 2008-05-28
Hi,

I have two partitions.
I just want to ask if it is possible and advisable
to install ubuntu on one of the partitions (as in using the whole partition). It is not the primary one.

Thanks for all replies!

---

### Post by YldGuy on 2008-05-29
what i would suggest is to carve out one more NTFS partition out of the second and use it to share data between XP and Ubuntu. You can then install Ubuntu over the third partition.

---

### Post by aresgodofwar30 on 2008-05-29
with linux you want to have at least two partitions from what I understand. one for swap and one for the OS. the swap needs to be at least 2 to 3 times the amount of ram you have installed.
If you want to get advanced, you can have more. 
I have a partition for swap, partition for OS and a partition for /home. This way if I need to reinstall, then I don't lose any of my information stored in my home directories.

---

### Post by samrat1985 on 2008-05-29
> **Vladislav Mkrtychev said:**
> Hi,

I have two partitions.
I just want to ask if it is possible and advisable
to install ubuntu on one of the partitions (as in using the whole partition). It is not the primary one.

Thanks for all replies!
yes a swap partition is req. need not be twice as ram if u have large ram. You can use swapfile later on  if req.

---

### Post by Vladislav Mkrtychev on 2008-05-29
> **YldGuy said:**
> what i would suggest is to carve out one more NTFS partition out of the second and use it to share data between XP and Ubuntu. You can then install Ubuntu over the third partition.

I like that idea of sharing data. It's just I have an external HD and all the data will reside there (be it from ubuntu or XP).
So I guess what I want to find out is if I give ubuntu whole second (non primary) partition, will it know what to do with it? Like creating a swap partition, etc.

Thanks!

---

### Post by james_bandido on 2008-05-29
i used to have a two partition system windows xp sp2 and ubuntu 7.10 ... 

unfortunately, i always mess up the files i access (read/write) in the windows partition whenever i am booted up in ubuntu ... usually i end up with messing the windows indexing system (i think) and my boot gets affected ... 

what i did was partition my hard disk as follows :
partition 1 : 20 GB <-- windows xp sp2 goes here
partition 2 : 10 GB <-- data storage
partition 3 : 10 GB <-- ubuntu 7.10 goes here 

after partitioning your hard drive, install XP first into the 1st partition ... 
once installed, format the 2nd partition using windows formatting ... 
now boot up a live CD then install ubuntu on the 3rd partition ... 
ubuntu will then reconfigure everything for you (grub menu etc) ... 
though my mistake was i forgot to create a swap area ...
but the system works :D

---

### Post by Vladislav Mkrtychev on 2008-05-29
> **james_bandido said:**
> i used to have a two partition system windows xp sp2 and ubuntu 7.10 ... 

unfortunately, i always mess up the files i access (read/write) in the windows partition whenever i am booted up in ubuntu ... usually i end up with messing the windows indexing system (i think) and my boot gets affected ... 

what i did was partition my hard disk as follows :
partition 1 : 20 GB <-- windows xp sp2 goes here
partition 2 : 10 GB <-- data storage
partition 3 : 10 GB <-- ubuntu 7.10 goes here 

after partitioning your hard drive, install XP first into the 1st partition ... 
once installed, format the 2nd partition using windows formatting ... 
now boot up a live CD then install ubuntu on the 3rd partition ... 
ubuntu will then reconfigure everything for you (grub menu etc) ... 
though my mistake was i forgot to create a swap area ...
but the system works :D

Thanks,
Are you saying that I have to reinstall XP?

...Off the topic - I just learned that during the installation ubuntu takes care of partitioning even if you have just one partition. Is that true?

---

### Post by james_bandido on 2008-05-29
if your windows xp already resides in the 1st partition and is working fine, then you might want to leave it as is ... 

all you have to do is to repartition your 2nd partition into 2 ... 

the only reason i have to re-install xp was that my system was totally corrupted, besides all my data are in an external drive so i dont worry much on reformat and reinstall ;)

---

### Post by Vladislav Mkrtychev on 2008-05-29
> **james_bandido said:**
> if your windows xp already resides in the 1st partition and is working fine, then you might want to leave it as is ... 

all you have to do is to repartition your 2nd partition into 2 ... 

the only reason i have to re-install xp was that my system was totally corrupted, besides all my data are in an external drive so i dont worry much on reformat and reinstall ;)

Yes, XP is on the primary partition and it is fine for now.
The second partition is around 80G NTFS. Do you have a suggestion on how I should allocate the space on that partition? 

I also plan to keep all my data on the external HD, so I am not worrying about "sharing" the data between XP and ubuntu, although I like that idea.

---

### Post by WitchBitch on 2008-05-29
Sheesh is this harder than it sounds? I was looking forward to trying this out, now not so sure....lol Will any of my software work on Ubuntu or is it any but microsoft stuff? I am so fed up with windows crashing every 10 mins I need to have to try Ubuntu.
I want to install along side XP too. But dont want to reformat at this time.
Thanks

---

### Post by Vladislav Mkrtychev on 2008-05-29
> **WitchBitch said:**
> Sheesh is this harder than it sounds? I was looking forward to trying this out, now not so sure....lol Will any of my software work on Ubuntu or is it any but microsoft stuff? I am so fed up with windows crashing every 10 mins I need to have to try Ubuntu.
I want to install along side XP too. But dont want to reformat at this time.
Thanks

It sure does!:lolflag:
What you can try to do is to install ubuntu via wubi.exe.
What it does is installing ubuntu "inside" Windows. That's what I have now. However, now I want total separation because of possible security issues.
Am I alone in this? I've used Windows all my life, and I am yet to experience a windows crash. I am serious and I am 37.

---

### Post by WitchBitch on 2008-05-29
> **Vladislav Mkrtychev said:**
> It sure does!:lolflag:
What you can try to do is to install ubuntu via wubi.exe.
What it does is installing ubuntu "inside" Windows. That's what I have now. However, now I want total separation because of possible security issues.
Am I alone in this? I've used Windows all my life, and I am yet to experience a windows crash. I am serious and I am 37.


I have "borrowed" my daughters comp, because I know it wont crash on me, then Im going to get a new hard drive for mine and install ubuntu  on that. AND i cant believe how lucky you are not to have crashes, I feel I am having them due to slagging off and laughing at Bill Gates.....:lolflag:

---

### Post by YldGuy on 2008-05-30
> **Vladislav Mkrtychev said:**
> Yes, XP is on the primary partition and it is fine for now.
The second partition is around 80G NTFS. Do you have a suggestion on how I should allocate the space on that partition? 

I also plan to keep all my data on the external HD, so I am not worrying about "sharing" the data between XP and ubuntu, although I like that idea.


installing ubuntu over the second partition should not be a problem. You have plenty of space. Just use twice your RAM size for swap partition and use another 10 gb for Ubuntu. You can decide what you wanna do with the rest. mebbe you can use it exclusively for ubuntu or share with xp or use only with xp. your call.

I used around 15 gb for my ubuntu partition and its fast filling up coz i play couple of games and use lot of apps. but thats just me.. ppl also do fine with just 5 or 6 gb for ubuntu.

---

### Post by Vladislav Mkrtychev on 2008-05-30
Installed ubuntu on the second partition.
I used a "Guided" option in terms of partitioning.
It works fine. No problems with installation. I think 
(or I'd like to think) that ubuntu took care of space allocation as far as 
swap partition etc.
Any thoughts on how can I check this out?

Thanks.

---

### Post by YldGuy on 2008-06-01
> **Vladislav Mkrtychev said:**
> Installed ubuntu on the second partition.
I used a "Guided" option in terms of partitioning.
It works fine. No problems with installation. I think 
(or I'd like to think) that ubuntu took care of space allocation as far as 
swap partition etc.
Any thoughts on how can I check this out?

Thanks.

type fdisk -p in the terminal. you will see something like Linux Swap in the list which comes up (look in the extreme right of the list).

OR

use Gparted (somewhere in Administration, i believe)in the live CD you have to see the no: of partitions graphically. (i listed this coz I am comfortable in using command line prompts but dont seem to remember the commands.. i google every single time for any simple command.. i dont want to remember them i guess.. i need some simple GUI like Gparted which will do things easily.. others might differ on this.)

---

### Post by cybrsaylr on 2008-06-02
> **Vladislav Mkrtychev said:**
> Installed ubuntu on the second partition.
I used a "Guided" option in terms of partitioning.
It works fine. No problems with installation. I think 
(or I'd like to think) that ubuntu took care of space allocation as far as 
swap partition etc.
Any thoughts on how can I check this out?

Another way to see your HHD state.
In terminal type;
 df 
or type; df -h
This will show the exact state of how your HDD is partitioned.

---

### Post by cybrsaylr on 2008-06-02
> **WitchBitch said:**
> Sheesh is this harder than it sounds? I was looking forward to trying this out, now not so sure....lol Will any of my software work on Ubuntu or is it any but microsoft stuff? I am so fed up with windows crashing every 10 mins I need to have to try Ubuntu.
I want to install along side XP too. But dont want to reformat at this time.
Thanks

It's not harder, just different, like going from Windows to Mac. Ubuntu has its own software all included, you just have to learn to use it and it's not that hard. Believe Ubuntu comes fully loaded with over 250 apps and programs, of couse all free. I've been using linux about a year now and don't need Windows anymore. I have a dual boot system with XP/Ubuntu that runs trouble free. Just got a laptop and plan on dual booting Vista and Ubuntu.
 
Ubuntu is a very nice OS.

---

### Post by Vladislav Mkrtychev on 2008-06-02
OK, I ran:

vlad@vlad-desktop:~$ fdisk -p
fdisk: invalid option -- p

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


Then I ran:

vlad@vlad-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb6             77173376   3686412  69597632   6% /
varrun                 1037616       100   1037516   1% /var/run
varlock                1037616         0   1037616   0% /var/lock
udev                   1037616        68   1037548   1% /dev
devshm                 1037616        12   1037604   1% /dev/shm
lrm                    1037616     38176    999440   4% /lib/modules/2.6.24-17-generic/volatile
gvfs-fuse-daemon      77173376   3686412  69597632   6% /home/vlad/.gvfs


And finally:

vlad@vlad-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6              74G  3.6G   67G   6% /
varrun               1014M  100K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   68K 1014M   1% /dev
devshm               1014M   12K 1014M   1% /dev/shm
lrm                  1014M   38M  977M   4% /lib/modules/2.6.24-17-generic/volatile
gvfs-fuse-daemon       74G  3.6G   67G   6% /home/vlad/.gvfs

But I hardly can make sense out of this. Where are the partitions?
And I do not have GParted for some reason.
I guess I would have to install it to see it graphically.

---

### Post by cybrsaylr on 2008-06-02
> **Vladislav Mkrtychev said:**
> 
But I hardly can make sense out of this. Where are the partitions?
And I do not have GParted for some reason.
I guess I would have to install it to see it graphically.

You have to learn to read that.

Here's how my dual boot system shows up.
I have a 120GB HDD that I partitioned into 3, 40GB partitions.
Then I took the 40GB Windows partition and split in in half so 20GB was for XP and 20GB was for Ubuntu.

This is how terminal shows this in my PC for;    df

desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda8             18745884   4123536  13670100  24% /
varrun                  192788       104    192684   1% /var/run
varlock                 192788         0    192788   0% /var/lock
udev                    192788        64    192724   1% /dev
devshm                  192788       176    192612   1% /dev/shm
lrm                     192788     38176    154612  20% /lib/modules/2.6.24-17-generic/volatile
/dev/sda1             19535004   6868496  12666508  36% /media/hda1
/dev/sda5             38804972    421648  38383324   2% /media/hda5
/dev/sda6             39343152  12098032  27245120  31% /media/hda6


...and here's how terminal shows this in my PC for;    df -h

desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              18G  4.0G   14G  24% /
varrun                189M  104K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
udev                  189M   64K  189M   1% /dev
devshm                189M  176K  189M   1% /dev/shm
lrm                   189M   38M  151M  20% /lib/modules/2.6.24-17-generic/volatile
/dev/sda1              19G  6.6G   13G  36% /media/hda1
/dev/sda5              38G  412M   37G   2% /media/hda5
/dev/sda6              38G   12G   26G  31% /media/hda6

The lines:
/dev/sda8 18G 4.0G 14G 24% /  = the Ubuntu partition
/dev/sda1              19G  6.6G   13G  36% /media/hda1  = the XP partition
/dev/sda5              38G  412M   37G   2% /media/hda5  = extra storage partition
/dev/sda6              38G   12G   26G  31% /media/hda6  = extra storage partition
The other lines in between are other minor Ubuntu sub-partitions needed by Ubuntu.

---

### Post by YldGuy on 2008-06-03
> **Vladislav Mkrtychev said:**
> OK, I ran:

vlad@vlad-desktop:~$ fdisk -p
fdisk: invalid option -- p

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


Then I ran:

vlad@vlad-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb6             77173376   3686412  69597632   6% /
varrun                 1037616       100   1037516   1% /var/run
varlock                1037616         0   1037616   0% /var/lock
udev                   1037616        68   1037548   1% /dev
devshm                 1037616        12   1037604   1% /dev/shm
lrm                    1037616     38176    999440   4% /lib/modules/2.6.24-17-generic/volatile
gvfs-fuse-daemon      77173376   3686412  69597632   6% /home/vlad/.gvfs


And finally:

vlad@vlad-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6              74G  3.6G   67G   6% /
varrun               1014M  100K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   68K 1014M   1% /dev
devshm               1014M   12K 1014M   1% /dev/shm
lrm                  1014M   38M  977M   4% /lib/modules/2.6.24-17-generic/volatile
gvfs-fuse-daemon       74G  3.6G   67G   6% /home/vlad/.gvfs

But I hardly can make sense out of this. Where are the partitions?
And I do not have GParted for some reason.
I guess I would have to install it to see it graphically.


I am sorry. You must use fdisk -l to see all the partitions.

---

