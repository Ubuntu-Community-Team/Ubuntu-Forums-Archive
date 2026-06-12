---
title: "[Ubuntu 7.04]How to mount an exsisting software raid0 partition?"
date: 2008-03-07
forum: General Help
---

### Post by earithramir on 2008-03-07
Hello,

I am trying to connect my Harddisks from my MyBook World Edition 2 wich runs on dual 1TB drives on software Raid0 to my computer to copy files to the striped software raid0 partition on those drives.

The drivers are connected correctly and in partition manager i can see all partitions and these have raid flags.

I am kinda new to ubuntu and are just trying to copy a lot of data at once to the discs.
But there for i need to mount the Raid0 parititions

I disconnected all other Harddisk drives except for those in need.
I succesfully mounted my Other drive (wich is from a MyBook world edition 1 and is not in raid) with EXT3 filesystem..

but i can not seem to get the 2 drives in software raid mounted.

Did a lot of searching on the web/this webpage but did not find any solution for this.

Harddisk drives:
/dev/sda:
 sda1 	ext3fs 	2.80 GiB   => linux boot partition in software raid1
 sda2 	swap (v1) 	101.98 MiB => linux swap in software raid1
 sda3 	ext3fs 	964.84 MiB  => System files in software raid1
 sda4 	ext3fs 	461.89 GiB => Shared folder in software Raid0
/dev/sdb:
 sdb1 	ext3fs 	2.80 GiB   => linux boot partition in software raid1
 sdb2 	swap (v1) 	101.98 MiB => linux swap in software riad1
 sdb3 	ext3fs 	964.84 MiB  => System files in software raid1
 sdb4 	ext3fs 	461.89 GiB => Shared folder in software Raid0
/dev/sdc:
 sdc1 	ext3fs 	2.80 GiB   => linux boot partition
 sdc2 	swap (v1) 	101.98 MiB => linux swap
 sdc3 	ext3fs 	964.84 MiB  => System files
 sdc4 	ext3fs 	461.89 GiB => Shared folder  [succesfully mounted with read/write premissions]

i want to mount sdb4 and sda4 in software raid0 without removing any existing files or changing any to the existing file system.

Please help.
Million thanks in advance !!

---

### Post by fjgaude on 2008-03-07
If you have dmraid on your system, try this:

```
sudo dmraid -tay
```

From there you should see a complex listing of devices with /dev/mapper lead-ins.

You mount one or more of these using:

```
sudo mount /dev/mapper/mmmmmmmmmmm /mountpoint
```

The mmmmmmms are unique to the devices. The mountpoint you create like so:

```
sudo mkdir /media/raid
``` or whatever you wish to call the mountpoint.

If you don't have dmraid on your computer, do this:

```
sudo apt-get install dmraid.
```

Let us know how you are doing.

---

### Post by earithramir on 2008-03-08
Hi,

Thank u very much for replying to my question...

I am testing it right this moment..

