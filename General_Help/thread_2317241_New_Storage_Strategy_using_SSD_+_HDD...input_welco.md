---
title: "New Storage Strategy using SSD + HDD...input welcomed"
date: 2016-03-14
forum: General Help
---

### Post by Magellan on 2016-03-14
Hi,

I've decided to make some upgrades to my pc running Ubuntu 14.04.

First off is to bump the memory up to 8GB (currently at 2GB). That's a pretty easy decision.

Next up is to re-build my storage, and here's where I'd like some input.

My uses for this machine are as follows:
[LIST]
[*]General home pc (browsing, email, dedit docs, etc).  Used by the whole family.
[*]Video Capture, editing, and storage
[*]Music rip and storage (I transfer to another device for streaming
[*]Photo editing and storage
[/LIST]

My current plan (wiling to change):
500GB SSD with Root, Swap, and Home.  I've read a lot about swap on an SSD and it seems like it's not much of an issue anymore.  I'm hoping that with 8GB of mem and reducing swappiness this will be OK.  

1TB HDD used to backup the SSD.  I'll use Deja Dup for this.  I'm also considering partitioning this drive in which case, I could put the Swap space here and also create a working partition for files I"m editing to reduce the write activity on the SSD.

2 X 3TB HDD in RAID-1 for storage of my media files (pics, music, videos).

Thoughts?  Some specific questions I have:
[LIST]
[*]Is 500GB overkill for the SSD?  I have a 320GB HDD now for root, swap, and home and I fill it every now and then when working with video files.
[*]Is Swap on the SSD a concern?  I'm thinking no, but I probalby woldn't be giving up much if I put it on the SSD.
[*]How much HDD needed to support backing up the SSD?  I've been thinking 1.5X should suffice to support some incremental backups.  Will probably back up daily
[/LIST]

Also, I do have an Amazon Cloud Drive.  I'm on the unlimited free trial, but am not sure if I'll pay for it when that expires due to the lack of Linux support.  I don't really need the access anywhere aspect.  Most things I need to get to from anywhere are small enough for my DropBox or Evernote accounts.  I get free photo storage at AWS as a Prime member and any videos I want to share I put on YouTube.  Music goes on a thumb drive.

I haven't bought anything yet, but am itching to ;-)

Thanks,

James

---

### Post by oldfred on 2016-03-15
My main desktop system had a 120GB SSD with two installs of Ubuntu, current working(14.04 will become 16.10) and a testing/new(was 15.10, now 16.04). HDD then has several more installs.

I do not backup / (root), but do backup some settings in /etc that I manually have edited. I copy those into /home so my standard backup of /home includes that. My /home is about 2GB with most that as .wine for Picasa. But all data is on HDD.
       Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413) 

    
While I do backup some data on each drive to another drive, I do not consider that as a real backup. If file is changed, but I want old version it otherwise is overwritten. So I use DVDs, flash drives or other image copies of most critical data.

       [http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)

---

### Post by Eva_Bouwman on 2016-03-19
I bought also a new ssd and I decided to treat it with care ;-)

With my installation I partitioned manualy and created root on my ssd and swap and home on my hdd, 
This is working very well os is responding very quickly.

On a learningsite from oracle I red a suggestion from a oracle expert you also can partition /var/spool /var/mail /usr/local /srv and /opt separately, I did this on my laptop during installation, also working very well. Installed / on ssd with /boot and on hdd I made /var/spool /var/mail /opt /srv /usr/local /home and swap. This site suggested to separate var and usr as far as possible so I did. Cant find this site now but will add it tonight when I really have enough time. 

I used gpt as partition table so all could be primary partitions and I made /boot a ext2 partition while others are ext4. I red about var better being ext3 in some post on this site, but this post was related with installing on ssd, have not find any evidence it also applies with installing on a hdd.

Hope it helps if any one else has some though I'll be glad to hear (sorry for my bad English)

---

### Post by Bucky Ball on 2016-03-19
OS on the SSD, /home and /swap on the HDD. 

I'm in the same school of thought as oldfred on one thing, though. I have symlinks in the default /home directory inside the / partition which link to the real data on another partition, on some machines another partition on another drive.

You want to put all OSs on the SSD, /swap on the HDD (as /swap really just takes up space as, depending on how much RAM you have, it will rarely get used anyway.)

Some go futher and put other folders - /boot, /var, /tmp - on the HDD. I wouldn't bother, but to each their own.

If you're backing up a 60Gb partition on the SSD you will need a 60Gb partition to back it up on the HDD if that is what you mean by your last question. :-k

@Eva_Bouwman: Be aware that having a /boot partition, on and SSD or HDD, can be more hassle than it's worth unless you have a specific reason for one. They fill up and that is that. You need to remember to clean out and delete old kernels on a regular basis or one day you machine will simply stop with an error message telling you boot is full. While having /var, /opt etc on the HDD was popular back when people were worried about too many read/writes on the SSD, SSDs are more robust now and splitting the root partition up over the SSD and HDD is not much of a 'thing' anymore as it can sometimes be problematic.

---

