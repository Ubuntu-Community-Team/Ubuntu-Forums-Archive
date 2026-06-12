---
title: "Formated wrong harddisk partition, how do I recover my data?"
date: 2006-12-28
forum: General Help
---

### Post by TuxCrafter on 2006-12-28
Formated wrong harddisk partition, how do I recover my data?

Hello people,

I made a mistake today I unmounted a ReiserFS partition and formated it to ReiserFS how do I get all my data back?

(some more info, I never remounted it or write any data to it, and I have enough space else were to do make a dd image of the harddisk)

---

### Post by budgie9 on 2006-12-28
You Can't. Not without some clever software, which means a trip to a data recovery expert.
What does it say when you are formatting a disk, 'All data will be lost do you wish to continue?'  There may be some software out there on the web, but even so it will be a long process of recovery and something you may feel is futile.
Someone may know different but from my experiences in the past, it is not even worth the effort.

---

### Post by TuxCrafter on 2006-12-28
I did not change any data bit on the harddrive so all info is still there.
It was a fast format, that only rewrites something in the journaling of the reiserfs file system.
Please no post about it could be hard or imposable.
There must be someone out there that know the right command for this job.

---

### Post by dannyboy79 on 2006-12-28
dd_rescue?

---

### Post by dannyboy79 on 2006-12-28
> **budgie9 said:**
> 
Someone may know different but from my experiences in the past, **it is not even worth the effort**.

why would you make such a comment, if he has 10 years of data, pics, movies, and music spending a week to retrieve it is worth it. Think about what you say before you say it.

---

### Post by anaconda on 2006-12-28
> **TuxCrafter said:**
> I did not change any data bit on the harddrive so all info is still there.
It was a fast format

That is true. The data is still there. But I have never used ReiserFS, so Cant help you.

dd_rescue might be a good idea....

I dont know of any unformat command in linux. Like they have in windows world..

---

### Post by TuxCrafter on 2006-12-28
[http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)
ddrescue

reading that I got the feeling that its more for bad blocks/sectors and thats is not the case here.
I was more thing about rebuilding the ReiserFS journaling tree, but i don't now how

---

### Post by TuxCrafter on 2006-12-28
I found this command  maybe it will help me

```
reiserfsck --rebuild-tree -S -l /root/recovery.log /dev/sda1
```

I will read the man page of reiserfsck again and do a ddimage like this:

```
dd if=/dev/sda1 of=/mnt/sdc1/backup/ddimage_sda1.iso
```

That sould backup every sector in the harddisk (it is not a boot disk)

Then I will try the recovery. I will do this tomorrow i have a appointment now.

Every help is welcome!

---

### Post by dannyboy79 on 2006-12-28
> **TuxCrafter said:**
> [http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)
ddrescue

reading that I got the feeling that its more for bad blocks/sectors and thats is not the case here.
I was more thing about rebuilding the ReiserFS journaling tree, but i don't now how
incorrect, dd_rescue is way better than dd because it does the same thing that dd does but it won't stop if it comes to a badblock where dd will!

---

### Post by budgie9 on 2006-12-28
The reason for making such a comment is this. It was stated by Tuxcrafter that he had formatted his disk, he did not state that he had quick formatted a disk, there is a difference. 
I have 20 years experience in data recovery and from that experience I would say it is few if any disks that are recovered fully. in fact most are not. It needs a lot of good software and time to get data back in the form that you can access fully.
Quick formatyting is a different matter it can and often is recovered, if time is taken to do it correctly. If the tables are damaged then it means sector by sector recovery. Try it and see how easy it really is.
As I stated there are software packages out there that WILL recover data, but rarely all. So perhaps now you will see why data recovery is so expensive.

---

### Post by dannyboy79 on 2006-12-28
> **budgie9 said:**
> The reason for making such a comment is this. It was stated by Tuxcrafter that he had formatted his disk, he did not state that he had quick formatted a disk, there is a difference. 
I have 20 years experience in data recovery and from that experience I would say it is few if any disks that are recovered fully. in fact most are not. It needs a lot of good software and time to get data back in the form that you can access fully.
Quick formatyting is a different matter it can and often is recovered, if time is taken to do it correctly. If the tables are damaged then it means sector by sector recovery. Try it and see how easy it really is.
As I stated there are software packages out there that WILL recover data, but rarely all. So perhaps now you will see why data recovery is so expensive.
well I disagree with you here. If the drive is repeatedly written over with zeroes and random data, then at some point it will be impossible for anyone to recover the original data.

Even after one write-over the process is probably difficult and complicated.

