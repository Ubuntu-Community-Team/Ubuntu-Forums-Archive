---
title: "Hard drive recovery"
date: 2014-02-02
forum: General Help
---

### Post by vangend.robert on 2014-02-02
Hello All,

I have Ubuntu Server 12.04 running on a physical machine as my data server. In this server I had (until about a month ago) 2 physical hard drives (one for the 12.04 OS and one for data).  

My desktop machine is a windows 7 machine.  I have an external usb drive (H: drive) connected to the windows 7 machine. On the windows machine I have Syncbackpro (a commercial backup solution for the windows environment) running. Synbackpro backs up  the data from the server to a Western Digital MyBook World white light. I have all the various directories on the server mapped on my windows machine.

About a month ago I installed a new hard drive on the server. _**I mounted this hard drive from the command line**_. 

After this I copied all my personal data onto the server (mapped as V: drive in windows) and also setup an incremental backup with Synpackpro to run 3 hourly incrementals with a full system dump (level 0) on the 1st of every month. This data is about 380GB in total. I did not want to overload the WD White light , so I ran the backup of this data to my H: drive (the usb connected to my windows machine). 

Syncbackpro will delete whatever backup has already been created when it cycles around through the next month. This means that I should in theory be able to revert to any changes in 3 hour increments at any point over a 1 month period. The intention is to dump all the data on the last day of the month onto another external usb connected to the server this time for removal and off site storage.

Today I had to do some server maintenance and after this restarted the server. When I restarted the machine, my V: drive was completely empty. At first I thought that this would not be  problem, because I could simply revert to my backups. To my horror the H: drive is also completely empty. Which means that ALL my data might be lost. Fortunately I have a backup that is about a month old and could revert to this, but this means I have lost a months worth of data.

I think that the problem is that when I mounted from the command line, and restarted this mount information was lost. I have tried to mount the same drive again (after restart) and it still seems empty. I have also added this drive to my fstab (which I should have done in the first place). Also no luck.

When I do df on /srv/pers (dev/sdd1) it says that the usage is only 1%. My data was about 380GB, so clearly it is not there anymore (or maybe at least not visible.)

My question is, is there anyway to remount this hard drive in such a way that this data can be recovered?

Regards
Rob

---

