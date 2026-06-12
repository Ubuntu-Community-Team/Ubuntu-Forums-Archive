---
title: "ubuntu server 12.04 RAID 1 install"
date: 2014-01-28
forum: General Help
---

### Post by mark103 on 2014-01-28
Hows it going I'm new to this site so i have a few questions in relation to installing Ubuntu server 12.04 in RAID 1 with 2 3TB drives.

First of I build a server over 2 years ago for the first time using windows home server 2011 to store all my media and pictures and college stuff.
it worked fine but i was always curious about Linux ubuntu server but the whole command line seemed a bit daunting so i said to myself ill stay with GUI WHS 2011 to start of with and see how it goes
now I'm not fully impressed with how WHS 2011 works but that's another story :) so here i am installing ubuntu server 12.04 so i went and bought 3 brand new Seagate 3TB drives for this project.

Now i wanted to use the 3 drives but RAID 1 lets you use 2 drives and that's fine i was thinking of using the spare drive as a backup ? but i'm not fully sure how that would work so i just left the third
drive of for the moment,so of i went with the install and followed a few tutorials on this site which were fine but my problem was that having 3TB drives i would run into a problem which i found out very quickly :(

But i used GPARTED and i partitioned the 2 drives and that sorted out the GRUB problem and everything is fine but my main question is when i was partitioning the drives i gave the first drive a 1MB file for GRUB 
with no file system and i set the flag to biosgrub.

Now the swap i partitioned and gave it 16GB and set the flag to raid and then the main partition i just used what was left in space on the drive now and set the file ext4 and set to raid i repeated this for the second drive and the install went fine

my question is when i typed into the command line to find the status of the array it says array size 16GB is this correct what i am doing as I'm new to this so would be nice if someone could tell me I'm heading in the right 
direction :) before i continue and start creating folders and transferring over files, sorry about the long post normally i don't post i just try my best to figure out things and do my research but I'm a little lost so this is why I'm here and i would appreciate if someone could help me :) 

thanks

mark

---

### Post by TheFu on 2014-01-28
HW-RAID, FakeRAID or software RAID?

Also the output of **sudo parted -l** (wrapped in "code" tags please) will be helpful.

RAID is for high availability.
Backups are for everything else like virus recovery, corrupted DBs, corrupted files, after being cracked online, many things.  Backups are much more important than RAID - MUCH, MUCH, MUCH more important.

---

### Post by mark103 on 2014-01-28
sorry its software raid

---

### Post by dnemcanin2 on 2014-01-28
It' would be fine if you posted rotated picture.

With cat /proc/mdstat you should see yours active raid array's. If it's everything you want then is OK. But if you have 3 *3TB HDD, and using mdadn, why you didn't make RAID5. Space is equal to size of 2 disks and 3rd is for backup in case of ...

in picture is:
md0 ->16.8GB
md1->2967GB 
That  looks correct

---

### Post by mark103 on 2014-01-28
sorry ill do that now

---

### Post by mark103 on 2014-01-28
so you would recommend me to do RAID 5 instead and use the third 3TB drive for backup i cant do that in RAID 1 ? thanks for your reply

---

### Post by dnemcanin2 on 2014-01-28
RAID 5 use min 3 disks.
Every chunk is striped on two disks, and parity is calculated on the 3rd. (never on the same disk)
in example -> first data is striped on disk0 and disk1 -> parity on disk2
second data is striped on disk1 and disk2 -> parity on disk0
That's why you have better speed to write and read data, and also have security if one of disk goes out to rebuild your array.

---

### Post by mark103 on 2014-01-28
ok cool but if i use RAID 1 as its is now, i cant incorporate that third drive to back up RAID 1  ? it will have to be RAID 5 ? thanks

---

### Post by dnemcanin2 on 2014-01-28
You mean real backup? But why on the same machine? If something goes wrong you wouldn't have any of data.

But if you want to have one disk to backup your data you can make it like that. In that case you will one (same) file have on 3 places. disk0 -> mirrored to disk1 -> backup  to disk2

---

### Post by dnemcanin2 on 2014-01-28
With RAID 5 you don't have backup of your data. If you delete some video file it's deleted.

---

### Post by mark103 on 2014-01-28
ye fair point i guess, but its not hard to add to my server now that everything is installed ? the third 3TB drive to backup everything ?
thanks for all your help really appreciate it

---

### Post by dnemcanin2 on 2014-01-28
just add him at /etc/fstab to mount it on boot

---

### Post by mark103 on 2014-01-28
and thats it and then how would i configure it for backup and times it would backup sorry about all the questions im new to ubuntu

---

### Post by dnemcanin2 on 2014-01-28
In ubuntu you have backup deja dup.  -> sorry this is on desktop version

You can make your own script with tar to backup any data on your system (on internet is many tutorial how to make backup with tar)

---

### Post by mark103 on 2014-01-28
ok cool thanks for all your help :) youve been very helpful

---