Do note though that a normal format does not actually erase the data at all, it just sets the file allocation tables on the start of the drive to show the drive as empty therefore data recovery would be possible. Like I said, if someone has enough info they can't afford to lose, any amount of time is worth spending to retrieve that data and even if they can't do it, it obviously would be worth it to pay a recovery company to get it for them so your statement was just out of line.

---

### Post by dannyboy79 on 2006-12-28
here is an app that you would install on a windows machine and then according to this recover data from your reiserfs partitions. you could at least try the demo prior to actually buying it. this is of course the data is that important to you. [http://www.nucleustechnologies.com/ReiserFS-Linux-Partition-Recovery-Software.html](http://www.nucleustechnologies.com/ReiserFS-Linux-Partition-Recovery-Software.html)

---

### Post by TuxCrafter on 2006-12-28
Thank you for the link, to bad it does not work native on linux :-D

I read the man page of dd_rescue 
(to install dd_rescue use this command sudo apt-get install ddrescue)

This wat the man page says, it still looks to me that dd_rescue is voor crashed and bad devices. (dd itself has also special options for this I think dd_rescue is dd with some small modifications, don't now that for sure do)

 dd_rescue  is  a program that copies data from one file or block device
       to another, it is a tool to help you to save data from  crashed  parti&#8208;
       tion.   It  tries  to  read and if it fails it will go on with the next
       sectors, where tools like dd will  fail.  If  the  copying  process  is
       interrupted  by  the  user  it  is possible to continue at any position
       later.  It can copy backwards.

I will give the previous dd command a trial first I am familiar with it and have faith in it. If my recovery fails I can do a retry by restoring the dd image. (dd will make a 1:1 copy of every sector of the disk)

Tomorrow a next day folks, i will keep you posted

---

### Post by dannyboy79 on 2006-12-28
it won't if it gets to a bad sector. that's what dd_rescue is for.

---

### Post by TuxCrafter on 2006-12-29
Not much progress today: spent several hours trying to get my data back.

These are the steps I took.

```

sudo umount /dev/hda3

sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1

sudo dd if=/dev/hda3 conv=noerror of=/mnt/sda1/dd_image_hda3_29_12_06.iso
sudo losetup -f
sudo losetup /dev/loop0 /mnt/sda1/dd_image_hda3_29_12_06.iso
sudo reiserfsck --rebuild-tree --scan-whole-partition --logfile /mnt/sda1/recovery.log /dev/loop0

sudo mkdir /mnt/recovery
sudo mount /dev/loop0 /mnt/recovery

#recover your files
#find node numbers
ls -i /mnt/recovery/Desktop
sudo find /mnt/recovery/lost+found/ -name '*' -exec sudo grep -H -n "jelledejong@powercraft.nl" '{}' \;
sudo thunar /mnt/recovery/lost+found

sudo umount /mnt/recovery
sudo losetup -d /dev/loop0
```

But the files I need are not there. The logfile gives me this:

```

rebuild_semantic_pass: The entry [21766 283] ("afspraken.txt") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [21766 72165] ("Foto's") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [21766 21767] ("Kill Application.desktop") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [21766 19620] ("Start logger.desktop") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [21766 21768] ("Start Hellanzb.desktop") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [21766 92717] ("eUYaWhoNsWdYq1zIGONKig==.jpg") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [21766 23833] ("logfile.txt") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [21766 21821] ("open staande facturen.txt") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [21766 5122] ("refcard-en-a4.pdf") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [21766 40] ("Introduction.odt") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [21766 76287] ("Beginning CSS Web Development: From Novice to Professional") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [21766 21773] ("linux problems.txt") in directory [2 21766] points to nowhere - is removed
rewrite_file: 2 items of file [21766 76609] moved to [21766 35394]
The entry [21766 76609] ("DIY Beamer - ®Jelle de Jong - 26-11-06 - v1.3.xls") in directory [2 21766] updated to point to [21766 35394]
rebuild_semantic_pass: The entry [21766 33422] ("PowerCraft Technology - Financieel Plan v0.1.odt") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [21766 21774] ("Pause Hellanzb.desktop") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [21766 60] ("kosten exclusiv.txt") in directory [2 21766] points to nowhere - is removed
rewrite_file: 2 items of file [21766 76602] moved to [21766 35395]
The entry [21766 76602] ("DIY_Beamer - ®Jelle de Jong - 15-02-05 - CAD.xls") in directory [2 21766] updated to point to [21766 35395]
rebuild_semantic_pass: The entry [21766 105] ("Modulaire Software Interface voor Remote Controller.doc") in directory [2 21766] points to nowhere - is removed
rebuild_semantic_pass: The entry [4120 4373] ("info.txt") in directory [2 21766] points to nowhere - is removed
```

It does find files and also repairs them but these files and folders I really need there were on my Desktop and I changed them daily.

---