This ubuntu software is really great i just had a broken harddrive recovered all of the lost data.
(it was a EXT3 partition on a linux shared drive wich was crashed i lost all partition table data .
installed a tool called testdisk for linux and this tool was able to recover 99% of all my documents 

ill be back with the results of this project...


by the way.. this will not build a new array, right? (just rebuild the existing one)

Hi, here i am again :P
I just installed dmraid and ran: sudo dmraid -tay
it returned with:   no RAID disks?
But in GNOME Partition manager i can see that SDA1/2/3/4 and SDB1/2/3/4 are flagged with RAID.
Whats next? (i am only trying to mount the 4th partition of SDA and SDB in software RAID0.

Adition information:
The Drives are identical SATA2 WD500GB. and GNOME does see them and the partitions on them i only get a explanation mark on both devices in the list with partition4 and gnome is unable to determent wich filesystem it uses but can tell me the size and flags of this device

---

### Post by earithramir on 2008-03-08
Would it work if i disconnected the other SATA drive?
I have connected three SATA devices and one PATA device (on wich ubuntu is running).
The first two sata devices are the identical ones and the 3th one is the one i want to copy the data from. (wich is the same brand but an other model the the other drives)

---

### Post by fjgaude on 2008-03-08
What does your BIOS say about the raid drives? This is how you set them up, is it not? Just wondering.

dmraid doesn't build or reassemble arrays. Your BIOS does this with its fakeraid features.

dmraid will show the array after it has been built in BIOS, and then in Ubuntu you will be able to mount and use it.

---

### Post by earithramir on 2008-03-08
Hi.

My motherboard has a nVidia Raid Chip wich i normaly use for my raid computer.
But the two drives i am trying to mount where created using SOFTWARE raid.
Wount i be destroying all data on it when i use a hardware raid to rebuild it.
I do not want to destroy data on the drives!

And i think if there where hardware raid information this disc the raid controller would have recognized the raid array and rebuild  it automatically, right?
When i installed this motherboard i was already using  hardware raid (on other harddisks witch are not connected right now) and it found the array automatically and rebuild it for me.

But with software raid this is not the same , is it?
Sow how do i recreate an existing SOFTWARE RAID0 partition (on two drives) , only partition4 was in this array of both discs sow it cant be hardware raid :S

---

### Post by earithramir on 2008-03-08
I Just rebooted and started nVidia's raid config util.
But it could not find any arrays, sow it defently is a SOFTWARE raid0!

should i use mdadm for rebuilding the array?
If so, how :P ?

Like stated in the TS (topic start) the drives are not  mirrored or striped but the partitions are;
The first 3 partitions are mirrored and the 4th partition is striped, so it can not be hardware raid(hardware raid will just mirror or stripe the whole drives!)!
The first 3 partitions of those drives i can easily mount and read/write data from/to.
But the 4th partition on both discs was striped and this partition i can not mount because ubuntu will not recognize the file-system of these partitions.
Sow my question, how can i mount the striped partition on those drives??
All partitions are flagged with raid.
A raid controller will not detect any arrays!

---

### Post by fjgaude on 2008-03-08
Gosh, how was the software raid built? by whom?

You boot from a raid1 array that has three partitions. Such was created by someone else, other than you? Plus there is another partition, the fourth, that is stripped? It doesn't show in Ubuntu.

The only modern software raid that is in use under Ubuntu is mdadm.

Install it and see what you can get.

```
sudo apt-get install mdadm
```

After it installs, run this command:

```
sudo mdadm --assemble --scan --verbose
```

And let's see what the result is. It's safe, will not destroy any data but will show arrays, partition by partition.

You might wish to read, study the **mdadm man** pages. It is a powerful, reliable software raid program in general use over the whole Linux world.

---

### Post by earithramir on 2008-03-09
Hi thanks,

> Gosh, how was the software raid built? by whom?

You boot from a raid1 array that has three partitions. Such was created by someone else, other than you? Plus there is another partition, the fourth, that is stripped? It doesn't show in Ubuntu.
Thats Right, Those partition/arrays where created by Western Digital, the creators of this disc.
Its a NAS wich runs linux the first three partitions are: EXT3 [2.8GB]/linux-swap [100MB]/EXT3 [965MB].
These NAS devices are populair because of the linux software running on it, wich makes is easy to install addition software link rtorrent or FTP services etc..

I did allready have this software installed, but didnt know if using it would remove any exsisting partitions/arrays.

I dont know what software WesternDigital used for building those arrays but my guess goes out too mdadm.

Ill post again in a couple of minutes with the results...

edit:
Just after a fresh restart:
[PHP]mdadm: cannot open device /dev/sdb4: Device or resource busy
mdadm: /dev/sdb3 is not built for host mark.
mdadm: cannot open device /dev/sdb2: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: no recogniseable superblock on /dev/sdb
mdadm: cannot open device /dev/sda4: Device or resource busy
mdadm: /dev/sda3 is not built for host mark.
mdadm: cannot open device /dev/sda2: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: no recogniseable superblock on /dev/sda
[/PHP]
Is there a way to fully unmount/disconnect all running tasks on a drive?
I do not have any of the partitions on one of these partitions mounted, what software can be using it right now?

I am going to read the documentation u requested right now... (thanks again!)
I really appreciate your help!!

---

### Post by fjgaude on 2008-03-09
Here's an old article on mdadm that might be useful:

[http://www.networknewz.com/2003/0113.html](http://www.networknewz.com/2003/0113.html)

See if you have a file in /etc/mdadm called **mdadm.conf**.

I'm thinking what you could try next... always thinking to not do something that would destroy your data.

---

### Post by earithramir on 2008-03-09
Thanks again, ill go through that artical and see if i can find something to help myself.
If ill manage to do the trix with mdadm or some other util ill let you know..

this file (mdadm.conf) should it be on the primairy partition of the discs in question or on the disc i use to run ubuntu ?
my quess goes for the partition on the disc in question :P

---

### Post by fjgaude on 2008-03-09
That conf file should be on the partition where the array is assembled during boot up.

Since you don't seem to show the /dev/md0 or whatever the name of the array is or arrays are, I'm confused. I have no knowledge of the WD device you are using... how is it connected to your computer, by LAN or USB?

---

### Post by earithramir on 2008-03-09
Hi,
 
its an Network Attatched Storage.
With only one port: LAN.

De device is just a harddisk that runs on the network with simple server software on it (using linux) all partitions are in EXT3 filesys.
The harddisk can be managed by webpage.

---

### Post by fjgaude on 2008-03-09
Okay, this is way out of what I usually consider. You are trying to mount on your computer through the LAN two drive partitions that are raid0, stripped.

I simply don't know how to do such a thing. No, I think you are moving the drives over to your computer and trying to work with them there, right?

Using mdadm didn't work to have them show. The /etc/mtab file likely doesn't show any /dev/md? names, eh?

The only think left is to try a force assembly using mdadm:

```
sudo mdadm --assemble --scan --force --verbose
```

I pretty sure the "force" will not cause any damage to data on either of the two partitions.

The next thing to try would be to assemble using the actual partition names:

```
sudo mdadm --assemble /dev/md0 /dev/sda4 /dev/sdb4
```

I not sure from memory what your two partitions are, but you know. <smile>

I gave the array a name, md0, and likely mdadm will not like this. But let's see what happens.

---

### Post by earithramir on 2008-03-09
Hi,

I dont know if i fully understand it, but i ment that i removed the harddrives from there case and plugged them directly into my computer using SATA2.
But by reading the rest of ur message it looks like u did understand me :P

Ill go and try forcing the  software to assemble the raid array on the discs, hopefully i do not damage any file system on the discs!

ill let u know in a minute, if eighter of those did the trick.. !

after testing;
the first method (force) gave the same result as without force, telling me that the device is busy.

mdadm: /dev/sda4 has no superblock - assembly aborted
gave error message: [PHP]SDA4 has no superblock, assembly aborted[/PHP]

Hi,
I just found out that i cannot mount any other partition, it will give me the message:
[PHP]mount: /dev/sda1 already mounted or /media/nas busy[/PHP]
This on both harddisk drives, the devices are NOT mounted, and i just started up the computer, sow i dont know what software should be working on either of those discs, mounting any other disc does work.
Does this help ??

Here i am (AGAIN!!) :P
I just reassembled my NAS just to check if the table data/arrays are still intact, and yes they are, when putting the harddrives back into my NAS device it started up and found the exsisting raid array and data that was on it!
Sow the array does exsist Ill go try and connect to the device over the network using ssh and check if i can find any data about the RAID arrays and what exact software is running on the device etc..
Ill keep u posted on the things i find about this device

I hope that u can understand me my english is not really good :P

---

### Post by fjgaude on 2008-03-09
Well, you know, I've been thinking, maybe the drives were created into a raid0 array by other than mdadm. I only know mdadm now, it's the Linux software raid tool, period.

The drives show busy because of the headers, or type of superblocks put on them to make the array in the first place.

Your English is fine... I believe we are understanding each other.

Let me know what you find out, please. Seems some utility could have come with the package, on the same CD or DVD that came with it box.

---

### Post by earithramir on 2008-03-09
Thats exactly what i was thinking.
But before i can find out i must hack the basterd :P (put other firmware on it so i can acces is through ssh).
And teach my self some more basics into the world of linux/unix 8)
when i can understand the language i properly can find an solution and find out what software was used for making the arrays in the first place..

Unfortiantly the drive comes without any restore disc only a annoying tool to acces it through the internet called mionet (i hate this software sow i did not install it) and this will not help me at all :P

I was hoping to get some files (total size of 1TB) from one disc to this drive without having to wait for ages (zapping it through network isnt the fastest way for copying files from one location to another :P but i think i better could have done this in the first place i proberly was nearly complete with this process by now.
But its allways nice to learn something new on computers, sow i cept on diggin to get it done with the drives connected to my computer and using linux :P

I allso think we can understand eachother , allways good to know that my english isnt that bad :P

thanks for all of your time, and when i find an solution i will tell you!!

---

### Post by fjgaude on 2008-03-10
Okay, and good luck!

Trust we all find our way, and are happy.

---

### Post by Sunaj on 2008-03-19
Any update on this? I have a MBWIIE and would like to move the harddrives over to an ubuntu box

---

### Post by fjgaude on 2008-03-19
Pray tell, what is a MBWIIE... more details please.

---

### Post by earithramir on 2008-03-19
> **fjgaude said:**
> Pray tell, what is a MBWIIE... more details please.

MBWIIE stands for : MyBook World 2 Edition, the NAS (Network attachted storage) device in question.. in other words a LAN-HDD, wich is running on linux software and is able to run raid config (eighter raid0 or raid1 over the data parition)

And no, no update yet, im pretty bussy with some other stuf, maybe later i can take an other look at it, and ill let u know!
But for now i just send all the files to the device other the ethernet (it took a total of 5 days for all the data to be send from computer to NAS)

Just one thing i found: When using a live CD youll get more results with it, in a freshly installed ubuntu i was unable to mount any partition , but when using the live session on CD i was able to mount the first three partitions, maybe mdadm will be able to mount the partitions with the live cd, not tested yet!

Please let me know if you find anything, i will !

---

### Post by fjgaude on 2008-03-19
Thanks... I guess we are all learning together... this is good!

---

### Post by earithramir on 2008-03-19
> **fjgaude said:**
> Thanks... I guess we are all learning together... this is good!

looks like it , doesnt it :P
well im going to bed, its 4:45am here :P

---

### Post by earithramir on 2008-03-26
Hi,

After inspecting the drives, i was able to mount them using a different version of ubuntu (now using x64 and version 7.10) 
i where able to mount partition 1 and 3 (wich contain system files)
and indeed i found mdadm.conf file in one of the directories.

The raid IS being made using mdadm i found in this file.
I did not yet test rebuilding this array using mdadm in ubuntu 7.10 but i am sure that that will do the trick!
All files are now allready being copied to the disc over the ethernet, took me while but its done.
I dont want to open the device again and plug the harddrive in my computer.

Thanks for helping me, and i hope some1 will find this information usefull!

---

### Post by fjgaude on 2008-03-27
Gosh, it's taken some time but it's all worth it, as we each learn something new.

Good luck with your computing adventure.

---

### Post by earithramir on 2008-03-27
Yeah, took a while :P
But im not using the computer every day ;)

And did not expect that ubuntu 7.04 was annoying me :P
everything worked out after running the new ubuntu like a live version!
Both versions x64 and x86 seem to work even still not decided wich version to use, i think ill stick with x86 because of the wide support of addons for e.g. firefox etensions i could not get flash working on x64...

---

### Post by fjgaude on 2008-03-27
I've been using the 64-bit Gutsy since it came out without issues... the only thing I'd recommend is to not manually install any multimedia or flash items. Just let the system prompt you when it needs to install a plugin. It will do it as you go to various sites that need flash, mp3, etc.

It has worked fine for me, and now the beta of Hardy works fine too, all 64-bit.

---

