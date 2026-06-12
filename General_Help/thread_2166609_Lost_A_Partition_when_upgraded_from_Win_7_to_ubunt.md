---
title: "Lost A Partition when upgraded from Win 7 to ubuntu 13.04"
date: 2013-08-10
forum: General Help
---

### Post by livingoff on 2013-08-10
Hi everyone.I just installed ubuntu 13.04 on my desktop.While installing i selected an option "Replace Windows 7 with ubuntu " thinking it remove all the files of win 7 in c drive but it deleted all the files and all the partitions.I just had 2 partitions C and D. On the C drive Win 7 was loaded and I had lots of important datas on the D drive.It was a 500Gb hard disk. It was split into 60Gb  in C and rest 420gb in D.

These datas are very valiable to me.I am currentlyu stuck here.Someone please help me to get the datas back.

Any suggestion and help is really truely appreciated.

Note: I have a 1Tb internal HDD with me.It has some free space about 300gb.Its not connected at  the moment.

xoxo
livingoff

---

### Post by livingoff on 2013-08-10
come one guys its been 2hrs and still no answer :(
I am so freaking out now that i forgot my ubuntu admin password :icon_frown:

---

### Post by livingoff on 2013-08-10
Okay i have been reading the forum for past 3hrs.What i came up with seems to me the best solution i guess.

I am gonna format ubuntu 13.04 and install win xp using NTFS format.
Will install some recovery apps on windows xp.
Attach my another 1tb hard disk.
Run the recovery apps and recover what ever data is possible and save the data to the 1tb hard disk.

Is this method going to work ?

---

### Post by deadflowr on 2013-08-10
This advice may or may not help you
[http://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu](http://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu)

It's unclear what your disk looks like now.

If you can remember your password for Ubuntu, programs like fdisk, and parted can help show us what the partition table layout looks like.
```
sudo fdisk -l
```
```
sudo parted -l
```

---

### Post by livingoff on 2013-08-10
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e3cac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   969437183   484717568   83  Linux
/dev/sda2       969439230   976771071     3665921    5  Extended
/dev/sda5       969439232   976771071     3665920   82  Linux swap / Solaris
livingoff@PirateTheNet:~$ 


livingoff@PirateTheNet:~$ sudo parted -l
Model: ATA ST3500418AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  3754MB  extended
 5      496GB   500GB  3754MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

livingoff@PirateTheNet:~$

---

### Post by deadflowr on 2013-08-10
Yep, unfortunately you chose to install over whole disk option.
I hoping it wasn't like that, but can't cry over spilled milk.
As stated in my earlier post, the link I provided may or may not be helpful.
Data recovery can be either very/mostly successful, or complete failure.

---

### Post by livingoff on 2013-08-10
> **deadflowr said:**
> Yep, unfortunately you chose to install over whole disk option.
I hoping it wasn't like that, but can't cry over spilled milk.
As stated in my earlier post, the link I provided may or may not be helpful.
Data recovery can be either very/mostly successful, or complete failure.

will installing windows Xp help ?
windows Xp takes the same space.

I read from here.he said he was successful.
Please have a look here : 
[http://ubuntuforums.org/showthread.php?t=1879640](http://ubuntuforums.org/showthread.php?t=1879640)

---

### Post by livingoff on 2013-08-10
I have been waiting here for 6hrs someone please help.

---

### Post by SuperFreak on 2013-08-10
You would do best to boot off a live disk and recover files using [TestDisk & PhotoRec ]("http://www.cgsecurity.org/wiki/TestDisk_Download"). Installing XP will likely overwrite the files you are trying to save. Take another look at the link deadflowr provided

booting to the hard drives you are having trouble with will likely overwrite your files, Live disk is the better way to go

---

### Post by livingoff on 2013-08-10
> **SuperFreak said:**
> You would do best to boot off a live disk and recover files using [TestDisk & PhotoRec ]("http://www.cgsecurity.org/wiki/TestDisk_Download"). Installing XP will likely overwrite the files you are trying to save. Take another look at the link deadflowr provided

okay from where will i get a live disk ?
I just have with me the ubuntu 13.04 installation disk

And where will i install this [TestDisk & PhotoRec ]("http://www.cgsecurity.org/wiki/TestDisk_Download"). ?
In the live disk ?

please am new to linux. some help in details will be great

---

### Post by jonathanp2 on 2013-08-10
You should be able to boot the Ubuntu installation disk as a live disk. Choose try Ubuntu instead of install.

---

### Post by jonathanp2 on 2013-08-10
after you get onto the Ubuntu live, you should be able to install the programs temporarily and use them, but once you reboot off the live disk, you will loose the programs. Is you installation on a live USB or DVD?

---

### Post by livingoff on 2013-08-10
> **jonathanp2 said:**
> after you get onto the Ubuntu live, you should be able to install the programs temporarily and use them, but once you reboot off the live disk, you will loose the programs. Is you installation on a live USB or DVD?

I have installed it on a dvd.

So i need to get my another Hard disk connected rite in order to take the backup.
I dont know how this program [Testdisk  ]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")and etc work ?
Do they have a GUI ?
how will i recover ?

---

### Post by livingoff on 2013-08-11
Okay I finally recovered all my data.I recovered every bit of it.Nothing was lost.

If you are a linux n00b like me then dont do anything like TestDisk or boot with system rescue etc etc stuffs.This will get you more complicated and confused since there is no GUI here.All its commands and stuffs.So stay away. And do the easy way.Follow me o/

Here is what I did :-

In my hard disk there was only 1 partition of 500gb  where ubuntu was installed.
So i formatted it using windows xp Sp3.
When go to format windoes will give you a  message that windows cannot format the partition.Dont worry Just Delete the partition and make a new partition.but remember Dont split your partition.Make just one partition.

now Format the partition using NTFS [Quick Format]
Once format is done Xp loads up.

Just setup your ethernet driver so that you are connected to the net.
Download Runtime GetDataBack for NTFS.

If GetDataBack is able to recovery any data you will have to purchase the software to unlock it.

Now run the application. It mat give you the error that disk not found etc but you keep on hitting continue botton.Finally you will get 2-3 NTFS Drives.
Check the ones which have got the datas you need for backup and copy them to another hard disk or a temporary storage device/ pendrive etc
But remember never copy anything on the same hard disk.If you do that then you are gone.All your datas will just vanish and you will not be able to backup any thing.

I recovered over 250Gb stuffs which were there on my D drive.
Total 100% recovery.Nothing is lost.

good luck o/

---

### Post by livingoff on 2013-08-11
And i am not done with ubuntu o/
I will install it again but this time will not make any mistakes lol.

I will learn and will master linux.Enjoyed the os very much.

---

### Post by Vaphell on 2013-08-11
dude, back your stuff up ASAP, seriously. Count your lucky stars that you were able to recover data but don't push it. Sure, it was your own action that caused grief but flukes and hardware failures happen too. What will you do in case your HDD simply dies? Do you have thousands of bucks to pay data recovery specialists? Operations on partitions are inherently dangerous, power fluke in the middle can leave disk in a borked state.

Long story short: always back up things you can't afford to lose.

---

### Post by livingoff on 2013-08-11
> **Vaphell said:**
> dude, back your stuff up ASAP, seriously. Count your lucky stars that you were able to recover data but don't push it. Sure, it was your own action that caused grief but flukes and hardware failures happen too. What will you do in case your HDD simply dies? Do you have thousands of bucks to pay data recovery specialists? Operations on partitions are inherently dangerous, power fluke in the middle can leave disk in a borked state.

Long story short: always back up things you can't afford to lose.

Advice well taken mate.
being a college guy I dont have lots of money to buy another external storage to backup everything like Tv series/Hd movies/Flacs (All media stuffs) But I have backed Up most of the data files(txt,doc,pdf) etc to dropbox.
I will upload them to some other cloud storage too incase dropbox is gone :p

---

### Post by Vaphell on 2013-08-11
true, tv/movies and such are a few clicks away if you are into torrenting so no big deal, stuff like school/work related docs, ten years worth of family photo collection, etc is what matters.
I am a long time user of these forums and have seen quite a few cases where people lost their important project/master thesis because they had all their work (weeks if not months) in a single instance of the file (no copies, no versioning, no nothing) which got zeroed out by an unclean shutdown. I cringed hard when i read their posts, daayuum :/

If you see your friends being careless with their important data, feel free to smack them upside their heads :) You will do them a favor and spare them quite a few panic attacks ;-)

---

