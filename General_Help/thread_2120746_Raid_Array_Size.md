---
title: "Raid Array Size"
date: 2013-02-27
forum: General Help
---

### Post by The Big Baddie on 2013-02-27
Hi, new to ubuntu but I wanted to make a media server I could access from my home or over the internet and during my research I was led to believe ubuntu server was the route to go. I have just completed creating a raid array of 5 2TB HDDs but the sizing looks a little off to me. I was wondering if someone had experienced a similar issue and could point me in the right direction. 

It is a raid 5 array of 10 TB so there should be roughly 8TB available as many of you know.

It is telling me the raid array is as follows
NAME     SIZE   USED  AVAIL
/dev/md0 7.3TB  172M  6.9TB

---

### Post by TheFu on 2013-02-27
Ubuntu is like any other Linux, so yes, it can do what you want.
To understand HDD sizes, first you need to understand that 2TB is not 2TB. It is the difference between 1024 and 1000 bytes. That is 2.4% difference for every 1000 bytes. 

2,000,000,000 bytes is 2TB to the HDD manufacturers, but 1,952,000,000 Bytes to the rest of the world. That isn't technically correct, but you get the idea.

Then there is the overhead of the file system used.
On my RAID1 2TB setup, the available storage after putting a file system on it is, 1,912,523,780 bytes.  In 1024B/KB that converts to 1.8TB.

1.8TB x 4 = 7.2TB.  Good enough?

There are wikipedia articles that do a good job explaining this stuff.  Much better than I can.

---

### Post by alarme on 2013-02-27
Creating a new filesystem ext2, ext3 o ext4 with default options, mkfs reserves 5% of space for root user.
This is convenient for system area, but not for independent (non-sytem) storage partitions.

Check mkfs man page option to override this.

---

### Post by The Big Baddie on 2013-02-27
That would make sense if I had 4 2TBs but I have 5 so
 
1.8*5=/=7.2 but 9
 
> **TheFu said:**
> Ubuntu is like any other Linux, so yes, it can do what you want.
To understand HDD sizes, first you need to understand that 2TB is not 2TB. It is the difference between 1024 and 1000 bytes. That is 2.4% difference for every 1000 bytes. 
 
2,000,000,000 bytes is 2TB to the HDD manufacturers, but 1,952,000,000 Bytes to the rest of the world. That isn't technically correct, but you get the idea.
 
Then there is the overhead of the file system used.
On my RAID1 2TB setup, the available storage after putting a file system on it is, 1,912,523,780 bytes. In 1024B/KB that converts to 1.8TB.
 
1.8TB x 4 = 7.2TB. Good enough?
 
There are wikipedia articles that do a good job explaining this stuff. Much better than I can.

---

### Post by Impavidus on 2013-02-27
5*2TB=10TB, RAID 5 with 5 disks, so 1-1/5=80% space efficient, gives 8TB. Assuming these are real TBs of 1000^4 bytes, we can convert to TiBs of (2^10)^4 bytes by division by 1.024^4, giving 8/1.0995=7.276TiB, exactly what you found out. To be sure, check the exact number of bytes available, the 13 digit number. 5% reserved for root is no way to explain the 9.95% difference.

Remember, to the entire world "tera" means 10^12 times the base unit, only the computer guys are confused. They thought powers of 1024 to be more convenient as everything in computers comes in powers of 2. Well, it doesn't.

---

### Post by The Big Baddie on 2013-02-27
I understand it now. Thanks.

---

