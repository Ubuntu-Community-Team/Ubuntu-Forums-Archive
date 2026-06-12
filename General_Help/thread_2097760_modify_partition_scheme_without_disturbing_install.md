---
title: "modify partition scheme without disturbing installation."
date: 2012-12-24
forum: General Help
---

### Post by techvish81 on 2012-12-24
i've attached screenshots of my current partitioning scheme with a 60gb ssd and a 500gb hdd.

i'm facing problem with /tmp mounted on a 7gb partition on hdd, which runs out of space frequently,  can i put it in the partition for /home which is 100+gb?

if yes, how?  or is there any other way to solve this issue?

---

### Post by oldfred on 2012-12-24
With SSDs there is a lot of discussion on what should be on SSD, what on hard drive and even mounting tmp in RAM.

Somewhat follow Herman as he was one of the first to post instructions on installing to SSD.
       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

    
But I do have a swap partition on rotating drive, but it is almost never used with my 4GB of RAM. I do not consider my 4GB of RAM to be enough to mount temporary folders into RAM as some suggest.

I have / & /home on my SSD, but almost all data in /home is in my data partitions on my rotating drive and data folders linked back to /home. I use about 9GB of my 25GB / partition on my SSD with 2GB for /home. My /home would be only 250KB, but .wine for Picasa uses a lot of space.

---

### Post by techvish81 on 2012-12-24
actually i'm very much satisfied with my current setup , the only problem is /tmp mounted on a separate 7gb hdd partition, i just want to either grow the partition or mount /tmp under the parttion for /home . is it possible or not?

---

### Post by oldfred on 2012-12-24
You can shrink /home since it is inside the extended partition and create a newer larger /tmp. Then use that partition as /tmp.

To expand current /tmp would mean moving current /home which is a bigger task. I generally do not like moving partitions, but it can be done. Best to have really good backups and depending on amount of data it may take a long time.

---

### Post by techvish81 on 2012-12-25
how much /tmp is enough for smooth operation of tasks like video encoding, graphics designing, creating , editing pdf  etc..

---

